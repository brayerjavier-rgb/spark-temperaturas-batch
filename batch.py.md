from pyspark.sql import SparkSession

from pyspark.sql.functions import when, col



spark = SparkSession.builder \\

&#x20;   .appName("TemperaturasStreaming") \\

&#x20;   .config("spark.jars.packages", "org.apache.spark:spark-sql-kafka-0-10\_2.12:3.5.0") \\

&#x20;   .getOrCreate()



df = spark.readStream.format("kafka") \\

&#x20;   .option("kafka.bootstrap.servers", "localhost:9092") \\

&#x20;   .option("subscribe", "temperaturas") \\

&#x20;   .load()



\# ¡Aquí está la corrección del cast string!

df = df.select(col("value").cast("string").cast("float").alias("temperatura"))



df = df.withColumn("tipo",

&#x20;   when(col("temperatura") >= 30, "caluroso").otherwise("frio"))



resultado = df.groupBy("tipo").count()



query = resultado.writeStream \\

&#x20;   .outputMode("complete") \\

&#x20;   .format("console") \\

&#x20;   .start()



query.awaitTermination()

