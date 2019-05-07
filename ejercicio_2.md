### OBJETIVO
* Ingestar datos desde base de dato de forma incremental

### GUIA
1. Buscar el ultimo valor del campo de corte en Hue.  

Entrar http://52.23.213.56:8888/hue y ejecutar la query 

`SELECT max(orden_trabajo_id) FROM tu_nombre` 

2. Ejecutar la in    
`sqoop import --driver com.mysql.jdbc.Driver --connect jdbc:mysql://10.0.0.101:3306/taller --username taller --password taller --table orden --split-by orden_trabajo_id --hive-import --hive-table default.tu_nombre --incremental append --check-column orden_trabajo_id --last-value ultmo_valor`

3. Ver los nuevos registros  
`SELECT orden_trabajo_id FROM default.tu_nombre ORDER BY orden_trabajo_id desc LIMIT 20`

4. Revisar los nuevos archivos ingestados en el directorio HDFS  
`hdfs dfs -ls /user/hive/warehouse/tu_nombre`

5. Imprime el contenido de uno de los archivos  
`hdfs dfs -cat /user/hive/warehouse/tu_nombre/part-00005`


