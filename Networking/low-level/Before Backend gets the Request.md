- This whole process is reversed when sending back the Response
## Accept

- opens a Connection, listens on a Port & receives bytes
- Syn Queue inside the Kernel and does lookup for the specified Address
- Accept Queue receives the Connection after Syn has found the Address 
- accept is a Sys Call that creates a File Descriptor and gives the Backend a Pointer.
## Read

- recv Sys Call is initiated for the Backend to read the Connection
- Receive Queue is created
- Send Queue is created
## Decrypt

- Use the Symmetric Key to Decrypt 
## Parse

- Checks if Request is Complete to be fulfilled
## Decode

- What am i reading ?
- Deserialize
## Process

- Do whatever you want with it
