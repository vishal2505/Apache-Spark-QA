CREATING EXTERNAL TABLE

	CREATE EXTERNAL TABLE IF NOT EXISTS EMPLOYEES (
	EMP_NO INT,
	BIRTH_DATE STRING,
	FIRST_NAME STRING,
	LAST_NAME STRING,
	GENDER VARCHAR(1),
	HIRE_DATE STRING
	)
	ROW FORMAT DELIMITED
	FIELDS TERMINATED BY ',' 
	LINES TERMINATED BY '\n'
	LOCATION '/user/hortonworks/employees.db/employees'

NOTE: WITHOUT ROW FORMAT SPECIFICATION ABOVE WILL NOT CORRECTLY READ EXTERNAL DATA

CREATE TABLE WITH PARQUET SERDE
	
	CREATE TABLE EMP_PARQ (
	EMP_NO INT,
	BIRTH_DATE STRING,
	FIRST_NAME STRING,
	LAST_NAME STRING,
	GENDER STRING,
	HIRE_DATE STRING)
	STORED AS PARQUET; 

CREATE TABLE WITH AVRO FILE FORMAT

	CREATE TABLE orders_avro 
	ROW FORMAT SERDE
	  'org.apache.hadoop.hive.serde2.avro.AvroSerDe'
	  STORED AS INPUTFORMAT
	  'org.apache.hadoop.hive.ql.io.avro.AvroContainerInputFormat'
	  OUTPUTFORMAT
	  'org.apache.hadoop.hive.ql.io.avro.AvroContainerOutputFormat'
	  TBLPROPERTIES ('avro.schema.url' = 'hdfs://quickstart.cloudera:8020/user/cloudera/orders.avsc');
	  
CREATE TABLE WITH JSON SERDE

	ADD JAR '/usr/lib/hive-hcatalog/share/hcatalog/hive-hcatalog-core.jar';


	CREATE TABLE JSON_TABLE (product_id int,
	product_cat_id int,
	product_name string,
	product_description string,
	product_price double,
	product_image string)
	ROW FORMAT SERDE
	'org.apache.hive.hcatalog.data.JsonSerDe' 
	STORED AS TEXTFILE;

CREATE PARTITIONED TABLE :
  	
	CREATE TABLE IF NOT EXISTS EMP_PARTITIONED (
  	EMP_NO INT,
  	BIRTH_YEAR STRING,
 	FIRST_NAME STRING,
 	LAST_NAME STRING,
  	HIRE_DATE STRING)
  	PARTITIONED BY (HIRE_YEAR INT)
  	ROW FORMAT DELIMITED
  	FIELDS TERMINATED BY '\t'
  	LINES TERMINATED BY '\n';

create a static partition : 

	ALTER TABLE EMP_PARTITIONED ADD PARTITIONED (HIRE_YEAR = 2016)

inserting into partition :

	INSERT INTO TABLE EMP_PARTITIONED PARTITION (HIRE_YEAR = 2016)
	VALUES (10001,'1984','HELENA','BARBA','2016-01-01');

CREATING DYNAMIC PARTITION :

	set hive.exec.dynamic.partition.mode = nonstrict;
	set hive.exec.max.dynamic.partitions = 2000;
	set hive.exec.max.dynamic.partitions.pernode = 2000;

	INSERT OVERWRITE TABLE EMP_PARTITIONED 
	PARTITION (HIRE_YEAR)
	SELECT EMP_NO, SUBSTR(BIRTH_DATE,1,4) AS BIRTH_YEAR,FIRST_NAME,LAST_NAME,
	HIRE_DATE,SUBSTR(HIRE_DATE,1,4) AS HIRE_YEAR 
	FROM DEFAULT.EMPLOYEES;

