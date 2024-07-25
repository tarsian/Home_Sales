

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

# Read in the AWS S3 bucket into a DataFrame.
from pyspark import SparkFiles

url = "https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.2/22-big-data/home_sales_revised.csv"
spark.sparkContext.addFile(url)
df = spark.read.csv(SparkFiles.get("home_sales_revised.csv"), sep=",", header=True)
df.show()


<img src="https://capsule-render.vercel.app/api?type=waving&color=BDBDC8&height=150&section=footer" />
