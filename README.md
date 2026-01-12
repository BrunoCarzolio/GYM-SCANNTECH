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

**ENTREGA 2**
Vistas:
* vista_socios_activos:
Tablas Componentes: socios, membresias
Objetivo: Facilitar consultas rápidas de miembros activos para control de acceso, reportes y gestión diaria del gimnasio. Muestra todos los socios con membresías actualmente vigentes, incluyendo información relevante de contacto, tipo de membresía y días restantes hasta el vencimiento.

* vista_clases_disponibles:
Tablas Componentes: clases, horarios_clases, asistencias, empleados
Objetivo: Permitir a recepción y socios ver rápidamente qué clases tienen espacio para nuevas reservas y facilitar la gestión de inscripciones. Lista las clases programadas con información de cupos disponibles, porcentaje de ocupación, detalles del instructor, horario y sala.

Funciones:
* fn_calcular_edad:
Vista que Complementa: vista_socios_activos
Objetivo: Obtener la edad exacta en años para reportes demográficos, clasificaciones por grupo etario y estadísticas de socios del gimnasio.
Manipula: Recibe la fecha_nacimiento de la tabla socios y retorna un entero con la edad en años completos calculada a partir de la fecha actual del sistema.

* fn_descuento_cupon:
Vista que Complementa: N/A (utilizada principalmente en procesos de venta)
Objetivo: Automatizar cálculos de descuento en el proceso de venta, garantizando que solo se apliquen cupones válidos y vigentes. Valida estado activo del cupón y su vigencia temporal.
Manipula: Tabla cupones. Recibe el código del cupón y el monto original, retorna el monto de descuento aplicable en formato decimal. Valida fechas de vigencia y estado activo del cupón.

Stored Procedures:
* sp_registrar_nuevo_socio:
Parámetros:

IN: @p_nombre, @p_apellido, @p_email, @p_telefono, @p_fecha_nacimiento, @p_tipo_membresia, @p_precio, @p_duracion_dias
OUT: @p_nuevo_socio_id, @p_nueva_membresia_id

Tablas con las que Interactúa: socios, membresias
Objetivo: Simplificar y estandarizar el proceso de alta de socios, asegurando que cada nuevo miembro tenga una membresía asociada desde el momento de su registro. Garantiza la integridad de datos mediante transacciones atómicas y validaciones de campos obligatorios.

* sp_procesar_venta:
Parámetros:

IN: @p_socio_id, @p_codigo_cupon, @p_metodo_pago
OUT: @p_pedido_id, @p_total_final

Tablas con las que Interactúa: pedidos, pedido_items, inventario, pagos, cupones
Objetivo: Ejecutar una transacción atómica que asegure la consistencia de datos en todo el proceso de venta, desde la creación del pedido hasta la actualización de stock y el registro del pago. Aplica descuentos automáticos mediante cupones y calcula totales finales. Garantiza rollback automático en caso de errores.
