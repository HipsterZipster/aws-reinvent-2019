# SVS308-R - Moving to event-driven architectures

Event-driven architectures are getting a lot of attention. We have recently invested in tools and infrastructure to make event-driven architectures easier to implement and operate. In this session, we discuss what events are, why the community is increasingly interested in event-centric applications, and what’s new in the domain and with AWS in particular. In addition, we discuss the challenges that still face us and our customers. By the end of this session, you understand the key principles and benefits of being event-driven.

**Speakers**

- Tim Bray - VP/Distinguished Engineer, Amazon Web Services

**Session Info**

- Session Level:300 - Advanced
- Wednesday, Dec 4, 10:45 AM - 11:45 AM
- Venetian, Level 2, Venetian Theatre

---

## Amazon.com Needs

- amazon.com needs
- scalable ingestion
- reliable order
- fan ont

## Amazon.com Doesn't Need

- strong ordering
- de-duplication
- push delivery
- ultra-low latency

## Is event-driven for you?

1. Are you passing around self-contained transactions
1. are useful events avialbe for free
1. do you need to decouple your microservices?

#### Example of small AWS event

- "detail-type" field determines what it is

## What is an "event"?

### Event Processing Facets

1. Strict Ordering: Do we care about the order that the events are digested?
1. De-duplication: Does it matter if somehow the same event is sent more than once?
1. Point-to-point vs pub/sub
1. Serverless vs broker/cluster
1. Filtering vs firehouse
1. Data blobs vs structured objects (protobuffs, avro, thrift, parquet...)
1. Records vs Documents (records meaning Relational database rows that have relationships for their nested objects)
1. Uniform vs heterogeneous events

#### Amazon EventBridge Schema registry

- Generates code bindings for python, typescript, vs code, intellij

### Events vs APIs

- Virtual queues - where i put a field inside the message that contains how we would like to be called back

### Events vs Service Mesh

- Istio / AWS App-Mesh

## Eventing things that still need work

- Loops!
- Too much pipe-fitting
- Easier and safer access control
- Blobby events, discovery, and autocomplete needed

