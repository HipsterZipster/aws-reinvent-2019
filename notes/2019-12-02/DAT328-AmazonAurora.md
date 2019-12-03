# DAT328-R Deep dive on Amazon Aurora with PostgreSQL compatibility

Amazon Aurora with PostgreSQL compatibility is a relational database service that combines the speed and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases. In this session, we review the functionality in order to understand the architectural differences that contribute to improved scalability, availability, and durability. You'll also get a deep dive into the capabilities of the service and a review of the latest available features. Finally, we walk you through the techniques that you can use to migrate to Amazon Aurora.

**Speakers**

- Kevin Jernigan - Principal Product Manager, Amazon Aurora PostgreSQL, Amazon Web Services
- Grant McAlister - Senior Principal Engineer, Amazon Web Services

**Session Info**

- Session Level:300 - Advanced
- Monday, Dec 2, 10:45 AM - 11:45 AM
- Venetian, Level 2, Venetian Theatre

# Amazon RDS PostgreSQL universe

- Concurrency: Remove Log Buffer
- uses a durability buffer
- they write less

# Conventional Database backups

- full -> diff incremental -> diff incremental -> current incremental
- incremental backups
  - optimal case - all writes are to the same database blocks
  - non-optimal case - every write goes to a non optimal block - 10x more work
- aurora backups have no concept of days, it's a continuous backup

## insert test

- test table
- inserts per second vertical axis, minutes running the test x axis
- 25k inserts per second no issue
- increasing the log size means 97% faster recovery time
- as you generate more WAL, it takes longer to recover
- regular PostgreSQL 3gb 19 seconds, 10 gb redo recovered 50 seconds, 30 gb redo recovery 126 seconds
- aurora has no redo, recovered in 3 seconds while maintaining significantly greater throughput

# Durability: 4/6 quurom

- Typical synchronous replication: 3 locations (AZs)
- 1 primary, 1 secondary, 1 tertiary
- Cost of additional synchronous replicas
- 4 9s means 1/10000 io operations can fail
- All replications are sent out simultaneously
- 3 AZs, 6 copies
- Amazon aurora gives >2x lower response times
- sysbench p-95 30 gib 1024 clients
- response time says under 100 ms even with 30gb constant input
- Replicas: PostgreSQL
- Fast clones
  - You don't have to spawn up completely new instances to do a fast clones
  - they use copy on write
  - fast clone example rw rate - 10k, target rate 20k tps
  - main database, clone database

# Replication

- logical replication support
- converts physical; changes wal to sql statements (LOGICAL)\_
- logical decoding plugin

# Amazon Aurora Global Database

- 2 regions - 3 azs
- storage to storage based replications
- replication servers -> replication agents
- all our RO EXCEPT FOR one which is RW
- caching changes - no double buffering
- Query plan management
