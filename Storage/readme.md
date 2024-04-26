### Storage

#### Amazon s3
-  buckets - globally unique name  but defined at the region level
-  object -  max size 5 TB

S3 Security
- User based - IAM policies
- Resource based
  - Bucket policies
  - Object access control list
  - Bucket access control list
 -Encryption - uisng encryption keys


S3 bucket policies
- Public access - Use bucket policy
- User access to s3 -  IAM permissions
- EC2 instance access - Use IAM roles
- Cross account access - Use bucket policy

S3 versioning
  - enabled at bucket level
  - default value before versioning is `null`


S3 Replication (CRR & SRR)
  - Must enable versioning
  - Cross region replication (CRR)
  - Same region replication (SRR)
  - Buckets can be different AWS Accounts
  - Copying is asynchronous
  - Must give proper IAM permissions to S3
  - After enable replication new object only replicated
  - S3 batch replication - existing objects
  - Can replicate delete markers
  - There is no chain of replication

S3 storage classes
- Amazon S3 Standard - General purpose
- Amazon S3 standard-infrequent access(IA)
- Amazon S3 One zone infrequent Access
- Amazon S3 Glacier Instant retrieval
- Amazon S3 Glacier Flexible retrieval
- Amazone S3 Glacier Deep Archieve
- Amazone S3 Intelligent Tiering

Can move storage classes manually or using S3 life cycle configuration

Durability - 11'9 - 99.999999999 %
Availability - 99.99 %


S3 Standard - General purpose
- 99.99% Availability
- Used for frequently accessed data
- Low latency and high throughput
- sustain 2 concurrent facility failures


S3 storage classes - Infrequent access
- less frequently accessed data , but requires rapid access when needed
- Lower cost than s3 standard
- S3 Standard - IA
   - 99.9 % Availability
   - Usecases - Disaster recovery, backups
- S3 One Zone - IA - One zone
  - Durability - 11'9
  - Availability - 99.5 %
  - Usecases : Storing secondary backup copies of on-premises data, or data you can recreate

S3 Glacier Storage classes
- Low cost storage meant for archieving / Backup
- Pricing : Price for storage + Object retreival cost
- S3 Glacier Instant retrieval
  - Millisecond retrieval, great for data accessed once a quarter
  - Minimum storage duration of 90 days
- S3 Glacier Flexible retrieval
  - Expedited (1-5 mins), Standard (3- 5 hours), Bulk (5 - 12 hours) - free
  - Minimum storage duration of 90 days
- S3 Glacier Deep Archive - For long term storage
  - Standard (12 hours), Bulk (48 hours)
  - Minimum storage duration of 180 days


 S3 Intelligent Tiering
 - Small monthly monitoring and auto-tiering fee
 - Move objects automatically between Access Tiers based on usage
 - There is no retrieval charges in S3 intelligent tiering


S3 - Moving between storage classes

-  transition objects between storage classes
-  Infrequent accessed object, Move them to Standard IA
-  Archieve object - Glacier or Glacier Deep archieve
-  Lifecycle rules for automatic

S3 Lifecycle rules
- Transition rules
   - Move objects to standard IA class 60 days after creation
    - Move to Glacier for archiving after 6 months
- Expiration rules
 - Access log files can be set to delete after 365 days


 S3 Analytics - Storage class analysis
 - Help us decide when to transition objects to right storage class
 - recommended for standard and standard IA
 - daily report


S3 Notification
- SNS, SQS, Lambda trigger
- S3:ObjectCreated, S3:ObjectRemoved, S3:ObjectRestore, S3:Replication
- Object name filtering
- Usecase - generate thumbnailes of images uploaded to S3
- Need IAM permissions
- We can integrate with Event bridge for Advanced filtering, multiple destinations, EventBridge capabilities

S3 - Baseline performance
- 3,500 PUT/COPY/POST/DELETE or 5,500 GET/HEAD requests per second per prefix in a bucket.
- Multi-part upload
    - recommended for > 100 MB
    - must for > 5 GB
    - parallelize uploads
- S3 Transfer acceleration
    - transfer file to aws edge location
    - compatible with multi-part upload
- S3 Byte Range fetches

S3 Select & Glacier Select
- Retrieve less data using SQL by performing server-side filtering


S3 - Object Encryption

- Server-side encryption (SSE)
   - Server side encryption with Amazon S3 managed keys (SSE-S3)
   - Server side encryption with KMS keys stored in AWS KMS (SSE-KMS)
   - Server side encryption with customer provided keys (SSE-C)
- Client-side encryption


S3 - Encryption in transit - (SSL/TLS)

S3- Access points
- similar to bucket policy
- simplify security managment for S3 buckets

S3- Access points - VPC origin
- set within VPC access
- Need VPC Endpoint and VPC endpoint policy to access target bucket


S3 Object Lambda
- Use lambda function to change the object before it's retrieved by the caller application



EC2 Instance storage section 

**EBS - Elastic block storage**
- Network drive
- can only be mounted to one instance at a time
- a specific availability zone
- default EBS with EC2 instance
- Delete on termination attribute

**EFS-Elastic File system**
- Network file system that can be mounted on many EC2
- EFS works with Ec2 instance in multi-AZ
- usecases - content managment, web serving, data sharing, wordpress
- linux based system support
- EFS storage class - life cycle management feature - move file after N days


**AWS Backup**
- Centrally manage and automate backups across AWS services
- No need for manual and script process
- support cross region and cross account support
- In backup plan  - Need mention frequency and retention policy
- AWS Backup Vault lock
   - Backups can't be deleted
   - Write once read many


