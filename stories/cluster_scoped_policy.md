# Cluster Scoped Policy

## User Story

A a platform operator or cluster administrator, I need to create policies that
impact all pods across multiple (or all) namespaces. As an example, these
"cluster scoped" policies could allow access to and from platform shared
services. I would like to specify the binding of policy to pods by composing both
pod and namespace selectors.