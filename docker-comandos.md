# Comandos y Alias Esenciales de Docker

Este documento recopila los comandos más utilizados para la gestión de Docker y Docker Compose, organizados por secciones temáticas. Incluye una sección de alias personalizados para agilizar el trabajo diario.

---

## Gestión de contenedores

| Comando                        | Descripción                                      |
|-------------------------------|--------------------------------------------------|
| `docker ps`                   | Lista los contenedores en ejecución              |
| `docker ps -a`                | Lista todos los contenedores (incluidos detenidos)|
| `docker start <id/nombre>`    | Inicia un contenedor detenido                    |
| `docker stop <id/nombre>`     | Detiene un contenedor en ejecución               |
| `docker restart <id/nombre>`  | Reinicia un contenedor                           |
| `docker rm <id/nombre>`       | Elimina un contenedor detenido                   |
| `docker exec -it <id> bash`   | Abre una terminal bash en un contenedor activo   |
| `docker logs -f <id/nombre>`  | Muestra logs en tiempo real de un contenedor     |

---

## Gestión de imágenes

| Comando                        | Descripción                                      |
|-------------------------------|--------------------------------------------------|
| `docker images`                | Lista todas las imágenes locales                 |
| `docker pull <imagen>`         | Descarga una imagen desde Docker Hub             |
| `docker build -t <nombre> .`   | Construye una imagen desde un Dockerfile         |
| `docker rmi <imagen>`          | Elimina una imagen local                         |

---

## Gestión de volúmenes y redes

| Comando                        | Descripción                                      |
|-------------------------------|--------------------------------------------------|
| `docker volume ls`             | Lista todos los volúmenes                        |
| `docker volume rm <volumen>`   | Elimina un volumen                               |
| `docker network ls`            | Lista todas las redes                            |
| `docker network rm <red>`      | Elimina una red                                  |

---

## Docker Compose

| Comando                              | Descripción                                      |
|--------------------------------------|--------------------------------------------------|
| `docker compose up`                  | Levanta los servicios definidos en docker-compose.yml |
| `docker compose up -d`               | Levanta los servicios en segundo plano           |
| `docker compose down`                | Detiene y elimina los servicios                  |
| `docker compose build`               | Construye las imágenes de los servicios          |
| `docker compose logs -f`             | Muestra logs en tiempo real de los servicios     |
| `docker compose ps`                  | Lista el estado de los servicios                 |

---

## Limpieza y mantenimiento

| Comando                                        | Descripción                                      |
|-----------------------------------------------|--------------------------------------------------|
| `docker system prune -f`                      | Elimina recursos no utilizados (contenedores, redes, imágenes) |
| `docker system prune -a -f --volumes`         | Limpieza profunda, incluye volúmenes e imágenes sin usar |
| `docker volume prune -f`                      | Elimina volúmenes no utilizados                   |

---

## Alias Docker básicos

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
