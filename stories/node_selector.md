# Node Selector

## Owners

- @jayunit100 (Jay Vyas)

## User Story

As a policy creator, I need to limit ingress from and egress to
nodes (and specifically, their Kubernetes recognized network interfaces) that
belong to a Kubernetes cluster. Additionally, I would like to select a set of
node IP addresses based upon the node's labels. With this capability, network
policies could target specific nodes and selectors would automatically update
the set of IP addresses as nodes join and leave a cluster.
