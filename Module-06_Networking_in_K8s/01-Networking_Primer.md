# Kubernetes Networking Basics 
   - Kubernetes is designed for managing complexities of distributed data and applications.
   - Workloads can be scheduled on a set of nodes to distribute
the load. 
   - The Kubernetes network model enables networking communication
and needs to fulfill the following requirements:
     - Container-to-Container Communication
     - Pod-to-Pod Communication
     - Pod-to-Service communication
     - Node-to-node communication

## Connectivity between containers
   - Containers running in a Pod often need to communicate with each other. 
   - Containers within the same Pods can send Inter Process Communication (IPC) messages, share files, and communicate directly through the loopback interface using the localhost hostname.
   - Because each Pod is assigned a unique virtual IP address, each container in the same Pod is given that context and shares the same port space.
   
## Connectivity between Pods

