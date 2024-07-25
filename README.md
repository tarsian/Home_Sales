

# Home_Sales
<img src="https://capsule-render.vercel.app/api?type=waving&color=BDBDC8&height=150&section=header" />

# Home Sales Analysis with PySpark

This project demonstrates the use of PySpark for data analysis on a home sales dataset. The data is read from an AWS S3 bucket, processed, and queried using Spark SQL. Key tasks include creating temporary views, caching data, and partitioning data in Parquet format.

## Project Overview

1. **Data Loading**: Read data from an AWS S3 bucket into a Spark DataFrame.
2. **Data Processing**: Create temporary views and perform SQL queries to analyze the data.
3. **Caching**: Cache the data to improve query performance and measure runtime improvements.
4. **Partitioning**: Partition the data by the `date_built` field and save it in Parquet format.
5. **Querying**: Run various queries to gain insights, such as average prices based on different criteria and view ratings.

## Key Features

- **Spark SQL**: Utilize SQL queries within Spark to analyze the dataset.
- **Performance Optimization**: Cache data to speed up query execution and compare runtimes.
- **Data Partitioning**: Organize data using Parquet format for efficient storage and retrieval.

1. Initialize Spark
```python
# Import findspark and initialize.
import findspark
findspark.init()
```

2. Create a Spark Session
```python
# Import packages
from pyspark.sql import SparkSession
import time

# Create a SparkSession
spark = SparkSession.builder.appName("SparkSQL").getOrCreate()
```

3. Read Data from S3
```python
# Read in the AWS S3 bucket into a DataFrame.
from pyspark import SparkFiles

url = "https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.2/22-big-data/home_sales_revised.csv"
spark.sparkContext.addFile(url)
df = spark.read.csv(SparkFiles.get("home_sales_revised.csv"), sep=",", header=True)
df.show()
```

4. Create a Temporary View
5. Set Queries
6. Run Cached Query
7. Partition Data in Parquet Format
```python
# Partition by the "date_built" field on the formatted parquet home sales data.
df.write.mode("overwrite").partitionBy("date_built").parquet("home_sales_partitioned")
```
8. Read and Query Parquet Data
```python
# Read the formatted parquet data.
parquet_df = spark.read.parquet("home_sales_partitioned")
parquet_df.show()

# Create a temporary table for the parquet data.
parquet_df.createOrReplaceTempView("parquet_home_sales")

# Run the query using parquet data and measure the runtime.
start_time = time.time()
query = """
SELECT view, ROUND(AVG(price), 2) AS AvgPrice
FROM parquet_home_sales
GROUP BY view
HAVING AVG(price) >= 350000
ORDER BY AvgPrice DESC
"""
spark.sql(query).show()
print("--- %s seconds ---" % (time.time() - start_time))
```
9. Uncached the table and Check


<img src="https://capsule-render.vercel.app/api?type=waving&color=BDBDC8&height=150&section=footer" />
