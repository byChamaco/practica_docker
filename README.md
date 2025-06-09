# Proxecto Docker con mounts e volume

## Descripción do proxecto

Este proxecto contén unha arquitectura web básica composta por tres servizos:

- **Frontend** que amosa unha páxina ('index.html')
- **Backend** desenvolvido con Python
- **Base de datos** usando PostgreSQL

O proxecto é unha demostración da integración de servizos usando 'Docker Compose' e comprobar a persistencia de datos mediante volumes.

---

## Composición dos servizos

| Servizo   | Tecnoloxía         | Descrición                                          					 |
|-----------|--------------------|------------------------------------------------------------------------------------------|
| `frontend`| `nginx:alpine`     | Serve a páxina HTML estática usando un bind mount desde `./frontend`     		 |
| `backend` | `Flask` en `Debian`| Código Python cargado vía bind mount sen recompilar tras cada cambio e usando Dockerfile |
| `db`      | `postgres:15`      | Base de datos SQL con volume persistente            					 |

---


