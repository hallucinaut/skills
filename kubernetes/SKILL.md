---
name: kubernetes
description: "Deploy and manage Kubernetes applications. Use when working with K8s manifests, Helm charts, deployment strategies, or cluster configuration."
---

# Kubernetes Skill

Deploy and manage applications in Kubernetes clusters.

## When to Use

Use this skill when the user wants to:
- Create Kubernetes manifests (YAML)
- Use Helm charts for deployments
- Configure Pods, Services, Deployments
- Set up Helm repositories
- Implement K8s networking
- Configure RBAC and security
- Use ingress controllers

## Kubernetes Resources

### Core Resources
- **Pod**: The smallest deployable unit in Kubernetes; contains one or more containers.
- **Deployment**: Manages a set of identical Pods, providing declarative updates to the desired state (e.g., scaling, rolling updates).
- **Service**: An abstraction that defines a logical set of Pods and a policy by which to access them (provides stable IP/DNS).
- **StatefulSet**: Used for applications that require unique identities and stable storage (e.g., databases).
- **DaemonSet**: Ensures that all (or some) Nodes run a copy of a Pod (e.g., logging or monitoring agents).
- **ConfigMap & Secret**: Manage configuration data and sensitive information separately from the application code.

### Ingress & Networking
- **Ingress**: Manages external access to services in a cluster, typically HTTP/HTTPS.
- **Service Types**: 
    - `ClusterIP`: Internal communication within the cluster.
    - `NodePort`: Exposes the service on each Node's IP at a static port.
    - `LoadBalancer`: Uses a cloud provider's load balancer to expose the service externally.
- **NetworkPolicies**: Control traffic flow between Pods and other network endpoints (firewalling).

### Storage
- **PersistentVolume (PV)**: A piece of storage in the cluster that has been provisioned by an administrator.
- **PersistentVolumeClaim (PVC)**: A request for storage by a user/Pod.
- **StorageClass**: Allows administrators to describe the "classes" of storage they offer (e.g., SSD vs HDD).

## Implementation Examples

### Simple Deployment and Service

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: web-container
        image: nginx:1.25
        ports:
        - containerPort: 80
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"

---
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```

## Helm Charts

```yaml
# Chart structure
my-chart/
├── Chart.yaml          # Metadata about the chart
├── values.yaml         # Default configuration values
├── templates/           # Kubernetes manifests with templating (Go templates)
│   ├── deployment.yaml
|   ├── service.yaml
|   └── ingress.yaml
└── .helmignore        # Files to ignore during packaging
```

## Deployment Strategies

- **RollingUpdate**: Gradually replaces old Pods with new ones, ensuring no downtime.
- **Recreate**: Terminates all existing Pods before creating new ones (causes downtime).
- **Canary**: Roll out the new version to a small subset of users first to test stability.
- **Blue/Green**: Maintain two identical environments; switch traffic from "Blue" (old) to "Green" (new) once verified.

## Common Pitfalls

- **Missing Resource Limits**: Not setting CPU/Memory requests and limits, which can lead to "noisy neighbor" issues or OOM kills.
- **Hardcoding Configs**: Embedding configuration directly in the container image instead of using ConfigMaps/Secrets.
- **Using `latest` Tag**: Relying on the `:latest` tag for images, making deployments non-deterministic and hard to roll back.
- **Ignoring Liveness/Readiness Probes**: Not defining health checks, causing traffic to be sent to Pods that aren't ready or are dead.

## Deliverables

- Kubernetes manifests (YAML).
- Helm charts (if using Helm).
- Deployment documentation.
- Testing scripts (e.g., `kubectl` commands, `kubetest`).

## Quality Checklist

- [ ] All resources have appropriate labels and selectors.
- [ ] Resource requests and limits are defined for all containers.
- [ ] Liveness and readiness probes are configured.
- [ ] Services use the correct `type` (ClusterIP, LoadBalancer, etc.).
- [ ] ConfigMaps and Secrets are used for sensitive/environment-specific data.
- [ ] RBAC is configured following the principle of least privilege.
