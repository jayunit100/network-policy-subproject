Initial proposal or priorities, based on feasabiliy and overall user engagement... reprioritization welcome, please PR changes and in case of any major conflicts we can discuss in the broader group.  

Taken from 
- conversations and zoom meetings
- https://docs.google.com/document/d/10t4q5XO1ED2PnK3ishn4y3G4Tma7uMYgesG-itQHMiU/edit# 
- https://docs.google.com/document/d/1AtWQy2fNa4qXRag9cCp5_HsefD7bxKe3ea2RPn8jnSs/edit . 

# Terminology

- *app*: a program or collection of programs running in a namespace that comprise a end-user consumed service.  Common "guestbook", "blackduck", "backend API services", or the "ELK" stack, which usually is consumed through Kibana.

# Application scoped User stories

## tier-1

### non v1 modifying
- I want 2 apps in different namespaces to connect via namespace NAME, because I can't read (or write) the labels for those namespaces from my Kubernetes client.   I cannot select pods for this because I don't know all the labels and names of pod/services that I want to contact ahead of time. 

- I want different pods (with potentially different labels) that fulfill a service to be able talk to each other, without talking to other services but I don't know the labels on these services.

- I dont want to look at 10 or 100 policies to figure out whether I have the right allow rules.

- I wrote a policy, but am not sure if my policy did the right thing, nor if it has taken effect on the pods that I'm concerned with, yet.

### v1 modifying

- I don't want to directly update my CIDR rules for a policy every time I add a new node or other group of IPs, which need to have policies associated with them.
  - We can use a slice instead of a string for CIDR (KEP-able)

- Writing network policies is hard, I forget what the defaults for ports, ingress/egress, and nil/empty collections (for label selectors and policy structs) are (see https://github.com/kubernetes/kubernetes/issues/51726 for official issue pointing to this).  This might result in revising or removing policy types.

## tier-2

- I want to be able to scrape from pod endpoints for every pod in my cluster, but can't afford to make new policies for each one given the large rate of pod churn.

# Cluster scoped user stories

## tier-1

- I only want pods on nodes that are labeled as “infrastructure” nodes to be able to access the Kubernetes apiserver; 
other pods should be blocked from accessing it via any IP.

- I want all namespaces matching X to be completely 100% locked-down by default; no pods can talk to any other pods until the developers specify policies allowing it - I may also want the converse situation for namespace Y.

- I want to target all apps with network policies, but most of my apps need apiserver access, and i dont know the k8s service IP because all of my clusters have different Service CIDRs.

- I want to block all pods from being able to reach ports on nodes. The rule should automatically cover all nodes, and all IPs on those nodes, except for port 53.

## tier-2

- I want all namespaces to be “isolated” (don’t accept traffic from other Namespaces) by default; developers must specify if they want other namespaces to be able to access their services.

- I want to administratively put a choke point (gateway) between pods that arent in the same app so i can audit cross-app dependencies and implement ingress controls by default in my cluster.  (Workaround: Create a namespace selector around the targetted namespace, which only allows traffic from a predetermined ingress point.  See https://github.com/jayunit100/network-policy-subproject/issues/14) for further discussion. 

- I want to block all pods from being able to reach the AWS metadata server (169.254.169.254)
except for pods in Namespace X, except I want to run kube2iam as a metadata proxy, so pods trying to access the metadata server should be redirected to that instead.

- I want pods in Namespace X to only have cluster egress via a proxy server provided by Service Y.

- I want all pods to be blocked from accessing the internet, no matter what, without having to explicitly add my K8s CIDR ranges allow rules .  This would be a convenience story (otherwise, CIDR ranges are sufficient to satisfy this user stories). 

- I want all pods to be blocked from accessing the internet by default, with exception allowing case-by-case allow-listing of certain IP ranges.  Convenience/Sugar story.

# Descoped from NetworkPolicy API

These still might be explored by this group but are descoped from the primary use cases reported to the SIG.

## Tier 1

- Prioritize Network Policy - I want to create a rule that I’m sure will be executed before anything else.

- I want to log all the times that someone from the outside world was deined access to a pod in my cluster by a NetworkPolicy rule.

- I want a pool of DMZ nodes in my cluster to prevent all outgoing traffic to my cassandra cluter which has highly sensitive data on it which is known to be vulnerable due to a recently discovered CVE.

- I want a developer in Namespace X to build an app that automatically requests access to a database in Namespace Y, but I don't want to *grant* that access until an admin approves it.

- I want visualization of my network policies, as a tool to help me create accurate network policies as well as to help me verify existing network policies for correctness

## Tier 2

- I want to restrict certain processes in a pod without restricting others, so that  some processes are not able to make certain network calls in a cluster where certain set pods running an old version of Nginx are at risk of being comprimised.

- I want to have a named way to add a policy for containers that can or cannot access a MySQL instance in my data center, without knowing that services IP address.


# CHANGELOG

As we move things via PRs, lets note the context so that we can detect cycles and or changes that are reversing previous user requests.  If we notice any obvious disagreements, we can resolve it as a group.  This is an alterantive to voting which might collect 'passive' opinions which havent been deeply thought out.

CHANGELOG
- *Jay* addressed clarity issues in the 'cant connect to the internet' and 'namespace by NAME' user stories.  
- *Abhishek, Chris, Jay* linking to tim hockins issue around defining `empty from` as `none`.
- *Matt Fenwick* requested adding a visualization story to tier-1.
- *Jay vyas* Moved the abov request for tier-1 to "Descoped" since its not an API thing, but it is a valid user story. 
