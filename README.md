# What is Kubernetes?
Kubernetes (also refered as K8s) is an open source container orchestration tool created by Google.

# What problem Kubernetes solve?
The increase usage of application containers, mainly from the trend to moving from monolitic applications architecture to microservices applications architecture demanded a tool to perform container orchestration.
Kubernetes helps with:
- High availability for applications (no downtime)
- Scalability
- Backup and restore

# Kubernetes architecture
K8s architecture is very complex.
A K8s cluster (where K8s was deployed) is composed by nodes. A Node is a virtual or physical machine. It also have what is called a **virtual network**, which is responsible to enabling communication between the nodes, making them act like a single machine. Each node also have what is called a **kubelet**, which is a kubernetes agent.
We have two different types of nodes: 

## Master Node 
Is the most important node on the cluster, responsible for the management of the cluster. We have at least one per cluster. The master node have many components:

1. **API Server**: It's a running container responsible for the entrypoints of kubernetes, ie how the user interacts with it (can be through **UI**, **API** or **CLI**). 

2. **Scheduler**: It's a running container responsible for scheduling pods operations

3. **Controller Manager**: It's a running container responsible for tracking what is happening on the cluster.

4. **etcd**: It's a key value store responsible for storing previous state of the cluster and backup informations.

## Worker Node
The nodes where the applications are actually running. They normally have a bigger workload, so uses more computational resources.

# Kubernetes main components
## Pod
## Service
## Ingress
## ConfigMap
## Secret
## Deployment
## StatefulSet
## DaemonSet

# References 
- [Kubernetes Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=s_o8dwzRlu4)
