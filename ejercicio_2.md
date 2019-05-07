### OBJETIVO
* Ingestar datos desde base de dato de forma incremental

### GUIA
1. Buscar el ultimo valor del campo 

2. Verificar si existe conexión con la base de datos    
`sqoop list-tables --driver com.mysql.jdbc.Driver --connect jdbc:mysql://10.0.0.101:3306/taller --username taller --password taller`

Deberá listada la tabla "orden" de la base de datos.  

3. Ejecutar el siguiente comando de Sqoop  
`sqoop import --driver com.mysql.jdbc.Driver --connect jdbc:mysql://10.0.0.101:3306/taller --username taller --password taller --table orden --split-by orden_trabajo_id --target-dir /user/tu_nombre/orden_trabajo --hive-import --hive-table tu_nombre`

4. Revisar los archivos ingestados en el directorio HDFS  
`hdfs dfs -ls /user/tu_nombre/orden_trabajo`

5. Imprime el contenido de uno de los archivos  
`hdfs dfs -cat /user/tu_nombre/orden_trabajo/part-00000`


