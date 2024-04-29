### APP integration


#### AWS SQS

- Older offering service (10 years old)
- Fully managed
- scales 1 msg - 15000 per second
- retention - 4 days to 14 days
- No limit to how many messages can be in the queue
- Low latency (<10ms)
- Horizontal scaling in terms of no of consumers
- can have duplicate messages
- can have out of order messages
- limitation of 256 KB per message sent

Producing messages
- Define body
- add message - attributes (metadata - optional)
- Provide Delay Delivery (optional)
- Getback - message identifier &  MD5 hash of the body

Consuming messages
- Poll SQS for messages (receive up to 10 messages at a time)
- Process the message within the visibility timeout
- Delete the message using the message ID & receipt handle


AWS SQS - FIFO Queue
- FIFO
- queue name ends with .fifo
- messages are sent exactly once
- no duplication

SQS Extended client
- message size more than 256KB, use SQS extended client (Java library)

SQS Usecases
- Decouple applications
- Buffer writes to a database
- Handle large loads of message coming

SQS Limits - refer PPT

SQS Security
- Encryption  in flight using HTTPS endpoint
- Can enable SSE using KMS
- IAM policy must allow usage of SQS
- SQS Queue access policy

Kinesis Data stream Vs SQS - Refer PPT

SQS VS Kinesis - Refer PPT

Amazon SQS - Dead letter Queue - DLQ
 - Consumer fails to process a message within the visibility timeout, the message goes back to the queue
 - We can set threshold of how many times a message can go back to the queue
 - useful for debugging
 - DLQ of a FIFO = source Queue also FIFO and same for standard queue also

SQS DLQ - Redrive to source
- Feature to help consume messages in the DLQ to understand what is wrong with them
- when our code is fixed, we can rederive the messages from DLQ back into the source queue
 


#### AWS SNS

- to send one messages to many receivers
- pub-sub model
- producer will send message to topic, subscriber will receive the message
- up to 12, 500, 000 subscriptions per topic
- 100000 topics limit
- many aws services can send data directly to sns for notifications

SNS - How to publish
- Topic publish
- Direct publish

SNS - Security
- Encryption
- Access controls
- SNS access policies

SNS + SQS Fan out
- push once in SNS, receive in all SQS queues that are subscribers
- fully decoupled , no data loss

Application : S3 events to mutiple queues

Application: SNS to amazon S3 through Kinesis Data firehose


SNS - FIFO topic
- ordering & deduplication
- Can have SQS standard and FIFO queues are subscribers

SNS FIFO + SQS FIFO : Fan out - you need fan out + ordering + deduplication

SNS - message filtering
- json based filtering option to subscribers

#### AWS step functions
- use to design workflows
- Easy visualization
- Advanced error handling and retry
- history of workflows
- ability to wait for an arbitary amount of time
- max execution time of a state machine is 1 year
- your workflow is called state machine
- Each step in a workflow is a state
- Types of state
- - Task
  - Choice
  - Wait
  - Parallel
  - map
  - Also pass, succeed, Fail


Full data engineering pipeline real time layer

Full data engineering pipeline video layer

Full data engineering pipeline batch layer

Full data engineering pipeline analytics layer

#### Amazon Appflow
- Fully managed integration service that enables you to securely transfer data between saas application and AWS
- Source :  Salesforce, SAP, Zendesk, Slack and service now
- Destination: Amazon S3, Redshift, non AWS such as Snowflake and salesforce
- Frequency
- Data transformation
- Encryption

#### Amazon EventBridge

 - schedule - cron jobs
 - Event pattern - Event rules to react to a service doing something
 - Trigger lambda function, send SQS, SNS messages
 - 

Event bridge - Schema registry

event bridge -Resource based policy
- manage permissions for a specific event bus
- allow / deny events from another AWS account or AWS region
- 



#### Amazon Managed Workflows for Apache Airflow

- Apache airflow is batch oriented workflow tool
- Develop, schedule and monitor your workflows
- workflows are defined as python code that creates a directed acyclic graph

