# ACID Properties of Relational Databases

## Transaction

- Transaction is a Collection of Queries that must be applied Together.
- Transaction starts with a BEGIN and ends with a COMMIT or ROLLBACK.

## Acidity

- All Queries must succeed. if one fails, all queries are rolled back. 
- The DB must clean up and ROLLBACK after crash.

## Isolation
- Read Phenomena includes Dirty Reads, Unrepeatable Reads, Phantom Reads.

### Dirty Reads

- Reads that read data that has been changed by other transactions before being committed.
- value of 50 + 80 is read as 155 because another query has 15 that gets added despite not being commited

### Unrepeatable Reads

- Reads that read data that has been changed by other transactions after being committed.
- value of 50 + 80 is read as 155 because another COMMMIT has 15 that gets added
- Postgres makes a new version for the row 
- MYSQL & Oracle make an undo table

### Phantom Reads

- Reading a Sum after a Row has been commited, 50 + 80 are 155 because another row was commmited before the sum was calculated (Selecting 50,80 first then summing them)

### Solutions 

- Read Uncommited - No Isolation
- Read Commited - Default Isolation (Each Query only sees commited data)
- Repeatable Read - Isolation (ensures row is unchanged while it's running) (prevents up to Dirty Reads)
- Snapshot Isolation - Isolation (only sees changes that have been commited up to start of transaction) (prevents up to Phantom Reads)
- Serializable - Isolation (Transactions run as if they were single threaded) (Slowest but prevents all Phenomenas)

## Consistency

- Consistency refers to the ability of a database to provide consistent results to queries.
- Eventual Consistency delays Consistency now for Availability 

## Durability

- Durable refers to the ability of a database to survive power outages.
- WAL (Write-Ahead Logging)
- Asynchronous Snapshot
