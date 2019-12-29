# Deep Dive Into Application-Level Network Management & Observability With App Mesh
* Service mesh
* Continuous flow management
* Failure isolation and protection
* Fine-grained deployment control
* Metrics, logs, tracing, etc. exposed through app mesh - complete visibility

* Sits between all services (it’s a proxy)
* GRPC-API known as XDS
* Translates intent to proxy config

## Design Intentions
* Declarative API
* Clear ownership boundaries
* Opinionated resources
    * Virtual services act as the pointer to real services
* Features that scale with your needs
    * Traffic shaping
    * Security
    * Resilience
* Virtual routes, virtual nodes

## Journey to App Mesh
### Mapping to the Mesh

* Frontend Virtual Node -> Backend Virtual Service -> Backend Virtual Node

* Difference virtual services can bind to the same virtual node (the actual backend)

* Use a virtual router to route specific virtual services to different nodes
    * Granular traffic shifting between nodes

* Point to point communication
* Virtual nodes are abstractions over actual services / deployments

### How do we configure Envoy proxy?

* Envoy provides lots of metrics and statistics over the network topology
* Envoy clusters are groups of endpoints that can be load-balanced
* Envoy service is equivalent to a VirtualHost (i.e., Apache) match a hostname to a destination

Example:
1. Envoy matches an incoming request to a VirtualHost -> determine destination
1. Routes match the specific cluster
1. Envoy forwards request to the appropriate cluster

## App Mesh and Amazon EKS at Chick-Fil-A
* 45k requests per minute on a single API endpoint
* Most services run in EKS backed by DynamoDB
* K8 cluster per restaurant 
* Kubernetes Common Platform (KCP)
    * Swappable components for building containers

## Why EKS?
* Declarative configuration
* Self healing 
* Decreased operational burden

## Why App Mesh?
* Single deployment
* Works across multiple AWS services
* Advanced deployment patterns
* Advanced monitoring