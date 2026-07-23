¿Por qué usaste LEFT JOIN para la Consulta 1 y no INNER JOIN? ¿Qué se perdería si usaras INNER JOIN?
 Use LEFT JOIN porque necesitaba mostrar todos los productos del catálogo, incluso aquellos que nunca fueron vendidos. Si hubiera utilizado INNER JOIN, solo se mostrarían los productos que tienen una venta asociada ( solo filas con coincidencia) y se perderían los productos 108 (Hub USB-C 7p) y 109 (Parlante Bluetooth), ya que no tienen registros en la tabla ventas.
 
¿Por qué usaste RIGHT JOIN para la Consulta 2? ¿Qué tabla está a la izquierda y cuál a la derecha en tu consulta?
Utilicé RIGHT JOIN porque necesitaba mostrar todas las ventas, incluso aquellas que no tienen un producto asociado en el catálogo. En la consulta, la tabla `productos` está a la izquierda y la tabla `ventas` está a la derecha. De esta forma se puede identificar la venta con `producto_id = 999`, que no existe en la tabla productos.

¿Qué representan los valores NULL en cada resultado? Explicá con un ejemplo concreto de los datos qué significa que venta_id sea NULL en la Consulta 1 y que producto_id de productos sea NULL en la Consulta 2.
Los valores NULL indican que no existe una coincidencia entre las tablas.
En la Consulta 1, un `venta_id` igual a NULL significa que el producto nunca fue vendido. Por ejemplo, los productos 108 y 109 aparecen con NULL porque no tienen registros en la tabla ventas.
En la Consulta 2, un `producto_id` de la tabla productos igual a NULL significa que existe una venta cuyo producto no está registrado en el catálogo. En este caso corresponde a la venta 10 con `producto_id = 999`.

¿Cuándo usarías FULL OUTER JOIN en un caso real de negocio?
Utilizaría FULL OUTER JOIN cuando necesite realizar una auditoría completa de los datos y detectar inconsistencias. Por ejemplo, para encontrar productos que nunca se vendieron, ventas registradas con productos inexistentes o cualquier registro que no tenga correspondencia entre ambas tablas. Esto permite identificar errores de carga de datos y mejorar la calidad de la información antes de generar reportes o dashboards.
