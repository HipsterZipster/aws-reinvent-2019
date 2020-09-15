# Transform The Way You Search And Interact With Enterprise Data Using AI
20% of the time looking for information
44% of the time can’t find the information

## Problems
* Low accuracy
* Keyword engines just look for words, not a knowledge graph
* Enterprise data is spread across different silos

## Rethinking Enterprise Search (Amazon Kendra)
* Continuous improvements
* ML models built to understand search queries, i.e., not keyword search
* Native connectors to pull data from multiple sources
* Reading comprehension
* FAQ matching
* Document ranking

* Where is the IT support desk? Location
* How long is maternity leave? Quantity
* How do I configure my VPN? Paragraph

* 16 levels of domain expertise, including financial services

* Captures click-through and user feedback
* Retrains models periodically

### Relevance Tuning
* Authoritative data sources
    * Control priority of sources
* Document freshness
    * Control priority of document metadata (i.e., recent documents)
* Authors or departments
    * Control priority of documents based on the query context (i.e., HR queries prioritize HR documents)
* Upvotes and popularity

### Connectors
S3, JWDBC, Sharepoint

### Test and Deploy Amazon Kendra
* Test your queries
* Tune your relevance

### Security
* In transit -> HTTPS/TLS
* At rest -> AWS KMS / Customer KMS

## How Kendra Works
* FAQ models
* Unstructured document models
* Recommended document models

### Create an index
1. Name it
2. Add a data source
    1. S3
    2. Sharepoint
    3. RDS
3. Add FAQ documents (curated Q&A)

Supports Query auto-completion

### Use Cases
* Internal search
    * Supporting business functions such as operations, customer support, RD
* External search
    * Helping your customers find the information they need
* CRM
* Content management
* EDiscovery
* ISVs can build more intelligent and data-driven applications using Kendra

### Customer References
* 3M, Sage, 
* Workgrid -> Self-service Q&A bot
* Woodside