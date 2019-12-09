CON421 - Amazon EKS Under the Hood
CON421-R1OFMGM - [OVERFLOW][repeat 1] Amazon EKS under the hood (Blue-MGM)

Kubernetes allows you to run containerized workloads and services using declarative configuration and automation. Amazon Elastic Kubernetes Service (Amazon EKS) is a managed service that makes it easy to run Kubernetes on AWS without needing to stand up or maintain your own Kubernetes clusters. Amazon EKS takes care of the undifferentiated heavy lifting around securing, patching, qualifying, and upgrading Kubernetes clusters. Join us for a look under the hood at how Amazon EKS manages Kubernetes at scale. We also discuss some of the key design decisions in building out the infrastructure to manage one of the industry's fastest-growing open-source projects.

Additional Information
Session Type:Overflow
Topic:
Session Level:400 - Expert
Please note that session information is subject to change.
Session Schedule
Thursday, Dec 5, 4:00 PM - 5:00 PM
– MGM, Level 1, Boulevard Ballroom 170, Content Hub, Theater 1, Blue

- user-endpoints - eks - k8s

EKS service endpoint

platform services team

- Cluster administrator
- Regionalized eks service endpoint - amazon EKS
- Kubernetes resident application

developers

- ci / cd git ops automation -> kubernetes api server endpoint

- you can run a k8s cluster on your laptop while eks runs a very opinionated version of k8s across 3 azs
- eks managed vpc - > single tenant eks control plane
- customer managed vpc of instances and spot instances

they've split the contrl plane
all run in a single ASG across a minimum of 3 AZs
everything runs in a private subnet
managed ingress and egress

- they built a managed control plane that was durable, performant, and secure
- the etcd cluster itself has its own load balancer
- balancers for every aspect of the network traffic
- they let us scale up vertically and horizontally

# EKS Under the Hood

## Cellular Archtiectre

- one complete instance of a software component is an instance of a cell
- you can test a cell to failure with predictable failure modes
- what are the dimensions for scaling out horizontally and vertically

## EKS Scalable Architectural Components

- aws cli/sdk, console

### Frontend

- amazon api gateway
- aws lambda
- amazon cloudwatch events

### Cluster Events

- api gateway
- lambda
- aws step functions
- amazon dynamodb
- s3 bucket events

### Control plane management

- lambda
- aws cloudformation
- amazon dynamodb
- aws step functions

amazon.com runs a signifcant portion of their front page and other pages on EKS

- high degree of flexibility

## EKS Operations

### EKS Regional Deployment Safety

- prow cluster
- canaries
- integration system tests
- geometric deployment pattern from 1 to 2 to 4
- never touch 2 regions at the same time
- when deploying to multiple cells in a single region, all cells must start successfully

## EKS Components

- 50 different pipelines to release EKS
- for the last quarter, there were 17k atomic operations for one pipeline out of the 50 testing and deployment
- 1500 pipeline events a week

### EKS Enhancements

- Over 75 features added this year
- Control plane logs can be put into your amazon cloudwatch
- API Server endpoint access control
- cluster creation limit raised to 50 per region
- 99.9% SLA
- Windows worker node support for production mode
- Managed Node Groups -> This is where the auto-provision and de-provision the nodes from your cluster depending on need.
- AWS ALB Ingress Controller
- Kubernetes v1.14 upgrade

### AWS IAM ROles for Service accounts

secure

- iam policy restrictions can restrict roles to Service Accounts or Namespaces
- Enables ioslated aws permissions per service account
- credential are automatically oratted
  -the cluster's isgning key is autmatically rotated

Eay ingtegration

- annotate the service account
- built into the defaul t credential chains in the aws sdks and cli

- Project service account token , "projected" is special.
- You can use it and validate it against a 3rd party provider
- AWS security token service

## Priorities

- p0 - reliability

## Investments in security and reliability

- Cellular arch
- Cumulatively run millions of clusters, performed millions of cluster version upgrades
- Version qualification and release
- Security patching
- Operations tooling

## AWS Fargate for Amazon EKS

- Fargate is a serverless compute platform for containers on AWS

- Bring existing pods
- Production ready
- Right-sized and integrated
  - only pay for the resources

* EKS FARGATE PROFILE TEMPLATE
* subnets to launch the pods in
* selection criteria into faragte
* iam role to be associated to the kubelet

If you use fargate

- things you no long need to do
  manage k8s work nodes
  pay for unused capacity
  use k8s cluster autoscalaer (ca)

#### Things you get out of the box

- VM isolation at pod level
- Pod-level billing
- Easy charging in multi-tenant scenarios

#### Things you cant do (for now)

- Deploy daemonsets
- Use service type LoadBalancer (CLB, NLB), you can only use ALB (level 7)
- Running privileged containers
- Run stateful workloads

# Snap Service Mesh on EKS

- Security by default
- Standardized traffic management and routing policies
  - Service discovery - just call `<service>.snap`
  - Zonal affinity and regional proximity to favor closest endpoints
  - Traffic splitting, mirroring, and fail-over
  - Automatic resilience and circuit breakers
- observability by default
