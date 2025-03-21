# Simple_web_k8s
# 🚀 Deploying a Simple Web Application in Kubernetes

## 📌 Prerequisites
- Ubuntu VM with **Docker** installed
- **Minikube** installed and running
- **kubectl** CLI installed

---

## 🛠️ Step 1: Start Minikube
Start Minikube with Docker as the driver:
```bash
minikube start --driver=docker --force
```
This initializes a local Kubernetes cluster.

---

## 🚀 Step 2: Deploy the Web App
Create a deployment using the official **Nginx** image:
```bash
kubectl create deployment webapp --image=nginx --port=80
```
This deploys an **Nginx web server** inside a Kubernetes pod.

---

## 🌍 Step 3: Expose the Deployment
Expose the deployment as a **NodePort** service:
```bash
kubectl expose deployment webapp --type=NodePort --port=80 --target-port=80
```
This makes the web app accessible externally.

---

## 🔍 Step 4: Verify the Deployment
Check if the pod is running:
```bash
kubectl get pod
```
Check the exposed service:
```bash
kubectl get svc
```
You'll see an output like this:
```
NAME      TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
webapp    NodePort   10.108.210.196   <none>        80:31319/TCP   5m
```
Here, **31319** is the **NodePort** assigned.

---

## 🌐 Step 5: Access the Web App
Open the service in your browser:
```bash
minikube service webapp
```
Alternatively, use `curl` to test:
```bash
curl http://<minikube-ip>:<NodePort>
```
Replace `<minikube-ip>` with `minikube ip` output and `<NodePort>` with the port from `kubectl get svc`.

---

## 📊 Step 6: Monitor Pods & Logs
Watch the pod status:
```bash
watch kubectl get pod
```
Check logs for troubleshooting:
```bash
kubectl logs <pod-name>
```
Replace `<pod-name>` with the pod name from `kubectl get pods`.

---

## ✅ Deployment Complete!
Your **Kubernetes-based Nginx web app** is now running and exposed externally. 🎉
