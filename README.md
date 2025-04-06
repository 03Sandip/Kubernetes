@"
# 🐳 Kubernetes with Kind (Kubernetes in Docker)

This project sets up a **multi-node local Kubernetes cluster** using [Kind](https://kind.sigs.k8s.io/), and demonstrates basic Kubernetes operations like creating namespaces, deploying pods, and accessing containers.


## 🧠 Core Concepts
- Monolithic vs Microservices
- Kubernetes Architecture  
- `kubectl cluster-info` - Display cluster information 🛰️

## 💻 Setup On Local / AWS EC2
```bash
kind create cluster --name=tws-cluster --config=config.yml
kubectl config use-context kind-tws-cluster
```

## 🧩 Kubectl and Pods
```bash
kubectl get nodes                             # 🔍 View nodes
kubectl run nginx --image=nginx -n nginx      # 🚀 Launch pod
kubectl describe pod nginx -n nginx           # 📄 Pod info
```

## 🗂️ Namespaces, Labels, Selectors, Annotations
```bash
kubectl create namespace monitoring           # ➕ New namespace
kubectl get namespace                         # 📋 List namespaces
kubectl label namespace monitoring team=devops # 🏷️ Add label
kubectl describe namespace monitoring         # ℹ️ Details
```

## ⚙️ Workloads

### 🛠️ Deployments
```bash
kubectl apply -f deployment.yml
kubectl scale deployment nginx-deployment --replicas=3 -n nginx
```

### 🧬 StatefulSets
```bash
kubectl apply -f statefulset.yml
kubectl describe statefulset mysql -n database
```

### 🧹 DaemonSets
```bash
kubectl apply -f daemonset.yml
kubectl describe daemonset fluentd -n logging
```

### 🧪 ReplicaSets
```bash
kubectl apply -f replicaset.yml
kubectl describe replicaset nginx-replicaset -n nginx
```

### ⏱️ Jobs and CronJobs
```bash
kubectl apply -f job.yml
kubectl apply -f cronjob.yml
```

## 🌐 Networking

### 🔌 Cluster Networking
```bash
kubectl get svc -A
```

### 📡 Services
```bash
kubectl apply -f service.yml
kubectl describe svc nginx-service -n nginx
```

### 🚪 Ingress
```bash
kubectl apply -f ingress.yml
kubectl describe ingress nginx-ingress -n nginx
```

### 🔒 Network Policies
```bash
kubectl apply -f networkpolicy.yml
```

## 💾 Storage

### 🧱 PVs and PVCs
```bash
kubectl apply -f persistentVolume.yml
kubectl apply -f persistentVolumeClaim.yml
```

### 📦 Storage Classes
```bash
kubectl get storageclass
```

## 🛠️ ConfigMaps and Secrets
```bash
kubectl create configmap app-config --from-file=config.properties
kubectl create secret generic db-credentials   --from-literal=username=admin --from-literal=password=admin123
```

## 📈 Scaling and Scheduling

### 📊 HPA and VPA
```bash
kubectl autoscale deployment nginx --cpu-percent=50 --min=1 --max=10 -n nginx
kubectl apply -f vpa.yml
```

### 📍 Node Affinity & Taints
```bash
kubectl taint nodes node1 key=value:NoSchedule
kubectl apply -f node-affinity.yml
```

### 🚦 Resource Quotas & Probes
```bash
kubectl apply -f resourcequota.yml
kubectl describe quota my-quota -n dev
```

## 🔐 Cluster Administration

### 🧑‍⚖️ RBAC
```bash
kubectl apply -f role.yml
kubectl apply -f rolebinding.yml
```

### 📄 CRDs
```bash
kubectl apply -f crd.yml
kubectl get crd
```

## 📊 Monitoring and Logging

### 📏 Metrics Server
```bash
kubectl apply -f metrics-server.yml
kubectl top node
```

### 📈 Prometheus and Grafana
```bash
helm install prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring
kubectl port-forward svc/prometheus-stack-grafana 3000:80 -n monitoring --address=0.0.0.0
```

## 🧩 Advanced Features

### 🧰 Helm
```bash
helm create my-chart
helm install my-app my-chart -n my-namespace --create-namespace
```

### 🧼 Init & SideCar Containers
```bash
kubectl apply -f init-container.yml
kubectl apply -f sidecar-container.yml
```

## 🔐 Security
```bash
kubectl apply -f podsecuritypolicy.yml
kubectl apply -f secrets-encryption.yml
```

## ☁️ Cloud-Native Kubernetes

### 🌍 Managed Services
```bash
eksctl create cluster --name my-cluster
```

### ⚙️ Cluster Autoscaler
```bash
kubectl apply -f cluster-autoscaler.yml
```

## 🛠️ Debugging and Troubleshooting
```bash
kubectl logs pod-name -n namespace
kubectl describe pod pod-name -n namespace
kubectl exec -it pod-name -n namespace -- bash
```
