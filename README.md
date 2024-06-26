# Kubernetes Documentation

This repository contains some required details about kubernetes. It will help you to know about kubernetes i.e what is kubernetes, why we use kubernetes, Architecture of kubernetes, Objects of kubernetes. 

## 1] WHAT IS KUBERNETES?

 - Kubernetes is also know as k8s.
 - K8s is a Open-source orchestration tool developed by google. 
 - In terms of k8s orchestration refers to the automated management, co-ordination, and deployment of containerized applications across a cluster of nodes. Kubernetes is an open-source platform designed to automate the deployment, scaling, and management of containerized applications.
 - It schedules, runs, and manages isolated containers that are running on virtual/physical/cloud machines.
## 2] WHY KUBERNETES (K8s)?
 
 - All top cloud providers supports K8s. 
 - K8s offers a variety of features that help manage applications efficiently using just one tool. This means you don't need to juggle multiple tools or systems to handle different aspects of your applications. Instead, Kubernetes provides everything you need in a single platform, making it easier to deploy, scale, and maintain your applications without the hassle of dealing with various separate tools.
 - Kubernetes offers a bunch of useful features that Docker doesn't provide on its own. These include:

    - Autoscaling: Kubernetes can automatically adjust the number of containers running your application based on how much traffic it's getting. So, if there's a sudden spike in users, Kubernetes can quickly add more containers to handle the load, and scale them back down when the demand decreases.

    - Load Balancer: It helps distribute incoming traffic across multiple containers running the same application, ensuring that no single container gets overwhelmed. This keeps your application running smoothly even during high traffic times.

    - Authentication: Kubernetes provides mechanisms for controlling access to your applications and resources, ensuring that only authorized users and services can interact with them.

    - Security Mechanisms: It includes various security features to protect your applications and data from unauthorized access or attacks.

    - Automatic Container Restart: If a container crashes or becomes unresponsive, Kubernetes can automatically restart it, ensuring that your application stays up and running.

    - Basic Routing and DNS: Kubernetes includes built-in mechanisms for routing network traffic to the appropriate containers and resolving domain names to their corresponding IP addresses, making it easier to access and communicate with your applications.

   These features make Kubernetes a powerful platform for deploying and managing containerized applications, providing capabilities beyond what Docker offers alone.

## 3] UNDERSTANDING THE ARCHITECTURE OF K8S CLUSTER ?

Group of nodes is known as cluster. At the hardware level, a Kubernetes cluster is composed of many nodes, which can be split into two types:

 - The master node, which hosts the Kubernetes Control Plane that controls and manages the whole Kubernetes system. The Control Plane is what controls the cluster and makes it function. It consists of multiple components that can run on a single master node or be split across multiple nodes and replicated to ensure high availability. These components are
    - API Server
    - ETCD
    - Schedular
    - Controller Manager
   And many more componants are there but this four are the default componants of control plane.

 - Worker nodes that run the actual applications you deploy. The worker nodes are the machines that run your containerized applications. The task of running, monitoring, and providing services to your applications is done by the following components:
   - Kubelet
   - Kube-proxy
   - Container Engine
   - Pods

 ![alt text](<Arc k8s.png>)

  - API Server :-
      - API Server acts as a middle-ware. The Kubernetes API Server, which you and the other Control Plane components communicate.
      - This api-server interacts directly with the user (i.e we apply .yml or .json manifest to kube-api-server).
      - This kube-api-server is meant to scale automatically as per load.
      - Kube-api-server is the front end of the control plane.

  - ETCD :-
     - ETCD is a reliable distributed data store that persistently stores the cluster configuration.
     - Stores metadata and status of the cluster.
     - etcd is a consistent and high-available store (key-value-store).
     - Source of touch for cluster state (info about the state of the cluster).

  - Schedular :-
     - The Scheduler, which schedules your apps (assigns a worker node to each deployable component of your application).
     - When users request the creation & management of Pods, Kube scheduler is going to take action on these requests.Handles POD creation and Management.
     - Kube-scheduler match/assigns any node to create and run pods.
     - A scheduler watches for newly created pods that have no node assigned. For every pod that the scheduler discovers, the scheduler becomes responsible for finding the best node for that pod to run.
     - The scheduler gets the information for hardware configuration from configuration files and schedules the Pods on nodes accordingly.

  - Controller Manager :-
      - The Controller Manager, which performs cluster-level functions, such as replicating components, keeping track of worker nodes, handling node failures, and it matches the actual state and desired state.
      -  Make sure the actual state of the cluster matches the desired state. Two possible choices for controller manager 
        1. If K8s is on the cloud, then it will be a cloud controller manager.
        2. If K8s is on non-cloud, then it will be kube-controller-manager.

  - Kubelet :- 
      - Kubelet is an agent that runs on each node in the cluster. It is responsible for managing the node and its containers.
      - Kubelet receives pod specifications from the API server and ensures that the pods are running and healthy.
      - It interacts with the container runtime (e.g., Docker, containerd) to create, start, stop, and delete containers.

  - Kube-proxy :- 
      - Kube-Proxy is a network proxy that runs on each node and implements Kubernetes service abstraction.
      - It maintains network rules on the host and performs packet forwarding, enabling communication between pods and services within the cluster.
      - Kube-Proxy is responsible for load balancing and routing traffic to the appropriate pods.

  - Container Engine :-
      - The container engine is responsible for running the containers within pods. It provides the necessary infrastructure to create, manage, and execute containerized applications.
      - Kubernetes supports various container runtimes as container engines, including Docker, containerd.
      - The container engine interacts directly with the underlying operating system's kernel to create isolated environments for running containers.

  - Pods :-
      - Pods are the smallest deployable units in Kubernetes. They represent a group of one or more containers that share networking, storage, and other resources.
      - Pods encapsulate one or more containers that are tightly coupled and need to run together on the same node.
      - Each pod gets its own unique IP address and can communicate with other pods in the cluster.
      - Pods are scheduled onto nodes in the cluster by the Kubernetes scheduler.
      - Pods provide a higher level of abstraction than individual containers, allowing for easier management of multi-container applications.

