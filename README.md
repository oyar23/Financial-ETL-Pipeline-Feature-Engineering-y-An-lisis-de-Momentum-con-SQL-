### Financial ETL Pipeline: Feature Engineering y Análisis de Momentum con SQL 

Este proyecto implementa un Pipeline ETL (Extract, Transform, Load) para transformar datos históricos de acciones (AAPL, MSFT, TSLA) en métricas financieras procesables. El objetivo principal es aplicar técnicas avanzadas de SQL (Funciones de Ventana) y Python para crear features valiosos para el análisis técnico, que son esenciales en la preparación de datos para modelos de forecasting y dashboards de trading.

# Flujo del pipeline y metodología sql 

El pipeline aborda el problema de la siguiente manera:

    Extracción (Extract): Se extraen los datos históricos de precios, dividendos y stock splits para Apple (AAPL), Microsoft (MSFT) y Tesla (TSLA) utilizando la librería yfinance.

    Transformación Avanzada (Transform): En esta capa, se realizan dos tipos de enriquecimiento de datos esenciales:

        Limpieza y Normalización: Se calcula el daily_return y se ajustan las fechas para la base de datos.

        Feature Engineering con SQL: Se utiliza la potencia de las Funciones de Ventana SQL y CTEs (Common Table Expressions) para generar métricas técnicas directamente sobre la base de datos (SQLite).

    Carga (Load): Los datos enriquecidos se consolidan en la tabla prices_enriched de la base de datos SQLite, dejando la información lista para el consumo.

Las consultas SQL avanzadas fueron críticas para generar la inteligencia del negocio. Por ejemplo, utilizamos AVG(Close) OVER (...) para calcular el Promedio Móvil de 30 días, y SUM(LOG(...)) OVER (...) para medir el Retorno Acumulado, sentando las bases para el análisis de rendimiento y riesgo.

# Análisis y Resultados Claves 
Este proyecto produce features esenciales para cualquier analista o modelo de trading:

    Retorno Acumulado (Log Returns): Mide el rendimiento compuesto real de los activos a largo plazo.

    Promedio Móvil (Moving Average): Define la tendencia subyacente y la suaviza.

    Desviación del MA (Momentum): Cuantifica qué tan lejos está el precio actual de su tendencia, lo cual es vital para identificar condiciones de sobrecompra o sobreventa.
   
