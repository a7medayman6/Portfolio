---
title: "Symphony II -  K8s Architecture"
date: 2021-09-09T19:22:29+02:00
draft: false
# for projects
ShowReadingTime: true
hideSummary: false
showtoc: false
cover: 
    image: ''
weight: 2
---

# Containers Orchestration

Author : [Ahmed Ayman](https://a7medayman6.github.io/)

# The Desired State

What does that even mean ? well, let's think of k8s as a genie, we wish and desire things and he makes sure it happens.

So, the desired state is a manifest written by the administrator (or k8s user at this case) to tell k8s exactly the state that we want the application to be in at all times, for example .. we want 10 front-end containers, and 20 back-end containers, we want ports x and y to be exposed and mapped with ports i and j, we want to access the app from outside. 

Then the administrator sends the file to k8s API, Kubernetes stores the file (an application’s desired state) in a database called the Key-Value Store (etcd). 

And everything else then is up to k8s! he does all the magic .. which is create the containers on the worker nodes inside the cluster and load balances between the servers.

Then Kubernetes continuously monitors the elements of the cluster to make sure the current state of the application does not vary from the desired state.

# So, how do we really communicate with the k8s ?

![Untitled](/blog/devops/k8s/day2/Untitled.png)

We now know that there is at least one master node, and some worker nodes. 
So, where do we (administrator) come in ? well we contact with the master node through it's API. we send commands to k8s API using kubectl which is a command line interface that sends HTTP requests to the API (actually we can just send HTTP requests but kubectl does that in a more elegant way), or using k8s dashboard.

Then, the API sends commands for the scheduler, controllers, and stores key-store values in **etcd**.

We'll learn all about kubectl commands later, but let's focus on how that happens.

# Let's dig into the Master Node ..

Also called the control plane, because it controls the worker nodes got it? and does that by dividing the work on multiple components each does some specific tasks :  

### **API Server**

The **API Server** is **the front-end** of the control plane and the only component in the control plane that we interact with directly. **Internal system components, as well as external user components, all communicate via the same API.**

### **Key-Value Store (etcd)**

The Key-Value Store, also called **etcd**, is a database Kubernetes uses to back-up all cluster data. It stores the entire configuration and state of the cluster. The Master node queries **etcd** to retrieve parameters for the state of the nodes, pods, and containers.

### **Controller**

The role of the **Controller** is to **obtain the desired state** from the API Server. It **checks the current state of the nodes** it is tasked to control, and **determines if there are any differences**, and resolves them, if any.

### **Scheduler**

A **Scheduler** watches for new requests coming from the API Server and **assigns them to healthy nodes.** It **ranks the quality of the nodes and deploys pods** to the best-suited node. **If there are no suitable nodes, the pods are put in a pending state until such a node appears.**

# Worker Nodes Turn

- These nodes are the actual machines that does the work and serves the application components, so how does that happen ?

![Untitled](/blog/devops/k8s/day2/Untitled%201.png)

### **Kubelet**

The **kubelet** runs on every node in the cluster. It is the principal Kubernetes agent. By installing kubelet, the node’s CPU, RAM, and storage become part of the broader cluster. It **watches for tasks sent from the API Server**, **executes the task**, and **reports back to the Master**. It also **monitors pods and reports back to the control panel if a pod is not fully functional**. Based on that information, t**he Master can then decide how to allocate tasks and resources to reach the desired state.**

### **Container Runtime**

The **container runtime** pulls images from a **container image registry** and starts and stops containers. A 3rd party software or plugin, such as **Docker**, usually performs this function.

### **Kube-proxy**

The **kube-proxy** makes sure that **each node gets its IP address**, implements local *iptables* and rules to handle routing and traffic load-balancing.

### **Pod**

A **pod** is the smallest element of scheduling in Kubernetes. It's where the container actually lives. Without it, a container cannot be part of a cluster. If you need to scale your app, you can only do so by adding or removing pods.

The pod serves as a ‘wrapper’ for a single container with the application code. Based on the availability of resources, the Master schedules the pod on a specific node and coordinates with the container runtime to launch the container.

The pod can have multiple containers inside it, but it's better to create a pod for each container.

BUT, in some cases you might need to deploy multi containers to the same pod. These containers might be relatively tightly coupled. In a pre-container world, they would have executed on the same server.

For the sake of simplicity you can imagine that the pod = container.

![Untitled](/blog/devops/k8s/day2/Untitled%202.png)

So, to wrap this up .. 

- The administrator creates a yaml deployment manifest defining the desired state.
- The administrator sends (applies) the yaml file to the master node, through the API.
- The master node stores the manifest in the etcd.
- The API contacts with the scheduler to schedule the creation of the pods, on the worker nodes.
- The controller obtains the desired state, and makes sure the current and desired states are matching.
- The container and scheduler does that by contacting with each node through it's kubelet, to create the pods and monitor them.
- If at any time a pod in a node is not working correctly or goes down the kubelet reports to the master node, the master node sends a request to the scheduler to create a new pod, the scheduler looks for a suitable healthy worker node and assigns the pod to it. Then the selected node deploy the new pod using the run-time container inside it.
- ALL THE COMMUNICATION BETWEEN THE MASTER NODE AND THE WORKERS OR THE USER HAPPENS THROUGH REQUESTS FROM/TO THE API.

## The Chain of Command

How I see kubernetes work is by assigning a task for a component, then makes another component monitor it and report and/or take actions accordingly. Let's see some examples for that.

- The container run time (Docker) inside the worker nodes deploys the pods.
- The kubelet monitors the environment including Docker containers, and reports back to the master node if something happens.
- The scheduler monitors the  new requests and gives tasks to the worker nodes

### The sole goal of a k8s cluster is to try to obtain the desired state all the time using the available resources with the minimum down time, isn't that the dream of every OPs team ?

## Resources

- [https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams](https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams)
- [https://kubernetes.io/docs/concepts/overview/components/](https://kubernetes.io/docs/concepts/overview/components/)
