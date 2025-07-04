# Documentación del Perfil `.bashrc` Optimizado

Este documento explica el funcionamiento del archivo `.bashrc`, diseñado para un flujo de trabajo de desarrollo eficiente, limpio y moderno, basado en la contenerización de herramientas con Docker.

## Filosofía Principal

El objetivo de esta configuración es mantener el sistema operativo anfitrión (`host`) lo más **limpio y minimalista** posible. En lugar de instalar herramientas como Node.js, npm, etc., directamente en el sistema, se utilizan contenedores de Docker efímeros para ejecutar sus comandos. Esto ofrece:
- **Aislamiento:** Evita conflictos de versiones y dependencias globales.
- **Consistencia:** El entorno de desarrollo es idéntico sin importar la máquina.
- **Limpieza:** No se "contamina" el sistema anfitrión con paquetes y binarios.

---

## Secciones del `.bashrc`

### 🧠 Historia y Rendimiento
Configuraciones estándar para mejorar la gestión del historial de comandos.
- `HISTSIZE`: Número de comandos a recordar en la sesión actual.
- `HISTFILESIZE`: Número de comandos a guardar en el archivo `~/.bash_history`.
- `HISTCONTROL`: Evita duplicados en el historial.
- `shopt -s histappend`: Añade el historial nuevo al final del archivo, en lugar de sobrescribirlo.

### 🎨 Prompt de Terminal (`PROMPT_COMMAND`)
Esta es una de las características más potentes. `PROMPT_COMMAND` es una variable especial que ejecuta su contenido **antes** de mostrar el prompt.

1.  **`auto_activate_venv`**:
    - Busca un entorno virtual de Python (`.venv` o `venv`) en el directorio actual y en sus directorios padres.
    - Si lo encuentra, lo **activa automáticamente**.
    - Si sales del directorio del proyecto, lo **desactiva automáticamente**.

2.  **`setup_custom_prompt`**:
    - Muestra el nombre del `venv` de Python si está activo.
    - Muestra la ruta actual (`\w`).
    - **Detecta si estás en un repositorio Git** y muestra información crucial:
        - Nombre de la rama actual.
        - `⇡N`: Número de commits locales listos para hacer `push`.
        - `⇣N`: Número de commits remotos listos para hacer `pull`.
        - `●N`: Número de archivos en *staging* (listos para `commit`).
        - `✚N`: Número de archivos modificados pero no en *staging*.
        - `…N`: Número de archivos sin seguimiento (*untracked*).

### 🐳 Node.js Dockerizado (`dnode`)

Esta es la joya de la corona de la configuración.

- **Función `dnode`**: Es el motor principal. Ejecuta un contenedor `node:<version>-alpine`.
- **Alias**: Los comandos `node`, `npm`, `npx` y `yarn` son alias que llaman a la función `dnode`.

**¿Cómo funciona?**
1.  Al escribir `npm install`, en realidad estás ejecutando `dnode npm install`.
2.  `dnode` busca un archivo `.nvmrc` en tu directorio. Si existe, usa la versión de Node.js especificada.
3.  Si no hay `.nvmrc`, busca un archivo `package.json` y lee la versión del campo `engines.node`.
4.  Si no encuentra ninguno, usa la versión `20` por defecto.
5.  Lanza un contenedor Docker con la versión correcta de Node.js.

**Mejoras Clave Implementadas:**
- **`--rm`**: El contenedor se elimina automáticamente al terminar, no deja basura.
- **`-u "$(id -u):$(id -g)"`**: **(¡MUY IMPORTANTE!)** Ejecuta el proceso dentro del contenedor con tu mismo ID de usuario y grupo del host. Esto asegura que los archivos creados por `npm install` (como `node_modules`) tengan los **permisos correctos** y no necesites `sudo` para modificarlos.
- **`-v "$PWD":/app`**: Monta tu directorio actual dentro del contenedor en `/app`.
- **`-v ~/.npm:/root/.npm`**: Monta tu caché local de `npm` en el contenedor para no tener que descargar paquetes una y otra vez.

### 🔧 Otras Utilidades y Alias

- **Alias de conveniencia**: Atajos para `python3`, `ls`, `cd`, `git`, etc.
- **Alias de Docker**: Atajos para los comandos más comunes de Docker y Docker Compose (`dps`, `dcupd`, `dcleanall`).
- **Función `d-preheat`**: Una nueva función para optimizar el rendimiento. Ejecútala para descargar las imágenes de Docker más comunes que usas. La próxima vez que `dnode` necesite una de esas versiones, el inicio será instantáneo.

### 🛠️ Integraciones de Herramientas

Configuraciones para que herramientas externas como **GitHub CLI** (`gh`) y **Gemini CLI** funcionen correctamente, incluyendo el autocompletado y la gestión de claves de API a través de un archivo `~/.env`.