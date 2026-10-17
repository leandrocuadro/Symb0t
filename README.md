# Symb0t

Búsqueda de códigos internos a partir del símbolo de catalogación de un cliente.

Symb0t ayuda a los vendedores a relacionar la catalogación de un cliente (**símbolo**) con el código de producto de la empresa (**código**). Cuando un cliente pide una cotización indicando su símbolo, la app devuelve el código interno correspondiente.

## Uso

### Búsqueda estándar

1. Ingresá el **nro de cliente**.
2. Si el cliente existe y tiene base de símbolos cargada, aparece su nombre y se habilita el campo **Símbolo**.
3. Ingresá el símbolo y hacé clic en **Buscar** (o presioná Enter).
4. Se muestra el **código** interno.

### Búsqueda avanzada

1. Ingresá el **nro de cliente** y verificá el nombre.
2. Cargá un archivo **Excel o CSV de una sola columna** con los símbolos a buscar. La primera fila es el encabezado.
3. La tabla muestra **NRO ITEM**, **SIMBOLO** y **CODIGO**:
   - El nro de item sigue el orden de las filas: la fila 2 del archivo es el item 1.
   - Si un símbolo no existe en la base del cliente, el código es `0`.
4. Exportá el resultado a Excel con el botón correspondiente.

## Reglas de validación

Ambas búsquedas siguen el mismo orden:

| Caso | Mensaje | Resultado |
|---|---|---|
| El nro no existe en `clientes.csv` | "El nro de cliente no existe en la base de clientes." | La consulta queda vacía. |
| El cliente existe, pero no tiene `SIMBOLOS/<nro>.csv` | "El cliente no tiene base de símbolos cargada." | La consulta queda vacía. |
| Ambas condiciones se cumplen | — | Se habilita la búsqueda. |

## Fuentes de datos

Symb0t lee los datos directamente desde GitHub:

- **Clientes:** `leandrocuadro/clientesegu/clientes.csv`, con las columnas `codigo;nombre`.
- **Bases de símbolos:** `leandrocuadro/SIMBOLOS/<nro_cliente>.csv`, con las columnas `simbolo;codigo`.

Cada base de cliente se agrega como un archivo nuevo con el nro de cliente como nombre. Por ejemplo, la base de Mastellone es `22434.csv`.

### Formato de las bases de símbolos

- Separador `;`, con encabezado `simbolo;codigo`.
- Codificación UTF-8 (con o sin BOM). Si el archivo está en Windows-1252, la app lo decodifica automáticamente.
- Si un mismo código corresponde a varios símbolos, la app lo **advierte** sin modificar la base. La revisión de la base es responsabilidad de quien la carga.

## Ejecutar localmente

Descargá `index.html` (o `Symb0t.html`) y abrilo en el navegador. Necesita conexión a internet para leer los CSV de GitHub y la librería SheetJS (lectura y exportación de Excel).

El logo se toma del archivo `LOGO AltF2.png` en la misma carpeta. Si no existe, se muestra el texto "AltF2".

## Estado

Versión 0.1 (prototipo). Solo lectura: las altas de vínculos símbolo ↔ código están previstas para una versión posterior, con almacenamiento escribible.

Ver [CHANGELOG.md](CHANGELOG.md) para el historial de cambios.

## Diseño

Interfaz en el mismo estilo que el buscador de productos internos y el generador de presupuestos. Diseño: AltF2.
