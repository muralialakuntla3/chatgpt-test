# Module 1: Introduction to Containers & Kubernetes

## 1. What are Containers?
A **container** is a lightweight, standalone, and executable software package that includes everything needed to run an application:
- **Code**  
- **Runtime** (software dependencies like libraries)  
- **System Tools**  
- **Settings**

Containers solve the "it works on my machine" problem by isolating the application and its dependencies, ensuring consistency across environments.

### Key Features of Containers:
1. **Lightweight**: Containers share the host OS kernel, making them smaller and faster than traditional virtual machines.
2. **Portability**: Works consistently across development, testing, and production.
3. **Isolation**: Applications are isolated from each other, avoiding conflicts.
4. **Scalability**: Containers can be easily scaled up/down.

---

## 2. Docker Basics
To understand Kubernetes, you need to know about **Docker**—the most popular containerization tool.

### Core Docker Concepts:
1. **Image**: A blueprint (template) of a container (like a snapshot).
   Example: An image of Nginx, Python, or Node.js.
2. **Container**: A running instance of an image.
3. **Dockerfile**: A file containing instructions to build a Docker image.
4. **Registry**: A repository to store Docker images. Example: Docker Hub.

### Practical Task: Run Your First Docker Container
1. **Install Docker**:
   - For Windows/Mac: Install **Docker Desktop**.
   - For Linux: Follow the instructions on [Docker's website](https://docs.docker.com/get-docker/).

2. **Run a Container**:
   Open a terminal and run the following command:
   ```bash
   docker run -d -p 8080:80 nginx
   ```
   - `-d`: Run container in detached mode (background).
   - `-p 8080:80`: Map port 80 (container) to port 8080 (host).
   - `nginx`: Official image for Nginx web server.

3. **Verify the Container**:
   - Check running containers:
     ```bash
     docker ps
     ```
   - Access the application in a browser at **http://localhost:8080**.
   - Stop the container:
     ```bash
     docker stop <container_id>
     ```

---

## 3. Challenges of Managing Containers
While containers are great, managing hundreds or thousands of them at scale becomes difficult:
- **Orchestration Issues**: How do you start, stop, or restart containers automatically?
- **Scaling**: How do you scale containers up and down based on demand?
- **Networking**: How do containers communicate with each other?
- **Resource Management**: How do you ensure efficient resource usage?
- **Fault Tolerance**: What happens when a container or server fails?

This is where **Kubernetes** comes in.

---

## 4. What is Kubernetes?
**Kubernetes** (often abbreviated as **K8s**) is an **open-source container orchestration platform** that automates the deployment, scaling, and management of containerized applications.

### Why Kubernetes?
Kubernetes solves the challenges of managing containers by providing features like:
1. **Automatic Scaling**: Scale up or down based on demand.
2. **Self-Healing**: Restart containers that fail automatically.
3. **Load Balancing**: Distribute traffic across containers.
4. **Automated Rollouts and Rollbacks**: Deploy updates safely without downtime.
5. **Resource Management**: Optimize CPU and memory usage.
6. **Declarative Configuration**: Define your desired state using YAML or JSON.

---

## 5. Kubernetes Architecture Overview
Kubernetes has a **master-worker** architecture:

### Master Node (Control Plane):
Manages the Kubernetes cluster. Key components:
- **API Server**: The front end for the Kubernetes cluster. All requests (via `kubectl`) go through it.
- **etcd**: A distributed key-value store to keep the cluster state.
- **Controller Manager**: Ensures the desired state of the cluster matches the actual state.
- **Scheduler**: Assigns pods to available nodes based on resource availability.

### Worker Node:
Runs the containers (workloads). Key components:
- **Kubelet**: Agent on the worker node that communicates with the API server.
- **Kube-proxy**: Manages networking for pods.
- **Container Runtime**: Runs containers (e.g., Docker, containerd).

### Pods:
The smallest, most basic deployable unit in Kubernetes. A pod can have **one or more containers**.

---

## 6. Hands-On: Your First Kubernetes Setup
We’ll use **Minikube** to set up a local Kubernetes cluster.

1. **Install Minikube**:
   - Follow the installation guide: [Minikube Installation](https://minikube.sigs.k8s.io/docs/start/).

2. **Start a Cluster**:
   Open a terminal and run:
   ```bash
   minikube start
   ```
   - Minikube will create a single-node Kubernetes cluster locally.

3. **Verify the Cluster**:
   - Check the nodes in your cluster:
     ```bash
     kubectl get nodes
     ```
   - It should show the single node created by Minikube.

4. **Run Your First Pod**:
   - Create a simple pod using the `kubectl` command:
     ```bash
     kubectl run my-first-pod --image=nginx --port=80
     ```
   - Verify the pod is running:
     ```bash
     kubectl get pods
     ```
   - Access the pod using port forwarding:
     ```bash
     kubectl port-forward pod/my-first-pod 8080:80
     ```
   - Open your browser and go to **http://localhost:8080** to see Nginx in action.

---

## Key Takeaways
- Containers are lightweight and portable solutions for running applications.
- Docker is the leading tool for containerization.
- Kubernetes simplifies container management at scale with features like **self-healing**, **scaling**, and **load balancing**.
- Minikube helps you create a local Kubernetes cluster for learning and development.
