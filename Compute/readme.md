### Compute

#### AWS EC2
- spot - can tolerate loss, low cost
- Reserved - long running clusters , databases
- On demand : remaining workloads

AWS Graviton
- own family of processors

AWS Lambda
- serverless data processing
- realtime file processing
- realtime stream processing
- ETL
- Cron replacement
- process AWS events


refer PPT for usecases


AWS SAM
- SAM - Serverless application model
- framework for development and deploying serverless applications
- all the configuration is YAML code
- helps to run Lambda, API gateway and DynamoDB locally


AWS Batch
-  Run batch jobs are dockr images
-  fully serverless
-  Schedule batch jobs using Cloudwatch events
-  Orchestrate batch jobs using step functions
