# Walmart Sales ETL Pipeline (Python → SQL Server)

## Project Overview

This project implements an **end-to-end ETL (Extract, Transform, Load) pipeline** for Walmart sales data using **Python (Pandas)** and **SQL Server**.

The pipeline ingests raw retail sales data from CSV files, applies data quality checks and transformations, and loads the cleaned, analytics-ready data into SQL Server for downstream **SQL-based analysis and reporting**.

This project is designed to be **portfolio-ready** and aligned with real-world **Data Engineering workflows**.

## ETL Architecture

<img width="1018" height="711" alt="Image" src="https://github.com/user-attachments/assets/e0c34e6e-37ed-43c2-9326-344a380d0913" />

### Component Breakdown

* **Extract Layer**: Ingests raw CSV files from local storage using Pandas with encoding handling.
* **Transform Layer**: Applies data quality checks, removes duplicates, inspects schema, and validates nulls and data types.
* **Load Layer**: Persists cleaned, structured data into SQL Server via SQLAlchemy using an idempotent load strategy.

This architecture mirrors a **production-style ETL pipeline**, where Python acts as the transformation engine and SQL Server serves as the analytical data store.

## ETL Objectives

* Extract raw Walmart sales data from CSV files
* Perform data quality checks and transformations
* Ensure schema consistency and analytics readiness
* Load cleaned data into SQL Server
* Enable efficient SQL analytics on structured data

## Tech Stack

* **Python**
  * Pandas
  * SQLAlchemy
* **SQL Server** (Windows Authentication)
* **Jupyter Notebook**
* **Git & GitHub**

## ETL Pipeline Breakdown

### Extract

* Load raw CSV data using Pandas
* Handle encoding issues gracefully

```python
df = pd.read_csv('Walmart.csv', encoding_errors='ignore')
```

### Transform

Applied multiple transformation and data quality steps:

* Schema inspection (`info`, `describe`)
* Duplicate detection and removal
* Null value analysis
* Data type validation
* Dataset shape verification

Examples:

```python
df.drop_duplicates(inplace=True)
df.isnull().sum()
```

These transformations ensure the dataset is **consistent, clean, and analytics-ready**.

### Load

* Establish SQL Server connection using SQLAlchemy
* Load cleaned data into a relational table
* Replace existing table for idempotent loads

```python
df.to_sql(
    'Walmart',
    con=engine,
    if_exists='replace',
    index=False
)
```

## SQL Analytics Enabled

Once loaded into SQL Server, the data supports queries such as:

* Total sales by branch
* Revenue by product line
* Average transaction value
* Sales distribution by location
* Trend analysis over time

## Key Learnings & Skills Demonstrated

* End-to-end ETL pipeline design
* Data cleaning and validation using Pandas
* SQL Server integration via Python
* Analytics-oriented data modeling
* Real-world Data Engineering workflow

---

## Future Improvements

* Incremental loads instead of full refresh
* Data validation with Great Expectations
* Workflow orchestration using Airflow
* Cloud deployment (Azure / AWS)
* Star schema modeling for BI tools

---

## Author

**Moavia Mahmood**
Data Engineer | Python | SQL | ETL Pipelines
