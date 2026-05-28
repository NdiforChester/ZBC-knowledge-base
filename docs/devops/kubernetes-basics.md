# Kubernetes Basics

Kubernetes is a container orchestration platform. It automates deployment, scaling, networking, and recovery for containerized applications across a cluster of machines.

Docker helps package and run containers. Kubernetes helps operate many containers reliably in production.

## 1. Why Kubernetes Exists

Running one container manually is simple. Running many containers across many servers is harder.

Kubernetes helps with:

- Scheduling containers onto available nodes.
- Restarting failed workloads.
- Scaling applications.
- Service discovery.
- Load balancing.
- Rolling updates.
- Declarative infrastructure through YAML manifests.

## 2. Cluster Architecture

A Kubernetes cluster contains a control plane and worker nodes.

### Control Plane

The control plane manages the cluster state. It decides where workloads should run and responds to changes.

Important components:

- API server: entry point for cluster operations.
- Scheduler: chooses nodes for pods.
- Controller manager: keeps desired state and actual state aligned.
- etcd: stores cluster state.

### Worker Nodes

Worker nodes run application workloads.

Important components:

- kubelet: communicates with the control plane and manages pods on the node.
- container runtime: runs containers.
- kube-proxy: handles network rules for services.

## 3. Core Objects

| Object | Meaning |
| --- | --- |
| Pod | Smallest deployable unit; usually runs one application container |
| Deployment | Manages replicated pods and rolling updates |
| ReplicaSet | Ensures a desired number of pod replicas exists |
| Service | Provides stable network access to pods |
| ConfigMap | Stores non-secret configuration |
| Secret | Stores sensitive configuration |
| Namespace | Separates resources inside a cluster |
| Ingress | Routes external HTTP or HTTPS traffic |

## 4. Declarative Configuration

Kubernetes usually uses YAML manifests. You describe the desired state, then Kubernetes works to maintain it.

Example Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: web
          image: nginx:alpine
          ports:
            - containerPort: 80
```

Apply it:

```bash
kubectl apply -f deployment.yaml
```

## 5. Essential kubectl Commands

```bash
kubectl get nodes
kubectl get pods
kubectl get deployments
kubectl get services
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl apply -f file.yaml
kubectl delete -f file.yaml
kubectl scale deployment web --replicas=5
```

## 6. Services

Pods are temporary. Their IP addresses can change. Services provide stable access.

Common service types:

| Type | Use |
| --- | --- |
| ClusterIP | Internal cluster access |
| NodePort | Exposes service on node ports |
| LoadBalancer | Uses cloud load balancer when supported |

## 7. Health and Self-Healing

Kubernetes can restart failed containers and replace unhealthy pods.

Health checks include:

- Liveness probe: checks whether a container should be restarted.
- Readiness probe: checks whether a pod should receive traffic.
- Startup probe: gives slow-starting applications more time.

## 8. Scaling

Manual scaling:

```bash
kubectl scale deployment web --replicas=3
```

Automatic scaling can be handled by the Horizontal Pod Autoscaler when metrics are available.

## 9. Security Basics

Important security controls:

- RBAC for permissions.
- Namespaces for separation.
- Secrets for sensitive values.
- Resource requests and limits.
- Network policies where supported.
- Least privilege service accounts.

## 10. Beginner to Intermediate Practice Path

1. Explain pods, deployments, and services.
2. Apply a deployment manifest.
3. Expose the deployment with a service.
4. View logs and describe resources.
5. Scale a deployment.
6. Update an image and observe rollout behavior.
7. Create a ConfigMap and mount it into a pod.

## 11. Common Mistakes to Avoid

- Editing running pods manually instead of updating manifests.
- Storing passwords in ConfigMaps.
- Forgetting resource requests and limits.
- Exposing services publicly without understanding the security impact.
- Ignoring readiness probes for production workloads.
