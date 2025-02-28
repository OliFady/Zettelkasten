# IP Tables

- 80 is the default port on linux
- It consists of several tables (filter, nat, mangle, raw, and security) 
- Each table contains chains (INPUT, OUTPUT, FORWARD, PREROUTING, POSTROUTING)

## Port Redirection

- Rules can be applied when pre-routing
- Rules are matched in the order they are added

```
iptables --table nat --append PREROUTING --protocol tcp --dport 80 --jump\
REDIRECT --to-port 8080
```
