# 🗄️ Diseño de Base de Datos - Sistema de Gestión Documental (SGD)

El diseño de la base de datos del **Sistema de Gestión Documental (SGD)** se realizó con el objetivo de garantizar **integridad, seguridad y escalabilidad**.  
Se utilizó **SQL Server** como motor de base de datos, con un modelo **relacional normalizado** y soporte de **procedimientos almacenados** para operaciones críticas.

---

## 🔹 Modelo Entidad-Relación (MER)

El MER define las principales entidades del sistema y sus relaciones.  

![MER](screenshots/MER-SGD.png)

---

## 🔹 Modelo Relacional

El modelo lógico/físico de la base de datos se representa a través del siguiente diagrama:  

![Modelo Relacional](screenshots/DER-SGD.PNG)

---

## 📑 Descripción de Tablas

### 👤 `usuarios`
- **Campos clave**: `id_usuario (PK)`, `id_rol (FK)`
- Almacena la información de los usuarios que acceden al sistema.  
- Incluye credenciales seguras (contraseña con hash + salt) y estado de la cuenta.

### 📝 `documentos`
- **Campos clave**: `id_documento (PK)`, `id_usuario (FK)`, `id_categoria (FK)`
- Contiene los documentos gestionados dentro del sistema.  
- Guarda metadatos como nombre, fecha, estado, extensión y archivo binario.

### 📂 `categorias_documentos`
- **Campos clave**: `id_categoria (PK)`, `id_padre (FK opcional)`
- Define la estructura jerárquica de clasificación de documentos.  
- Permite organizar documentos en categorías y subcategorías.

### 🔐 `roles`
- **Campos clave**: `id_rol (PK)`
- Define los distintos roles de usuario dentro del sistema.  
- Controla el nivel de acceso y permisos asignados.

### ✅ `permisos`
- **Campos clave**: `id_permiso (PK)`
- Contiene la lista de permisos específicos del sistema.  
- Se utiliza junto con la tabla intermedia `roles_permisos`.

### 🔗 `roles_permisos`
- **Campos clave**: `id_rol (FK, PK)`, `id_permiso (FK, PK)`
- Relación **muchos a muchos** entre roles y permisos.  
- Define qué acciones puede realizar cada rol dentro del sistema.

### 📊 `bitacora_ingresos`
- **Campos clave**: `id_ingreso (PK)`, `id_usuario (FK)`
- Registra los accesos al sistema con fecha/hora de ingreso y salida.  
- Permite auditar el uso del sistema por usuario.

### 🔎 `bitacora_movimientos`
- **Campos clave**: `id_movimiento (PK)`, `id_usuario (FK)`
- Almacena las operaciones realizadas por los usuarios dentro del sistema.  
- Guarda la acción realizada, descripción y fecha/hora.

---

## 🔒 Consideraciones de Seguridad en la Base de Datos
- Contraseñas almacenadas con **hash + salt**.  
- Uso de **roles y permisos** para el control de acceso.  
- **Procedimientos almacenados** para evitar inyecciones SQL.  
- **Bitácoras** que permiten trazabilidad y auditoría de usuarios.

---

## 🚀 Escalabilidad y Mantenimiento
- Base de datos normalizada hasta **3FN**.  
- Soporte de **categorías jerárquicas** para documentos.  
- Posibilidad de migrar a **servicios en la nube (Azure SQL, AWS RDS)** en caso de crecimiento.  
