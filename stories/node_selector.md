# Node Selector

## Owners

- @jayunit100 (Jay Vyas)

## User Story

As a policy creator, 

- I need to limit ingress from and egress to nodes (and specifically, their Kubernetes recognized network interfaces), so that 'special' nodes which may scale up and down dynamically over time, can be protected from sending or recieveing traffic.
- Since these nodes can increase/decrease, targetting them via metadata rather then IP addresses is required, and the obvious metadata to use would be `labels`.

## Notes

- This may involve changing the semantics around health checks, which are always ALLOW policies (nodes sending traffic to pods is always allowed).
- This may be considerd a Cluster scoped policy, since it can effect many different target namespaces, and since it is administrative in nature (as opposed to application centered).


