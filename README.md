# 🛍️ API RESTful de Productos — Flask + JWT

> Tarea 1 — Fase 1 | Desarrollo de Aplicaciones Web  
> Framework: Flask (Python) | Autenticación: JWT

---

## 🖼️ Evidencias — Pruebas en Postman

### Evidencia 1 — Login (POST /api/v1/auth/login)
![Evidencia 1 - Login](evidencias/evidencia1_login.png)

### Evidencia 2 — Listar Productos (GET /api/v1/productos)
![Evidencia 2 - Listar Productos](evidencias/evidencia2_productos.png)

### Evidencia 3 — Crear Producto (POST /api/v1/productos)
![Evidencia 3 - Crear Producto](evidencias/evidencia3_crear.png)

---

## 📋 Descripción

API RESTful construida con **Flask** que implementa un sistema de gestión de productos con autenticación mediante **JWT (JSON Web Tokens)**. El proyecto aplica los principios REST: stateless, uso correcto de verbos HTTP, códigos de estado apropiados y diseño de URIs con sustantivos en plural.

---

## 🚀 Tecnologías utilizadas

| Tecnología | Versión | Uso |
|------------|---------|-----|
| Python | 3.x | Lenguaje base |
| Flask | 3.x | Framework web |
| PyJWT | 2.x | Generación y verificación de tokens JWT |

---

## ⚙️ Instalación y ejecución

```bash
# 1. Clonar el repositorio
git clone https://github.com/TU_USUARIO/api-flask-tarea1.git
cd api-flask-tarea1

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Ejecutar la API
python app.py
```

La API quedará disponible en: `http://127.0.0.1:5000`

---

## 🔑 Credenciales de prueba

| Usuario | Email | Password | Rol |
|---------|-------|----------|-----|
| Admin | admin@api.com | admin123 | admin |
| Juan Pérez | juan@api.com | juan123 | usuario |

---

## 📌 Endpoints disponibles

### 🔐 Autenticación

| Método | Endpoint | Descripción | Auth |
|--------|----------|-------------|------|
| POST | `/api/v1/auth/login` | Iniciar sesión y obtener JWT | ❌ Pública |
| GET | `/api/v1/auth/perfil` | Ver perfil del usuario autenticado | ✅ JWT |

### 📦 Productos (CRUD completo)

| Método | Endpoint | Descripción | Auth |
|--------|----------|-------------|------|
| GET | `/api/v1/productos` | Listar todos los productos | ❌ Pública |
| GET | `/api/v1/productos/<id>` | Obtener producto por ID | ❌ Pública |
| POST | `/api/v1/productos` | Crear nuevo producto | ✅ JWT |
| PUT | `/api/v1/productos/<id>` | Reemplazar producto completo | ✅ JWT |
| PATCH | `/api/v1/productos/<id>` | Actualizar campos específicos | ✅ JWT |
| DELETE | `/api/v1/productos/<id>` | Eliminar producto | ✅ JWT Admin |

### 🩺 Salud

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/v1/health` | Verificar estado de la API |

---

## 🧪 Cómo probar con Postman

### Paso 1 — Login (obtener token)

```
POST http://127.0.0.1:5000/api/v1/auth/login
Content-Type: application/json

{
  "email": "admin@api.com",
  "password": "admin123"
}
```

### Paso 2 — Usar el token en requests protegidos

En el header de cada request que requiera JWT:

```
Authorization: Bearer <token_obtenido_en_login>
```

### Paso 3 — Crear un producto

```
POST http://127.0.0.1:5000/api/v1/productos
Authorization: Bearer <token>
Content-Type: application/json

{
  "nombre": "Teclado Mecánico",
  "precio": 850.00,
  "categoria": "Electrónica",
  "stock": 20
}
```

---

## 📁 Estructura del proyecto

```
api_flask/
├── app.py            # Código principal de la API
├── requirements.txt  # Dependencias del proyecto
└── README.md         # Este archivo
```

---

## 💡 Comentario de aprendizaje

> Con este ejercicio entendí de manera práctica cómo funciona realmente una API RESTful. Antes solo sabía la teoría de los verbos HTTP (GET, POST, PUT, PATCH, DELETE), pero al implementarlos en Flask entendí cuándo usar cada uno y por qué importa usar el código de estado correcto en cada respuesta.
>
> Lo que más me llamó la atención fue el funcionamiento de JWT: al hacer login el servidor genera un token firmado que el cliente guarda, y en cada petición lo manda en el header para identificarse, sin que el servidor guarde ninguna sesión. Eso es exactamente el principio stateless de REST que investigué en la fase teórica.
>
> También aprendí la diferencia entre autenticación (¿quién eres?) y autorización (¿qué puedes hacer?), implementada con los decoradores `@requiere_token` y `@requiere_admin`. Esto me ayudó a entender cómo se protegen rutas en aplicaciones reales.
>
> Herramientas como Postman fueron clave para probar cada endpoint de forma ordenada, porque me permitieron ver exactamente qué responde la API, los códigos de estado y el JSON completo, sin necesidad de tener un frontend listo.

---

## 📄 Licencia

Proyecto académico — Desarrollo de Aplicaciones Web.
