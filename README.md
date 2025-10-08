# Comprehensive E-commerce Data Pipeline

This project is a data engineering pipeline that processes e-commerce data, transforming it from raw files into aggregated reports. The pipeline follows a bronze-silver-gold data warehousing architecture, implemented using a series of Databricks notebooks.

## Dataflow Diagram

![image](https://github.com/user-attachments/assets/79bfc022-f88f-4879-bbe1-8f9d65b5db8d)

## Project Structure

The project is organized into several notebooks, each responsible for a specific stage of the data pipeline:

- **`Assignment - utilities.ipynb`**: Contains helper functions for common tasks such as renaming columns, adding columns, and saving data to tables. This notebook is used by other notebooks in the project.
- **`Assignment - Ingestion.ipynb`**: Ingests raw data from various sources (CSV, XLSX, JSON) into the bronze layer of the data warehouse.
- **`Assignment - Enrichment.ipynb`**: Cleans, transforms, and enriches the data from the bronze layer, preparing it for the silver layer.
- **`Assignment - Aggregation.ipynb`**: Aggregates the enriched data from the silver layer to create business-level reports, which are stored in the gold layer.
- **`Assignment - Tests.ipynb`**: Contains a suite of tests to validate the data at each stage of the pipeline, ensuring data quality and the integrity of the transformations.

## Data Pipeline Architecture

The pipeline is designed using a bronze-silver-gold data warehousing architecture, which is a common pattern for organizing data in a data lake or data warehouse.

### Bronze Layer (Raw Data)

The bronze layer stores the raw, unprocessed data ingested from the source systems. In this project, the `Assignment - Ingestion.ipynb` notebook is responsible for ingesting the following files into the bronze layer:
- `Product.csv`
- `Customer.xlsx`
- `Order.json`

### Silver Layer (Enriched Data)

The silver layer contains cleaned, transformed, and enriched data that is ready for analysis. The `Assignment - Enrichment.ipynb` notebook performs several transformations to create the silver layer, including:
- Cleaning and formatting customer names.
- Rounding off profit values to two decimal places.
- Joining data from different sources to create a more comprehensive dataset.

### Gold Layer (Aggregated Data)

The gold layer contains aggregated data that is ready for business intelligence and reporting. The `Assignment - Aggregation.ipynb` notebook creates the gold layer by aggregating the enriched data to generate the following reports:
- Profit by Year
- Profit by Year and Product Category
- Profit by Customer
- Profit by Customer and Year

## How to Run the Pipeline

To run the pipeline, execute the notebooks in the following order:

1. **`Assignment - Ingestion.ipynb`**: To ingest the raw data.
2. **`Assignment - Enrichment.ipynb`**: To clean and enrich the data.
3. **`Assignment - Aggregation.ipynb`**: To aggregate the data and generate reports.

## How to Run the Tests

To ensure the data quality and the correctness of the pipeline, run the `Assignment - Tests.ipynb` notebook. This notebook contains a series of tests that validate the data at each stage of the pipeline. The tests include:
- Schema validation
- Record count validation
- Data quality checks (e.g., ensuring profit is rounded correctly)
- Validation of aggregations

## Reports

The `Assignment - Aggregation.ipynb` notebook generates the following reports, which are stored in the `presentation` database (gold layer):

- **Profit by Year**: Total profit for each year.
- **Profit by Year and Product Category**: Total profit for each product category, broken down by year.
- **Profit by Customer**: Total profit for each customer.
- **Profit by Customer and Year**: Total profit for each customer, broken down by year.