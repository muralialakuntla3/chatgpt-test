Module 1: Introduction to Containers & Kubernetes
🚀 1. What are Containers?
A container is a lightweight, standalone, and executable software package that includes:

Code
Runtime (libraries, dependencies)
System Tools
Settings
Why Containers?

Lightweight (shared host OS kernel)
Portable across environments
Isolated (no conflicts)
Scalable
🐳 2. Docker Basics
Key Concepts:

Image: A blueprint/template for a container.
Container: A running instance of an image.
Dockerfile: Instructions to build an image.
Registry: Storage for images (e.g., Docker Hub).
Practical Task: Run Your First Container
Install Docker

Download Docker.
Run a Container

bash
Copy code
docker run -d -p 8080:80 nginx
-d: Run container in the background
-p 8080:80: Map port 80 (container) → 8080 (host)
Verify

View running containers:
bash
Copy code
docker ps
Open http://localhost:8080 in a browser.
Stop the container:
bash
Copy code
docker stop <container_id>
🔧 3. Challenges of Managing Containers
Managing multiple containers is complex due to:

Orchestration issues: Starting, stopping, restarting containers.
Scaling: Automatically scaling based on load.
Networking: Ensuring container communication.
Resource management: CPU, memory allocation.
Fault tolerance: What happens when a container fails?
☸️ 4. What is Kubernetes?
Kubernetes (K8s) is an open-source container orchestration platform that automates deployment, scaling, and management of containers.

Why Kubernetes?
🚀 Automatic Scaling: Adjust pods based on demand.
🛠 Self-Healing: Restart failed containers.
⚖ Load Balancing: Distribute traffic evenly.
🔄 Automated Rollouts/Rollbacks: Safe updates.
📊 Resource Management: Optimize CPU/memory.
📝 Declarative Configurations: Define the "desired state" using YAML.
🏗 5. Kubernetes Architecture Overview
Master Node (Control Plane):
API Server: Accepts all requests (via kubectl).
etcd: Stores cluster state.
Controller Manager: Ensures desired state = actual state.
Scheduler: Assigns pods to nodes.
Worker Node:
Kubelet: Talks to the API server, manages pods.
Kube-proxy: Handles networking.
Container Runtime: Runs containers (e.g., Docker).
Pod: The smallest deployable unit in Kubernetes, containing one or more containers.

🛠 6. Hands-On: Set Up Kubernetes Locally
We’ll use Minikube to create a local Kubernetes cluster.

Step 1: Install Minikube
Install Minikube: Installation Guide.
Step 2: Start Your Cluster
Run the following command:

bash
Copy code
minikube start
Step 3: Verify the Cluster
Check the nodes in your cluster:

bash
Copy code
kubectl get nodes
You should see a single node running.
✅ Step 4: Run Your First Pod
To deploy a simple pod, run the following command:

bash
Copy code
kubectl run my-first-pod --image=nginx --restart=Never
Verify the pod:

bash
Copy code
kubectl get pods
Check pod details:

bash
Copy code
kubectl describe pod my-first-pod
🧰 Tools Needed
Docker: Install Docker
Minikube: Install Minikube
kubectl: Install kubectl
