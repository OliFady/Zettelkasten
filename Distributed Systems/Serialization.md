- Serialization describes the process of taking an object’s state and transforming it into a stream of bytes
- A stream of bytes is a sequence of bytes that is made available over time.
- A stream is an abstract definition of a sequence of data that is made available over time.
- A byte is an 8 bit (0s or 1s) group of data.
![[Pasted image 20231220115610.png]]

## Deserialization
- The stream of bytes created by serialization only includes the member variables of an object and not its methods.
- Deserialization creates a copy of the original object. This copy shares the same state but is an entirely new object in memory.