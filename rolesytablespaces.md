# Tienda de Ropa y Accesorios - Roles, Tablespaces y Administración
![Diagrama sin título drawio](https://github.com/user-attachments/assets/224993ed-dc94-436f-8b99-64e62b59e2e1)


## Tablespaces Asignados a Cada Rol
### 1. **DBA (Administrador de Base de Datos)**
- **Tablespaces utilizados**:
  - **SYSTEM**:
    - Contiene los metadatos y el esquema del sistema.
    - Gestionado exclusivamente por el DBA.
  - **UNDO**:
    - Gestiona transacciones y operaciones de deshacer (rollback).
  - **TEMP**:
    - Maneja consultas temporales, como clasificaciones y uniones grandes.
- **Justificación**: 
  - El DBA necesita acceso completo para gestionar el sistema, realizar ajustes y asegurar la integridad del sistema.

---

### 2. **Desarrollador**
- **Tablespaces utilizados**:
  - **USERS**:
    - Contiene las tablas, vistas, procedimientos almacenados y otros objetos creados por el desarrollador.
    - **Ejemplo de contenido**: Las tablas `Ropa`, `Accesorios`, `Clientes`, `Ventas` y `Detalle_Ventas`.
- **Justificación**: 
  - El desarrollador trabaja en `USERS` para implementar y probar los modelos de datos sin interferir con los metadatos del sistema.

---

### 3. **Operador**
- **Tablespaces utilizados**:
  - **USERS**:
    - Acceso restringido a las tablas relevantes, como `Clientes`, `Ventas` y `Detalle_Ventas`, para insertar datos y realizar consultas.
  - **TEMP**:
    - Utilizado indirectamente para ejecutar consultas temporales como búsquedas específicas o reportes.
- **Justificación**: 
  - El operador interactúa con los datos reales de la base de datos pero no tiene permisos de desarrollo o administración.

---

## Resumen en Tabla:

| **Rol**          | **Tablespaces Asignados**                          | **Contenido en el Tablespace**                                            |
|-------------------|----------------------------------------------------|----------------------------------------------------------------------------|
| **DBA**           | SYSTEM, UNDO, TEMP                                | Metadatos, transacciones, operaciones temporales.                         |
| **Desarrollador** | USERS                                              | Tablas de la tienda (`Ropa`, `Accesorios`, `Clientes`, etc.), vistas, SPs.|
| **Operador**      | USERS (limitado), TEMP                             | Acceso restringido a tablas operativas (`Clientes`, `Ventas`, etc.).      |

---

## Ejemplo de Configuración SQL para Tablespaces

### Crear los tablespace:
```sql
CREATE TABLESPACE users
    DATAFILE 'users_data.dbf' SIZE 500M
    AUTOEXTEND ON NEXT 100M MAXSIZE 5G
    EXTENT MANAGEMENT LOCAL;

CREATE TEMPORARY TABLESPACE temp
    TEMPFILE 'temp_data.dbf' SIZE 200M
    AUTOEXTEND ON NEXT 50M MAXSIZE 2G
    EXTENT MANAGEMENT LOCAL;
```

### Crear Usuarios y Asignar Tablespaces:
### DBA:

```sql
CREATE USER dba_user IDENTIFIED BY password 
    DEFAULT TABLESPACE system
    TEMPORARY TABLESPACE temp;
```
```sql
CREATE USER dev_user IDENTIFIED BY password 
    DEFAULT TABLESPACE users
    TEMPORARY TABLESPACE temp;
```
```sql
CREATE USER operator_user IDENTIFIED BY password 
    DEFAULT TABLESPACE users
    TEMPORARY TABLESPACE temp;
```
### Asignar Roles y Permisos:
### DBA:
```sql
GRANT DBA TO dba_user;
```
```sql
GRANT CREATE TABLE, SELECT, INSERT, UPDATE TO dev_user;
```
```sql
GRANT SELECT, INSERT ON Clientes TO operator_user;
```
