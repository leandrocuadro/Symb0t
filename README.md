# Symb0t

Búsqueda de códigos internos a partir del símbolo de catalogación de un cliente.

Symb0t ayuda a los vendedores a relacionar la catalogación de un cliente (**símbolo**) con el código de producto de la empresa (**código**). Cuando un cliente pide una cotización indicando su símbolo, la app devuelve el código interno y el detalle del artículo.

## Uso

El **nro de cliente** es común a las dos búsquedas: lo que se ingresa en una se replica en la otra y se valida en ambas.

Si no recordás el nro de cliente, escribí parte del nombre en el campo **Nombre de cliente**. Aparecen sugerencias con el formato `nro - nombre`; al elegir una, se carga el nro.

### Búsqueda estándar

1. Ingresá el **nro de cliente** (o elegilo por nombre).
2. Si el cliente existe y tiene base de símbolos cargada, se habilita el campo **Símbolo**.
3. Ingresá el símbolo y hacé clic en **Buscar** (o presioná Enter).
4. Se muestran el **código** interno, el **detalle** del artículo y su **marca**. Hacé clic en el código para copiarlo.
5. Si querés hacer otra consulta con el mismo cliente, usá **Limpiar resultado** para borrar el símbolo y el código.

### Búsqueda avanzada

1. Ingresá el **nro de cliente** (o elegilo por nombre) y verificá la validación.
2. Si necesitás, descargá la **plantilla** Excel con la columna `SIMBOLO`.
3. Cargá un archivo **Excel o CSV de una sola columna** con los símbolos a buscar. La primera fila es el encabezado.
4. La tabla muestra **NRO ITEM**, **SIMBOLO**, **CODIGO**, **DETALLE** y **MARCA**:
   - El nro de item sigue el orden de las filas: la fila 2 del archivo es el item 1.
   - Si un símbolo no existe en la base del cliente, el código es `0` y el detalle queda vacío.
5. Hacé clic en un código para copiarlo.
6. Exportá el resultado a Excel con el botón que está encima de la tabla. La exportación incluye las columnas DETALLE y MARCA.
7. Con **Limpiar resultado** se borran la tabla, el resumen y el archivo cargado. El nro de cliente se mantiene.

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
- **Productos:** `leandrocuadro/productos.csv/productos.csv`, con las columnas `Código;Código alternativo;Nombre;Marca;Descripción;Característica;Tipo de reposición;Cantidad por bulto`. Se usan `Código` (para cruzar con el código de la base del cliente) y `Nombre` (detalle).

Cada base de cliente se agrega como un archivo nuevo con el nro de cliente como nombre. Por ejemplo, la base de Mastellone es `22434.csv`.

### Formato de las bases de símbolos

- Separador `;`, con encabezado `simbolo;codigo`.
- Codificación UTF-8 (con o sin BOM). Si el archivo está en Windows-1252, la app lo decodifica automáticamente.
- Si un mismo código corresponde a varios símbolos, la app lo **advierte** sin modificar la base. La revisión de la base es responsabilidad de quien la carga.

### Advertencias

Sin modificar datos, la app advierte cuando (las advertencias se muestran en un bloque plegable, con el conteo y el detalle al desplegarlo):

- un código está asociado a varios símbolos en la base del cliente;
- un símbolo aparece repetido en su base con códigos distintos (se usa el primero);
- un código aparece en `productos.csv` con nombres distintos (se muestra el primero);
- no se puede cargar la base de productos (el detalle no está disponible).

## Ejecutar localmente

Descargá `index.html` y abrilo en el navegador. Necesita conexión a internet para leer los CSV de GitHub y la librería SheetJS (lectura y exportación de Excel).

El logo se toma del archivo `LOGO AltF2.png` en la misma carpeta. Si no existe, se muestra el texto "AltF2".

## Estado

Versión 0.4.1 (prototipo). Solo lectura: las altas de vínculos símbolo ↔ código están previstas para una versión posterior, con almacenamiento escribible.

Ver [HISTORIAL.md](HISTORIAL.md) para el registro de cambios versión por versión, y [CHANGELOG.md](CHANGELOG.md) para el detalle técnico.

## Diseño

Interfaz en el mismo estilo que el buscador de productos internos y el generador de presupuestos. Diseño: AltF2.
