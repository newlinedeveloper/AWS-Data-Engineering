### Containers

#### Docker
 Docker basics - refer PPT


 Docker containers management of AWS
 
 - AWS Elastic container service - ECS
 -  - Amazon's own container platform
 - Amazon Elastic kubernetes service - EKS
   - Amazon's managed kubernetes (Opensource)
 - Fargate
   - Amazon's own serverless container platform
   - Works with ECS and with EKS
 - ECR
   - Store container images
  

#### ECS
- EC2 launch type
  - you must provision & maintain the infrastructure 
- Fargate launch type
  - it's all serverless
- Iam roles for ECS
  - Ec2 instance profile (EC2 launch type only)
  - ECS Task role
- load balancer integration
   - Application load balancer
   - Network load balancer
   - classic load balancer - Not recommended
 - Data volumns (EFS)

#### ECR
 - private and public docker image registry

#### EKS
- managed kubernetes cluster on AWS
- support EC2 and Fargate work nodes deployment
- cloudwatch contianer insights
- Node Types
  - Managed Node groups
  - self-managed nodes
  - AWS fargate
- Data volumes
   - EBS
   - EFS
   - FSx for lustre
   - FSx for NetApp ONTAP
