# BBVIDEO

Base local con Django, Django REST Framework y PostgreSQL.

## Iniciar (PowerShell)

```powershell
Copy-Item .env.example .env
docker compose up --build -d
docker compose exec django python manage.py createsuperuser
```

Si `.env` ya existe, conserva sus valores. El servidor aplica las migraciones al iniciar.

Admin: http://localhost:8001/admin/

Para cambiar el puerto local, edita `DJANGO_PORT` en `.env`.

## Comandos

```powershell
docker compose logs -f django
docker compose exec django python manage.py check
docker compose exec django python manage.py migrate
docker compose down
```

`docker compose down` conserva los datos. Agregar `-v` elimina el volumen de esta base de datos.

Compose usa el proyecto `bbvideo`, con su propia red y volumen. PostgreSQL queda disponible dentro de esa red, sin publicar un puerto en Windows.

Esta configuración usa el servidor de desarrollo de Django. Todavía no incluye APIs de negocio, Redis, Celery ni procesamiento de video.
