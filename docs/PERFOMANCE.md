# Comparación de Rendimiento: RDD vs DataFrame vs SQL

Este documento presenta un análisis comparativo entre los enfoques de procesamiento en Apache Spark: RDD, DataFrame y SQL, utilizando la misma operación de agregación (promedio de calificaciones por producto).

## ⚙️ Escenario

- Dataset: `/data/Books_rating.csv`
- Operación: Calcular el promedio de calificación (`rating`) por `book_id`
- Condición: Agrupar y filtrar `avg_rating > 3.5`

## ⏱️ Tiempos de ejecución (aproximados)

| Enfoque    | Tiempo (segundos) | Persistencia Usada |
|------------|-------------------|---------------------|
| RDD        | 11.015            | MEMORY_ONLY         |
| DataFrame  | 4.427             | MEMORY_AND_DISK     |
| Spark SQL  | 2.8               | MEMORY_AND_DISK     |

## 📊 Visualización

```python
import matplotlib.pyplot as plt

etiquetas = ['RDD', 'DataFrame', 'SQL']
tiempos = [11.015, 4.427, 2.8]

plt.bar(etiquetas, tiempos, color=['red', 'green', 'blue'])
plt.ylabel("Tiempo (s)")
plt.title("Comparación de Rendimiento")
plt.show()