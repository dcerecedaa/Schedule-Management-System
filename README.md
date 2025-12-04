# ✨ Sistema de Gestión de Horarios y Fichaje

**Sistema web completo para la gestión de horarios, fichajes de empleados y administración de ausencias, desarrollado con tecnologías modernas para empresas que buscan optimizar sus procesos de control horario.**

---

## 💻 Descripción General

Esta aplicación proporciona una solución integral para la gestión de recursos humanos mediante:

- **Sistema de fichaje digital** en tiempo real  
- **Gestión completa de horarios** con validaciones inteligentes  
- **Control de ausencias y permisos** con flujo de aprobación  
- **Roles diferenciados** (administrador/empleado) con permisos específicos  
- **Estadísticas y seguimiento** de horas trabajadas

**Además, este proyecto cuenta con un servidor desplegado en *Railway*, lo que permite un funcionamiento estable, accesible y preparado para entornos de producción.**

**Ideal para empresas que necesitan automatizar sus procesos de control horario y gestión de personal.**

---

## 🚀 Características Principales

### 🔐 Autenticación y Seguridad
- ✅ **Sistema de registro y login** con roles (admin/usuario)  
- ✅ **Encriptación avanzada** con `bcrypt` y migración `SHA-256`  
- ✅ **Manejo seguro de sesiones** con `localStorage`  
- ✅ **Validación robusta** de entradas en todas las rutas

### 👨‍💼 Panel de Administrador
- 🎯 **Gestión completa de usuarios**: altas, bajas y modificaciones  
- 🎯 **Creación y validación de horarios**: con límites de horas anuales  
- 🎯 **Aprobación de ausencias**: flujo de trabajo con estados  
- 🎯 **Visualización de estadísticas**: horarios y fichajes consolidados

### 👩‍💼 Panel de Empleado
- ✨ **Sistema de fichaje intuitivo**: entrada/salida con validaciones  
- ✨ **Control visual de horas**: progreso anual con alertas  
- ✨ **Solicitud de ausencias**: vacaciones, enfermedad y permisos  
- ✨ **Consulta de horarios**: visualización clara de turnos

### ⚙️ Validaciones Inteligentes
- 🧠 **Bloques de días libres**: (lunes-martes, miércoles-jueves, viernes-domingo)  
- 🧠 **Límite de horas anuales**: 1,784 horas máximo por empleado  
- 🧠 **Control de secuencia**: no permite fichajes duplicados  
- 🧠 **Validación de archivos**: solo `PDF`, `JPG`, `PNG` para justificantes

---

## 📋 Estructura de la Aplicación

| Módulo | Descripción |
|--------|-------------|
| **🔄 Autenticación** | Login, registro y gestión de sesiones |
| **📅 Gestión de Horarios** | Creación, modificación y validación |
| **⏰ Sistema de Fichaje** | Registro y cálculo de horas trabajadas |
| **🏖️ Gestión de Ausencias** | Solicitud y aprobación de permisos |
| **📊 Panel Administrativo** | Gestión global de usuarios y datos |
| **👤 Panel de Empleado** | Interfaz personalizada para usuarios |

---

## 🎮 Roles del Sistema

| Característica | 👑 **Administrador** | 👤 **Empleado** |
|----------------|---------------------:|----------------:|
| **Gestión usuarios** | Completa (CRUD) | Solo visualización propia |
| **Creación horarios** | ✅ Sí | ❌ No |
| **Aprobación ausencias** | ✅ Sí | ❌ No |
| **Registro fichaje** | ❌ No | ✅ Sí |
| **Solicitud ausencias** | ❌ No | ✅ Sí |
| **Ver estadísticas** | Todos los usuarios | Solo propias |

---

## 🛠️ Instalación y Configuración

### Prerrequisitos
- Node.js (v14 o superior)  
- MySQL (v5.7 o superior)  
- `npm` o `yarn`

### 🚀 Pasos de Instalación (PowerShell)

