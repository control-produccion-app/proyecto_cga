# Control de Producción y Gestión Alimenticia

Sistema web para apoyar el control operativo de producción, pedidos, movimientos comerciales, saldos y bodega en una panadería o pequeño negocio alimenticio.

## Descripción del proyecto

El proyecto busca reemplazar la dependencia de consolidación manual en planillas por una solución con base de datos relacional, backend API y frontend web. El foco es ordenar la operación diaria y disponer de información consultable para producción, despacho, clientes, saldos y control básico de insumos.

## Objetivo general

Desarrollar una aplicación web que permita registrar, consultar y controlar información operativa del negocio, manteniendo trazabilidad diaria sobre producción, pedidos, movimientos y estado comercial de clientes.

## Arquitectura del sistema

- **Base de datos:** PostgreSQL
- **Backend:** Django + Django REST Framework
- **Autenticación API:** JWT
- **Frontend:** Angular
- **Despliegue actual del backend:** Railway
- **Despliegue previsto del frontend:** Vercel

La arquitectura sigue un esquema de tres capas: el frontend consume la API del backend y el backend centraliza acceso a datos, validaciones y exposición de recursos.

## Módulos funcionales del sistema

- **Producción:** registro y consulta de producción por jornada, turno y tipo.
- **Bodega:** control de insumos, movimientos de entrada, salida y ajuste, y conteos físicos.
- **Pedidos / despacho:** registro de pedidos, detalle de productos y distribución.
- **Clientes / saldos:** información comercial del cliente y seguimiento básico de deuda o saldo.
- **Reportes operativos:** endpoints de consulta para apoyo a control diario.
- **Administración:** mantenimiento y revisión de datos mediante Django Admin.

## Estado técnico actual

### Backend

El backend está implementado en Django y expone:

- panel de administración Django (`/admin/`)
- API REST bajo `/api/`
- endpoint de health check (`/api/health/`)
- autenticación JWT (`/api/token/` y `/api/token/refresh/`)

### Recursos principales expuestos por la API

- `turnos`
- `distribuciones`
- `insumos`
- `tipos-produccion`
- `jornadas`
- `producciones`
- `movimientos-bodega`
- `conteos-bodega`
- `clientes`
- `productos`
- `pedidos`
- `detalles-pedido`
- `movimientos`
- `reportes`

### Base de datos y modelo actual

El backend implementa modelos para las principales entidades operativas del sistema:

- Turno
- Distribucion
- Insumo
- TipoProduccion
- JornadaDiaria
- Produccion
- MovimientoBodega
- ConteoBodega
- Cliente
- Producto
- Pedido
- DetallePedido
- DetalleMovimiento

Estos modelos cubren la operación base del proyecto: producción diaria, bodega, catálogo comercial, pedidos y movimientos asociados.

## Estructura del repositorio

```text
proyecto_cga/
├── backend/
│   ├── api/
│   ├── panaderia_backend/
│   ├── manage.py
│   └── requirements.txt
├── frontend/
├── documentos_apoyo/
├── documento_lider_backend_frontend.md
├── script_maestro_panaderia_v2(1).sql
└── README.md
```

## Backend desplegado

URL pública actual del backend:

```text
https://proyectocga-production-2e12.up.railway.app
```

Rutas técnicas relevantes:

- `https://proyectocga-production-2e12.up.railway.app/admin/`
- `https://proyectocga-production-2e12.up.railway.app/api/`
- `https://proyectocga-production-2e12.up.railway.app/api/health/`
- `https://proyectocga-production-2e12.up.railway.app/api/token/`

## Estructura técnica del backend

Dentro de `backend/` el proyecto incluye:

- configuración principal Django
- aplicación `api` con modelos, serializers, vistas y rutas
- archivos de despliegue para Railway
- dependencias Python declaradas en `requirements.txt`
- comandos de gestión para carga de datos y soporte de prueba

## Frontend

El repositorio incluye una carpeta `frontend/` para la aplicación Angular. El frontend está pensado para consumir la API del backend y organizar la interfaz por módulos funcionales del sistema.

## Base de datos

El proyecto utiliza PostgreSQL como motor principal. En el repositorio también existe un script SQL maestro y documentación de apoyo para la estructura y contexto del sistema.

## Tecnologías principales

- PostgreSQL
- Python
- Django
- Angular

## Componentes de soporte del backend

- Django REST Framework para exponer la API REST
- SimpleJWT para autenticación basada en tokens
- psycopg2-binary para conexión con PostgreSQL
- gunicorn para despliegue del backend
- whitenoise para manejo de archivos estáticos
- django-cors-headers para integración entre frontend y backend
- dj-database-url para configuración de base de datos por entorno
- python-dotenv para carga de variables de entorno en desarrollo

### Base de datos
- PostgreSQL

### Frontend
- Angular
- TypeScript


