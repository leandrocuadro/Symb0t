# Historial de versiones

Registro de cambios de Symb0t, versión por versión. La entrada más reciente va primero.

Cada subida a GitHub agrega una entrada nueva con el número de versión, el título, la fecha, el commit y la lista de cambios. Junto con el README y el CHANGELOG, este archivo se actualiza en cada subida.

---

## v0.4.1 — Sugerencias de campos en formato de oración

**Fecha:** 2026-10-17 · **Commit:** ver `git log` (subida siguiente)

### Cambiado
- Sugerencias de los campos vacíos en formato de oración, sin "Ej:": "Ingresá el nro de cliente", "Ingresá el símbolo del cliente" e "Ingresá parte del nombre del cliente".
- Las sugerencias usan la misma tipografía que el texto de ayuda ("Ingresá un cliente válido para habilitar la carga.").

---

## v0.4.0 — Marca del artículo y botón Limpiar resultado

**Fecha:** 2026-10-17 · **Commit:** `64f79b8`

### Agregado
- Marca del artículo (columna `Marca` de `productos.csv`): debajo del detalle en la búsqueda estándar, y como columna MARCA en la avanzada y en la exportación a Excel.
- Botón **Limpiar resultado** en ambas búsquedas. En la estándar borra el símbolo y el código. En la avanzada borra la tabla, el resumen, las advertencias y el archivo cargado. El nro de cliente se mantiene.

---

## v0.3.0 — Copiar código al hacer clic y ajustes visuales

**Fecha:** 2026-10-17 · **Commit:** `baa3cc8`

### Agregado
- Clic en un código para copiarlo, en ambas búsquedas. El código muestra "¡Copiado!" en verde durante 1,2 segundos. Si el navegador no permite copiar, aparece un aviso.
- Negrita en el texto buscado dentro de las sugerencias del autocompletado de nombre de cliente.

### Cambiado
- Código con el mismo estilo que el buscador de productos internos (pastilla con 📋).
- Advertencias de la búsqueda avanzada en un bloque plegable, con el conteo visible.
- El botón Exportar a Excel se movió encima de la tabla.
- Anchos de columna fijos en la tabla de la búsqueda avanzada.

---

## v0.2.0 — Detalle de producto, nro de cliente compartido y plantilla

**Fecha:** 2026-10-17 · **Commits:** `a26baa4`, `22a5d92`, `525b215`, `5738a69`, `c835b0c`

### Agregado
- Detalle del artículo (columna `Nombre` de `productos.csv`) en la búsqueda estándar, al lado del código, y como columna DETALLE en la avanzada, también incluida en la exportación.
- Campo **Nombre de cliente** con autocompletado en ambas búsquedas, con formato `nro - nombre`. Se navega con flechas, Enter y Esc.
- Botón **Descargar plantilla** en la búsqueda avanzada, con la columna `SIMBOLO`.
- Advertencias cuando un código de `productos.csv` tiene nombres distintos, o cuando no se puede cargar la base de productos.

### Cambiado
- El nro de cliente se replica entre la búsqueda estándar y la avanzada, y se valida en ambas.
- El archivo principal pasa de `Symb0t.html` a `index.html`, para publicarlo en Vercel.
- Logo AltF2 recortado y ajustado en la barra superior.

---

## v0.1.0 — Primer prototipo

**Fecha:** 2026-10-17 · **Commit:** `6fab9c3`

### Agregado
- Búsqueda estándar: nro de cliente → nombre → símbolo → código.
- Búsqueda avanzada: carga de Excel o CSV de una columna, con resultado en NRO ITEM / SIMBOLO / CODIGO.
- Exportación del resultado de la búsqueda avanzada a Excel.
- Validación del cliente en dos pasos, con mensajes separados: el nro no existe en `clientes.csv`, o el cliente no tiene base en `SIMBOLOS`.
- Advertencias (sin modificar datos) cuando un código está asociado a varios símbolos, o un símbolo aparece repetido con códigos distintos.
- Lectura de los CSV desde GitHub, con soporte para UTF-8 (con o sin BOM) y Windows-1252.
- Interfaz en el estilo del buscador de productos internos y del generador de presupuestos.

### Notas
- Los clientes marcados "NO USAR" en `clientes.csv` se excluyen de las búsquedas.
- Las filas vacías en medio del Excel de la búsqueda avanzada se contabilizan como item y dan código `0`.
