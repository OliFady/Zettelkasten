# Web Sockets

- ws and wss are websockets protocols
- Websockets prevents polling

## WebSockets Handshake

- The first GET req contains a Connection: UPGRADE Header.
- The Server responds with a 101 Switching Protocols Header.
- RFC 8441 uses CONNECT Method, which dedicates Sreams for each Front-end Client 
