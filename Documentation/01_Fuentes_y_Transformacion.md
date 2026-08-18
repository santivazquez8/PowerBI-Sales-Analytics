# 01. Fuentes y Transformación de Datos

## Proceso ETL

El proyecto implementa un proceso **ETL (Extract, Transform, Load)** mediante Power Query en Power BI.

### Extract

Se utilizaron tres fuentes de datos de práctica:

* **XLSX:** clientes, productos, vendedores y ventas.
* **PDF:** métodos de pago.
* **TXT:** información territorial y coordenadas geográficas.

### Transform

Cada fuente fue preparada según sus características, aplicando transformación de tipos de datos, filtrado de registros, eliminación de campos innecesarios, corrección de valores y transformación de códigos.

### Load

Los datos transformados fueron cargados en Power BI y posteriormente integrados en un modelo dimensional mediante relaciones entre las tablas.

---

## 1. Fuente XLSX

El archivo Excel contiene las hojas `Cliente`, `Producto`, `Vendedor` y `Ventas`.

### Cliente

Transformaciones realizadas:

* Promoción de la primera fila como encabezados.
* Conversión de tipos de datos.
* Filtrado de registros sin `Codigo`.
* Eliminación de `Descuento`, `Cliente frecuente` y `Nombre`.

### Producto

Transformaciones realizadas:

* Promoción de encabezados.
* Conversión de tipos de datos.
* Separación de `Codigo unico` utilizando un espacio como delimitador.
* Conversión de la primera parte del código a tipo numérico.
* Filtrado de registros sin código de producto.
* Eliminación de la segunda parte del código.

### Vendedor

Transformaciones realizadas:

* Promoción de encabezados.
* Conversión de tipos de datos.
* Filtrado de registros sin `ID vendedor`.

### Ventas

Transformaciones realizadas:

* Promoción de encabezados.
* Conversión de tipos de datos.
* Conversión de campos de fecha a tipo `date`.
* Eliminación de `Columna 1`.
* Filtrado de registros sin `ID`.

Esta tabla constituye la **tabla de hechos** del modelo.

---

## 2. Fuente PDF — Métodos de Pago

La información fue extraída del PDF mediante `Pdf.Tables`.

Transformaciones realizadas:

* Promoción de encabezados.
* Conversión de tipos de datos.
* Corrección de descripciones truncadas.
* Renombrado de columnas.

Correcciones principales:

| Valor original          | Valor corregido             |
| ----------------------- | --------------------------- |
| `arjeta Debito Maste`   | `Tarjeta Debito Master`     |
| `arjeta de credito Vis` | `Tarjeta de credito Visa`   |
| `ta de credito Maste`   | `Tarjeta de Credito Master` |

Renombrados:

* `Categoría de pagocuento método de p` → `Formas de Pago`
* `Column5` → `Reintegro`

La tabla resultante se utiliza como dimensión de métodos de pago.

---

## 3. Fuente TXT — Territorio

La información territorial fue importada mediante `Csv.Document`, utilizando el tabulador como delimitador.

Transformaciones realizadas:

* Promoción de encabezados.
* Conversión de tipos de datos.
* Conversión de `Latitud` y `Longitud` a tipo numérico.

La tabla contiene:

* `Cod Territorio`
* `País`
* `Continente`
* `Ciudad`
* `Latitud`
* `Longitud`

Esta información permite segmentar las ventas geográficamente y alimentar el mapa utilizado en el dashboard.

---

## Resultado de la transformación

Como resultado del proceso ETL se obtuvieron tablas preparadas para el modelado:

* `Ventas`
* `Cliente`
* `Producto`
* `Vendedor`
* `Territorio`
* `Metodos de Pago`

Estas tablas fueron posteriormente complementadas con la dimensión `Calendario` y la tabla `Medidas` dentro del modelo de Power BI.
