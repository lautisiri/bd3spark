# Laboratorio Spark: Movilidad STM Montevideo

Base de Datos III, Universidad de Montevideo. A. Perez, L. Rocumpaj, L. Siri.

Pipeline de datos de movilidad del Sistema de Transporte Metropolitano (STM) en Databricks, siguiendo la Medallion Architecture (bronze, silver y gold) con tablas Delta.

## Notebooks (orden de ejecución)

| # | Notebook | Capa | Qué hace |
|---|---|---|---|
| 1 | `01_descarga_movilidad_stm_a_volumes` | Raw | Descarga viajes y horarios desde la API de CKAN de la Intendencia al volumen `workspace.movilidad.raw` |
| 2 | `02_bronze` | Bronze | Convierte los CSV a tablas Delta en `movilidad_bronze` (todo como texto) |
| 3 | `03_control_completitud` | Control | Verifica que no falten meses ni días de viajes |
| 4 | `04_silver` | Silver | Limpieza, tipado, deduplicación y validaciones en `movilidad_silver` |
| 5 | `05_paradas_ubicacion` | Raw / Silver | Ubicación de paradas: UTM 21S a latitud/longitud |
| 6 | `06_gold` | Gold | Métricas para la Intendencia en `movilidad_gold` |
| 7 | `07_gold_mapa_cobertura` | Gold | Cobertura por zona (H3) y hora, y mapa interactivo |

Los notebooks están pensados para ejecutarse en Databricks: usan `spark`, `dbutils` y `display`, y los parámetros (catálogo y esquemas) se configuran con widgets.