1. Clona el repositorio:
```powershell
git clone <repositorio>
cd proyecto-gestion-horarios
```

2. Instala las dependencias:
```powershell
npm install
```

3. Configura las variables de entorno (copia el ejemplo y edítalo):
```powershell
Copy-Item .env.example .env
# Luego edita .env con tu editor preferido
```

4. Ejemplo de contenido de `.env`:
```
DB_HOST=localhost
DB_USER=tu_usuario
DB_PASSWORD=tu_contraseña
DB_NAME=gestion_horarios
DB_PORT=3306
PORT=3000
```

5. Configura la base de datos (importa el esquema SQL):
```powershell
mysql -u root -p < database/schema.sql
```

6. Inicia el servidor:
```powershell
npm start
npm run dev
```

7. Accede a la aplicación:
- Login: `http://localhost:3000/login/a.html`  
- Admin: `http://localhost:3000/admin/Admin.html`  
- Usuario: `http://localhost:3000/usu/User.html`

---

## 📁 Estructura del Proyecto (resumen)

```
proyecto/
├── server.js
├── package.json
├── .env
├── conector/
│   └── db.js
├── vista/
│   ├── admin/
│   ├── login/
│   └── usu/
├── routes/
├── database/
├── uploads/
└── icono/
```

---

## 🔌 API Endpoints Principales

### 🔐 Autenticación
- `POST /api/login/login`
- `POST /api/login/register`

### 👥 Gestión de Usuarios
- `GET /api/usuarios`  
- `POST /api/usuarios`  
- `PUT /api/usuarios/:id`  
- `DELETE /api/usuarios/eliminar`

### 📅 Gestión de Horarios
- `GET /api/horario`  
- `POST /api/horario`  
- `PUT /api/horario/:idHorario`  
- `DELETE /api/horario/:idHorario`

### ⏰ Sistema de Fichaje
- `POST /api/fichaje`
- `GET /api/fichaje/ultimo/:id_usuario`
- `GET /api/fichaje/horas/:id_usuario`

### 🏖️ Gestión de Ausencias
- `GET /api/ausencias`
- `POST /api/ausencias`
- `PUT /api/ausencias/:id`

---

## 💻 Stack Tecnológico

| Categoría | Tecnologías |
|-----------|-------------|
| Backend   | Node.js, Express.js |
| Frontend  | HTML5, CSS3, JavaScript |
| Base de Datos | MySQL |
| Estilos   | Bootstrap 5, CSS personalizado |
| Autenticación | bcrypt, localStorage |
| Manejo de Archivos | multer |
| Iconos    | Bootstrap Icons |
| Hosting Backend | **Railway** |

---

## 🛡️ Consideraciones de Seguridad

- 🔒 Contraseñas encriptadas con `bcrypt`.  
- 🛡️ Consultas SQL parametrizadas.  
- 📁 Validación de archivos.  
- 🔐 Sesiones seguras.  
- 🌐 CORS configurado.

---

## 📈 Escalabilidad y Mantenimiento

- Arquitectura modular.  
- Pool de conexiones MySQL.  
- Estructura clara por funcionalidades.  
- Frontend y backend desacoplados.  
- Logs y validaciones en múltiples capas.

---

## 🔄 Flujo de Trabajo Típico

1. Registro/login.  
2. Fichaje entrada.  
3. Consulta de horario.  
4. Solicitud de ausencia.  
5. Fichaje salida.  
6. Aprobación por admin.  
7. Consulta de estadísticas.

---

## 🤝 Contribuciones

1. Fork del repositorio.  
2. Crear rama.  
3. Implementar cambios.  
4. Actualizar documentación.  
5. Abrir Pull Request.

---

## 👨‍💻 Autor

**David Cereceda**  
📧 david.cereceda.perez@gmail.com  
🔗 LinkedIn: https://www.linkedin.com/in/david-cereceda-perez-3ba0962b6/

