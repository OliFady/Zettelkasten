- Each Machine on the Network is called a *Node*
- Every Node has an Address (Sequence of Bytes)
- All Networks are packet-switched (Checksums are used to validate the Packet)
- HTTP is the most commonly used protocol for Communication
## Message Flow

- Layer 7 => when a web browser sends a request to a web server, the browser is actually talking to the transport layer on the local client machine.  
- Layer 4 => The transport layer breaks the request into TCP *segments*, adds some sequence numbers and checksums to the data, ensures packets arrived in-order, and then passes the request to the local internet layer. 
- Layer 3 => The internet layer fragments the segments into IP *datagrams* of the necessary size for the local net‐ work and passes them to the host-to-network layer for transmission onto the wire. 
- Without the internet layer or something like it, each computer could only talk to other computers that shared its particular type of network. The internet layer is responsible for connecting heterogenous networks to each other using homogeneous protocols.
- Layer 2 => The host-to-network layer encodes the digital data as analog signals

## Types of Networks

- Client/Server
- Peer-to-Peer