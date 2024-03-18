# Kubernetes Documentation

This repository contains some required details about kubernetes. It will help you to know about kubernetes i.e what is kubernetes, why we use kubernetes, Architecture of kubernetes, Objects of kubernetes and also what are the services used in kubernetes. I had providend some examples on each object which will help you to understand.

## 1] WHAT IS KUBERNETES?

 - Kubernetes is also know as k8s.
 - K8s is a Open-source orchestration tool developed by google. 
 - In terms of k8s orchestration refers to the automated management, co-ordination, and deployment of containerized applications across a cluster of nodes. Kubernetes is an open-source platform designed to automate the deployment, scaling, and management of containerized applications.
 - It schedules, runs, and manages isolated containers that are running on virtual/physical/cloud machines.
## 2] WHY KUBERNETES (K8s)?
 
 - All top cloud providers supports K8s. 
 - K8s offers a variety of features that help manage applications efficiently using just one tool. This means you don't need to juggle multiple tools or systems to handle different aspects of your applications. Instead, Kubernetes provides everything you need in a single platform, making it easier to deploy, scale, and maintain your applications without the hassle of dealing with various separate tools.
 - Kubernetes offers a bunch of useful features that Docker doesn't provide on its own. These include:

   Autoscaling: Kubernetes can automatically adjust the number of containers running your application based on how much traffic it's getting. So, if there's a sudden spike in users, Kubernetes can quickly add more containers to handle the load, and scale them back down when the demand decreases.

   Load Balancer: It helps distribute incoming traffic across multiple containers running the same application, ensuring that no single container gets overwhelmed. This keeps your application running smoothly even during high traffic times.

   Authentication: Kubernetes provides mechanisms for controlling access to your applications and resources, ensuring that only authorized users and services can interact with them.

   Security Mechanisms: It includes various security features to protect your applications and data from unauthorized access or attacks.

   Automatic Container Restart: If a container crashes or becomes unresponsive, Kubernetes can automatically restart it, ensuring that your application stays up and running.

   Basic Routing and DNS: Kubernetes includes built-in mechanisms for routing network traffic to the appropriate containers and resolving domain names to their corresponding IP addresses, making it easier to access and communicate with your applications.

   These features make Kubernetes a powerful platform for deploying and managing containerized applications, providing capabilities beyond what Docker offers alone.

## 3] UNDERSTANDING THE ARCHITECTURE OF K8S CLUSTER ?

Group of nodes is known as cluster. At the hardware level, a Kubernetes cluster is composed of many nodes, which can be split into two types:

 - The master node, which hosts the Kubernetes Control Plane that controls and manages the whole Kubernetes system. Control Plane contains following:-
    - API Server
    - ETCD
    - Schedular
    - Comtroller Manager
   And many more componants are there but this four are the default componants of control plane.

 - Worker nodes that run the actual applications you deploy. Worker nodes contains components are as follows:-
   - Kubelet
   - Kube proxy
   - Container Engine
   - Pods
  
  ![alt text](<Arc k8s.png>)







