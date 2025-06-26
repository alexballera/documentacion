# Comandos y Alias Esenciales de Docker

Este documento recopila los comandos más utilizados para la gestión de Docker y Docker Compose, organizados por secciones temáticas. Incluye una sección de alias personalizados y un resumen conceptual para usuarios nuevos y avanzados.

---

## 🐳 ¿Qué son los Contenedores e Imágenes de Docker?

### 📦 Imagen de Docker
Una **imagen de Docker** es como una "plantilla" que contiene el sistema operativo base, aplicaciones, dependencias y configuraciones necesarias para ejecutar una aplicación.

**Analogía**: Es como una receta de cocina que especifica todos los ingredientes y pasos necesarios.

### 🏃‍♂️ Contenedor de Docker
Un **contenedor de Docker** es una instancia en ejecución de una imagen. Es un proceso aislado, ligero y portable, que contiene la aplicación y todas sus dependencias.

**Analogía**: Es como el plato preparado siguiendo la receta (imagen).

---

## 📋 Comandos Más Comunes de Docker

### 🔍 Consulta y monitoreo
| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker ps`                             | Ver contenedores en ejecución                    |
| `docker ps -a`                          | Ver todos los contenedores (incluidos detenidos) |
| `docker images`                         | Ver todas las imágenes                           |
| `docker system df`                      | Ver información del sistema Docker               |
| `docker logs <container>`               | Ver logs de un contenedor                        |
| `docker stats`                          | Ver estadísticas de uso de recursos              |
| `docker stats <container>`              | Estadísticas de un contenedor específico         |
| `docker top <container>`                | Ver procesos en ejecución en un contenedor       |

---

### 🚀 Gestión de contenedores
| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker run <imagen>`                   | Ejecutar un contenedor                           |
| `docker run -d <imagen>`                | Ejecutar en segundo plano                        |
| `docker run -p 8080:80 <imagen>`        | Ejecutar con puerto mapeado                      |
| `docker run --name mi_contenedor <img>` | Ejecutar con nombre personalizado                |
| `docker start <container>`              | Iniciar un contenedor detenido                   |
| `docker stop <container>`               | Detener un contenedor                            |
| `docker restart <container>`            | Reiniciar un contenedor                          |
| `docker rm <container>`                 | Eliminar un contenedor                           |
| `docker rm -f <container>`              | Eliminar un contenedor en ejecución (forzar)     |

---

### 🖼️ Gestión de imágenes
| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker pull <imagen>`                  | Descargar una imagen                             |
| `docker build -t <nombre> .`            | Construir una imagen desde un Dockerfile         |
| `docker rmi <imagen>`                   | Eliminar una imagen                              |
| `docker rmi -f <imagen>`                | Eliminar una imagen forzadamente                 |
| `docker tag <origen> <destino>`         | Etiquetar una imagen                             |

---

### 🧹 Limpieza masiva
| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker stop $(docker ps -q)`           | Detener todos los contenedores                   |
| `docker rm $(docker ps -aq)`            | Eliminar todos los contenedores                  |
| `docker rmi $(docker images -q)`        | Eliminar todas las imágenes                      |
| `docker rmi $(docker images -q) --force`| Eliminar todas las imágenes forzadamente         |
| `docker system prune -a`                | Limpiar todo el sistema                          |
| `docker container prune`                | Limpiar solo contenedores detenidos              |
| `docker image prune`                    | Limpiar solo imágenes no utilizadas              |
| `docker volume prune`                   | Limpiar volúmenes no utilizados                  |

---

### 🔧 Interacción y utilidades
| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker exec <container> <cmd>`         | Ejecutar un comando en un contenedor             |
| `docker exec -it <container> /bin/bash` | Acceder a la terminal de un contenedor           |
| `docker cp <container>:/ruta /local`    | Copiar archivos desde un contenedor              |
| `docker cp /local <container>:/ruta`    | Copiar archivos hacia un contenedor              |
| `docker inspect <container|imagen>`     | Inspeccionar un contenedor o imagen              |

---

### 🐙 Docker Compose (multi-contenedor)
| Comando                                 | Descripción                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker compose up`                     | Iniciar servicios definidos en docker-compose.yml |
| `docker compose up -d`                  | Iniciar servicios en segundo plano               |
| `docker compose down`                   | Detener servicios                                |
| `docker compose logs`                   | Ver logs de todos los servicios                  |
| `docker compose up --build`             | Reconstruir e iniciar servicios                  |

---

## 💡 Consejos Útiles

1. **Usar nombres descriptivos**: Siempre nombra tus contenedores con `--name`
2. **Limpiar regularmente**: Usa `docker system prune` para liberar espacio
3. **Revisar logs**: Usa `docker logs` para diagnosticar problemas
4. **Mapear puertos**: Usa `-p` para acceder a aplicaciones desde el host
5. **Usar volúmenes**: Para persistir datos usa `-v` o `--mount`

---

## ⚡ Alias Docker básicos

```bash
alias d='docker'
alias dc='docker compose'
alias dps='docker ps'
alias dpsa='docker ps -a'
alias di='docker images'
alias dv='docker volume ls'
alias dn='docker network ls'
alias dcup='docker compose up'
alias dcupd='docker compose up -d'
alias dcdown='docker compose down'
alias dcbuild='docker compose build'
alias dclogs='docker compose logs -f'
alias dcps='docker compose ps'
alias dexec='docker exec -it'
alias dclean='docker system prune -f && docker volume prune -f'
alias dcleanall='docker system prune -a -f --volumes'
```

---

> _Documento generado automáticamente. Puedes personalizarlo y ampliarlo según tus necesidades._
