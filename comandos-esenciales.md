# Comandos Esenciales de Terminal en Linux/Ubuntu

Este documento recopila los comandos más utilizados en la línea de comandos de Linux/Ubuntu, organizados por categorías para facilitar su consulta y aprendizaje.

---

## Navegación y gestión de archivos

| Comando                | Descripción                                      |
|------------------------|--------------------------------------------------|
| `ls`                   | Lista archivos y carpetas en el directorio actual|
| `ls -l`                | Lista detallada de archivos                      |
| `ls -a`                | Incluye archivos ocultos                         |
| `cd <directorio>`      | Cambia de directorio                             |
| `pwd`                  | Muestra el directorio actual                     |
| `mkdir <nombre>`       | Crea un nuevo directorio                         |
| `rmdir <nombre>`       | Elimina un directorio vacío                      |
| `rm <archivo>`         | Elimina un archivo                               |
| `rm -r <directorio>`   | Elimina un directorio y su contenido             |
| `cp <origen> <destino>`| Copia archivos o carpetas                        |
| `mv <origen> <destino>`| Mueve o renombra archivos o carpetas             |
| `touch <archivo>`      | Crea un archivo vacío                            |
| `cat <archivo>`        | Muestra el contenido de un archivo               |
| `less <archivo>`       | Visualiza archivos de forma paginada             |
| `head <archivo>`       | Muestra las primeras líneas de un archivo        |
| `tail <archivo>`       | Muestra las últimas líneas de un archivo         |

---

## Gestión de procesos y sistema

| Comando                | Descripción                                      |
|------------------------|--------------------------------------------------|
| `ps aux`               | Lista todos los procesos                         |
| `top`                  | Monitoriza procesos en tiempo real               |
| `htop`                 | Monitor avanzado de procesos (si está instalado) |
| `kill <PID>`           | Finaliza un proceso por su ID                    |
| `killall <nombre>`     | Finaliza procesos por nombre                     |
| `df -h`                | Muestra uso de disco                             |
| `du -sh <directorio>`  | Muestra tamaño de un directorio                  |
| `free -h`              | Muestra uso de memoria                           |
| `uptime`               | Tiempo encendido del sistema                     |
| `uname -a`             | Información del sistema                          |
| `whoami`               | Usuario actual                                   |
| `id`                   | Muestra información del usuario actual           |

---

## Red y descargas

| Comando                 | Descripción                                      |
|-------------------------|--------------------------------------------------|
| `ping <host>`           | Comprueba conectividad con un host               |
| `curl <url>`            | Descarga o consulta recursos web                 |
| `wget <url>`            | Descarga archivos desde la web                   |
| `ifconfig`              | Muestra configuración de red                     |
| `ip a`                  | Muestra interfaces de red                        |
| `ssh <usuario>@<host>`  | Conexión remota por SSH                          |
| `scp <origen> <destino>`| Copia archivos por SSH                           |

---

## Permisos y usuarios

| Comando                             | Descripción                                 |
|-------------------------------------|---------------------------------------------|
| `chmod <permisos> <archivo>`        | Cambia permisos de archivo                  |
| `chown <usuario>:<grupo> <archivo>` | Cambia propietario de archivo               |
| `sudo <comando>`                    | Ejecuta un comando como superusuario        |
| `su <usuario>`                      | Cambia de usuario                           |
| `passwd`                            | Cambia la contraseña del usuario actual     |

### Ejemplos de permisos con `chmod`

| Comando                | Descripción                                                       |
|------------------------|-------------------------------------------------------------------|
| `chmod 755 archivo`    | Permiso total para el propietario, lectura y ejecución para otros |
| `chmod 644 archivo`    | Lectura y escritura para el propietario, solo lectura para otros  |
| `chmod +x archivo`     | Añade permiso de ejecución                                        |
| `chmod -x archivo`     | Quita permiso de ejecución                                        |
| `chmod u+r archivo`    | Añade permiso de lectura al propietario                           |
| `chmod go-w archivo`   | Quita permiso de escritura a grupo y otros                        |

### Ejemplos de permisos con `chown`

| Comando                        | Descripción                                      |
|--------------------------------|--------------------------------------------------|
| `chown usuario archivo`        | Cambia el propietario del archivo                |
| `chown usuario:grupo archivo`  | Cambia propietario y grupo del archivo           |
| `chown -R usuario:grupo dir/`  | Cambia propietario y grupo de forma recursiva    |

---

## Instalación y actualización de paquetes

| Comando                      | Descripción                               |
|------------------------------|-------------------------------------------|
| `sudo apt update`            | Actualiza la lista de paquetes            |
| `sudo apt upgrade`           | Actualiza los paquetes instalados         |
| `sudo apt install <paquete>` | Instala un paquete                        |
| `sudo apt remove <paquete>`  | Elimina un paquete                        |
| `sudo apt autoremove`        | Elimina dependencias no necesarias        |

---

## Formas típicas de instalar paquetes en Ubuntu

### Desde el repositorio oficial (APT)

```bash
sudo apt update
sudo apt install <paquete>
```

### Descargando y ejecutando binarios

- **Con wget:**

```bash
wget https://ejemplo.com/archivo.deb
sudo dpkg -i archivo.deb
sudo apt-get install -f  # Corrige dependencias si es necesario
```

- **Con curl:**

```bash
curl -LO https://ejemplo.com/archivo.deb
sudo dpkg -i archivo.deb
```

### Instalación desde scripts remotos

```bash
curl -fsSL https://ejemplo.com/instalador.sh | bash
```

### Instalación con Snap

```bash
sudo snap install <paquete>
```

### Instalación con Flatpak

```bash
flatpak install <paquete>
```

---

## Utilidades varias

| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `history`                               | Muestra el historial de comandos                 |
| `clear`                                 | Limpia la pantalla de la terminal                |
| `man <comando>`                         | Muestra el manual de un comando                  |
| `echo <texto>`                          | Imprime texto en la terminal                     |
| `date`                                  | Muestra la fecha y hora actuales                 |
| `cal`                                   | Muestra el calendario                            |
| `tar -czvf archivo.tar.gz <dir>`        | Comprime un directorio en tar.gz                 |
| `tar -xzvf archivo.tar.gz`              | Descomprime un archivo tar.gz                    |

---

> _Documento generado automáticamente. Puedes personalizarlo y ampliarlo según tus necesidades._
