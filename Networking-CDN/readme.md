#### Networking and Content Delivery

- VPC - Virtual private cloud
- Subnets - Tied to an Az, network partition of the VPC
- Internet Gateway - At the VPC level, provide internet access
- NAT Gateway / Instances - Give internet access to private subnets
- NACL - Stateless, subnets rules for inbound and outbound
- Security groups - Stateful, operate at the EC2 instance level or ENI
- VPC peering - Connect two VPC with non overlapping IP ranges, non transitive
- VPC endpoints - Provide private access to AWS services within VPC
- VPC flow logs - Network traffic logs
- Site to Site VPN - VPN over public internet between on-promises DC and AWS
- Direct connect - Direct Private connection to a AWS

AWS Private link
- Most secure & Scalable way to expose a service to 1000s of VPCs
- Do not require VPC peering, Internet gateway, NAT, route tables
- Requires a network load balancer (service VPC) and ENI (customer VPC)

DNS
- www.google.com => 172.217.18.36

Terminologies 
- Domain registrar:  Amazon route 53 , goDaddy
- DNS records: A, AAAA, CNAME, NS
- Zone file: Contains DNS records
- Name server: resolves DNS queries
- Top level Domain - TLD - .com, .us, .in, .gov, .org
- Second level Domain - SLD - amazon.com, google.com

Route 53
- A high available , scalable fully managed and authoritative DNS
- Route 53 is also a Domain registerar
- 53 is DNS Port
- 100 % availability SLA
- ability to check resource health

Route 53 - Records
- Domain/subdomain name - e.g: example.com
- Record Type - A or AAAA
- Value - 12.34.56.78
- Routing policy - how route 53 responds to queries
- TTL - Amount of time the record cached at DNS resolvers


Route 53 - Record Types
- A - maps a hostname to IPV4
- AAAA - maps a hostname to IPV6
- CNAME - maps a hostname to another hostname
- NS - Name servers for the hosted zone

Route 53 - Hosted Zone
- public hosted zone - application1.mypublicdomain.com
- private hosted zones - application1.company.internal

AWS Cloudfront
- CDN
- improves read performance content is cached at the edge
- DDoS protection (because worldwide), integration with shield, AWS Web application firewall

Cloudfront origins

- S3 bucket
- - distributing files and caching them at the edge
  - Origin access control
- Custom origin (HTTP)
-   - Application load balancer
    - Ec2 instance
    - S3 bucket (must first enable the bucket as a static S3 website)
    - Any HTTP backend you want


Cloudfront - Cache invalidation
- `Cloudfront Invalidation` - to force update the entire or partial cache refresh
- you can invalidate all the files (*) or a special path ("/images/*")


