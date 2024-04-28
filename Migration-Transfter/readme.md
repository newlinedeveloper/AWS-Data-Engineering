## Migration & Transfer


### Application discovery service
 - Plan migration projects by gathering information about on-premises data centers
 - server utilization data
 - Agentless discovery
 - Agent-based discovery


### Application Migration service
- Lift and shift solution for migrating applications to AWS
- minimal downtime, reduced costs

### Database migration service
- Quickly and securely migrate databases to AWS, resilient, self healing
- source database remains available during migration
- support, homogeneous migrations, hetrogeneous migrations
- Continuous data replication using CDC
- Need Ec2 instance for replication tasks


AWS Schema conversion tools
- Convert your Databases schema from one db engine to another DB engine
- you don't need to use SCT if you are migrating the same DB engine

DMS - Continuous Replication

AWS DMS - Multi-AZ deployment

AWS DataSync
- Move large amount of data to and from
-  - On premises / other cloud to AWS - need agent
   - AWS to AWS - no agent needed
 

AWS Snow Famil
- Highly secure, portable devices to collect and process data at the edge and migrate data into and out of AWS
- Offline devices to perform data migrations
- if it tasks more than a week to transfer over the network, use snowball devices
- Data migration
   - Snowcone
   - Snowball Edge
   - Snowmoile
- Edge computing
   - snowcone
   - Snowball Edge
 
Snowball Edge
- Physical data transport solution - Move TBs of PBs data in or out of AWS
- Pay per data transfer job
- snow ball edge storage optimized
- snowball edge compute optimized

Snowcone & Snowcone SSD
- small, portable computing, anywhere, rugged & secure
- snowcone - 8TB of HDD storage
- snowcone SSD - 14 TB of SSD storage

Snowmobile
- Transfer exabytes of data (1 EB = 1000PB = 1000000 TBs)
- Each snowball has 100 PB of capacity
- High security
- better than snowball if you transfer more than 10 PB


Edge computing
- process data while it's being created on edge location
- snowball edge / snowcone

AWS OpsHUB
- to manage snowfamil device


AWS Transfer Family
- securely transfer files into and out of amazon s3 or amazon EFS using FTP protocol
- FTP
- FTPS
- SFTP
