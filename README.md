# Modern ELT Pipeline: DBT + Snowflake + Airflow Integration

An enterprise-grade ELT pipeline demonstrating modern data stack principles.
Extracts TPCH sample data from Snowflake, transforms it using DBT with modular data modeling patterns and orchestrates workflows via Airflow with Astronomer Cosmos.

## 🌟 Key Features
- **Zero-Copy Data Ingestion**: Leverages Snowflake's TPCH shared dataset (no storage costs)
- **Multi-Layer Transformations**:
  - **Staging**: Source-aligned raw data mirroring the raw TPCH_SF1 dataset
  - **Intermediate**: Business logic encapsulation
  - **Marts**: Analytics-ready fact/dimension tables
- **Data Quality Gates**: Generic/singular tests and referential integrity checks at each transformation layer
- **Macros**: Reusable business logic code(e.g., discount calculations)
- **CI/CD Ready**: Containerized Airflow environment with dependency management

## 🛠️ Core Technologies
| Component       | Tools                          | Purpose                          |
|-----------------|--------------------------------|----------------------------------|
| **Extract/Load**| Snowflake TPCH_SF1 dataset     | Raw data ingestion               |
| **Transform**   | DBT Core + dbt-utils           | Modeling, macros, data quality   |
| **Orchestrate** | Airflow + Cosmos library       | Pipeline scheduling/monitoring   |
| **Storage**     | Snowflake Warehouse (X-Small)  | Scalable cloud data storage      |

## 🛠️ Core Components Deep Dive

### Extract/Load Layer
- **Snowflake TPCH Dataset**: Pre-loaded transactional dataset simulating supply chain operations with +6 millions rows

### Transformation Layer Deep Dive
**DBT-powered transformation engine implementing a medallion architecture**:

#### Transformation Philosophy
```mermaid
graph LR
    A[Raw TPCH Data] --> B(Staging: Source of Truth)
    B --> C(Intermediate: Business Logic)
    C --> D(Marts: Analytics Products)
 

