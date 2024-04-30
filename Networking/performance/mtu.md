# MTU & MSS

## Basics 

- MTU is the Size of the Frame (default 1500 Bytes)
- 1 IP Packet must fit in a single Frame
- Larger IP Packets will be fragemented into multiple Frames
- Larger Frames can't be sent 

## MSS

- Segement must fit inside a Packet that fits inside a Frame
- MSS = MTU - IP Headers - TCP - Headers
