---
title: "Symphony III - Services"
date: 2021-09-09T19:22:32+02:00
draft: false
# for projects
ShowReadingTime: false
hideSummary: false
showtoc: false
cover: 
    image: ''
weight: 3
---

# Containers Orchestration

Author : [Ahmed Ayman](https://a7medayman6.github.io/)

# Can you spot the problem ?

**PODS GETS CREATED AND DESTROYED ALL THE TIME!** 

How can we we count on there IP addresses, also how can we communicate with all the the pods of the same kind at once ?

# The Solution : K8s Services

One of the best features Kubernetes offers is that non-functioning pods get replaced by new ones automatically. however these new pods have a different set of IPs. It can lead to processing issues, and IP churn as the IPs no longer match. If left unattended, this property would make pods highly unreliable.

Services are introduced to provide reliable networking by bringing stable IP addresses and DNS names to the unstable world of pods.

By controlling traffic coming and going to the pod, a Kubernetes service provides a stable networking endpoint – a fixed IP, DNS, and port. Through a service, any pod can be added or removed without the fear that basic network information would change in any way.

For example, consider a stateless image-processing back-end which is running with 3 replicas. Those replicas are fungible—front-ends do not care which back-end they use. While the actual Pods that compose the back-end set may change, the front-end clients should not need to be aware of that, nor should they need to keep track of the set of back-ends themselves.

Don't panic, K8s does all that on it's own you just need to ask for a server and the genie will provide!  

# How Services Works ?

Pods are associated with services through key-value pairs called **labels** and **selectors**. A service automatically discovers a new pod with labels that match the selector.

This process seamlessly adds new pods to the service, and at the same time, removes terminated pods from the cluster.

For example, if the desired state includes **three replicas of a pod** and a node running **one replica fails**, the current state is reduced to two pods. Kubernetes observers that the desired state is three pods. It then **schedules one new replica** to take the place of the failed pod and assigns it to another node in the cluster.

The same would apply when updating or scaling the application by adding or removing pods. Once we update the desired state, Kubernetes notices the discrepancy and adds or removes pods to match the manifest file. The Kubernetes control panel records, implements, and runs background reconciliation loops that continuously check to see if the environment matches user-defined requirements.

With services you can hit one endpoint and that service load-balances between the nodes. 

## Resources

- [https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams](https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams)
