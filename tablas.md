# Modelo Relacional: Tienda de Ropa y Accesorios

## Tablas

### 1. Tabla: `Ropa`
| Campo       | Tipo         | Clave |
|-------------|--------------|-------|
| ID_Ropa     | NUMBER       | PK    |
| Nombre      | VARCHAR(100) |       |
| Talla       | VARCHAR(10)  |       |
| Color       | VARCHAR(50)  |       |
| Precio      | NUMERIC      |       |
| Categoria   | VARCHAR(50)  |       |

---

### 2. Tabla: `Accesorios`
| Campo         | Tipo         | Clave |
|---------------|--------------|-------|
| ID_Accesorio  | NUMBER       | PK    |
| Nombre        | VARCHAR(100) |       |
| Tipo          | VARCHAR(50)  |       |
| Color         | VARCHAR(50)  |       |
| Precio        | NUMERIC      |       |

---

### 3. Tabla: `Clientes`
| Campo       | Tipo         | Clave |
|-------------|--------------|-------|
| ID_Cliente  | NUMBER       | PK    |
| Nombre      | VARCHAR(100) |       |
| Correo      | VARCHAR(100) |       |
| Telefono    | VARCHAR(20)  |       |

---

### 4. Tabla: `Empleados`
| Campo         | Tipo         | Clave |
|---------------|--------------|-------|
| ID_Empleado   | NUMBER       | PK    |
| Nombre        | VARCHAR(100) |       |
| Cargo         | VARCHAR(50)  |       |

---

### 5. Tabla: `Ventas`
| Campo         | Tipo         | Clave |
|---------------|--------------|-------|
| ID_Venta      | NUMBER       | PK    |
| Fecha         | DATE         |       |
| ID_Cliente    | NUMERIC      | FK (Clientes.ID_Cliente) |
| ID_Empleado   | NUMERIC      | FK (Empleados.ID_Empleado) |
| Total         | NUMERIC      |       |

---

### 6. Tabla: `Detalle_Ventas`
| Campo         | Tipo         | Clave |
|---------------|--------------|-------|
| ID_Detalle    | NUMBER       | PK    |
| ID_Venta      | NUMBER       | FK (Ventas.ID_Venta) |
| ID_Producto   | NUMBER       |       |
| Tipo_Producto | VARCHAR(50)  | Indica si es "Ropa" o "Accesorio" |
| Cantidad      | NUMeric      |       |
| Precio_Unitario | NUMERIC    |       |

---

## Relaciones

1. **`Ventas` ➡️ `Clientes`**
   - Relación: **1:N**
   - Campo de relación: `Ventas.ID_Cliente` ➡️ `Clientes.ID_Cliente`

2. **`Ventas` ➡️ `Empleados`**
   - Relación: **1:N**
   - Campo de relación: `Ventas.ID_Empleado` ➡️ `Empleados.ID_Empleado`

3. **`Ventas` ➡️ `Detalle_Ventas`**
   - Relación: **1:N**
   - Campo de relación: `Detalle_Ventas.ID_Venta` ➡️ `Ventas.ID_Venta`

4. **`Detalle_Ventas` ➡️ `Ropa` y `Accesorios`**
   - Relación: **N:M**
   - Campo genérico: `Detalle_Ventas.ID_Producto`
   - Distinción por: `Detalle_Ventas.Tipo_Producto` (que indica si es Ropa o Accesorio)
```

Este formato se puede copiar y pegar directamente en un editor de Markdown o en una herramienta como **GitHub** para documentar el modelo. 😊
