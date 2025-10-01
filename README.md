# 🔄 Trueketeo

**Sistema de intercambio P2P para productos y servicios entre usuarios**

Plataforma fullstack que permite a usuarios publicar productos, buscar intercambios y gestionar transacciones de trueque de forma segura y eficiente.

## 🚀 Tech Stack

**Frontend:** React.js • JavaScript • Bootstrap  
**Backend:** Python • Flask • SQLAlchemy  
**Database:** PostgreSQL  
**Auth:** JWT (JSON Web Tokens)  
**Deploy:** Render.com

## ✨ Características

- **Sistema de autenticación** - Registro, login y gestión de sesiones con JWT
- **Gestión de productos** - Publicar, editar y eliminar productos para intercambio
- **Sistema de matching** - Búsqueda y filtrado de productos disponibles
- **Perfiles de usuario** - Gestión completa de datos y productos publicados
- **API RESTful** - Endpoints bien estructurados con validación de datos
- **Responsive design** - Interfaz adaptable a dispositivos móviles

## 📋 Requisitos Previos

- Python 3.10+
- Node.js 20+
- PostgreSQL
- Pipenv
- npm/yarn

## 🛠️ Instalación

### Backend Setup

```bash
# Instalar dependencias de Python
pipenv install

# Crear archivo de variables de entorno
cp .env.example .env

# Configurar DATABASE_URL en .env
# Ejemplo: postgres://username:password@localhost:5432/trueketeo

# Ejecutar migraciones
pipenv run migrate
pipenv run upgrade

# Iniciar servidor backend
pipenv run start
```

### Frontend Setup

```bash
# Instalar dependencias de Node
npm install

# Iniciar servidor de desarrollo
npm run start
```

La aplicación estará disponible en `http://localhost:3000`

## 🗄️ Estructura de Base de Datos

### Modelos principales:
- **User** - Usuarios de la plataforma
- **Product** - Productos disponibles para intercambio
- **Exchange** - Transacciones de trueque
- **Category** - Categorías de productos

## 🔑 Variables de Entorno

```env
DATABASE_URL=postgres://user:password@localhost:5432/dbname
FLASK_APP=src/app.py
FLASK_ENV=development
JWT_SECRET_KEY=your-secret-key
```

## 📡 API Endpoints

### Autenticación
```
POST /api/auth/signup    - Registro de usuario
POST /api/auth/login     - Inicio de sesión
GET  /api/auth/profile   - Obtener perfil (protegido)
```

### Productos
```
GET    /api/products        - Listar productos
POST   /api/products        - Crear producto (protegido)
GET    /api/products/:id    - Detalle de producto
PUT    /api/products/:id    - Actualizar producto (protegido)
DELETE /api/products/:id    - Eliminar producto (protegido)
```

### Usuario
```
GET  /api/users/:id         - Perfil público de usuario
GET  /api/users/:id/products - Productos de un usuario
```

## 🧪 Testing

```bash
# Insertar usuarios de prueba
flask insert-test-users 5

# Insertar datos de prueba personalizados
pipenv run insert-test-data
```

## 📦 Deploy

### Deploy en Render.com

1. Conectar repositorio de GitHub
2. Configurar variables de entorno
3. Deploy automático con cada push a main

Para más detalles: [Render Deployment Guide](https://4geeks.com/docs/start/deploy-to-render-com)

## 🏗️ Arquitectura del Proyecto

```
src/
├── api/
│   ├── models.py          # Modelos SQLAlchemy
│   ├── routes.py          # Definición de rutas
│   ├── commands.py        # CLI commands
│   └── utils.py           # Utilidades
├── front/
│   ├── js/
│   │   ├── component/     # Componentes React
│   │   ├── pages/         # Páginas principales
│   │   ├── store/         # Estado global (Flux)
│   │   └── layout.js      # Layout principal
│   └── styles/            # Estilos CSS
└── app.py                 # Entry point Flask
```

## 📝 Comandos Útiles

```bash
# Revertir última migración
pipenv run downgrade

# Conectar a PostgreSQL (Codespaces)
psql -h localhost -U gitpod trueketeo

# Limpiar caché de Python
find . -type d -name __pycache__ -exec rm -r {} +
```

## 🐛 Troubleshooting

**Error de conexión a base de datos:**
- Verificar que PostgreSQL esté corriendo
- Comprobar DATABASE_URL en .env
- Asegurar que la base de datos existe

**Error en migraciones:**
- Ejecutar `pipenv run downgrade` y luego `pipenv run upgrade`
- Revisar models.py por errores de sintaxis
