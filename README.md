# Databricks Medallion Architecture ETL Pipeline

## Project Overview

Built an end-to-end ETL pipeline in Databricks using Medallion Architecture (Bronze → Silver → Gold).

The project ingests raw transaction data from Amazon S3, performs data cleansing and validation in the Silver layer, and creates business-ready analytical tables in the Gold layer.

The pipeline is orchestrated using Databricks Workflows.

---

# Architecture

![{8CAE8645-5494-4E8E-8742-7432E25149A0}_1778340273014.png](./{8CAE8645-5494-4E8E-8742-7432E25149A0}_1778340273014.png "{8CAE8645-5494-4E8E-8742-7432E25149A0}_1778340273014.png")
---

# Tech Stack

* Databricks
* Databricks SQL
* Delta Lake
* Amazon S3
* Unity Catalog
* Databricks Workflows

---

# Project Structure

```text
transactions/
│
├── 01_bronze_to_silver
├── 02_data_quality_checks
├── 03_silver_to_gold
└── README.md
```

---

# Medallion Layers

## Bronze Layer

* Raw transaction data ingested from S3
* Preserved original source formatting
* Stored as Delta tables

Table:

```text
transactions.bronze.transactions
```
![{59C752DC-3D22-4B06-B2F1-C41F37FB9B99}_1778341270266.png](./{59C752DC-3D22-4B06-B2F1-C41F37FB9B99}_1778341270266.png "{59C752DC-3D22-4B06-B2F1-C41F37FB9B99}_1778341270266.png")


---

## Silver Layer

Performed:

* Timestamp conversion
* Product name standardization
* Whitespace cleanup
* Datatype casting
* Decimal precision handling
* Data quality validation

Table:

```text
transactions.silver.transactions
```
![{4D1422E3-788D-4FC8-9106-FC394ABEE85B}_1778341316830.png](./{4D1422E3-788D-4FC8-9106-FC394ABEE85B}_1778341316830.png "{4D1422E3-788D-4FC8-9106-FC394ABEE85B}_1778341316830.png")

---

# Data Quality Checks

Implemented validations for:

* Null transaction IDs
* Invalid amount calculations
* Invalid quantities
* Invalid pricing values
* Duplicate transaction IDs

---

## Gold Layer

Created business-ready reporting tables.

### sales_by_store

Metrics:

* total transactions
* total sales
* average order value

### product_sales

Metrics:

* quantity sold
* total revenue

Tables:

```text
transactions.gold.sales_by_store
```
![sales_by_stores](https://github.com/jaynitdhamanskar/transactions/blob/main/screenshots/sales_by_stores.png)


```text
transactions.gold.product_sales
```
![{50A2262A-22FA-4EB5-A15F-E549DDC4C780}_1778341118997.png](./{50A2262A-22FA-4EB5-A15F-E549DDC4C780}_1778341118997.png "{50A2262A-22FA-4EB5-A15F-E549DDC4C780}_1778341118997.png")


---

# Workflow Orchestration

```text
Created Databricks Workflow pipeline:
```
![{6E548A3F-B69A-4C23-B471-202950CF5089}_1778340863643.png](./{6E548A3F-B69A-4C23-B471-202950CF5089}_1778340863643.png "{6E548A3F-B69A-4C23-B471-202950CF5089}_1778340863643.png")

The workflow automates transformation and validation tasks sequentially.

---

# Learning Outcomes

* Built Medallion Architecture pipeline
* Implemented ETL transformations using SQL
* Performed data quality validation
* Created Gold layer business aggregations
* Orchestrated workflows in Databricks
* Worked with Delta tables and Unity Catalog

---
