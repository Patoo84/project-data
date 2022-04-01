Ingest files from the site :
https://www.ecobici.cdmx.gob.mx/en/informacion-del-servicio/open-data

download from the site file csv 
set the architecture via Terraform 
gcs and dataset via bigquery 
transform via airflow :

![image](https://user-images.githubusercontent.com/93529690/161269038-d6a29e88-7a93-4fb3-af56-aa2162109362.png)


change the external table to non partionned Table with transformation 
CREATE OR REPLACE TABLE `dtc-de-project-344521.dataset.mexbike_non_partitioned` AS
SELECT Genero_Usuario,Edad_Usuario,Bici,Ciclo_Estacion_Retiro,safe.PARSE_DATE('%m/%d/%Y',  Fecha_Retiro) as Fecha_Retiro,PARSE_TIME("%T", Hora_Retiro) as Hora_Retiro,Ciclo_Estacion_Arribo,
PARSE_DATE('%d/%m/%Y',  Fecha_Arribo) as Fecha_Arribo,PARSE_TIME("%T", Hora_Arribo) as Hora_Arribo

 FROM `dtc-de-project-344521.dataset.mexbike_external_table` 


partionned Table:

CREATE OR REPLACE TABLE `dtc-de-project-344521.dataset.mexbike_partitioned`
PARTITION BY Fecha_Retiro
   AS
SELECT * FROM `dtc-de-project-344521.dataset.mexbike_non_partitioned` ;

and Finally make the dashboard via data studio  

![image](https://user-images.githubusercontent.com/93529690/161269729-d1886080-a0c5-469b-8641-e3c5b7fae8a8.png)


