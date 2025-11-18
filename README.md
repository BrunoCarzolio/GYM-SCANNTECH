# GYM-SCANNTECH
Modelo SQL GYM SCANNTECH
# GYM SCANNTECH - CARZOLIO

Es un proyecto de base de datos para un gimnasio que gestiona socios, membresías, clases, empleados y ventas de productos, incluyendo inventario, pedidos, pagos y reseñas.
## Modelo Entidad - Relación

El modelo E-R se adjuntó junto al script en el archivo: **GYM SCANNTECH MODEL - Bruno Carzolio**

## Listado de Tablas

El modelo de datos y la creación de las tablas se organizaron en tres grupos funcionales, clasificados según el tipo de procesos que representan dentro del gimnasio. Esta estructura facilita la comprensión del sistema y separa claramente las actividades operativas, comerciales y administrativas. Los grupos son:

1. Operaciones del Gimnasio y Servicios al Socio

Incluye todas las tablas relacionadas con la gestión de socios, clases, empleados y asistencia.
(Tablas: socios, membresias, empleados, clases, horarios_clases, asistencias)

2. Inventario, Productos y Ventas

Agrupa las entidades necesarias para administrar productos, proveedores, inventario y todo el proceso de ventas.
(Tablas: proveedores, productos, depositos, inventario, imagenes_producto, etiquetas, producto_etiquetas, pedidos, pedido_items)

3. Gestión Administrativa y Finanzas

Reúne los elementos vinculados con pagos, descuentos y evaluaciones de los socios.
(Tablas: cupones, pagos, resenas)
