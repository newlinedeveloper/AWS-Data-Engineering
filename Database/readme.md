## Database


### Amazon DynamoDB
- No SQL database - Not a relational database
- made of Tables
- Primary key (must be decided at creation time)
- Each item has attributes
- max size of item is 400KB

DynamoDB - Primary Keys
- Partition key
- partition key + sort key


DynamoDB  -  Read/write Capacity modes
- Provisioned Mode (default)
- On-Demand Mode

DynamoDB - write Capacity Units
- WCU - One write per second for an item up to 1 KB in size
- Example : 10 * (2kb/1kb) = 20 WCUs

- Strongly consistent read
- Eventually consistent read (default)


DynamoDB - read Capacity Units
- One Read capacity unit (RCU)
    - One strongly consistent read per second
    - two eventually consistent reads per second for item up to 4 KB
- Example 1: 10 storngly consistent reads per second, with item size 4 KB
   - 10 * (4 KB / 4KB) = 10 RCUs
- Example 2: 16 eventually consistent reads per second, with item size 12 KB
  - (16/2) * (12KB/4KB) = 24 RCUs
 

DynamoDB - Paritions Internal

DynamoDB - Throttling
- `ProvisionedThroughputExceedException` issue
- Reasons:
    - Hot keys
    - Hot partitions
    - Very large items
- Solutions
    - Exponential backoff
    - Distribute partition keys
    - we can use DynamoDB accelerator


DynamoDB - Writing Data
- PutItem
- UpdateItem
- Conditional writes


DynamoDB - Reading Data
- GetItem
- Query
   - KeyConditionExpression
   - FilterExpression
- Scan
   - return upto 1 MB of data
   - ProjectionExpression &  FilterExpression
 
DynamoDB - Deleting Data
- DeleteItem
- DeleteTable

DynamoDB - Batch operations
- BatchWriteItem
- BatchGetItem

DynamoDB - PartiQL

```
Select OrderID, Total
From Orders
Where OrderID In [1,2,3]
Order by OrderID Desc

```

DynamoDB - Local Secondary Index
- Alternative sort key
- Upto 5 local secondary index
- must be defined at table creation time
- Uses the WCU and RCUs of the main table
- No special throttling considerations

DynamoDB - Global Secondary Index
- Alternative primary key
- can be added / modified after table creation
- Choose your GSI partition key carefully
- Assign your WCU capacity carefully

DynamoDB Accelerator (DAX)
- in-memory cache for DynamoDB
- solves the "Hot key" problem
- 5 minutes TTL for cache

DynamoDB streams
- Ordered stream of item-level modifications(Create/update/delete) in a table
- retention for upto 24 hours
- stream records can be:
  - sent to kinesis Data streams
  - Read by AWS Lambda
  - Read by Kinesis Client library applications
 

#### Amazon RDS

- Hosted Relational database
  - Amazon Aurora
  - MySql
  - PostgreSQl
  - MariaDB
  - Oracle
  - SQL server
- Not for bigdata
- it fully offers ACID property

Amazon Aurora
- Mysql and postgresql - compatible
- Up to 5x faster than MySql , 3X faster than PostgreSQL
- 1/10 cost of commercial database
- Upto 128TB per database volume
- up to 15 read replicas
- Continuous backup to S3
- replication across regions
- automatic scaling
- security
  - VPC network isolation
  - At-rest with KMS
  - in-transit with SSL
- LOCK command
  - Shared lock - read only
  - Exclusive lock - No read and write

#### Document DB
- DocumentDB is same for mongoDB
- automatically grows in increments in 10GB

#### Amazon Memory DB for Redis
- In memory database service
- ultra fast performance with over 160 millions requests/second

#### Amazon Keyspaces (for Apache Cassandra)
- Apache cassandra is an opensource Nosql distributed database

#### Amazon Neptune
- Graph database for social network dataset

#### Amazon Timestream
- Time series database
- 1000s times faster & 1/10th the cost of relational databases


#### Amazon Redshift
- Fully managed, Petabyte-scale data warehouse
- 10 * better performance than other DW's
- Designed for OLAP , not OLTP
- SQL, ODBC, JDBC interfaces
- Built in replication &  backups & scale up and down on demand
- Monitoring via Cloudwatch / CloudTrail


Redshift spectrum
- Query exabytes of unstructured data in S3 without loading
- Limitless concurrency
- Horizontal scaling
- Seperate storage & Compute resources
- wide variety of data formats
- Support of Gzip and snappy compression

Redshift performance
- Massively parallel processing (MPP)
- Columnar Data storage
- Column compression

Redshift durability
- Replication within cluster
- Backup to S3

Scaling Redshift
- Vertical and Horizontal scaling - Read PPT for more details


Redshift Distribution styles
- Auto - Redshift figures it out based on size of data
- Even - Rows distributed across slices in round-robin
- Key - Rows distributed based on one column
- All - Entire table is copied to every node

Importing / Exporting Data
- COPY command - use COPY to large amounts of data from outside of redshift
- UNLOAD command
- Enhanced VPC routing
- Auto-copy from amazon s3
- Amazon aurora zero-ETL integration
- Redshit streaming integration

Redshift copy grant for cross-region snapshot copies

DBlink
- Connect Redshift to PostgreSQL
- Good way to copy and sync data between postgresql and redshift

Integration with other services
- S3
- DynamoDB
- EMR/EC2
- Data pipeline
- Database migration

Redshift workload management

concurrency scaling

Automatic workload management

Manual workload management

short query acceleartion(SQA)

Resizing Redshift clusters

VACUUM command
-
