# Backend Simulador de Negocios (Bolivia)

Backend academico en Django + Django REST Framework + PostgreSQL para simulacion de decisiones empresariales.

## Funcionalidades implementadas

- Autenticacion por email con JWT (registro, login, refresh, perfil).
- Roles de usuario: `estudiante` y `profesor`.
- CRUD de escenarios economicos.
- Envio de decisiones por estudiante/profesor.
- Calculo de resultados economicos simulados.
- Exportacion de reportes en JSON y CSV.
- Documentacion OpenAPI con Swagger y ReDoc.
- Panel de administracion Django para usuarios, escenarios, decisiones y resultados.
- Contenedores Docker para despliegue.

## Modelos principales

- `Usuario`: email, rol.
- `Escenario`: nombre, descripcion, inflacion, impuestos, tipo de cambio, demanda, oferta.
- `Decision`: usuario, escenario, produccion, inversion, precios, contratacion.
- `Resultado`: usuario, escenario, decision, ganancias, perdidas, PIB simulado, inflacion simulada.

## Configuracion local

1. Crear entorno virtual e instalar dependencias:
   - `python -m venv .venv`
   - `.venv\Scripts\pip install -r requirements.txt`
2. Copiar variables:
   - `copy .env.example .env`
3. Ejecutar migraciones:
   - `.venv\Scripts\python manage.py migrate`
4. Crear superusuario:
   - `.venv\Scripts\python manage.py createsuperuser`
5. Ejecutar servidor:
   - `.venv\Scripts\python manage.py runserver`

## Docker

1. Copiar variables:
   - `copy .env.example .env`
2. Levantar servicios:
   - `docker compose up --build`

La API quedara en `http://localhost:8000/api/`.

## Endpoints principales

- Auth:
  - `POST /api/auth/registro/`
  - `POST /api/auth/login/`
  - `POST /api/auth/refresh/`
  - `GET /api/auth/perfil/`
- Escenarios:
  - `GET/POST /api/escenarios/`
  - `GET/PUT/PATCH/DELETE /api/escenarios/{id}/`
- Decisiones:
  - `GET/POST /api/decisiones/`
  - `POST /api/decisiones/{id}/calcular-resultado/`
- Resultados:
  - `GET /api/resultados/`
  - `GET /api/resultados/exportar/?formato=json`
  - `GET /api/resultados/exportar/?formato=csv`

## Documentacion API

- Swagger UI: `http://localhost:8000/api/docs/swagger/`
- ReDoc: `http://localhost:8000/api/docs/redoc/`
- Schema OpenAPI: `http://localhost:8000/api/schema/`
