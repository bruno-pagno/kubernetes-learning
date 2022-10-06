# What is Kubernetes?
Kubernetes (also refered as K8s) is an open source container orchestration tool created by Google using Golang programming language.

# What problem Kubernetes solve?
The increase usage of application containers, mainly from the trend to moving from monolitic applications architecture to microservices applications architecture demanded a tool to perform container orchestration.
Kubernetes helps with:
- High availability for applications, decreasing no downtime
- Scalability in a simple way
- Backup and restore

# Kubernetes architecture
K8s architecture is very complex.
A K8s cluster (where K8s was deployed) is composed by nodes. A Node is a virtual or physical machine. It also have what is called a **virtual network**, which is responsible to enabling communication between the nodes, making them act like a single machine (distributed system principle). Each node also have what is called a **kubelet**, which is a kubernetes agent.
We have two different types of nodes: 

## Master Node 
Is the most important node on the cluster, responsible for the management of the cluster. We have at least one per cluster. The master node have many components:

1. **API Server**: It's a running container responsible for the entrypoints of K8s, i.e. how the user interacts with it (can be through **UI**, **API** or **CLI**). 

2. **Scheduler**: It's a running container responsible for scheduling pods operations.

3. **Controller Manager**: It's a running container responsible for tracking what is happening on the cluster.

4. **etcd**: It's a key value store responsible for storing previous state of the cluster and backup informations.

As mentioned, the master node is very important, so it's a good practice to have a backup of it, which usually is a replica running with the same configuration.

## Worker Node
The nodes where the applications are actually running. They normally have a bigger workload, so uses more computational resources than the master node.

# Kubernetes main components
## Pod
- Smallest unit in Kubernetes
- Is an abstraction for a container. This is used to don't limit kubernetes to Docker container technology. Instead, You only interacts with kubernetes. 
- Usually we have one application per pod
- Each pod get its own internal **IP Address**, which changes if the pod are replaced
- Are ephemeral: can die any time and be replaced by other pod (and do not store data)

## Service
It's a **permanent Ip address** that can be attached to each pod. Lifecycle of pods and services are not connected.
An **external service** open communications with an external service (e.g. browser) and a **internal service** can only receive internal communication from the K8s network. The IP aaddresses of the services follow the model **http://${NODE-IP}:{PORT}**

## Ingress
Is used to give an domain name and secure protocol (e.g. HTTPS) for the application, forwarding the requests to the service component.

## ConfigMap
Is an external configuration for the application, acting like envinronment variables. It's in plain text. 

## Secret
It's like configMap, but is used to store secret data (like credentials), but instead of plain text, are encrypted.

## Volume
Attaches a physical storage to a pod (can be on local machine or outside of the K8s cluster). This is used because pods are ephemeral, so they cannot persist data as mentioned.

## Deployment
It's a blueprint of how the application pods should behave. You only create the deployment file, not the pods directly. It's used for **stateless applications** (i.e. applications that dont need to store permanent data).

## StatefulSet
It's the opposite of deployments, used mostly to database applications but also to any type of **stateful application** (i.e. applications that need to store permanent data). They are harder to manage than deployment, and that's why is a good idea to have databases outside of K8s cluster.

# Kubernetes configuration
All the configuration of the cluster is made through the master node, on the **API server** process. K8s client can be **UI**, **API** or **CLI** are the main entrypoint for the cluster. The requests can either be on **YAML** or **JSON** file format. The configuration file is declarative. The **controller manager** alwas check if the actual state equals the desired state. 
The configuration have three main blocks: 
1. metadata: name and labels
2. specification: attributes of the component
3. status: current state vs desired state (managed by K8s etcd)

# Minikube
Minikube is a tool created to learn K8s, where the cluster is implemented using a single master node 
and a worker node on a single machine.
## commands

The cli is only used to start and delete the cluster. All the other parts are done through kubeclt CLI.
```
minikube start -> starts the cluster
minikube stop -> stops the cluster
minikube ip -> shows minikube ip
```

# Kubectl
CLI tool to interact with K8s cluster, being the most powerful between UI, API and CLI.

## commands
```
kubectl get nodes -> Show all the nodes of the cluster and status
kubectl apply -f file -> Creates what is defined on a file
kubectl get all -> Show pods, services, deployments 
kubectl get pods -> Show all the pods
kubectl get configmaps -> Show all the configmaps
kubectl get deplyments -> Show all the deployments
kubectl get secrets -> Show all the secrets
```


# References 
- [Kubernetes Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=s_o8dwzRlu4)
- [Kubernetes Documentation](https://kubernetes.io/docs/home/)