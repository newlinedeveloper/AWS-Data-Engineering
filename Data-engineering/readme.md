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
- Grouping - `group by department_id`
- Nested grouping, sorting
```
group by sale_year, product_id
order by sale_year, total_sales desc

```

- Pivoting - Pivoting is the act of turning row-level data into columnar data
```
select salesperson, [jan] As Jan_sales, [Feb] as Feb_sales
from
(select salesperson, month, sales from sales) as sourceTable
pivot
(
sum(sales)
for month in ([jan], [feb])
) as pivotTable;

```

The same thing is achieved with conditional aggregation, without requiring a specific pivot operation

```
select
salesperson,
sum(case when month = 'jan' then sales else 0 end) as jan_sales,
sum(case when month = 'feb' then sales else 0 end) as Feb_sales
from sales
group by salesperson;
```

- Inner join
```
select c.customerName, p.paymentDate, p.amount
from customers c
inner join payments p on c.customerNumber = p.customerNumber

```

- Left outer join

```
select c.customerName, p.paymentDate, p.amount
from customers c
left join payments p on c.customerNumber = p.customerNumber

```

- Right outer join

```
select c.customerName, p.paymentDate, p.amount
from payments p
right join customers c on c.customerNumber = p.customerNumber

```

- Cross outer join
```
select c.customerName, p.paymentDate, p.amount
from payments p
cross join customers c
```

**SQL Regular experssions** - pattern matching - Think a much more powerful "Like"
- `~` is the regular expression operator
- `~*` is case-insensitive
- `!~*` would mean "not match expression, case insensitive"
- Regular expression 101
  - ^ - match a pattern at the start of a string
  - $ - match a pattern at the end of a string (boo$ would match boo but not book)
  - | - alternative character
  - Ranges([a-z] match any lower case letter)
  - Repeats ([a-z]{4} matches any four letter lower case word)
  - special metacharacters
    - \d - any digit
    - \w - any letter, digit or underscore
    - \s - whitespace
    - \t - tab
- Example
  select any rows where name starts with fire or ice (case insensitive)
```
select * from name where name ~*'^[fire|ice]';

```

