# TCP Handshake

## Why

- The Client and Server need to communicate with Sequence Numbering (SN) or
    Acknowledgement Numbering (AN) protocol
- This happens by sending the SYN packet and waiting for the SYN-ACK packet
- The Server sends the SYN-ACK packet and waits for the client's ACK packet
- The Sequence is a 32-bit Number that is refreshed when limit is hit

## 3-way Handshake

- The Client sends the SYN packet and waits for the server's SYN-ACK packet
- The Server sends the SYN-ACK packet and waits for the client's ACK packet
- SYN-ACK are sent in 1 response to save resources
- The Client sends the ACK packet

## Every-Request

- The Server sends an ACK packet in every request
- The Client sends a FIN packet to close the Connection
