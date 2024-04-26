## Data engineering fundamentals

Types of Data
- Structured
- Unstructured
- Semi-structured


Properties of Data
- Volume
- Velocity
- Variety

Datawarehouses Vs Datalakes
- **Data warehouses** - A centralized repository optimized for analysis where data from different sources is stored in a structured format, ETL (Schema on write)
- Examples: Amazon Redshift, Google Bigquery, Microsoft SQL data warehouse
- **Datalakes** - A storage repository that holds vast amounts of raw data in its native format, including structured, semi-structured and unstructured data - ELT (Schema on read)
- Examples: S3, Azure data lake storage, Hadoop Distributed file system


Data lakehouse
- Combination of data lake and data warehouse features
- Examples: AWS lake formation, Delta lake, Databricks lakehouse platform, Azure synapse analytics

Data Mesh: Individual teams own data products within a given domain

ETL pipelines - Extract Transform Load

Data sources - JDBC, ODBC, Raw logs, APIs, Streams

Common Data formats - CSV, JSON, Avro, Parquet

Data modeling - This sort of diagram is an Entity Relationship Diagram (ERD)

Data lineage - A visual representation that traces the flow and transformation of data through its lifecycle, from its source to its final destination

Schema Evolution - Ability to adapt and change the schema of a dataset over time without disrupting existing processes or systems

Database performance optimization
- Indexing
- Partitioning
- Compression

Data sampling techniques
- Random sampling
- Stratified sampling
- others - systemic, Cluster, Convenience, Judgmental

Data skew Mechanism - unequal distribution or imbalance of data across various nodes or partitions in distributed computing systems
- Addressing Data skew
  - Adaptive partitioning
  - Salting
  - Repartitioning
  - Sampling
  - Custom partitioning

Data validation and profiling
- Completeness
- Consistency
- Accuracy
- Integrity


**SQL**

Aggregation
- Count
- sum
- avg
- max/min

Aggregate with Case
- where clauses are specified after aggregation, you can only filter on one thing at a time
```
select count(*) as high_salary_count from employees where salary > 7000;
```

- One way to apply multiple filters to what you're aggregating
```
select
count(case when salary > 7000 then 1 end) as high_salary_count,
count(case when salary between 50000 and 70000 then 1 end) as medium_salary_count,
count(case when salary < 50000 then 1 end) as low_salary_count
from employees;

```

