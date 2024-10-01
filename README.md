# Architecture Diagram

![Architecture Diagram](image.png)


# Sequence of execution

1. Assignment - Ingestion.ipynb
2. Assignment - Enrichment.ipynb
3. Assignment - Aggregation.ipynb

# Other notebooks

1. Assignment - utilities.ipynb (imported by other notebooks for execution)
2. Assignment - Tests.ipynb (Unit test cases)

# Steps

1. Data is first loaded in Data Lake (AWS S3)
2. Assignment - Ingestion (Databricks notebook) pulls data from Data Lake and loads in bronze layer of lakehouse.
3. Assignment - Enrichment (Databricks notebook) pulls data from bronze layer, processes them and stores in silver layer. This notebook also joins orders data with Customer and Product before saving those to Orders silver layer.
4. Assignment - Aggregation (Databricks notebook) aggregates data from orders enriched table w.r.t. the report dimensions, i.e. customer_name, year, category and sub_category to measure profit against them.
5. SQL queries used for creating reports have been saved in aggregation notebook, but this can be seggregated for a production project.

# Assumptions

- Cluster has this library installed to read excel files. com.crealytics:spark-excel_2.12:0.13.5
- year of profit is marked by order date and not ship date


# Enhancements

- Handle schema changes
- Parameterize filenames
- For Data quality checks, may be Great Expectations library can be used.
- Utilities file was created as part of refactoring the code, it's necessary to create test cases for utilities file as well.
- Product Table can be partitioned on 'category'.
- Customer table can be partitioned on 'segment'
- Orders table can be partitioned on 'order_date' 
- depending on frequency, volume and nature (full/ incremental), cdc should be implemented.