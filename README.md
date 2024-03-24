# Kubernetes Documentation

This repository contains some required details about kubernetes. It will help you to know about kubernetes i.e what is kubernetes, why we use kubernetes, Architecture of kubernetes, Objects of kubernetes. I had providend some examples on each object which will help you to understand.

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

Nodes
Pods
Service
Namespace
Replication controller
Replicaset
Deployment
Stateful set
Daemon set
Config Map
Secrets
H

