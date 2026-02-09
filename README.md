"# DataTalksDataEng_HM3" 

-- Create an external table referring to the files you just uploaded
CREATE OR REPLACE EXTERNAL TABLE `zoomcamp.external_yellow_tripdata`
OPTIONS (
  format = 'PARQUET',
  uris = ['gs://dezoomcamp_hw3_suleyman_2026/yellow_tripdata_2024-*.parquet']
);

SELECT count(*) FROM `zoomcamp.external_yellow_tripdata`
WHERE fare_amount = 0;

SELECT DISTINCT VendorID
FROM `zoomcamp.external_yellow_tripdata` 
WHERE tpep_dropoff_datetime BETWEEN '2024-03-01' AND '2024-03-15';

CREATE OR REPLACE TABLE `zoomcamp.yellow_tripdata_non_partitioned` AS
SELECT * FROM `zoomcamp.external_yellow_tripdata`;

SELECT count(*) FROM `zoomcamp.yellow_tripdata_non_partitioned`;
