# Pod Reachability Query

## User Story

As a policy creator or developer, I want to query the network policy enforcement
engine to ask if a specific type of network traffic (IP protocall and port) is
permissible between two pods in a specific direction. If this is not
permissible, I would like the query results to explain what policies (either
egress and/or ingress) prevented the network connection.

