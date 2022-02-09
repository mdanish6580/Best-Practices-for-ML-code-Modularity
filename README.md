# Databricks Reusable and modular ETL Pipeline
This article explains the ETL architecture for maintaining a reusable and modular Spark pipeline on Databricks 

------
![Image Link](https://github.com/mdanish6580/Best-Practices-for-ML-code-Modularity/blob/main/testt.png)

----
# Description
* **Source DB:** This source db could be any source. Eg. ADLS raw container, Blob Storage container, raw folder in S3 bucket

* **config file:** In pythonic code it would be .ini,  or .yaml file but in databricks environment it could be another notebook where the configuration details of source db and target db would be listed. For more details refer to database connection repository. This file will also hold all static information necessary for ETL.

* **script:** This is the master script where config files/notebooks will be ran using databricks utility function. This script also has all the transformation or data manipulation methods that could be used for data transformation. The transformed data will then be pushed into target db.

# Data warehouse Practice
As per Microsoft architecture, it is not recommended to push whole transformed dataset into a data warehouse (Azure Data Pool or Redshift or Snowflake). While it is recommended to store dataset if we are not planning to run queries pertaining to aggregation or query which would be computationally expensive. Generally, after performing aggregation on the transformed dataset, it is pushed to data warehouse.
