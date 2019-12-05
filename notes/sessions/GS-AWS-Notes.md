# GS Private Meeting + AWS Leadership around API Gateway

**AWS Reps - All API Gateway**

- Ata Ivanov - Lead Engineer
- Svetlana -
-

## API Gateway

- New version of API Gateway released this year
- Cheaper: They've created a lighter second variation of the API Gateway
- Faster: Latency drops by 60% - P99 latency is under 10%
- Easier: one step to create API instead of 7 steps

### Coming Soon:

- Mutual TLS should be available around April
- Currently can't connect API Gateway to ECS/EKS unless you go through an NLB, they will add support for ECS clusters that are exposed by an ELB
- What will be the integration with AppMesh?
  - They're starting to work with the container team to work on cross-cluster communication.
- How does API Gateway interact with the EKS cluster?
  - If your cluster uses a sidecar to rate limit to 1000 TPS, how do you manage that on both internal and external requests to the cluster?
- Added support for CloudMap
- Can we access the API Gateway control plane from within the VPC? They're working on it, maybe by end of Jan.
- Limit management is more DIY for Account managers
- Integrate with events that can get triggered when any of the configuration changes are made for any of the APIs

**GS Folks**

- David Burford - ?
- Ankur Gurha - GIR
- Robert Waugh - Core Eng?
- Roman Novichenok - Linux Eng
- Isabelle Disler - SRE
- Ismeet Dhillon
- Alistar Mcdougal
- Swami ?
-
