2019-12-02

# Amazon RDS PostgreSQL universe

- Concurrency: Remove Log Buffer
- uses a durability buffer
- they write less
- 

# Conventional Database backups
- full -> diff incremental -> diff incremental -> current incremental 
- incremental backups
  - optimal case - all writes are to the same database blocks
  - non-optimal case - every write goes to a non optimal block - 10x more work
- aurora backups have no concept of days, it's a continuous backup 

# insert test
- test table
- inserts per second vertical axis, minutes running the test x axis
- 25k inserts per second no issue
- increasing the log size means 97% faster receovery time
- as you generate more WAL, it takes longer to recoover 
- regular postgres 3gb 19 seconds, 10 gb redo recovered 50 seconds, 30 gb redo recovery 126 seconds
- aurora has no redo, recovered in 3 seconds while mainting singnficiatly greater thoroughuput

# Durability: 4/6 quurom 

- Typical synchronous replication: 3 locations (AZs)
- 1 primary, 1 secondary, 1 tertiary
- Cost of additional synchronous replicas
- 4 9s means 1/10000 io operations can fail
- All replications are sent out simultaneously
- 3 AZs, 6 copies
- Amazon aurora gives >2x lower reponse times
- systebnech -95 30 gib 1024 clients
- response time says under 100 ms even with 30gb constant input
- Replicas: PostgreSQL
- Fast clones
  - You dont have to spawn up completly new instances to do a fast clones
  - they use copy on write
  - fast clone example rw rate - 10k, target rate 20k tps
  - main database, clone database

# replication
- logical replicagion support
- converts physical; changes wal to sql statements (LOGICAL)_
- logcal decoding plugin

# Amaazon Aurora Global Database
- 2 regions - 3 azs
- storage to storage based replications
- replication servers -> replication agents 
- all our RO EXCEPT FOR one which is RW
- caching changes - no double buffering
- Query plan management


# ARC203 Innovation At Speed 

Venetian Theater 12:15 - 

## Culture 

- new needs: personalization, customer analytics, new channels direct to consumer, more scale, rapid changes
- leadership system and feedback problems
-centralized slow decision-making lack of trust
- inflexible policies and processess

- ahead in the cloud - stephen orban https://www.amazon.com/Ahead-Cloud-Practices-Navigating-Enterprise/dp/1981924310
- a seat at the table and war and peace and IT - mark schwartz https://www.amazon.com/Seat-Table-Leadership-Age-Agility/dp/1942788118

## Nordstrom - culture
- "use good judgement in all situations"
- trust yet verify


## netflix -0 culture
- values are what we value
- high peformance
- freedom and reponsibility
- context not control
- highly aligned loosely coupled
- pay top of market
- promotions and development


 ## amazon culture
 - customer obsessions
 ownership
 invent and simplify
 are right, a lot
 hire and develop the best
 insist on the highest standards
 think big
 bias for action
 frugality
 learn and be curious
 earn trust of others
 drive 
 deep

intentional, appropriate, judgement

## Skills

### training and compensations
- train existing staff on cloud tech
- fund pathfinder teams
- be prepared to create incentives to keep the best people after training
- get out of the way of innovation
- read the recent book powerful by patty mccord - ex-netflix chief talent officer


# move from projects to product teams
- Long-0term product ownership
- Continuous delivery
- DevOps and run what you wrote
- Reduce tech debt and lock-in
- Project to product book - mik kersten 
- DevOps handbook team
- integrate business with devops
- AWS Service teams BusProdDevOps
  - business 

# reporting and learning
- Monday 
- Tuesday
- Wednesday
https://aws.amazon.com/blogs/opensource/the-wheel/


## Risk / Finance

- capex vs opex
- capitalized data center to expensed cloud
- capitalized development , expensed operations to combined DevOps
- plan ahead, don't surprise the CFO or your shareholders

# Whats the role of boards in the long-term success of their company
- Book: Transforming nokia - Risto Sillasmaa https://www.amazon.com/Transforming-NOKIA-Paranoid-Optimism-Colossal/dp/1260128725/ref=sr_1_1?keywords=transforming+nokia&qid=1575319167&s=books&sr=1-1

- compensation policy - short term focus 
- executive successsion
- oversight of finance
- oversight of risk
- oversight of strategy


-we cant change processes and policies because of our org chart
-change from project and product
- we cant change culture because incentives aren't aligned
- we cant change incentives because compensation isn't flexible enough
- 


# pathway to innnovation
- speed - time to value
- scale - distributed workloads
- strategic - critical 

## Speed

### What is the fundamental metrics for innovation
- There is no economy of scale in software
- Smaller changes are better


## Scale

### Distributed Optimized Capacity
- cloud native principles
- pay as you go, afterward
- self-service, no waiting
- globally distributed by default
- cross-zone/-region avaialbility models
- high utilization - turn idle resources off
- immutable code deployments

## Strategic


## Containers vs serverless comparision

| Containers | Serverless || -- 

## Observabilty high to low
- high - lambda functoin with no side effects
- microservice that does on e thing
- monolith with tracing and loging
- low monolith with logging
- Books: Engineering a SAfer World - systems thinkinh applied to safety by nancy g leveson
- STPA model 0- 


## Epidemic example
- linux leap - second bug



## Chaos Architecture
- four layers
- you can only be as strong as your weakest link
- failures are a system problem - lack of 
- dependble 
- cloud gives the automation for chaos engineering

- testing failure mitigation

- Cloud for CEOs - measure innovation with one metric - adrian cockcroft
