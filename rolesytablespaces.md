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
## crear usuarios

- ildefonso
- Valery
- Roberto

  ![imagen](https://github.com/user-attachments/assets/9ddae0b1-660f-454d-8a85-1468578224ee)

  ![imagen](https://github.com/user-attachments/assets/d7a17ca6-ecfd-49d5-893f-b71a46d6cdc8)



---
## tablespaces

### 1. **Desarrollador**

![imagen](https://github.com/user-attachments/assets/c991e851-2fee-4041-8f44-cef68000f2cf)

---

### 2. **Operador**

![imagen](https://github.com/user-attachments/assets/3ae63a8e-e229-410b-8e6a-b279e7659741)

---

### 3. **Temporal**

![imagen](https://github.com/user-attachments/assets/961927c0-0578-4e53-895e-96e8fb184e12)

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
