# Database Storage Manager

## Basics

- Database Files are only read and accessed by the DBMS.
- IO can only read Pages not Rows, Pages are inserted in Heap
- Files consists of Pages (Fixed size blocks of data)
- Each Page has a Unique ID for managing the Page
- Each Tuple has Unique ID for accessing the Tuple
- Slotted Pages have Slots that points to Tuples 
- Log structure for managing the Transactions sequentially based on insertion time
- Index organized Tables makes reading faster and writing slower

## File Organization

- Heap File Organization
- Tree File Organization (Indexing)
- Sequential File Organization (Batch Processing)
- Hash File Organization (equality Searches)

## Heap File Organization

- Uses Page Directory (Special Page in each File)
- Locates the page in each File including Empty Pages


