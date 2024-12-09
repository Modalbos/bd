# Tienda de Ropa y Accesorios - Roles, Tablespaces y Administración
![Diagrama sin título drawio](https://github.com/user-attachments/assets/224993ed-dc94-436f-8b99-64e62b59e2e1)


## crear roles

```sql
CREATE ROLE C##Administrador;

CREATE ROLE C##Desarrollador;

CREATE ROLE C##Operador;

```
![imagen](https://github.com/user-attachments/assets/8bab8267-5776-4b57-b913-61dfa8d017e6)

---
## asignar privilegios
### Administrador

```sql


```
![imagen](https://github.com/user-attachments/assets/2a8bebf4-9a98-4503-a7a2-15b732285291)


### Desarrollador

```sql
GRANT CREATE TABLE, ALTER ANY TABLE, DROP ANY TABLE TO C##Desarrollador;

```

![imagen](https://github.com/user-attachments/assets/d3e0f611-43ad-4a50-81a9-209fdb6c60ae)



```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON Ropa TO C##Desarrollador;
GRANT SELECT, INSERT, UPDATE, DELETE ON Accesorios TO C##Desarrollador;
GRANT SELECT, INSERT, UPDATE, DELETE ON Clientes TO C##Desarrollador;
GRANT SELECT, INSERT, UPDATE, DELETE ON Ventas TO C##Desarrollador;
GRANT SELECT, INSERT, UPDATE, DELETE ON Detalle_Ventas TO C##Desarrollador;

```

![imagen](https://github.com/user-attachments/assets/3fa7e25a-8894-4e55-bc20-502f185889df)


### Operador

```sql

GRANT SELECT, INSERT ON Clientes TO C##Operador;
GRANT SELECT, INSERT ON Ventas TO C##Operador;
GRANT SELECT, INSERT ON Detalle_Ventas TO C##Operador;

```
![imagen](https://github.com/user-attachments/assets/8406d52d-b7a3-4a3e-86a1-3348fe16efe2)


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


### Crear Usuarios y Asignar Tablespaces:
### 


```sql

```
```sql

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
