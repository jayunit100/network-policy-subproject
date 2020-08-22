# Create/Update developer focused NetworkPolicy API

Also refer the first and second section of https://docs.google.com/document/d/10t4q5XO1ED2PnK3ishn4y3G4Tma7uMYgesG-itQHMiU/edit# 

## Summary

Simplify application developer focused NetworkPolicy APIs.

## Motivation

The current NetworkPolicy API is confusing to users in the following ways:
- Misunderstanding of the default behavior (the difference in the semantics of
  the default ingress and egress policies dont help)
- Unable to understand the impact of the NetworkPolicy

In addition to the lack of clarity, some use cases documented hint at adding
more features to the NetworkPolicy API to assist developers in protecting their
workloads.

### Goals

The goals of this initiative are to enhance the developer focused NetworkPolicy
APIs. This could be achieved in the following two ways:
- Add new features to the existing NetworkPolicy API which are additive and
  can be added without backwards incompatibility
- Alternatively, create a new Application NetworkPolicy resource which gets rid
  of all the defaults of the prior definition and adds new features according
  to the user stories collected

### Non-Goals

- Add features that may be required by a cluster administrator
- Add a CLI/devOps tool to gain more visibility in traffic pattern

## Proposal

<abhishek...> 

### User Stories (Optional)

<abhishek...> 

### Notes/Constraints/Caveats (Optional)

<abhishek...>

### Risks and Mitigations

<abhishek...>

## Design Details

<abhishek...>

## Alternatives

<abhishek...>
