# Improvements to the V1 API

Taken from the first section of https://docs.google.com/document/d/10t4q5XO1ED2PnK3ishn4y3G4Tma7uMYgesG-itQHMiU/edit# 

## Summary

NetworkPolicies are currently difficult to use, and lack certain features which might be added in order to make them a more universal API.
This doucment serves as a parent integrating these policies into a single conceptual framework for a next iteration of the network policiy API.

## Motivation

NetworkPolicies should be easier to write in order to support real-world use cases with 100s of namespaces, and they should also be void of hidden defaults which are hard to reason about.

### Goals

The goal's of this initiative are to make the following improvements to the existing NetworkPolicy API.

- Add the ability to easily specifcy network policies port ranges with Exception.
- Add the ability to create cluster scoped policys and rules.
- Implement a level of indirection where in a policy can be requested, and fulfilled, asynchronously.
- Add the ability to target a network policy namespace, by its name.
- Add the ability to target a network policy service, by its name.

### Non-Goals

- Modify the NetworkPolicy API in a way that is incompatible with the current stable version
- Add Cluster level network policies.

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