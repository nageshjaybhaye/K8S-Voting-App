# 🚀 Kubernetes Monitoring Setup with Prometheus & Grafana (Minikube)

## 🔄 Grafana Dashboard

![Grafana](grafana.png)

## 📌 Project Overview

This project demonstrates how to set up a complete Kubernetes monitoring stack locally using Minikube, Helm, Prometheus, and Grafana.

A sample Voting Application is also deployed and monitored using Grafana dashboards.

---

## 🧰 Tech Stack

- Kubernetes (Minikube)
- Helm
- Prometheus
- Grafana
- Docker
- Voting Application (Microservices-based app)

---

## 🎯 Objectives

- Deploy a local Kubernetes cluster
- Install monitoring stack using Helm
- Visualize cluster metrics using Grafana
- Monitor application (Voting App)

---

## ⚙️ Prerequisites

Make sure the following tools are installed:

- Docker
- kubectl
- Minikube
- Helm

---

## 🚀 Setup Steps

### 1️⃣ Start Minikube

```bash
minikube start --memory=4096 --cpus=2 --driver=docker
```

---

### 2️⃣ Verify Cluster

```bash
kubectl get nodes
```

---

### 3️⃣ Install Helm

Verify installation:

```bash
helm version
```

---

### 4️⃣ Add Prometheus Helm Repository

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

---

### 5️⃣ Install Prometheus & Grafana

```bash
helm install prometheus-stack prometheus-community/kube-prometheus-stack \
--namespace monitoring \
--create-namespace \
--set grafana.service.type=NodePort \
--set prometheus.service.type=NodePort
```

---

### 6️⃣ Verify Pods

```bash
kubectl get pods -n monitoring
```

Wait until all pods are in **Running** state.

---

### 7️⃣ Access Grafana

```bash
minikube service prometheus-stack-grafana -n monitoring
```

---

## 🔐 Grafana Login

- Username: `admin`

Get password:

```bash
kubectl get secret prometheus-stack-grafana -n monitoring -o jsonpath="{.data.admin-password}"
```

Decode using any Base64 decoder.

---

## 📊 Monitoring

Grafana provides pre-built dashboards for:

- Node CPU & Memory Usage
- Pod Metrics
- Cluster Performance

---

## 🗳️ Voting Application Deployment

- Deployed a sample microservices-based voting app on Kubernetes
- Monitored application performance using Prometheus metrics
- Visualized data in Grafana dashboards

---

## ⚠️ Challenges Faced

- Insufficient resources on AWS (t3.small)
- Pods stuck in Pending / ContainerCreating state
- Docker memory limitation on Windows (WSL2)

---

## ✅ Solutions

- Switched to local setup using Minikube
- Increased WSL2 memory using `.wslconfig`
- Optimized resource allocation

---

## 🎯 Key Learnings

- Kubernetes cluster setup using Minikube
- Helm-based deployments
- Monitoring with Prometheus & Grafana
- Troubleshooting resource issues
- Real-world DevOps workflow

---

## 📸 Screenshots

_Add screenshots of Grafana dashboards, pod status, and application UI here_

---

## 🚀 Future Enhancements

- Custom Grafana dashboards
- Alerting with Alertmanager
- Deployment on cloud (EKS/GKE)
- CI/CD pipeline integration

---

## 👨‍💻 Author

**Nagesh Jaybhaye**  
CloudOps / DevOps Engineer

---

## ⭐ Conclusion

This project demonstrates a complete end-to-end Kubernetes monitoring setup, showcasing practical DevOps and observability skills.
