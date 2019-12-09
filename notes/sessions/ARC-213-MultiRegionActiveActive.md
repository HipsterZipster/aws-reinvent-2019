ARC213-R1 - [REPEAT 1] Architecture patterns for multi-region active-active

With global business, there is an ever-growing need to be able to implement multi-region active-active architecture. However, this requires first-order thinking and attention not just to app and database design but also to DNS, monitoring, traffic shaping, and so on. Furthermore, architecture complexity can increase rapidly, so multiple design trade-offs need to be made. In this session, we discuss challenges and solutions using various AWS services, like Amazon DynamoDB global tables, as well as open source products.

**Speakers**

-
Girish Dilip Patil - Senior Architect, Amazon Web Services

Jonathan Dion - Senior Technical Evangelist, Amazon Web Services
Thomas Jackson - Head of Core & Data Infrastructure, Wish (ContextLogic)

**Session Info**

Additional Information
Session Type:Session
Topic:Architecture
Session Level:200 - Intermediate
Please note that session information is subject to change.
Session Schedule
Wednesday, Dec 4, 3:15 PM - 4:15 PM
– Venetian, Level 3, Lido 3005

---

Agenda

- why do you need it?
- design principles
- foundational pillars
- a customer's journey - Wish's path

Why do you need a multi-region active-active archyiecture?

- Everything fails, all the time "Werner Vogels" CTO Amazon.com

Guarding against failure of your application in one region?

- You need to reduce the blast radius of any catastrophic events

### Problems with conventional DR solutions

- DR environments aren't used
- fall out of sync, eventually
- waste money

### Tolerance for network partitionaing

- see pic
- any problem in one region should no lead to failure of applicatoin another
- minimal blocking api and database calls traversing regions

### Minimal data replication requirements

- does all data need to be replicated
- if yes does it need to be replicated synchronously

### data classification

- example ecommerce workload
- pruchase recoprd, product details, clikc wstream, https logs
- low vol, highly critical -> high volume, less critical

# Sync vs Async

replication modes

- see pic
- SYnc - Region A: app write, replicate to B, ack to A
- Async - A writes to
- FOLLOWW UP

#### Pattern 1: read local, write local

- ## see pic

#### Pattern 2: read local, write global

### Single-region high-availability approach

- leverage multiple AZs
- they see the vast majority of EC2 customers not spreading their instances across multiple AZs within a given region
- try to colocate resources in the same AZ to save on data transfer cost

### Example of Services that are Multi-AZ

they replicate data 6 ways across 3 AZs

# Data Replication

## s3 cross-region replication

- automatically replicate data to any other WS region
- replicate by object, bucket, or prefix
- anything not transferred in 15 minutes is free

Amazon Elastic Block store snapshots
-point in time

# DynamoDB Global Tables (read local, write local)

- replicate table across multiple regions
- read and write any items in any region
- eventual convergence
- conflicting updates resolved with last write wins
- data is replicated in seconds max to all regions

# Global Tables management

- amazon cloudwatch metrics

# Amazon RFS cross-region replication -

- one master, many replicas
- replica lag

## Multi region consolidation of analytics data

- dont run every service in all regions, only the ones that are critical, client facing, and wont cause data loss

Foundational Pillars

- High availability
- Data replicatiopn
- Networking
- Traffic routing
- Manangment

## Networking

### Amazon VPC and software VPN

### AWS Global Infrastructure

- redundant 100 GbE network
  -private network capacity between all regions except china

### Inter-region VPC Peering

- Encrypted
- No single point of failure
- No bandwidth bottleneck
- Always-on AWS backbone

## Traffic Routing

- traffic routing with amazon route 53
- latency-based routing - pick a regional resource by latency
  - The request does not go through route 53, but router 53 stores the session / ip address in a global cache
- Geo-location Routing
- DNS Failover

### Traffic routing with AWS Global Accelerator

- all clients point to the same static IPs and are directed to the closest PoP
- Global Accelerator chooses the optimal AWS Region based on the geography of the client
- Anycast IP ?

### DNS-based solutions vs Global Accelerator

#### DNS-based traffic management solutions

##### Global Accelerator

- no reliance on IP address caching of client devices
- reduced downtime (change propogation in seconds)
- Static IP addresses - No need to update DNS or client when moving endpoints across regions/azs

##### DNS-based traffic management solutions

- client devices can cache dns answer for a long time
- hard to know when users will have the update ip addresses
- this matters for blue/green deployments, backend failure, or change in routing preferences

Traffic routing with Amazon CloudFront + Lambda@Edge

- user from ca

## Management

| Management area         | AWS service                  |
| ----------------------- | ---------------------------- |
| security and compliance | aws config rules             |
| automation inventory    | aws systems manager          |
| monitoring and logs     | amazon cloudwatch            |
| resources provisioning  | AWS CloudFormation Stacksets |

### AWS CloudFormation StackSets

- provision resources across multiple AWS accounts and regions

## Multi-Region Architectures on AWS

- wish shopping
