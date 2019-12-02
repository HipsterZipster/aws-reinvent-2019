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


---