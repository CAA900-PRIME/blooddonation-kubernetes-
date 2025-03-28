# blooddonation-kubernetes
Kubernetes Deployment for Cloud Infrastructure
This repository contains Kubernetes YAML configurations for deploying a cloud-based infrastructure. The setup includes separate deployments and services for the frontend, backend, MySQL database, and other essential services.

##### Key Components
- Frontend Pod: Exposed via a NodePort service.
- Backend Pod: Communicates internally via a ClusterIP service.
- MySQL Database Pod: Runs as a separate pod using a ClusterIP service for internal access.
- Service Layer Pod: Manages API requests and is exposed using a NodePort service.

##### Objectives
- Automate deployment using Kubernetes manifests
- Ensure scalability and high availability
- Implement network isolation and service communication
- Enable easy maintenance and updates


### Installation
Ensure the following are installed before continuing. This should work locally in a linux environemnt or using Azure Virtual VM.
1. Install docker
2. Install kind
3. Install Kubectl

Must create a single node cluster `kubernetes in docker` kind. 

```bash
kind create cluster --config kind-cluster.yaml
```

Deploy MySQL Database (ClusterIP)

```bash
kubectl apply -f mysql-deployment.yaml
```

Deploy Backend Service (ClusterIP)

```bash
kubectl apply -f backend-deployment.yaml
```
Deploy Frontend Service (NodePort)

```bash
kubectl apply -f frontend-deployment.yaml
```
Deploy Services (NodePort for external access)

```bash
kubectl apply -f services.yaml
```

Verify the Deployment

```bash
kubectl get pods
kubectl get services
```
