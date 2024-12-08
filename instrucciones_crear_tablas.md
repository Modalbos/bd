# Comandos SQL para Crear las Tablas: Tienda de Ropa y Accesorios

## 1. Crear la tabla `Ropa`
```sql
CREATE TABLE Ropa (
    ID_Ropa INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100),
    Talla VARCHAR(10),
    Color VARCHAR(50),
    Precio DECIMAL(10, 2),
    Categoria VARCHAR(50)
);
```

---

## 2. Crear la tabla `Accesorios`
```sql
CREATE TABLE Accesorios (
    ID_Accesorio INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100),
    Tipo VARCHAR(50),
    Color VARCHAR(50),
    Precio DECIMAL(10, 2)
);
```

---

## 3. Crear la tabla `Clientes`
```sql
CREATE TABLE Clientes (
    ID_Cliente INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100),
    Correo VARCHAR(100),
    Telefono VARCHAR(20)
);
```

---

## 4. Crear la tabla `Empleados`
```sql
CREATE TABLE Empleados (
    ID_Empleado INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100),
    Cargo VARCHAR(50)
);
```

---

## 5. Crear la tabla `Ventas`
```sql
CREATE TABLE Ventas (
    ID_Venta INT AUTO_INCREMENT PRIMARY KEY,
    Fecha DATE,
    ID_Cliente INT,
    ID_Empleado INT,
    Total DECIMAL(10, 2),
    FOREIGN KEY (ID_Cliente) REFERENCES Clientes(ID_Cliente),
    FOREIGN KEY (ID_Empleado) REFERENCES Empleados(ID_Empleado)
);
```

---

## 6. Crear la tabla `Detalle_Ventas`
```sql
CREATE TABLE Detalle_Ventas (
    ID_Detalle INT AUTO_INCREMENT PRIMARY KEY,
    ID_Venta INT,
    ID_Producto INT,
    Tipo_Producto VARCHAR(50),  -- 'Ropa' o 'Accesorio'
    Cantidad INT,
    Precio_Unitario DECIMAL(10, 2),
    FOREIGN KEY (ID_Venta) REFERENCES Ventas(ID_Venta)
);
```

---

## Notas Importantes:

- **Tipo de datos**:
    - `INT` es usado para identificadores numéricos (claves primarias o foráneas).
    - `VARCHAR(100)` es usado para cadenas de texto de longitud variable (nombres, correos).
    - `DECIMAL(10, 2)` es usado para almacenar precios, con 2 decimales de precisión.
    - `DATE` es usado para almacenar fechas (por ejemplo, la fecha de la venta).

- **Claves Foráneas**: En las tablas `Ventas` y `Detalle_Ventas`, se definen relaciones con las tablas `Clientes`, `Empleados` y `Ventas`, asegurando la integridad referencial entre las tablas.
