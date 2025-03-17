Kubernetes Minikube Deployment
This repository contains Kubernetes configurations for deploying an Nginx web server on Minikube. The goal is to understand container orchestration, scaling, and service exposure using Kubernetes.

📌 Project Overview
This project demonstrates how to: ✅ Deploy a simple web server (Nginx) on Minikube
✅ Expose the application using a Kubernetes Service
✅ Scale the deployment to multiple replicas
✅ Retrieve the application's external accessible URL
✅ Manage Kubernetes deployments efficiently

📂 Project Structure
java
Copy
📁 kubernetes-minikube
 ├── 📄 deployment.yaml  → Kubernetes Deployment definition
 ├── 📄 service.yaml     → Kubernetes Service definition
 ├── 📄 README.md        → Project documentation (this file)
⚙️ Prerequisites
Before you start, ensure you have:

Kubernetes & Minikube installed (kubectl and minikube)
Git installed to manage version control
A working VirtualBox/Docker setup (for running Minikube)
🚀 Deployment Steps
Step 1: Start Minikube
sh
Copy
minikube start --driver=virtualbox
If using Docker:

sh
Copy
minikube start --driver=docker
Step 2: Deploy the Web Server
sh
Copy
kubectl create deployment hello-world --image=nginx
This command:

Creates a deployment named hello-world
Uses the Nginx image from Docker Hub
Step 3: Expose the Deployment as a Service
sh
Copy
kubectl expose deployment hello-world --type=NodePort --port=80
This:

Exposes the deployment to allow access from outside
Opens port 80 (default HTTP)
Step 4: Scale the Deployment
sh
Copy
kubectl scale deployment hello-world --replicas=3
This increases the number of running pods to 3, improving fault tolerance.

Step 5: Retrieve the Service URL
sh
Copy
minikube service hello-world --url
Copy the URL output and open it in a browser. You should see the Nginx Welcome Page.

🔍 Verification
Check if everything is running properly:

sh
Copy
kubectl get pods       # Lists running pods
kubectl get services   # Shows available services
kubectl get deployments # Confirms deployment status
🗑️ Cleanup
To remove the deployed resources:

sh
Copy
kubectl delete deployment hello-world
kubectl delete service hello-world
minikube stop
Why clean up?

Free up system resources (Minikube uses RAM & CPU)
Avoid running unnecessary containers
Ensure a fresh start for future projects
📜 Understanding Kubernetes Objects
Kubernetes Object	Purpose
Deployment	Ensures the correct number of app instances run
Service	Exposes the app to be accessible
ReplicaSet	Manages the number of running pods
Pod	Smallest deployable unit (runs the container)
📌 Lessons Learned
Minikube allows local Kubernetes cluster testing
Scaling with Kubernetes helps handle traffic efficiently
Kubernetes Services provide networking for deployments
Using YAML for defining Kubernetes resources simplifies deployments
📡 Future Improvements
🔹 Automate the deployment using Helm Charts
🔹 Implement a CI/CD pipeline using GitHub Actions
🔹 Deploy a real web application instead of a static Nginx page

👨‍💻 Author
🔹 Name: Mustafa Mukhtar
🔹 GitHub: MustafaMuk
