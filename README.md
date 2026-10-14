Proyecto Mini Core - Aplicación de Gestión de Ventas (React - Django)
Aplicación interconectada de gestión de comisiones que combina la robustez de Django REST Framework para exponer una API REST, con un frontend React + Vite que consume esos endpoints mediante Axios y ofrece una UI en modo oscuro moderno y responsivo. El stack se despliega en Render : el backend corre como Web Service (Gunicorn + Django, con migraciones automáticas y archivos estáticos recopilados) y el frontend como Static Site generado por Vite, con una regla global de reescritura (/* → /index.html) para permitir el enrutado del SPA.

Descripción del Proyecto
Este proyecto contempla un Sistema de Comisiones completo que permite a los usuarios desarrollar las funciones:

Crear, listar y eliminar Ventas .
Gestionar Reglas de Comisión configurables por monto mínimo y porcentaje.
Cálculo automático de comisiones basado en las reglas establecidas.
Informes detallados de comisiones por vendedor y período.
Filtrar comisiones por rango de fechas con análisis comparativo.
El backend se encuentra construido con Django y utiliza SQLite en desarrollo para almacenar la información. El frontend usa React (Javascript) con Vite y consume la API REST vía Axios .

🌐 Demo en Vivo
🖥️ Aplicación Frontend: https://proyecto-mini-core-mvc-static.onrender.com
Tabla de Contenidos
Instalación
Uso del Proyecto
Características
Estructura del Proyecto
Puntos finales de la API
Despliegue
Contribución
Créditos
Licencia
Instalación
Requisitos previos
Node.js y npm instalados para el frontend (Versión recomendada: Node: v18+ ).
Python 3.8 o superior instalado para el backend (Versión utilizada: 3.11+ ).
Django , Django REST Framework y django-cors-headers instalados en el backend.
Axios , date-fns y React Router en el frontend.
La base de datos SQLite se utiliza por defecto en desarrollo y PostgreSQL en producción (Render).

Pasos para instalar y ejecutar el proyecto
Configuración del Backend
Clonar el repositorio:
git clone https://github.com/Mattair39/Proyecto-Mini-Core-MVC.git
Ubicarse en la carpeta principal del proyecto:
cd Proyecto-Mini-Core-MVC
Ir a la carpeta backend:
cd backend
Crear un entorno virtual e instalar dependencias:
python -m venv env
source env/bin/activate  # En Windows: env\Scripts\activate
pip install -r requirements.txt
Aplicar las migraciones:
python manage.py migrate
(Opcional) Cargar datos de ejemplo:
python manage.py loaddata commission_app/fixtures/initial_data.json
Iniciar el servidor del backend:
python manage.py runserver
El servidor estará disponible en http://127.0.0.1:8000/

Configuración del Frontend
Regresar a la carpeta raíz del proyecto y ubicarse en frontend :
cd ../frontend
Instalar las dependencias:
npm install
Ejecución
Iniciar el Backend (Django)
Desde la carpeta backend (donde se encuentra administrar.py):
python manage.py runserver
El servidor de Django estará disponible en http://127.0.0.1:8000/
API disponible en http://127.0.0.1:8000/api/
Iniciar el Frontend (React)
Ir a la carpeta frontend y ejecutar:
npm run dev
La aplicación de React estará disponible en http://localhost:3000/
Uso del Proyecto
📊 Gestión de Ventas:
Registrar Ventas: Agregar ventas asociando vendedor, fecha y monto.
Visualizar Comisiones: Ver automáticamente la comisión calculada para cada venta.
📈 Cálculo de Comisiones:
Configurar Reglas: Definir reglas de comisión por porcentaje y monto mínimo.
Análisis por Período: Seleccione rango de fechas para calcular comisiones.
Reportes Detallados: Ver resumen por vendedor con desglose individual.
Métricas Comparativas: Analizar totales, promedios y rendimiento.
🔍Funcionalidades Avanzadas:
Desplegable Expandible: Explorar comisiones individuales por vendedor.
Cálculo Automático: Las comisiones se calculan automáticamente según las reglas.
Validación de Datos: Controles de entrada y mensajes de error informativos.
Interfaz Responsiva: Optimizada para escritorio y móvil.
Características
🚀 Funcionalidades Principales:
Cálculo automático de comisiones basado en reglas configurables
Sistema de informes con filtros por rango de fechas
Interfaz de usuario moderna con modo oscuro
Desplegable desplegable para análisis detallado por vendedor
🔧 Tecnologías Backend:
Django REST Framework con endpoints RESTful
SQLite (Desarrollo)
CORS habilitado para comunicación segura
Migraciones automáticas y accesorios para datos iniciales
🎨 Tecnologías Frontend:
React 19 con Vite para desarrollo rápido
Axios para consumo de API REST
date-fns para manejo de fechas
Propiedades personalizadas CSS para la creación de temas consistente
🌐 Despliegue:
Backend: Servicio Web y Render con Gunicorn
Frontend: Static Site en Render con rewrite rules
Base de datos: SQLite automático en Render
Variables de entorno para configuración de producción
Estructura del Proyecto
Proyecto-Mini-Core-MVC/
├── backend/
│   ├── commission_app/
│   │   ├── models.py          # Modelos de Vendedor, Venta, Regla, ComisionCalculada
│   │   ├── serializers.py     # Serializers para API REST
│   │   ├── views.py           # ViewSets y vistas personalizadas
│   │   ├── urls.py            # URLs de la API
│   │   ├── admin.py           # Configuración del panel admin
│   │   └── fixtures/          # Datos iniciales
│   ├── commission_project/
│   │   ├── settings.py        # Configuración con soporte para producción
│   │   ├── urls.py            # URLs principales
│   │   └── wsgi.py            # WSGI para deployment
│   ├── requirements.txt       # Dependencias de Python
│   └── manage.py              # Comando principal de Django
└── frontend/
    ├── src/
    │   ├── components/        # Componentes reutilizables
    │   ├── services/          # API client con Axios
    │   ├── utils/             # Utilidades para formateo y fechas
    │   ├── App.jsx            # Componente principal
    │   └── main.jsx           # Punto de entrada
    ├── public/                # Archivos estáticos
    ├── package.json           # Dependencias de Node.js
    └── vite.config.js         # Configuración de Vite
Puntos finales de la API
📋 Vendedores
GET    /api/vendedores/           # Listar vendedores
POST   /api/vendedores/           # Crear vendedor
GET    /api/vendedores/{id}/      # Obtener vendedor
PUT    /api/vendedores/{id}/      # Actualizar vendedor
DELETE /api/vendedores/{id}/      # Eliminar vendedor
GET    /api/vendedores/{id}/ventas/     # Ventas de un vendedor
GET    /api/vendedores/{id}/comisiones/ # Comisiones de un vendedor
💰 Ventas
GET    /api/ventas/              # Listar ventas (con filtros)
POST   /api/ventas/              # Crear venta
GET    /api/ventas/{id}/         # Obtener venta
PUT    /api/ventas/{id}/         # Actualizar venta
DELETE /api/ventas/{id}/         # Eliminar venta
⚙️ Reglas de Comisión
GET    /api/reglas/              # Listar reglas activas
POST   /api/reglas/              # Crear regla
PUT    /api/reglas/{id}/         # Actualizar regla
📊 Cálculo de Comisiones
POST   /api/comisiones/calcular/ # Calcular comisiones por rango de fechas
GET    /api/comisiones/resumen/  # Resumen general de comisiones
📈 Parámetros de consulta disponibles:
?vendedor={id}- Filtrar por vendedor
?fecha_inicio={YYYY-MM-DD}- Filtrar desde fecha
?fecha_fin={YYYY-MM-DD}- Filtrar hasta fecha
Despliegue
🚀 Despliegue de renderizado
Este proyecto está configurado para implementación automática en Render:

Variables de entorno - Backend:
SECRET_KEY=tu-secret-key-generada
DEBUG=False
DATABASE_URL=postgresql://user:pass@host:port/db
CORS_ALLOWED_ORIGINS=https://proyecto-mini-core-mvc-static.onrender.com
Variables de Entorno - Frontend:
VITE_API_URL=https://proyecto-mini-core-mvc.onrender.com
Comandos de Build:
Backend: pip install -r requirements.txt && python manage.py collectstatic --noinput && python manage.py migrate
Interfaz: npm install && npm run build
🔧 Desarrollo Local
Para desarrollo local, el proyecto usa configuración automática:

Backend: SQLite +DEBUG=True
Frontend: API URL apunta ahttp://127.0.0.1:8000
Contribución
Para contribuir a este proyecto, sigue estos pasos:

Realizar un fork del repositorio.
Crea una nueva rama ( git checkout -b feature/nueva-funcionalidad).
Realiza tus cambios y haz commit ( git commit -m "Agregar nueva funcionalidad").
Haz push a la rama ( git push origin feature/nueva-funcionalidad).
Abrir un Pull Request.
📝 Pautas de Contribución:
Seguir las convenciones de código existentes
Agregar pruebas para nuevas funcionalidades
Actualizar documentación cuando sea necesario
Usar commits descriptivos y claros
Créditos
Este proyecto fue desarrollado por:

Gabriel Argüello (Universidad de las Américas)
GitHub
🙏 Tecnologías utilizadas:
Django - Marco web de Python
Django REST Framework - API REST para Django
React - Biblioteca de JavaScript para UI
Vite : herramienta de compilación para desarrollo frontend
Render - Plataforma de implementación
