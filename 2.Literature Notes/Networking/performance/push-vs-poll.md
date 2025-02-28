# Pushing vs Polling

## Pushing

- Once Server gets Data, Pushed to Client
- Client doesn't request anything from the Server
- Needs a Bi-Directional Connection
- Used by RabbitMQ
- Client must be Online and able to handle sent Data

## Polling

- Client Sends Requests & Server responds with Handles (Are we there yet ?)
- Multiple Short Request-Response 

## Long Polling

- Client Sends a Request & Server will only Respond when Data is ready
- Not Real-time 
- Used by Kafka
