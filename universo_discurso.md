# Universo de Discurso

## Descripción General

Objetivo principal gestionar las operaciones de una tienda de ropa y accesorios. La tienda ofrece productos, incluyendo ropa de diferentes tallas y colores, así como accesorios como joyas, relojes y otros artículos. La base de datos está diseñada para manejar la información de clientes, empleados, productos, ventas y los detalles asociados a cada venta.

## Entidades Principales

### 1. **Ropa**
Representa todos los artículos de vestimenta disponibles en la tienda. Cada prenda tiene un nombre, una talla, un color, un precio y una categoría (como camisas, pantalones, chaquetas, etc.).

### 2. **Accesorios**
Almacena la información de los accesorios disponibles, como joyas, relojes y otros artículos de moda. Cada accesorio tiene un nombre, un tipo (por ejemplo, reloj, anillo, pulsera), color y precio.

### 3. **Clientes**
Esta entidad almacena la información de los clientes de la tienda, quienes pueden comprar ropa y accesorios. Cada cliente tiene un identificador único (ID), un nombre, correo electrónico y número de teléfono.

### 4. **Empleados**
Representa a los empleados que trabajan en la tienda. Cada empleado tiene un identificador único (ID), un nombre y un cargo (por ejemplo, cajero, vendedor, encargado de tienda).

### 5. **Ventas**
Almacena las transacciones realizadas en la tienda. Cada venta tiene un identificador único (ID), una fecha, un cliente asociado, un empleado que la procesó y el total de la venta.

### 6. **Detalle de Ventas**
Cada detalle de venta está relacionado con una venta específica e incluye información sobre el producto (Ropa o Accesorio), la cantidad comprada, y el precio unitario de ese artículo.

## Relaciones Entre Entidades

1. **Clientes y Ventas**
   - Un cliente puede realizar muchas compras (ventas), pero cada venta está asociada a un solo cliente.
   - Relación **1:N** entre `Clientes` y `Ventas`.

2. **Empleados y Ventas**
   - Un empleado puede procesar muchas ventas, pero cada venta es procesada por un solo empleado.
   - Relación **1:N** entre `Empleados` y `Ventas`.

3. **Ventas y Detalle de Ventas**
   - Cada venta puede tener múltiples productos asociados, y cada producto está vinculado a una sola venta.
   - Relación **1:N** entre `Ventas` y `Detalle_Ventas`.

4. **Detalle de Ventas y Productos**
   - Los productos vendidos pueden ser tanto de la tabla `Ropa` como de `Accesorios`. Cada detalle de venta puede hacer referencia a un artículo de cualquiera de estas dos tablas.
   - Relación **N:M** entre `Detalle_Ventas` y `Ropa` / `Accesorios` a través del campo `Tipo_Producto`, que distingue entre ambos tipos de productos.

## Objetivos del Sistema

El sistema tiene como propósito facilitar las siguientes funciones:
- **Gestión de Inventarios**: Seguimiento de las existencias de ropa y accesorios disponibles en la tienda.
- **Procesamiento de Ventas**: Registrar cada venta realizada, asociando los productos comprados, el cliente, y el empleado que procesó la venta.
- **Atención al Cliente**: Mantener un registro de los clientes para ofrecer un mejor servicio personalizado, con la posibilidad de contactarles por correo o teléfono.
- **Gestión de Empleados**: Mantener un registro de los empleados que trabajan en la tienda, sus cargos y las ventas que han procesado.
- **Control de Precios**: Establecer precios para cada producto y calcular el total de las ventas realizadas.

