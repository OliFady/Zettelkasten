		# Database Index

## Basics 

- Indexing prevent Full Table Scan (Alt: Parallel Scan \ Partitioning)
- List Index consists of Key and Location (O(N))
- BTree Index consists of Key and Location (O(log(N)))
- Like Query is still slow whether Column is Indexed or not

## Hash Indexing

- Best for Specific Key value grabbing not for Range Queries

## B Tree

- Each Node can contain K Children
- B Trees are always balanced (atleast half nodes should be filled)
- Keys are sorted (Best for Range Queries)

## B+ Tree

- Data Pointers are stored in the leaf nodes
- Leaf Nodes link to each other
