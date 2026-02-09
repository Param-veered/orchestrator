# SQL QUERIES

```sql
CREATE OR REPLACE EXTERNAL TABLE `utility-tempo-322808.ny_taxi.yellow_ext`
OPTIONS (
  format = 'PARQUET',
  uris = ['gs://kestra-test-bucket-12345/yellow_tripdata_2024-*.parquet']
);

CREATE OR REPLACE TABLE `utility-tempo-322808.ny_taxi.yellow`
AS
SELECT * FROM `utility-tempo-322808.ny_taxi.yellow_ext`;


-- count of records
SELECT COUNT(*) FROM `utility-tempo-322808.ny_taxi.yellow`; --20332093

-- Disctinct PULocationIDs
SELECT COUNT(DISTINCT PULocationID) FROM `utility-tempo-322808.ny_taxi.yellow`; --262

-- Count distinct PULocationIDs on External Table
SELECT COUNT(DISTINCT PULocationID) AS distinct_pu
FROM `utility-tempo-322808.ny_taxi.yellow_ext`;


-- 4. Records with fare_amount = 0:
SELECT COUNT(*) FROM `utility-tempo-322808.ny_taxi.yellow`
WHERE fare_amount = 0;


-- 6
SELECT DISTINCT VendorID
FROM `utility-tempo-322808.ny_taxi.yellow`
WHERE tpep_dropoff_datetime BETWEEN '2024-03-01' AND '2024-03-15';


--9 
SELECT COUNT(*) from `utility-tempo-322808.ny_taxi.yellow`;

```

