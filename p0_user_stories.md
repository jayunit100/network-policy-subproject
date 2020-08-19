Initial proposal or priorities, based on feasabiliy and overall user engagement... reprioritization welcome, please PR changes and in case of any major conflicts we can discuss in the broader group.

# Application scoped User stories

## tier-1

- I want 2 apps in different namespaces to connect, but can't read the labels for those namespaces from my Kubernetes client.

- I want 2 apps for different services to talk to each other, but don't know their labels.

- I don't want to directly update my CIDR rules for a policy every time I add a new node or other group of IPs, which need to have policy's associated with them.

- I dont want to look at 10 or 100 policies to figure out wether I have the right allow rules.

- I wrote a policy, but am not sure if my policy did the right thing, nor if it has taken effect on the pods that I'm concerned with, yet.

## tier-2

- Writing network policies is hard, I forget what the defaults for ports, ingress/egress, and nil/empty collections (for label selectors and policy structs) are.

- I want to be able to scrape from pod endpoints for every pod in my cluster, but can't afford to make new policies for each one given the large rate of pod churn.

# Cluster scoped user stories

## tier-1

- I only want pods on nodes that are labeled as “infrastructure” nodes to be able to access the Kubernetes apiserver; 
other pods should be blocked from accessing it via any IP.

- I want all namespaces matching X to be completely 100% locked-down by default; no pods can talk to any other pods until the developers specify policies allowing it - I may also want the converse situation for namespace Y.

- I want to target all apps with network policies, but most of my apps need apiserver access, and i dont know the k8s service IP because all my clusters have different Service CIDRs.

- I want to block all pods from being able to reach ports on nodes. And the rule should automatically cover all nodes, and should cover all IPs on those nodes, except for port 53.

## tier-2

- I want all namespaces to be “isolated” (don’t accept traffic from other Namespaces) by default; developers must specify if they want other namespaces to be able to access their services.

- I want to administratively put a choke point between  pods that arent in the same app so i can audit cross-app dependencies and implement ingress controls by default in my cluster.

- I want to block all pods from being able to reach the AWS metadata server (169.254.169.254)
except for pods in Namespace X, except I want to run kube2iam as a metadata proxy, so pods trying to access the metadata server should be redirected to that instead.

- I want all pods to be blocked from accessing the internet.

- I want all pods to be blocked from accessing the internet by default, but developers can add policies declaring what sites they need access to. Then those sites will be reachable, but if hackers break into the pod they can’t reach anywhere else besides those sites, except they can’t access 192.168.0.0/16 even if they declare it.

- I want pods in Namespace X to only have cluster egress via a proxy server provided by Service Y.

# Descoped from NetworkPolicy API

These still might be explored by this group but are descoped from the primary use cases reported to the SIG.

- Prioritize Network Policy - I want to create a rule that I’m sure will be executed before anything else.

- I want to log when a network policy rule is enforced administratively

- I want to enforce policies between nodes and proceses outside of nodes (which are not pods)

- Add a level of indirection between policies so that a request can be made for a security boundary that is fulfilled in a separate step (i.e OPA semantics)

- I want to have a named way to add a policy for containers that can or cannot access a MySQL instance in my data center, without knowing that services IP address.

- I want to restrict certain processes in a pod without restricting others, so that  some processes are not able to make certain network calls.

