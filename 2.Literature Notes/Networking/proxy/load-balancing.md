# Load Balancing

- We're concerned with the load of servers and Latency

## Round Robin 

- Each server has equal chance to be selected
- suitable for low-medium Latencies

## Weighted Round Robin

- Weights of servers are determined and assigned by their load
- Performs well in high percentiles

## Least Weight

- Server with least load is selected
- Least Requests Dropped at high Latency

## Peak Exponentially Weighted moving Averages

- Don't send requests to servers with high load
