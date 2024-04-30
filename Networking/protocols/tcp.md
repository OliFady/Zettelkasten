# TCP

## 3-way Handshake

- The Client sends the SYN packet and waits for the server's SYN-ACK packet
- The Server sends the SYN-ACK packet and waits for the client's ACK packet
- SYN-ACK are sent in 1 response to save resources
- The Client sends the ACK packet

## Every-Request

- The Server sends an ACK packet in every request
- The Client sends a FIN packet to close the Connection
- We want to send as much as possible withouth waiting for an ACK

## Flow Control

- Sliding Window Algorithm is used and exchanged at the Handshake
- RWND (Receiver Window) tells the sender how much to send before receiving an ACK
- RWND is updated with every ACK based on Available Memory 

## Congestion Control

- CWND starts with 1 MSS or more, sends 1 Segment and waits for ACK
- Slow Start increments CWND by 1 With each ACK
- Congestion Avoidance increments CWND by 1 Every Roundtrip
- CWND += MSS * MSS /CWND
