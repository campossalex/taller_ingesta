### OBJETIVO
* Ingestar datos desde base de datos

### PREPARACION 
Ejecutar export HADOOP_USER_NAME=hdfs

Crear carpeta:
hdfs dfs -mkdir /user/tu_nombre/  
Cambiar tu_nombre por su primer nombre

### GUIA
1. El instructor mostrará el formato de datos

2. Verificar si existe conexión con la base de datos    
`sqoop list-tables --driver com.mysql.jdbc.Driver --connect jdbc:mysql://10.0.0.101:3306/taller --username taller --password taller`

Deberá listada la tabla "orden" de la base de datos.  

3. Ejecutar el siguiente comando de Sqoop  
`sqoop import --driver com.mysql.jdbc.Driver --connect jdbc:mysql://10.0.0.101:3306/taller --username taller --password taller --table orden --split-by orden_trabajo_id --hive-import --hive-table default.tu_nombre`

4. Revisar los archivos ingestados en el directorio HDFS  
`hdfs dfs -ls /user/hive/warehouse/tu_nombre`

5. Imprime el contenido de uno de los archivos  
`hdfs dfs -cat /user/hive/warehouse/tu_nombre/part-00000`


