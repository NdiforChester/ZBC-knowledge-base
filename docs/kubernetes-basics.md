##  What is Kubernetes?
Kubernetes is a container orchestration platform. It helps you automatically deploy, manage, and scale containerized applications so you don't have to do it manually. Think of i>Kubernetes enhances containers by orchestrating them across clusters of machines, handling tasks such as scheduling, load balancing, and self-healing — making it easier to maint>

## Core Architecture
Understanding key Kubernetes terms helps in navigating and using the platform effectively. The fundamental concepts include nodes, pods, replica sets, services, and jobs:

1.  Nodes are the physical or virtual machines in the Kubernetes cluster that provide the resources needed to run containers.
2.  Pods are the smallest deployable units in Kubernetes. A pod can contain one or more containers that share networking and storage resources. Pods are always scheduled on spec>3.  ReplicaSets ensure that a specified number of pod replicas are running at any given time. They monitor pod health and replace any pods that fail or become unresponsive, main>4. Services  provide stable endpoints to access pods, abstracting the dynamic nature of pods that may be created or destroyed. They enable communication within the cluster or ex>

## Key Features
1. Self-Healing
If a pod fails, Kubernetes automatically restarts it. This ensures high availability and resilience, even during unexpected issues.
2. Auto-Scaling
The Horizontal Pod Autoscaler (HPA) automatically scales the number of pods based on metrics like CPU utilization or memory consumption.
3. Declarative Configuration (YAML)
Kubernetes uses a declarative approach to configuration, where you define the desired state of your system in YAML files called manifests. These manifests describe the resources>
4. Resource Management
Kubernetes allows you to define resource requests and limits for each pod, ensuring that applications have the resources they need without starving other workloads.
5. RBAC (Security)
Role-Based Access Control (RBAC) governs cluster access and permitted actions. By defining roles and assigning them to users or groups, you control permissions granularly. A rol>
6. Storage management – Persistent storage is abstracted by a consistent interface that works across providers, whether in the cloud, on a network share, or on a local filesystem.
7. Stateless and stateful applications – While Kubernetes initially focused on stateless containers, it’s now also got built-in objects to represent stateful apps too. You can run any kind of application in Kubernetes.
## Essential kubectl Commands
# List all running pods
kubectl get pods

# Create a deployment
kubectl create deployment my-app --image=my-image

# Scale a deployment
kubectl scale deployment my-app --replicas=3

# Expose a deployment as a service
kubectl expose deployment my-app --port=80
