# Hands-On: Building a Multi-Region Active-Active Solution
Why multi-region?
* Improved latency and performance
* Increased fault tolerance 

## Architecture
* Polyglot persistence using DynamoDB and Aurora MySQL
* Fault tolerance

## Route 53 Routing
* Health checks
* DNS-level failover to healthy resources
* Active-active DNS actively returns more than one resource

## CloudFront with S3 Origins Group
* Duplicate static content geographically
* S3 origin-group failover

## API Gateway
* Regional endpoints trigger lambda functions
* Custom domains for specific regions
* Wildcard custom domain name routing

## Aurora Multi-Region Read Replica
* Reduce geographic read latency
* Relieve pressure on master for reads
* Fast promotion of read to master in event of failure

## DynamoDB Global Tables
* Multi-region redundancy 
* Transactional dates
* Last writer wins for eventual consistency