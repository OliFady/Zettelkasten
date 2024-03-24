# SQL Databases (1)

# ACID Properties

## Atomicity

Sub-Actions will either all succeed or all fail (rollback)

# Consistency

future and past states of the Database are aware of each others.

## Isolation

multiple transactions can occur at the same time, but they’re actually put in a queue (sequentially)

the other query will hang until the first is committed.

## Durability

Effects of a transaction are permanent

# Indexing

additional data structure that’s optimized for fast searching on a specific Column.