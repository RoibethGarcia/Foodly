Foodly
Plataforma web de delivery de comida con tres tipos de usuario: clientes, locales y administradores. Los clientes recorren locales y platos, hacen pedidos y pagan online; los locales gestionan su menú, promociones y pedidos; los administradores supervisan la plataforma.

Proyecto final académico desarrollado en equipo de 6 personas (03/2026 – 08/2026).

Backend (este repositorio): API REST en Java y Spring Boot.
Frontend: Foodly-Front (React).
Funcionalidades
Cuentas y acceso: registro de clientes y locales, activación por correo, login con correo y contraseña o con Google, autenticación con JWT y recuperación de contraseña por correo.
Locales y menú: alta y edición de locales, gestión de platos, imágenes (Cloudinary) y promociones.
Pedidos: creación, seguimiento de estados (incluye rechazo con motivo y entrega), cambios de dirección y tareas programadas para pedidos y facturas.
Pagos: integración con Mercado Pago, con confirmación mediante webhook, y pago con descuento.
Facturas en PDF.
Calificaciones, reclamos y notificaciones entre clientes y locales.
Estadísticas del local para gráficos de ventas y pedidos.
Tecnologías
Área
Stack
Lenguaje y framework
Java 21, Spring Boot 4
Persistencia
Spring Data JPA, PostgreSQL 16
Seguridad
Spring Security, JWT (jjwt), Google Sign-In
Integraciones
Mercado Pago (SDK Java), Cloudinary, correo SMTP
Pruebas
JUnit, Mockito, Spring Boot Test, Postman
Despliegue local
Docker y Docker Compose

Arquitectura
El código está organizado en capas bajo com.example.demo:

Logica/Controllers: endpoints REST, agrupados por recurso (/api/v1/clientes, /locales, /pedidos, /pagos, /reclamos, /calificaciones, /notificaciones, /usuarios, /admins). Hay unos 60 endpoints.
Logica/Service, Clases, DataTypes, Mappers: reglas de negocio, entidades y objetos de transferencia.
Logica/Schedule: tareas programadas (PedidoScheduler, FacturaScheduler).
Persistencia: repositorios JPA e implementaciones.
jwt y config: seguridad, CORS y configuración.
Cómo ejecutarlo
Requisitos: Docker y Docker Compose.

Clonar el repositorio.

Crear un archivo .env en la raíz con estas variables:

DB_NAME, DB_USER, DB_PASSWORD
MP_ACCESS_TOKEN, MP_SUCCESS_URL, MP_FAILURE_URL, MP_PENDING_URL, MP_WEBHOOK_URL, MP_WEBHOOK_SECRET
CLOUDINARY_CLOUD_NAME, CLOUDINARY_API_KEY, CLOUDINARY_API_SECRET
MAIL_USERNAME, MAIL_PASSWORD
GOOGLE_CLIENT_ID
APP_CORS_ALLOWED_ORIGINS   (por defecto: http://localhost:3000, http://localhost:5173)

Levantar los servicios:

docker compose up --build

La API queda disponible en http://localhost:8080 y PostgreSQL en el puerto 5432.

Para ejecutar el frontend, ver las instrucciones en Foodly-Front (npm install y npm run dev, con VITE_API_URL apuntando a este backend).
Pruebas
./mvnw test

El proyecto incluye unas 30 clases de prueba (JUnit y Mockito) sobre controladores y servicios.
Mi contribución
Participé en el backend y en el frontend:

Backend: módulo de pedidos y platos, integración de pagos con Mercado Pago (incluyendo webhook y pago con descuento), facturas en PDF, reclamos, datos para las estadísticas del local y correcciones sobre la recuperación de contraseña y el login con Google.
Frontend (React): panel del local (pedidos, platos, promociones, reclamos y estadísticas), flujo de pedidos y pago del cliente, registro con Google y gráficos.
Calidad: pruebas con JUnit, Mockito y Postman sobre los casos de uso críticos.
Equipo
Proyecto desarrollado por un equipo de 6 personas. Repositorio original del equipo: Proyecto_Equipo3_2026.
