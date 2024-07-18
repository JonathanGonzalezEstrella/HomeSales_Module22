# HomeSales_Module22
# Spark SQL Project

This project demonstrates various operations performed using Apache Spark SQL, including reading data, creating temporary views, caching tables, and running SQL queries. The dataset used is home sales data in CSV format.

## Prerequisites

- Apache Spark
- Java 11
- Python 3.x
- Jupyter Notebook (optional, but recommended)

## Steps

### 1. Setup and Initialization

- Import necessary packages and set up environment variables.
- Install Java and Spark, and set up the Spark session.

```python
import os

# Set Spark version
spark_version = 'spark-3.5.1'
os.environ['SPARK_VERSION'] = spark_version

# Install Spark and Java
!apt-get update
!apt-get install openjdk-11-jdk-headless -qq > /dev/null
!wget -q http://www.apache.org/dist/spark/$SPARK_VERSION/$SPARK_VERSION-bin-hadoop3.tgz
!tar xf $SPARK_VERSION-bin-hadoop3.tgz
!pip install -q findspark

# Set Environment Variables
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-11-openjdk-amd64"
os.environ["SPARK_HOME"] = f"/content/{spark_version}-bin-hadoop3"

# Start a SparkSession
import findspark
findspark.init()

from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("SparkSQL").getOrCreate()
