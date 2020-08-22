# A Cluster Scoped extension to the NetworkPolicy API

Also refer the fourth section of https://docs.google.com/document/d/10t4q5XO1ED2PnK3ishn4y3G4Tma7uMYgesG-itQHMiU/edit# 

## Summary

This proposal outlines a plan for implementing *cluster level* NetworkPolicies
in the Kubernetes API.

## Motivation

Current NetworkPolicy API is tailored towards application developers to protect
their workloads from unintended usage. Thus, the NetworkPolicy API is unable to
satisfy some of the use cases which are relevant to cluster administrators.

### Goals

The goal of this initiative is to develop a new security API with the
following in mind:

- Administrator focused APIs at a cluster scope
- Ability to set default security policy for the cluster
- Ability to secure traffic between Pod and Nodes in addition to regular
  Pod-Pod traffic

### Non-Goals

- Enable traffic policies that affect things outside the cluster
- Secure traffic between multiple clusters
- Cluster level monitoring or threat detection
- CLI/devOps tool to gain more visibility in the cluster

## Proposal

<abhishek, ...> 

### User Stories (Optional)

<abhishek, ...> 

### Notes/Constraints/Caveats (Optional)

<abhishek, ...>

### Risks and Mitigations

<abhishek, ...>

## Design Details

<abhishek, ...>

## Alternatives

<abhishek, ...>
