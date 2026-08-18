# 03. Medidas DAX

## Introducción

Se desarrollaron medidas DAX para centralizar los principales indicadores utilizados en los dashboards.

Las medidas se almacenaron en la tabla `Medidas`, manteniendo separada la lógica de cálculo de las tablas de datos.

## 1. Ventas Totales

```DAX
Ventas Totales = SUM(Ventas[Ventas])
```

Calcula el total de ventas acumulando los valores registrados en `Ventas[Ventas]`.

Se utiliza como principal indicador de facturación y como base para el cálculo de rentabilidad.

## 2. Costos Totales

```DAX
Costos Totales = SUM(Ventas[Costos])
```

Calcula el total de costos asociados a las ventas.

Permite analizar la estructura de costos y comparar los costos con el nivel de ventas generado.

## 3. Cant Unidades Vendidas

```DAX
Cant Unidades Vendidas = SUM(Ventas[Cantidad ])
```

Calcula la cantidad total de unidades vendidas.

Se utiliza como indicador del volumen comercial de las operaciones.

## 4. Avg Diff Dias

```DAX
Avg Diff Dias = AVERAGE(Ventas[Diferencia de Dias])
```

Calcula el promedio de la diferencia de días registrada en las ventas.

Permite evaluar el comportamiento promedio de los tiempos asociados a las operaciones y complementa el análisis del cumplimiento de entregas.

## 5. Rentabilidad

```DAX
Rentabilidad =
DIVIDE(
    [Ventas Totales] - [Costos Totales],
    [Ventas Totales],
    0
)
```

Calcula el margen sobre ventas a partir de la diferencia entre las ventas totales y los costos totales.

La función `DIVIDE()` permite realizar la división de forma segura y devuelve `0` cuando el denominador es cero.

El resultado se expresa como porcentaje.

## Resumen de medidas

| Medida                   | Función principal                         |
| ------------------------ | ----------------------------------------- |
| `Ventas Totales`         | Calcula la facturación total              |
| `Costos Totales`         | Calcula los costos totales                |
| `Cant Unidades Vendidas` | Calcula el volumen total de unidades      |
| `Avg Diff Dias`          | Calcula el promedio de diferencia de días |
| `Rentabilidad`           | Calcula el margen sobre ventas            |

## Uso en los dashboards

Las medidas se utilizan como indicadores y valores dinámicos en las diferentes visualizaciones del proyecto.

Al estar definidas como medidas DAX, sus resultados responden dinámicamente a los filtros aplicados en el dashboard, permitiendo analizar los indicadores por dimensiones como:

* Tiempo
* Cliente
* Producto
* Vendedor
* Territorio
* Método de pago

