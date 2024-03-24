# Postgres Differences

## No Primary Key

- Postgres does not support primary key, creates for you a unique id.
- Indexing using Secondary Index references the Unique ID
- Primary Key makes it that you have to insert in a specific Page (clustered)
- No Primary Key makes writing in any Disk Page easier than using Mutexs

