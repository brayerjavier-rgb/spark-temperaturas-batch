# Procesamiento Batch de Temperaturas con Apache Spark

Este repositorio contiene la solución para el procesamiento por lotes (Batch) de datos climáticos utilizando PySpark, desarrollado para la asignatura de Big Data.

## Archivos
*   `temperaturas.csv`: Conjunto de datos de entrada (incluye datos nulos y atípicos para demostrar la limpieza).
*   `batch.py`: Script de Python con la lógica de Spark.
*   `resultado_batch.png`: Imagen con las gráficas generadas por el script.

## Instrucciones para ejecutar
1. Clonar el repositorio o descargar los archivos.
2. Asegurarse de tener Python 3, Java (JDK 17) y PySpark instalados (`pip install pyspark pandas matplotlib`).
3. Ejecutar el script en la terminal:
   ```bash
   python3 batch.py
