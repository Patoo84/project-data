Ingest files from the site :
https://www.ecobici.cdmx.gob.mx/en/informacion-del-servicio/open-data

download from the site file csv 
set the architecture via Terraform 
gcs and dataset via bigquery 
transform via airflow :

![image](https://user-images.githubusercontent.com/93529690/161269038-d6a29e88-7a93-4fb3-af56-aa2162109362.png)


change the external table to partionned Table in Bigquery 

and Finally make the dashboard via data studio  



