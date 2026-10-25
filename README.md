# Day 15: Kubernetes Fundamentals

## Objective
Understand core Kubernetes architecture, deploy containerized workloads using declarative YAML manifests, inspect cluster runtime resources, scale replicas, expose the application via a NodePort Service, and demonstrate Kubernetes self-healing controller loops[cite: 8, 10, 11].

---

## Architecture and Key Concepts

- **Docker vs. Kubernetes**: Docker builds, packages, and runs standalone containers on an isolated host[cite: 9, 13]. Kubernetes is a distributed container orchestration platform that coordinates scheduling, horizontal scaling, self-healing, rolling updates, and service discovery across a multi-node cluster[cite: 9, 12, 13].
- **Cluster**: The complete Kubernetes environment, consisting of control plane nodes and worker nodes.
- **Control Plane**: Coordinates the cluster, makes scheduling decisions, monitors state, and enforces the declared desired state[cite: 9].
- **Worker Node**: A machine running the container runtime, `kubelet`, and `kube-proxy` responsible for executing application Pods[cite: 9].
- **Pod**: The smallest deployable and schedulable compute unit in Kubernetes, containing one or more tightly coupled containers[cite: 9, 12].
- **Deployment**: A declarative controller that manages replicated Pods, monitors health, and supports rolling updates[cite: 9, 12].
- **Service**: A stable network abstraction that routes traffic across dynamic, ephemeral Pods matching a label selector[cite: 9, 12].
- **Label Selector**: Key-value metadata queries used by Deployments and Services to dynamically identify and bind target Pods[cite: 10, 12].

---

## Cluster Setup
A local Kubernetes cluster named `winter-arc` was provisioned using `kind` (Kubernetes in Docker) backed by native Docker CE[cite: 9]:

```bash
kind create cluster --name winter-arc
kubectl cluster-info
kubectl get nodes
