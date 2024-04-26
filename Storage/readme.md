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
- - Access log files can be set to delete after 365 days