## 4] UNDERSTANDING THE LIFECYCLE OF PODS ?
 
![alt text](<K8S lifecycle policy.png>)

 - As we know it acts as a middle-ware or we can say frontend for kubernetes and also it is a primary management point for the cluster.
 - Its work is to communicate with users as well as other components.
 - API Server gives signals to ETCD as the project arrived. Ather which ETCD will stores the data and send signals to schedular through API Server to  schedule a task.
- Then after scheduling a task, the data has to be stored in ETCD so the signals will go throght API Server to ETCD, so as to store data.
- Now, moving towards the componants of worker nodes kubelate and kubeproxy. Kubelete will recive a task from schedular through API Server to create a pod.
- Kubepoxy is a network proxy that runs on each node and maintains network rules to enable communication between pods across the cluster. It manages network connectivity for services, load balancing, and routing traffic to the appropriate pods.

During the pod lifecycle, these components collaborate to ensure pods are created, scheduled onto nodes, monitored, and managed according to the desired state specified by users or administrators. The orchestration allows kubernetes to maintain the availabilty, and scalabilty and reliability of applications running in the cluster.

## 5] TYPES OF OBJECTS IN K8S

In Kubernetes, objects are entities used to represent the desired state of the cluster. They define what applications, services, and other resources should exist, how they should behave, and what their characteristics are. Kubernetes uses these objects to manage and orchestrate the various components within a cluster. Whatever we create on cluster will be known as object. Here are some commonly used Kubernetes objects:

- Nodes
- Pods
- Service
- Namespace
- Replication controller
- Replicaset
- Deployment
- Statefulset
- Daemonset
- Config Map
- Secrets
- hpa [Horizontal Pod Autoscaler]
- Ingress
- PV and PVC

# - Nodes :-

A node is a worker machine in Kubernetes. It may be a VM or physical machine, depending on the cluster configuration. Each node has the necessary services to run pods and is managed by the master components of Kubernetes. Nodes in a Kubernetes cluster are managed automatically, and their details are typically viewed through commands like 'kubectl' get nodes rather than through manifest files. However, you can use manifest files to apply labels and annotations to nodes if needed.

# - Pods :- 

Pods are the wrapper around the containers and also the smallest deployable units in Kubernetes. A Pod is the basic building block of Kubernetes, representing a single instance of a running process in your cluster. Pods can consist of one or more containers that are tightly coupled and share resources, such as networking and storage. Pods are ephemeral by nature, meaning they can be created, destroyed, and rescheduled dynamically by Kubernetes. They are designed to be disposable and replaceable, allowing for easy scaling, updating, and maintenance of containerized applications within the cluster.

# - Service :- 

