# Reglas de Oro para Optimización en Spark

Este documento presenta las mejores prácticas identificadas durante el laboratorio para mejorar el rendimiento en Apache Spark.

## ✅ Persistencia Estratégica

- Usar `persist(StorageLevel.MEMORY_AND_DISK)` en transformaciones costosas.
- Evitar `cache()` si los datos no caben completamente en memoria.

## ✅ Particionamiento Inteligente

- Aumentar las particiones: `spark.sql.shuffle.partitions = 2-4 * núm. de núcleos`
- Usar `.repartition(columna)` en lugar de `.coalesce()` para cargas balanceadas.

## ✅ Formatos de Salida Eficientes

- Preferir formatos columnares: `Parquet`, `ORC` (mejor compresión y escaneo).
- Usar `.write.parquet()` en lugar de `.csv` para outputs grandes.

## ✅ Optimización SQL + Catalyst

- Filtrar antes de agrupar (`push-down filters`).
- Aprovechar vistas temporales y expresiones SQL para el motor Catalyst.

## 🧠 Analogía útil

> "Los RDD son como arcilla en bruto que tienes que moldear a mano, los DataFrames son piezas de cerámica ya moldeadas listas para usar, y SQL es como comprar una vajilla completa y decorada, lista para la mesa."

## 🛠️ Checklist de Optimización

- [x] Persistencia en operaciones clave
- [x] Repartición controlada
- [x] Uso de formatos columnares
- [x] Reducción de shuffles innecesarios
- [x] Consultas SQL optimizadas
