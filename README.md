

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

## Getting Started

### Prerequisites

- Python
- Apache Spark
- PySpark

### Installation

1. Install `findspark`:
    ```bash
    pip install findspark
    ```

2. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/homesales-analysis.git
    cd homesales-analysis
    ```

3. Run the Jupyter notebook or Python script to execute the analysis steps.


<img src="https://capsule-render.vercel.app/api?type=waving&color=BDBDC8&height=150&section=footer" />