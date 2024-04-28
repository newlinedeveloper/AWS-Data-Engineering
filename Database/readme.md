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
