# AWS Services

## DNS Configuration 

- Route53 defines the DNS configuration for the domain.

## API Gateway

- Cognito creates User pools

## Load Balancer

- Elastic Load Balancer defines the load balancer and its configuration.

## Web Backend Layer \\ same services as Application Layer

- EC2 defines the web server and its configuration.
- Lambda is a serverless function that runs the web server.
- ECS helps managing containers and scaling them.

## DB

- Amazon Aurora defines the SQL database and its configuration.
- Amazon RDS defines the SQL database and its configuration. (lets you decide DB)
- DynamoDB is a Key Value Lookup
- DocumentDB is a NoSQL database (compatible with mongoDB)
- Opensearch is a Fuzzy Finder


## Caching

- ElastiCache defines the cache and its configuration. (Memcached, Redis)
- Cloudfront is a CDN (replicates Content across continents)

## Deployment

- CodeCommit, CodeBuild, CodeDeploy & CodePipeline help with deployment

## Monitoring

- CloudWatch defines the metrics and logs and its configuration.
- CloudTrail defines Operations that are performed and their configuration.

## Identity and Access Management

- IAM implicitly denies access to users.

## Infrastructure-as-Code (IaC)

- CloudFormation is a template-based solution that helps you build 
and deploy resources in the cloud. (YAML, JSON)
- CDK is a  framework for creating AWS Cloud Development Kits.(without using YAML)

## Event Coordination

- SNS is a PubSub messaging service.
- SQS is a Simple Queue Service that holds Msgs to be processed later on.
- EventBridge allows Third-Party Integrations.

## Object Storage

- S3 is a object storage service.
- Can be used to replicate data from DynamoDB or store Event Coordinator logs.



