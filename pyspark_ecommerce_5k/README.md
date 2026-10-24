# PySpark E-commerce Practice Dataset (up to 5K orders)

This ZIP contains synthetic sample CSV data for a Jupyter Notebook PySpark project.

## Files
- data/orders.csv — 5,000 order rows
- data/customers.csv — 1,000 customer rows
- data/products.csv — 20 product rows

All data is fictional. The orders file contains a few intentional invalid quantities and customer IDs for data-cleaning practice.

## Load in Jupyter Notebook
```python
import os
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("EcommerceProject").getOrCreate()
DATA_DIR = r"C:\path\to\pyspark_ecommerce_5k\data"  # change this path

orders = spark.read.csv(os.path.join(DATA_DIR, "orders.csv"), header=True, inferSchema=True)
customers = spark.read.csv(os.path.join(DATA_DIR, "customers.csv"), header=True, inferSchema=True)
products = spark.read.csv(os.path.join(DATA_DIR, "products.csv"), header=True, inferSchema=True)

print("Orders:", orders.count())
print("Customers:", customers.count())
print("Products:", products.count())
```
Expected counts: Orders 5000, Customers 1000, Products 20.
