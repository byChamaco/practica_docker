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

## Comando principais para executar o proxecto

Primeiro de todo colocámonos dentro da carpeta do proxecto para poder executar os seguintes comandos.

### 1. **Iniciar os servizos**

```bash
docker compose up
```

Este comando constrúe a imaxe do backend e arranca os tres contedores.

---

### 2. **Acceder á base de datos manualmente**

Primeiro executamos o seguinte comando para coñecer o nome do contedor da base de datos.
```bash
docker ps
```

Logo conectámonos o contedor con:
```bash
docker exec -it <nome_contenedor_db> psql -U user -d mydb
```

E por último para insertar datos para comprobar a persistencia executamos:
```bash
INSERT INTO visitas (ip) VALUES ('168.28.04.13');
```
---

### 3. **Deter os servizos**

```bash
docker compose down
```

Isto para todos os servizos pero **conserva os datos** da base de datos grazas ao volume `db_data`.

---

© 2025 - Desenvolvido por Oscar Blanco Lorenzo
