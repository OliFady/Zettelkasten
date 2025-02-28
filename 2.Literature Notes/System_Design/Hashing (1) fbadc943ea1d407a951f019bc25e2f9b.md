# Hashing (1)

## Simple Hashing

![Untitled](2.Literature%20Notes/System_Design/Hashing%20(1)%20fbadc943ea1d407a951f019bc25e2f9b/Untitled.png)

based on the number of servers (client hash % no of Servers)

## Consistent Hashing

Clients go to their nearest Servers in Clockwise Direction

on adding Servers ⇒ only a few Servers are affected (re-routed) in this example ⇒ Server A

![Untitled](2.Literature%20Notes/System_Design/Hashing%20(1)%20fbadc943ea1d407a951f019bc25e2f9b/Untitled%201.png)

## Rendezvous Hashing

Ranking Servers based on Scores and assigning Clients to their top ranked Servers