The Service object in Kubernetes is a crucial component for enabling networking and service discovery within the cluster. It abstracts away the underlying network details and provides a consistent way to access a set of Pods. Services play a critical role in Kubernetes networking, allowing Pods to communicate with each other and enabling external access to applications running within the cluster. They abstract away the complexities of network routing and provide a stable interface for accessing distributed applications.
As we know containers does not have ip, it contains ports. In one pod the port of the containers should be different because it can't expose on same port. 

   - When to communicate with the container present in the same pod, at that time we use LOCALHOST:8080
   - When to communicate with the container present in the same nodes but in different pods, at that time use Pod ip:port
   - When to communicate with the different containers present in the different nodes of pods, at that time use Pod ip:port.

# - Namespace :- 

A namespace is a virtual cluster inside a Kubernetes cluster. It is used to group resources together and provide a scope for their names. By default, kubernetes starts with a single namespace called 'default', but you can create additional namespaces to organize and isolate resource. Namespaces allow you to logically partition your kubernetes cluster, providing a way to organize and isolate resources for different teams, projects, or environments.

# - Replication Controller :-

The Replication Controller is one of the fundamental Kubernetes objects used for managing pod replication and ensuring that a specified number of pod replicas are running at any given time. It belongs to the core kubernetes API group and is widely used for basic pod lifecycle management.

# - Replicaset :-

A replicaset is a kubernetes object used to ensure that a specified number of pod replicas are running at any given time. It is a higher-level abstraction build on top of pods, designed to manage the lifecycle of multiple pod replicas. Replicasets are typically used for stateless application where individual pods can be replaced or scaled up or down without impacting the overall application.

# - Deployment :-

A Deployment in Kubernetes is a resource object used to manage the deployment of replica sets and the lifecycle of pods in a declarative manner. Deployments allow you to define the desired state for your application, such as the number of replicas, pod template, and update strategy. They ensure that the specified number of pods are running and handle updates and rollbacks seamlessly.

# - Statefulset :-

A StatefulSet is a Kubernetes object used to manage stateful applications. In statefulset pods created in a sequential order also pods deleted in a sequential order. Here the process of creation of pods is, one pod is created by template and the other one will create through the first one as the pods are sync to each other and like vice pods can be created.

# - Daemonset :-

A DaemonSet is a Kubernetes object used to ensure that a copy of a specific pod runs on all (or a subset of) nodes in a cluster. DaemonSets are commonly used for system-level or infrastructure-related tasks that need to run on every node, such as logging, monitoring, or networking agents.

# - ConfigMap :-

A ConfigMap in Kubernetes is an API object used to store configuration data in key-value pairs that can be consumed by containerized applications running in the cluster. ConfigMaps decouple configuration from application code, allowing for more flexible and portable deployments.

# - secrets :-

A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key. Secrets are stored within the cluster and can be mounted into containers as data volumes or exposed as environment variables.They provide a way to store and manage confidential data securely within a cluster. Secrets are typically used to pass sensitive information to pods without exposing it in plaintext within the pod definition or container image.

# - hpa [Horizontal Pod Autoscaler] :-

Horizontal Pod Autoscaler (HPA) is a Kubernetes resource that automatically adjusts the number of replica pods in a deployment, replication controller, or replica set based on observed CPU utilization or custom metrics. It helps in scaling applications in or out to meet varying demand.

# - Ingress :-

In Kubernetes, an Ingress is an API object that manages external access to services within a cluster, typically HTTP. It provides HTTP and HTTPS routing to services based on the requested host and path. Ingress is often used to expose HTTP and HTTPS routes from outside the cluster to services within the cluster without exposing them directly to the internet.

# - PV & PVC :-

It is a kubernetes object which is used to store data.Persistent Volumes (PV) and Persistent Volume Claims (PVC) are used to manage storage in a cluster. They allow pods to request and use storage resources independently of the specifics of the underlying storage infrastructure.A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator. It is a resource in the cluster, just like a node, that can be requested by users (via PersistentVolumeClaims) and consumed by pods. PVs are cluster-wide resources and can be dynamically provisioned or statically defined.

A PersistentVolumeClaim (PVC) is a request for storage by a user or a pod. It allows users to request storage resources without needing to know the details of the underlying storage infrastructure. PVCs are bound to PVs, and the system automatically provisions a suitable PV when a claim is created (if dynamic provisioning is enabled).



                                                   THANK YOU           