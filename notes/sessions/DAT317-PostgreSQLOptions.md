# PostgreSQL Options in Amazon
PostgreSQL
* More than 30 years of development
* A lot of amazon.com uses Aurora PostgreSQL
* All packages from amazon go through Postgres

## Running PostgreSQL on AWS
Self managed on EC2
Amazon RDS for PostgreSQL
Aurora with PostgreSQL compatibility
 Most companies are using stock PostgreSQL, in that case, go for managed

## Managed PostgreSQL on AWS
PostgreSQL 9.6, 10, or 11 with over 60 extensions
    * Additional data types
    * Additional index types
* Backup and recovery
* High availability and durability
* Security and authentication
* Management and monitoring

## Amazon RDS for PostgreSQL
* HA across two availability zones
* Supports 9.4, 9.5, 9.6, 10, and 11
* Many instance types, T, M, R family

## Amazon Aurora with PostgreSQL Compatibility
* Supports 9.6, 10, and 11
* 2-3x better throughput
* Highly available, durable, and fault tolerant storage layer with 6 way persistence across 3 availability zones
* Scalable up to 64TiB

## Amazon Aurora Serverless
* Supports 10.7
* Scales up/down automatically
* Highly available, durable, and fault tolerating storage layer with 6-way persistency across 3 availability zones
* HTTPS endpoint using a REST API for running queries without a persistent connection

## High availability for RDS PostgreSQL
* Multi AZ configurations with a fault tolerant   architecture
* Each host manages a set of volumes with a full copy of the data
* Redirection to the new primary instance is through DNS (Route 53)
* Detects infrastructure issues, not DB engine problems
* Single primary

## RDS PostgreSQL Backups
* Two options: automated acquisition and manual snapshots
* Uses Amazon Elastic Block Store
* Snapshots are stored in S3
* Transaction logs are stored every five minutes in S# to support PITR
* Snapshots can be copied between regions and accounts
 
## Security
* Encryption to ensure unauthorized users cannot see the data
    * In transit using SSL
    * At rest using AWS Key Management Service

* Authentication to ensure a user is known and trusted
* Auditing to verify the trusted user is only accessing permitted content

### Network Encryption
* RDS instances have an SSL certificate
* Set RDS.force_ssl to 1 to enforce SSL to reject all non-SSL connections
* Client requests the type of SSL connection
    * sslmode=require to enforce SSL from the client side
* You can use your own SSL Root certificate

### Authentication
* AWS ./ IAM
* Kerberos
* Local PostgreSQL accounts

Kerberos authentication
* Client machine must be in the same AWS Active Directory
* Grant privileges on an object-level role

AWS Secrets Manager to enforce password rotations
Logs are available in Amazon CloudWatch
