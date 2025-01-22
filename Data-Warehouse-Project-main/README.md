# Data Warehouse Project: SQL to AWS S3, Redshift, and Power BI

This project demonstrates the design, implementation, and functionality of a scalable data warehouse system. The system integrates SQL data sources into AWS S3 (data lake) and Redshift (data warehouse) using Apache Airflow for ETL processes. Data is transformed into dimensional and fact tables and visualized using Power BI for actionable insights.

---

## Objectives

The primary goals of this project include:

1. **Centralized Data Integration**: Move data from a SQL source to a data warehouse (Redshift) via a data lake (S3).
2. **Automated ETL Workflows**: Design scalable workflows to load, transform, and store data incrementally.
3. **Business Intelligence Support**: Enable analytics and interactive dashboards using Power BI.

---

## Architecture Overview

The project follows a multi-step architecture:

1. **Data Lake**: SQL source tables are exported to AWS S3 in CSV format.
2. **Staging Zone**: Data from S3 is loaded into Redshift's staging tables.
3. **Raw Zone**: Staging data is incrementally loaded into the raw zone, with a date column to track changes.
4. **Processing Zone**: Dimensional and fact tables are built from raw data. Slowly Changing Dimensions (SCD) Type 1 is implemented for dimension tables.
5. **Dashboard**: Redshift data is visualized in Power BI dashboards.

---

## ETL Workflow

The ETL process is automated using **Apache Airflow** and involves the following steps:

1. **SQL to S3 (Data Lake)**:
   - Data from the SQL source is extracted and exported as CSV files to an AWS S3 bucket.
   - Ensures fast and reliable access to the source data.

2. **S3 to Redshift (Staging Zone)**:
   - CSV files from S3 are loaded into Redshift's staging zone.

3. **Staging to Raw Zone**:
   - Incremental data is loaded into the raw zone.
   - New records are inserted, existing records are updated, and a date column is added to track changes.

4. **Raw to Processing Zone**:
   - Data is transformed into **dimension** and **fact tables**.
   - **SCD Type 1** is applied to dimension tables for maintaining the most current data.

5. **Power BI Visualization**:
   - Redshift is connected to Power BI to build interactive dashboards.

### ETL Workflow Diagram

![ETL Workflow](https://github.com/Saadullah45/Data-Warehouse-Project/blob/main/Data-Warehouse-Project-main/workflow.png)

### ETL Workflow Diagram


---

## Data Model

### Dimensions
- **Implementation**: Slowly Changing Dimension (SCD) Type 1.
- **Examples**:
  - `Dim_Customer`
  - `Dim_Product`
  - `Dim_Region`

### Fact Tables
- Examples of fact tables:
  - `Fact_Inventory_Transaction`
  - `Fact_OrderDetails`

---

### BI Dashboard
![BI Dashboard](https://github.com/Hamza-Jamil121/Data-Warehouse-Project/assets/70171169/dffa0e3c-5b96-49fd-85fa-630e09983f57)


---


## Future Work

1. **Optimization**:
   - Implement partitioning and indexing in Redshift for improved query performance.
   - Optimize column compression and distribution styles for large datasets.

2. **Additional Data Sources**:
   - Integrate data from NoSQL databases and API-based sources.

3. **Advanced ETL**:
   - Introduce **Delta Lake** features for real-time processing.
   - Evaluate **AWS Glue** for serverless ETL workflows.

4. **Enhanced Analytics**:
   - Incorporate predictive analytics and machine learning models into Power BI dashboards.

---

## Tools and Technologies

- **Data Sources**: SQL databases
- **Data Lake**: AWS S3
- **Data Warehouse**: AWS Redshift
- **ETL Orchestration**: Apache Airflow
- **Visualization**: Power BI

---

## How to Run the Project

1. **Set Up Infrastructure**:
   - Create an AWS S3 bucket and Redshift cluster.
   - Configure Airflow to connect to these resources.

2. **ETL Configuration**:
   - Define DAGs in Airflow for the ETL steps:
     - SQL to S3
     - S3 to Redshift
     - Data transformations

3. **Power BI Connection**:
   - Connect Power BI to Redshift using a direct query or import.

4. **Monitor and Iterate**:
   - Use Airflow logs to monitor ETL processes.
   - Regularly optimize data models and queries.

---

## Contributors

- **Saad Ullah**

---

## License

This project is licensed under the [MIT License](LICENSE).
