# Sales Analytics – Power BI

## Descripción

Proyecto de análisis de ventas desarrollado en Power BI, orientado al análisis de ventas, costos, rentabilidad, distribución geográfica y cumplimiento de entregas.

## Objetivo

Construir un dashboard interactivo que permita analizar el desempeño comercial desde diferentes perspectivas: tiempo, cliente, producto, vendedor, territorio y método de pago.

## Datos y transformación

El proyecto utiliza tres fuentes de datos de práctica:

* Archivo Excel con información de ventas, clientes, productos y vendedores.
* Archivo PDF con métodos de pago.
* Archivo TXT con información territorial.

Los datos fueron preparados y transformados mediante **Power Query**, realizando limpieza de registros, modificación de tipos de datos, eliminación de columnas innecesarias, corrección de valores y transformación de códigos.

## Modelo y DAX

Se construyó un modelo de datos basado en un **Star Schema**, con `Ventas` como tabla de hechos y las dimensiones `Cliente`, `Producto`, `Vendedor`, `Territorio`, `Metodos de Pago` y `Calendario`.

Se desarrollaron medidas DAX para analizar:

* Ventas Totales
* Costos Totales
* Rentabilidad
* Cantidad de Unidades Vendidas
* Promedio de Diferencia de Días

## Dashboard

### Overview

![Overview](Overview.png)

### Detalle de Ventas

![Detalle de Ventas](Detalle_de_Ventas.png)

## Insights principales

* El **99,12 %** de las operaciones se encuentran en tiempo, frente a un **0,88 %** vencidas.
* La zona **Sur** concentra aproximadamente el **37,3 %** de las ventas, con $513 M.
* La diferencia entre la zona Sur y Occidente alcanza aproximadamente **$292 M**.
* Los productos de tamaño **Grande** concentran aproximadamente el **32,6 %** de los costos.
* El margen sobre ventas calculado en el modelo alcanza el **79,73 %**.

## Herramientas

**Power BI · Power Query · DAX**
