# 🚀 CI/CD with Jenkins, Argo CD, and Minikube

This project demonstrates a **complete CI/CD pipeline** using **Jenkins** for Continuous Integration (CI) and **Argo CD** for Continuous Deployment (CD) — all running on a local **Minikube** Kubernetes cluster.

---

## ⚙️ CI: Build and Push Docker Image using Jenkins

1. **Jenkins Pipeline (Jenkinsfile)**  
   - Builds the application Docker image from the source repository [`bakehouse-ITI`](https://github.com/SamarGooda/bakehouse-ITI).  
   - Pushes the image to **Docker Hub**.  

2. **Steps Overview**
These steps are defined in the `Jenkinsfile` stored in the [`argocd-jenkins-demo`](github.com/ahmednabil208/argocd-jenkins-demo/blob/main/jenkinsfile) repository.  


## 🧩 CD: Deploy Argo CD inside Minikube

1. Start Minikube Cluster

```bash
minikube start --driver=docker --memory=2200mb --cpus=2
```

2. Install Argo CD
```bash
kubectl create namespace argocd
wget https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl apply -n argocd -f install.yaml
```

## 🌐 Access Argo CD UI using NGINX Ingress

1. Enable the Ingress Controller

```bash
minikube addons enable ingress
```

2. Create an Ingress for Argo CD

the file are defined in the `argocd-ingress-server` stored in the [`argocd-jenkins-demo`](github.com/ahmednabil208/argocd-jenkins-demo/blob/main/jenkinsfile) repository.  


Add Host Entry

<minikube-ip>  argocd.local


Access the Argo CD UI at 👉 https://argocd.local