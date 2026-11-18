# FlourFinder 🍞

## Descripción Breve

FlourFinder es una aplicación web desarrollada como proyecto del SENA (ADSO), cuyo objetivo es crear un directorio digital de establecimientos registrados en Garzón, Huila, dedicados a la elaboración y comercialización de productos derivados de la harina.

Su propósito es conectar a los clientes con panaderías, reposterías, pastelerías y establecimientos que vendan pan y postres, facilitando la búsqueda de productos, la realización de pedidos y las entregas a domicilio. Se busca expandir en un futuro a otros municipios.

---

## Tecnologías Utilizadas

| Tecnología     | Versión  | Descripción                                                      |
| -------------- | -------- | ---------------------------------------------------------------- |
| **Node.js**    | v18+     | Runtime de JavaScript para el backend                            |
| **Express**    | ^5.3.0   | Framework web para crear el servidor API                         |
| **PostgreSQL** | -        | Base de datos relacional para almacenamiento persistente         |
| **pg**         | ^8.23.1  | Driver oficial de Node.js para PostgreSQL con connection pooling |
| **dotenv**     | ^18.0.10 | Manejo seguro de variables de entorno                            |
| **cors**       | ^2.8.6   | Middleware para habilitar CORS en la API                         |
| **morgan**     | ^1.12.1  | Logger HTTP para monitoreo de peticiones                         |

---

## Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:

- [Node.js](https://nodejs.org/) (versión 18 o superior)
- [PostgreSQL](https://www.postgresql.org/download/) (versión 14 o superior) instalado localmente

---

## Instalación y Configuración Paso a Paso

### 1. Clonar el Repositorio

```bash
git clone <URL_DEL_REPOSITORIO>
cd backend
```

### 2. Instalar Dependencias

```bash
npm install
```

Esto instalará todas las dependencias listadas en `package.json`.

### 3. Configurar Variables de Entorno (.env)

El archivo `.env` ya está configurado con los valores por defecto, pero puedes personalizarlo según tu entorno:

```env
PORT=3000
NODE_ENV=development
PG_HOST=localhost
PG_PORT=5432
PG_DATABASE=flourfinder
PG_USER=postgres
PG_PASSWORD=tu_password_aqui
PG_MAX_CONNECTIONS=10
PG_IDLE_TIMEOUT=30000
```

**Importante**: Cambia `PG_PASSWORD` por la contraseña de tu usuario de PostgreSQL.

### 4. Crear la Base de Datos en PostgreSQL

Ejecuta los siguientes comandos en tu terminal:

```bash
# Conectarse a PostgreSQL
psql -U postgres

# Crear la base de datos (ejecutar dentro del psql)
CREATE DATABASE flourfinder;

# Salir de psql
\q
```

### 5. Ejecutar el Proyecto Localmente

Para iniciar el servidor en modo desarrollo:

```bash
npm run dev
```

El servidor se ejecutará en `http://localhost:3000`.

---

## Estructura del Proyecto

```
backend/
├── src/
│   ├── app.js              # Configuración principal de Express (middlewares, rutas)
│   ├── server.js           # Punto de entrada y gestión de conexiones DB
│   ├── config/             # Configuraciones del proyecto
│   │   ├── environment.js  # Variables de entorno cargadas desde .env
│   │   └── db.js           # Conexión a PostgreSQL con pooling
│   ├── controllers/        # Lógica de negocio (controladores)
│   │   └── healthController.js  # Controlador para endpoints de salud
│   ├── routes/             # Definición de rutas API
│   │   └── healthRoutes.js      # Rutas de diagnóstico del sistema
│   └── utils/              # Utilidades (carpeta futura)
├── FlourFinder/            # Configuración para Bruno API Testing
│   ├── api_health.yml      # Health check endpoint
│   └── opencollection.yml  # Colección OpenCollection
├── .env                    # Variables de entorno (no está en gitignore)
├── package.json            # Dependencias y scripts del proyecto
├── package-lock.json       # Bloqueador de versiones de dependencias
└── README.md               # Documentación del proyecto
```

### Explicación Breve:

- **`src/`**: Código fuente principal de la aplicación.
- **`src/config/`**: Configuraciones centralizadas (DB, entorno).
- **`src/controllers/`**: Manejadores de lógica de negocio para cada endpoint.
- **`src/routes/`**: Definición de rutas y métodos HTTP permitidos.
- **`FlourFinder/`**: Archivos de configuración para pruebas con Bruno API Testing Tool.

---

## Integrantes del Equipo

| Nombre                            | Rol                   |
| --------------------------------- | --------------------- |
| Yilver Arlex Jovel Angarita       | Desarrollador Backend |
| Jose Alejandro Rodriguez Calderón | Desarrollador Backend |

---

## Endpoints Disponibles (Actual)

### GET /api/health

**Ejemplo de respuesta:**

```json
{
  "status": "healthy",
  "timestamp": "2024-11-17T18:30:00.000Z",
  "services": {
    "api": {
      "status": "up",
      "uptime_seconds": 123456
    },
    "postgres": {
      "status": "healthy",
      "latency_ms": 12
    }
  }
}
```

---

## Licencia

ISC
