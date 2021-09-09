---
title: "Sympohny I - Intro"
date: 2021-09-09T19:22:26+02:00
draft: false
# for projects
ShowReadingTime: true
hideSummary: false
showtoc: false
cover: 
    image: ''
weight: 1
---

# Containers Orchestration

Author : [Ahmed Ayman](https://a7medayman6.github.io/) 

# What is container orchestration ?

![Untitled](/blog/devops/k8s/day1/Untitled.png)

Well, imagine you have an app that works with 3 containers for example back-end, front-end, database, when you deploy this application you can't just work with one instance of each container on 1 server. Because if there's a lot of traffic coming one server won't be enough to process them at the same time, and you'll end up with a dead server. so how we deploy an application that gets a lot of traffic?

easy, use multiple servers with multiple instances of your containers and use a load balancer in front of them .. easy right ? 

Now imagine you're deploying a service like amazon e-commerce website with millions of users each second and financial transactions all the time. YES you're right you'd probably need thousands of servers running your containers !

Great, now all we have to do is ssh into each server from those 231321 servers, run your containers, crazy right? no one can/should do that !  and even if we managed to do that, what if some containers got errors, or needs updates, or, or, .. there's tons of disasters that could happen.

Only if we have a tool that can run the containers on all the servers, load-balances them, and restart them if any container failed with dealing with master servers only !

Oh actually we do! that's what container orchestration is, it's art! it's the automatic process of managing/scheduling containers across multiple servers through master servers only.

Example of such tools is Kubernetes, Docker Swarm .

# What is container orchestration used for?

Use container orchestration to automate and manage tasks such as:

- Provisioning and deployment
- Configuration and scheduling
- Resource allocation
- Container availability
- Scaling or removing containers based on balancing workloads across your infrastructure
- Load balancing and traffic routing
- Monitoring container health
- Configuring applications based on the container in which they will run
- Keeping interactions between containers secure

# Kubernetes

**Also known as K8s, is a Container Orchestration tool.** 

Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. kubernetes services, support, and tools are widely available.

# Kubernetes Architecture

![Symphony%20I%20-%20Intro%2048dbedc26875401180fcb417bf6d058a/Untitled%201.png](/blog/devops/k8s/day1/Untitled%201.png)

## Terminologies

- **Cluster:** A control plane(master node) and one or more computer machines (worker nodes).
- **Control plane (Master Node):** The collection of processes that control Kubernetes nodes. This is where all task assignments originate, also called the master node.
- **Kubelet:** This service runs on nodes and reads the container manifests and ensures the defined containers are started and running.
- **Pod:** A group of one or more containers deployed to a single node. All containers in a pod share an IP address, IPC, host-name, and other resources.
- **Node (Worker node):** A machine with a container run time installed and runs the actual containers of the application (they are the machine that actually do the work).

# Control Plane Components

![Symphony%20I%20-%20Intro%2048dbedc26875401180fcb417bf6d058a/Untitled%202.png](/blog/k8s/day1/Untitled%202.png)

**The control plane's components make global decisions about the cluster (for example, scheduling), as well as detecting and responding to cluster events (for example, starting up a new pod when a deployment's replicas field is unsatisfied).**

Control plane components can be run on any machine in the cluster. However, for simplicity, set up scripts typically start all control plane components on the same machine, and do not run user containers on this machine.

### Kube-API Server

**The API server is the front end for the Kubernetes control plane.**

Kube-api server is the interface that the other components communicate with the control plane from.

kube-api server is designed to scale horizontally—that is, it scales by deploying more instances. You can run several instances of kube-api server and balance traffic between those instances.

### etcd

**Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data.**

### kube-scheduler

**Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.**

there are many factors the scheduler considers to choose which node the pod should get assigned to.

### kube-controller-manager

Control Plane component that runs controller processes.

Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.

Some types of these controllers are:

- Node controller: Responsible for noticing and responding when nodes go down.
- Job controller: Watches for Job objects that represent one-off tasks, then creates Pods to run those tasks to completion.
- Endpoints controller: Populates the Endpoints object (that is, joins Services & Pods).
- Service Account & Token controllers: Create default accounts and API access tokens for new namespaces.

# Node Components

**Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.**

### kubelet

**An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.**

The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy. The kubelet doesn't manage containers which were not created by Kubernetes.

### kube-proxy

**kube-proxy is a network proxy that runs on each node in your cluster.**

kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.

### **Container runtime[](https://kubernetes.io/docs/concepts/overview/components/#container-runtime)**

**The container runtime is the software that is responsible for running containers.**

Kubernetes supports several container run-times: [Docker](https://docs.docker.com/engine/), [containerd](https://containerd.io/docs/), [CRI-O](https://cri-o.io/#what-is-cri-o).

## So, to wrap all this up here is Kubernetes Architecture

![Symphony%20I%20-%20Intro%2048dbedc26875401180fcb417bf6d058a/Untitled%203.png](/blog/devops/k8s/day1//Untitled%203.png)

# Who Does What ?

looks like k8s does a lot of stuff, let's figure out what k8s does on it's own, and what we do!

[Roles](Symphony%20I%20-%20Intro%2048dbedc26875401180fcb417bf6d058a/Roles%2076a5d120ffb64b138c99998f5835273d.csv)

looks like k8s does the heavy work for us! 

# K8s Installation

to practice k8s you need servers to act as nodes, but that will cost us a lot for a practice right ? so to practice k8s we need two components 

## Kubectl

[**How to install Kubectl**](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

The kubectl (kube control) command line tool lets you control Kubernetes clusters.

## Minikube

**[How to install minikube](https://kubernetes.io/docs/tasks/tools/)**

Minikube sets up a k8s cluster using virtual machines or (wait for it) DOCKER CONTAINERS!! so when you use docker for minikube, then use kubectl to run a container, you're actually running a container inside a container! how cool is that?!

by default minikube starts 3 worker nodes, in addition to your master node that you use kubectl from.

## Resources

- [https://kubernetes.io/docs/concepts/overview/components/](https://kubernetes.io/docs/concepts/overview/components/)