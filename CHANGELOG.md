# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

Para el registro resumido por versión, ver [HISTORIAL.md](HISTORIAL.md).

## [0.5.0] - 2026-10-17

### Agregado
- Búsqueda estándar: datos adicionales del artículo (Código alternativo, Característica, Cantidad por bulto y Tipo de reposición), en letra más chica debajo de la marca.

### Cambiado
- Búsqueda estándar: el resultado se ordena por relevancia. Primero el detalle del artículo (grande), después la marca (destacada) y por último los datos menores.

## [0.4.1] - 2026-10-17

### Cambiado
- Sugerencias de los campos vacíos en formato de oración, sin "Ej:": "Ingresá el nro de cliente", "Ingresá el símbolo del cliente" e "Ingresá parte del nombre del cliente". Usan la misma tipografía que el texto de ayuda.

## [0.4.0] - 2026-10-17

### Agregado
- Marca del artículo (columna `Marca` de `productos.csv`): debajo del detalle en la búsqueda estándar, y como columna MARCA en la avanzada y en la exportación a Excel.
- Botón **Limpiar resultado** en ambas búsquedas. En la estándar borra el símbolo y el código; en la avanzada borra la tabla, el resumen, las advertencias y el archivo cargado. El nro de cliente se mantiene.

## [0.3.0] - 2026-10-17

### Agregado
- Clic en un código para copiarlo, en ambas búsquedas. El código muestra "¡Copiado!" en verde durante 1,2 segundos. Si el navegador no permite copiar, aparece un aviso.
- Negrita en el texto buscado dentro de las sugerencias del autocompletado de nombre de cliente.

### Cambiado
- Advertencias de la búsqueda avanzada en un bloque plegable, con el conteo visible.
- El botón Exportar a Excel se movió encima de la tabla.
- Anchos de columna fijos en la tabla de la búsqueda avanzada (DETALLE ocupa el espacio restante).
- El código del resultado de la búsqueda estándar tiene el mismo estilo que en el buscador de productos internos.

## [0.2.0] - 2026-10-17

### Agregado
- Detalle del artículo (columna `Nombre` de `productos.csv`) en la búsqueda estándar, al lado del código.
- Detalle del artículo en la búsqueda avanzada, como nueva columna DETALLE, también incluida en la exportación a Excel.
- Campo **Nombre de cliente** con autocompletado en ambas búsquedas, con formato `nro - nombre`. Se navega con flechas, Enter y Esc.
- Botón **Descargar plantilla** en la búsqueda avanzada, con la columna `SIMBOLO`.
- Advertencias cuando un código de `productos.csv` tiene nombres distintos, o cuando no se puede cargar la base de productos.

### Cambiado
- El nro de cliente se replica entre la búsqueda estándar y la avanzada, y se valida en ambas.
- El archivo principal pasa de `Symb0t.html` a `index.html`, para publicarlo en Vercel.
- Nuevo logo AltF2, recortado y ajustado en la barra superior.

## [0.1.0] - 2026-10-17

### Agregado
- Búsqueda estándar: nro de cliente → nombre → símbolo → código.
- Búsqueda avanzada: carga de Excel o CSV de una columna, con resultado en NRO ITEM / SIMBOLO / CODIGO.
- Exportación del resultado de la búsqueda avanzada a Excel.
- Validación del cliente en dos pasos, con mensajes separados:
  - el nro no existe en `clientes.csv`;
  - el cliente no tiene base en `SIMBOLOS`.
- Advertencias (sin modificar datos) cuando un código está asociado a varios símbolos o un símbolo aparece repetido con códigos distintos.
- Lectura de los CSV desde GitHub, con soporte para UTF-8 (con o sin BOM) y Windows-1252.
- Interfaz en el estilo del buscador de productos internos y del generador de presupuestos.

### Notas
- Los clientes marcados "NO USAR" en `clientes.csv` se excluyen de las búsquedas.
- Las filas vacías en medio del Excel de la búsqueda avanzada se contabilizan como item y dan código `0`.
- Si un símbolo aparece repetido en su base con códigos distintos, se usa el primero y se advierte.
