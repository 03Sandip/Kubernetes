@"
# 🐳 Kubernetes with Kind (Kubernetes in Docker)

This project sets up a **multi-node local Kubernetes cluster** using [Kind](https://kind.sigs.k8s.io/), and demonstrates basic Kubernetes operations like creating namespaces, deploying pods, and accessing containers.

---

## 📁 Folder Structure

.
├── kind-cluster/        # Cluster configuration files
│   └── config.yml       # Kind cluster definition
├── pod.yml              # NGINX pod YAML definition
└── README.md            # Project documentation

---

## 🛠️ Prerequisites

- [Docker](https://www.docker.com/)
- [Kind](https://kind.sigs.k8s.io/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

Ensure Docker is running before creating the cluster.

---

## 🚀 Create Cluster

kind create cluster --name=tws-cluster --config=config.yml
kubectl get nodes
kubectl get ns

---

## 🧱 Create Namespace

kubectl create ns nginx
kubectl get ns

---

## 🚀 Deploy Pod

### Option 1: From Command Line

kubectl run nginx --image=nginx -n nginx

### Option 2: From YAML

kubectl apply -f pod.yml

#### Sample pod.yml:
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  namespace: nginx
spec:
  containers:
    - name: nginx-container
      image: nginx

---

## 🔍 Check Pod and Namespace

kubectl get pods -n nginx
kubectl describe pod/nginx-pod -n nginx

---

## 💻 Access Pod Shell

kubectl exec -it nginx-pod -n nginx -- bash

---

## 🗑️ Delete Resources

kubectl delete pod nginx -n nginx
kubectl delete ns nginx

---

## 🧼 Cleanup Cluster

kind delete cluster --name=tws-cluster

---

## 🙌 Thanks for Learning Kubernetes with Kind!

Feel free to expand this setup with Deployments, Services, Ingress, or Helm charts.
"@ > README.md
