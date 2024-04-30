# ACID Properties of Relational Databases

- Transaction is a Collection of Queries that must be applied Together.

## Acidity

- All Queries must succeed. if one fails, all queries are rolled back. 

## Isolation

- Read Phenomena includes Dirty Reads, Unrepeatable Reads, Phantom Reads.
- Dirty Reads: A query is executed on a table that has been modified by another query.
- Unrepeatable Reads: Two queries are executed on the same table in a single transaction.
- Phantom Reads: A query is executed on a table that has not been modified by any query.

## Consistency

- Consistency refers to the ability of a database to provide consistent results to queries.
- Eventual Consistency delays Consistency now for Availability 
