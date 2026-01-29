# **Azure End-to-End Data Engineering Pipeline 🚀**

## 📋 Project Overview

This project demonstrates a production-grade, end-to-end data engineering solution built entirely on the Azure cloud ecosystem. The pipeline ingests raw data from external APIs, processes it through multiple transformation layers using the Medallion Architecture (Bronze → Silver → Gold), and delivers analytics-ready datasets for business intelligence and reporting.

**The solution showcases modern data engineering best practices including:**

Cloud-native data pipeline orchestration
Distributed data processing at scale
Incremental data loading strategies
Data quality and governance
Cost-effective serverless analytics


## 🏗️ Architecture

<img width="4170" height="2970" alt="architecture_diagram" src="https://github.com/user-attachments/assets/43c26956-e32c-44a1-9ddc-4114d056b859" />


## 🎯 Key Features & Technical Implementations

## **1. Data Ingestion with Azure Data Factory**

1. HTTP-based API ingestion from UK Veterinary APIs
2. Parameterized pipelines for dynamic data extraction
3. Copy Activity with schema mapping and error handling
4. Incremental load patterns using watermark columns
5. Pipeline monitoring and alerting configurations

**Real-World Scenarios Implemented:**

1. Handling API pagination and rate limiting
2. Dynamic file naming with timestamp patterns
3. Conditional routing based on data validation
4. Retry logic and failure handling

## **2. Distributed Data Processing with Apache Spark**

1. PySpark transformations on Databricks clusters
2. DataFrame API for structured data manipulation
3. Spark SQL for complex analytical queries

**Performance optimizations:**

1. Partitioning strategies
2. Broadcast joins for dimension tables
3. Caching for iterative operations
4. Adaptive Query Execution (AQE)



## **Transformation Techniques:**

#Data cleansing
- Null value handling (imputation, filtering)
- Deduplication using window functions
- Data type conversions and validations
- String standardization (trim, lowercase, regex)

#Feature engineering
- Date/time feature extraction
- Categorical encoding
- Aggregation pipelines
- Window functions for analytics

## **3. Medallion Architecture Implementation**
  
## 🥉 Bronze Layer (Raw)

Ingestion landing zone for unprocessed data

Preserves data lineage and audit trail

Minimal transformations, schema-on-read

## 🥈 Silver Layer (Cleansed)

Data quality validations applied

Schema enforcement and standardization

Deduplication and normalization

Delta Lake format for ACID transactions

## 🥇 Gold Layer (Curated)

Business-level aggregations

Dimensional modeling (facts & dimensions)

Optimized for analytical queries

Ready for consumption by BI tools

## **4. Azure Synapse Analytics Integration**

- Serverless SQL Pool for on-demand querying
- OPENROWSET() function for direct data lake queries
- External tables with CETAS (Create External Table As Select)
- Views and stored procedures for data abstraction
- Optimized for Power BI DirectQuery mode

**Advanced SQL Patterns:**

**sql**
-- Querying data lake directly
-- Partition pruning for performance
-- JSON and nested data handling
-- Common Table Expressions (CTEs)
-- Aggregations with grouping sets

## **5. Security & Governance**

Azure Active Directory integration
Service Principal authentication for Databricks
Azure Key Vault for secrets management
Role-Based Access Control (RBAC) across resources
Data Lake ACLs for fine-grained permissions
Managed Identity for secure resource communication


## 🛠️ Technologies & Tools
<img width="696" height="498" alt="image" src="https://github.com/user-attachments/assets/50f04867-b406-403d-9169-6c68b70c7341" />


## 📊 Dataset
**Source:** UK Veterinary Medicine Directorate Dataset

**Format:** JSON (API responses)

**Records:** ~8,000+ veterinary product records

**Update Frequency:** Daily incremental loads

**Key Attributes:**

- Product information (name, form, species)
- Active pharmaceutical ingredients
- Marketing authorization details
- Timestamps and metadata


## 🚀 Pipeline Workflow
**Phase 1: Ingestion (Bronze)**

1. ADF HTTP Linked Service connects to UK Vet API
2. Copy Activity retrieves JSON data
3. Raw files stored in bronze/ container
4. Metadata captured (ingestion timestamp, record count)

**Phase 2: Cleansing (Silver)**

1. Databricks notebook triggered via ADF
2. PySpark reads from bronze layer
3. Data quality checks applied:
   ✓ Schema validation
   ✓ Null handling
   ✓ Duplicate removal
   ✓ Data type standardization
4. Cleansed data written to silver/ as Delta tables

**Phase 3: Modeling (Gold)**

1. Business logic applied in PySpark
2. Aggregations and KPI calculations
3. Dimensional model created:
   - Fact tables (transactions, events)
   - Dimension tables (products, dates, species)
4. Optimized data written to gold/ layer

**Phase 4: Analytics (Synapse)**

1. Serverless SQL Pool queries gold/ layer
2. External tables created for Power BI
3. Views materialize complex joins
4. DirectQuery enables real-time dashboards


## 🔧 Setup & Deployment

Prerequisites

Azure subscription (Free tier works)
Azure CLI installed
Basic knowledge of Python and SQL

# Step 1: Azure Resources
bash# Login to Azure

Create resource group

Create Data Lake Storage Gen2

Create Data Factory

Create Databricks Workspace

Create Synapse Workspace

# Step 2: Configure Databricks

# Step 3: Deploy Pipelines

- Import ADF pipelines from adf/ folder
- Update linked service configurations
- Validate and publish pipelines
- Set up triggers (scheduled or event-based)

# Step 4: Run Databricks Notebooks

- Import notebooks from databricks/ folder
- Attach to cluster
- Configure cluster with appropriate node types
- Execute notebooks or integrate with ADF

# Step 5: Create Synapse Objects

sql
-- Run scripts from synapse/ folder
-- Create external data source
-- Define external tables
-- Build views and stored procedures

## 📈 Performance Optimizations
**Spark Optimizations**

- **Partition tuning:** Optimal partition size (128MB-1GB)
- **Broadcast joins:** For small dimension tables (<10MB)
- **Caching:** Frequently accessed DataFrames
- **Columnar storage:** Parquet/Delta for compression
- **Predicate pushdown:** Filter early in the pipeline

Synapse Optimizations

- **Statistics:** Create stats on frequently joined columns
- **Partition pruning:** Leverage ADLS folder structure
- **Result set caching:** Enable for repeated queries
- **Materialized views:** Pre-compute expensive aggregations

Cost Optimization

- **Autoscaling:** Databricks cluster auto-termination
- **Serverless:** Synapse on-demand SQL pool (pay-per-query)
- **Lifecycle policies:** Archive cold data to lower-cost tiers
- **Reserved capacity:** For predictable workloads




## 🔮 Future Enhancements

- Implement Delta Live Tables for streaming ingestion
- Add Azure Purview for data catalog and lineage
- Integrate Azure Machine Learning for predictive analytics
- Set up CI/CD pipelines with Azure DevOps
- Implement data versioning with Delta time travel
- Add unit tests for PySpark transformations
- Create automated data quality monitoring
- Build real-time dashboards with streaming data


## 📚 Resources & References

- Azure Data Factory Documentation
- Databricks Documentation
- Azure Synapse Analytics Guide
- PySpark API Reference
- Medallion Architecture Best Practices


## 🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author
Pratyush Saxena

LinkedIn: (https://www.linkedin.com/in/pratyushsaxena100/)

Email: pratyushsaxena100@gmail.com


## 🌟 Acknowledgments

UK Veterinary Medicine Directorate for providing the open dataset

Azure documentation team for comprehensive guides

Databricks community for best practices and examples
