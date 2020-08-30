This is a conceptual CRD, psuedo code to be iterated on in Markdown.
```
NetpolExtended {
    Spec:
        Scope:
            AllNamespaces: true/false
            AllNamespacesRegex: true/false
            IncludedNamespaces: (labels)
            // ^ Pick one
        PortSpec:
            Range: min,max
            []Ports:
            Port
            // ^ Pick one, either a 
        NodeSelectorSpec:
             matchLabels
            // will allow traffic to all nodes in this sector
        ServiceSelectorSpec:
            // will allow traffic to pods in services of this selector
            matchLabels
        NamespacesSelectorSpec:
            // will allow all traffic to all namespaces in this selector
            matchLabels
        K8sDefaultService: true
            // helps to stop you from shooting yourself in the foot by blocking egress to dns
        KubeDNSService: true
            // core dns?
   Status:
       // current 'status' to show you what your policy is *currently* doing -- think truthtables: something easy to visually grok
        List[Pod,Pod] ConnectedViaNetworkPolicy
        List[Pod,Pod] ConnectedViaClusterPolicy
}
```
