# 3-Tier Application Deployment on Kubernetes

## Overview

This project demonstrates the deployment of a 3-Tier Application on Kubernetes using Docker containers.

### Architecture

The application consists of:

* **Frontend:** React.js
* **Backend:** Node.js / Express.js
* **Database:** MongoDB

The application is containerized using Docker and deployed on Kubernetes with Deployments, Services, and Persistent Storage.

---

## Technology Stack

* Docker
* Kubernetes
* MongoDB
* Node.js
* Express.js
* React.js
* Docker Hub
* Minikube

---

## Architecture Flow

User → Frontend Service → Frontend Pod → Backend Service → Backend Pod → MongoDB Service → MongoDB Pod

---

## Kubernetes Resources Used

### Deployments

Separate deployments are created for:

* Frontend
* Backend
* MongoDB

Deployments provide:

* Pod management
* Self-healing
* Rolling updates
* Scalability

### Services

#### Frontend Service

* Type: NodePort
* Exposes the application to users

#### Backend Service

* Type: ClusterIP
* Internal communication within the cluster

#### MongoDB Service

* Type: ClusterIP
* Enables backend-to-database communication

### Persistent Storage

MongoDB uses:

* Persistent Volume (PV)
* Persistent Volume Claim (PVC)

Benefits:

* Data persistence across pod restarts
* Storage independent of pod lifecycle

---

## Docker Images

Docker images are stored in Docker Hub and pulled by Kubernetes during deployment.

---

## Deployment Steps

### Clone Repository

```bash
git clone <repository-url>
cd <repository-name>
```

### Apply Kubernetes Manifests

```bash
kubectl apply -f .
```

### Verify Deployments

```bash
kubectl get deployments
```

### Verify Pods

```bash
kubectl get pods
```

### Verify Services

```bash
kubectl get svc
```

---

## Access Application

For Minikube:

```bash
minikube service frontend
```

or

```bash
minikube service frontend-service
```

---

## Challenges Solved

### Pod Scheduling Issue

Issue:

* Incorrect node selector configuration prevented pod scheduling.

Resolution:

* Updated deployment configuration and removed invalid node selectors.

### Persistent Volume Claim Issue

Issue:

* MongoDB pod remained in Pending state due to missing PVC.

Resolution:

* Created and bound the required Persistent Volume Claim.

### Image Pull Issues

Issue:

* Kubernetes was unable to pull images.

Resolution:

* Pushed images to Docker Hub and updated deployment manifests.

---

## Learning Outcomes

Through this project, I gained hands-on experience with:

* Kubernetes Deployments
* Services and Networking
* Persistent Volumes and PVCs
* Docker Image Management
* Troubleshooting Kubernetes Workloads
* Container Orchestration
* Application Deployment Strategies

---

## Author

Neetesh Sahu

Computer Science Engineering Student | DevOps Enthusiast

