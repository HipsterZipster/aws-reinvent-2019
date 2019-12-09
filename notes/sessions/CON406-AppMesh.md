# CON406-R1 Deep dive into application-level network management & observability with App Mesh

AWS App Mesh provides enterprise-ready features beyond what is available through open-source solutions for application-level networks. In this session, we do a deep dive on best ways to onboard your applications to App Mesh, including how to configure your application, layer in different capabilities, tune your route settings, and configure dashboards needed to observe apps. You also learn what your teams should know to maximize value from App Mesh.

**Speakers**

- Brian Celenza - Sr. Software Engineer, Amazon Web Services
- Christopher Lane - Enterprise Architect, Chick-fil-A

**Session Info**

- Session Level:400 - Expert
- Wednesday, Dec 4, 5:30 PM - 6:30 PM
- Venetian, Level 3, Lido 3002

## What is ApMesh

- Consistent communications management
- Complete visibility
- Failure isolation and protection
- Fine-grained deployment controls

## How does App mesh work?

Proxy sits between all services manage and observes ice traffic

- gRPC connection
- Control Plane - translate intent to proxy config
- Distributes proxy config

## AppMesh Design Intentions

- Declarative API
- Clean ownership boundaries
- Opinionated resources, flexible mesh layouts
  - Virtual services act as the pointer to real services
  - How you construct the network graph is totally up to you
- Features that scale with your needs
  - Traffic shaping
  - Security
  - Resilience

## AppMesh API Design

- They'll automatically create a controller and injector for our k8s cluster

### Journey to App Mesh

- mappping to the mesh
- whats actually happening
- appmesh in action

"Strangular pattern" - a variwty of vertual services poin to a single action service node

### Mapping the Mesh

- FE Webserver virtual node
- BE /details virtual service
- BE /cart virtual service
- BE checkout virtual service -> checkout virtual router (route) -> checkout virtual node

#### What's actually happening

- Point to Point communication

- Proxy to Proxy Communication

#### 

How do we configure Envoy Proxy?

COM323 - Session deep dive how app mesh works

# Chick-fil-a

- Clusters per region, per edge, per environment
- Kubernetes Common Platform (KCP)
- Layers from bottom to top

  - k8s - amazon EKS
  - sys - external dns, ALB ingress, EFS Provisioner
  - Core - External secrets, argo CD, Ambassador, Prometheus, Grafana, AppMesh, Flagger
  - App - Containers

- Live demo of creating a cluster with appmesh
- `kcp create` - takes about 16 min and then starts with a
- They never run kubectl directly...they update a master Kubernetes repo

## Canary Deployments

- Using flagger from weaveworks
  - Defines canary CRD
- Automatically creates virtual nodes, routes, and services based on Canary spec
- See picture
- Primary track on top leads back to the primary deployment
- sets up 2 new virtual routes in the list
  - 100% to primary
  - 0% to canary
