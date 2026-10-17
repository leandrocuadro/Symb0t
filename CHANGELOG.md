# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

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
