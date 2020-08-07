# policy ++ wg artifacts

A starter repo to donate to Kubernetes-sigs so the community can own and iterate on stories over time, with issue tracking, as we close out the policy++ wg.  The ultimate goal of this repo is to make concrete, demonstrable examples of how network policies in Kubernetes could be updated, at some point in the future, to accomodate common use cases currently not covered.

# Background

Between April 28 - > August 13th of 2020, folks from 10 companies or so met once a week to discuss policies that they had wanted, heard about, or envisoned.  These included things like:

- node aware policies for controlling access to node-host services
- better metadata for targetting policies against services
- explicit deny, allow, logging policies for better administrative management
- being able to define policies as service level constructs, rather then pod constructs

The purpose of this repo is to codify each of these stories as

- a shell script / prototype which reproduces a k8s scenario which demonstrates the need for this policy
- a proposed solution to this need which might include
- current workarounds for this need

# Example

To get started, look at the 'apiserver example.  This example
- spins up a kind cluster.
- targets a pod with a specific policy, which disallows egress to the apiserver.
- demonstrates the problem - by running a kubectl container in this pod, we see it fails to do queries against the apiserver.

