# AWS App Mesh Under The Hood
## Principals
* Routing
    * Automatic retries
* Observability
    * One request might fan out to dozens of requests
    * Visualize the entire call graph of a single request
* Security
    * Encryption at rest and in-transit
    * Authentication
    * Authorization

## Handling Application Traffic
* Deploy a proxy with each application
* Uses iptables to transparently proxy all traffic

Virtual Node: Source and destination of all traffic within the mesh
Virtual Service: Defines a logical target for traffic
Virtual Router: Matches and routes traffic to virtual nodes

Virtual Node -> Virtual Service -> Virtual Router -> Virtual Node

Virtual because these don’t actually exist in the network. It’s a declarative model

## System Design
Users -> Frontend Service -> Transformer -> Envoy Management Service -> Envoy

Transformer converts the AppMesh model into an Envoy model