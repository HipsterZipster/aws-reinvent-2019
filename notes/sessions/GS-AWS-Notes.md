# GS Private Meeting + AWS Leadership around API Gateway

**AWS Reps**

- Ata Ivanov
-
-
-

## API Gateway

- New version of API Gateway released this year
- Cheaper
- Faster Latency drops by 60% - P99 latency is under 10%
- Easier One step to create API instead of 7

### Coming Soon:

- Mutual TLS should be available around April
- Currently can't connect API Gateway to ECS/EKS unless you go through an NLB, they will add support for ECS clusters that are exposed by an ELB
- What will be the integration with AppMesh?
  - They're starting to work with the container team to work on cross-cluster communication.
- How does API Gateway interact with the EKS cluster?
  - If your cluster uses a sidecar to rate limit to 1000 TPS, how do you manage that on both internal and external requests to the cluster?
- Added support for CloudMap
