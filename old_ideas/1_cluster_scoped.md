# A Cluster Scoped extension to the NetworkPolicy API

Taken from the fourth section of https://docs.google.com/document/d/10t4q5XO1ED2PnK3ishn4y3G4Tma7uMYgesG-itQHMiU/edit# 

## Summary

This proposal outlines a plan for implementing *cluster level* network policies in the Kubernetes API.

## Motivation

Administrators are not capable of easily administering clusters at large scales using policys as a Network security implementation.

### Goals

The goal's of this initiative are to make the following improvements to the existing NetworkPolicy API.

- Allow users to implement default cluster network policies
- Allow users to implemement common DNS rules for network policies across a cluster
- Allow users to implemement common APIServer access (internal service) rules for network policies across a cluster
- Allow users to select pod to node network allow policies

### Non-Goals

- Enable traffic policies that effect things outside the cluster
- Cluster level monitoring or threat detection

## Proposal

<abishek> 

### User Stories (Optional)

<abishek> 

### Notes/Constraints/Caveats (Optional)

<abishek>

### Risks and Mitigations

<abishek>

## Design Details

<abishek>

## Alternatives

<abishek>
