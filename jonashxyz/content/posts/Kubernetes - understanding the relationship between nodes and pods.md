---
id: Kubernetes - understanding the relationship between nodes and pods
aliases: []
tags:
  - Article
  - Kubernetes
  - DevOps
date: "2024-05-14"
title: Kubernetes - understanding the relationship between nodes and pods
draft: false
---

# The relationship between nodes and pods
In Kubernetes, the relationship between nodes and pods is central to how applications are deployed and managed. Understanding what nodes and pods are, individually, helps clarify their interaction.

### What are Pods?
A **pod** is the smallest deployable unit in Kubernetes and serves as a wrapper for one or more containers. Each pod is designed to run a single instance of a given application or service. It can contain one or multiple containers (usually Docker containers), and these containers within a pod share resources like networking and storage. Containers in the same pod can communicate with each other using `localhost`, as they share the same network namespace.

Pods encapsulate:
- Application containers
- Storage resources
- A unique network IP
- Options that govern how the container(s) should run

A pod is designed to run a single instance of a given application. If your application requires scaling, you create multiple instances of the same pod, each of which might be identical but isolated from others.

### What are Nodes?
A **node** is a worker machine in a Kubernetes cluster. This machine can be either a physical computer or a virtual machine (VM) depending on the environment in which the Kubernetes cluster is deployed. Each node is managed by the master components (such as the scheduler, API server, and controller manager), which make decisions about where to place pods, monitor node and pod status, and respond to changes in the cluster. Nodes have the necessary services to run pods, including the Docker runtime and the Kubelet, which is responsible for maintaining a set of pods as specified by the Kubernetes API.

Each node in a Kubernetes cluster fulfills one or more of the following roles:
- **Master Node**: Runs cluster management tasks.
- **Worker Node**: Hosts the Pods that are the components of the application workload.

Nodes are responsible for providing the resources (CPU, memory, network, and storage) that pods need to run their applications.


### Relationship between Nodes and Pods
- Nodes provide the runtime environments for pods. Each node can host multiple pods.
- Pods are assigned to nodes by the Kubernetes scheduler based on resource availability, policy, and other constraints.
- Each pod is bound to a node and remains on that node until terminated or deleted. If a node fails, the pods scheduled on that node are scheduled for deletion, and they may be recreated by the control plane on other nodes.

This relationship enables Kubernetes to manage large-scale, distributed environments efficiently, ensuring that applications are reliably available and can be scaled as needed across the various nodes in the cluster.

## Links:

202405142258

Kubernetes documentation home: https://kubernetes.io/docs/home/
