# Containerized Developer Portfolio with Docker & Kubernetes

A high-performance, containerized personal developer portfolio web server built using an Nginx alpine base image, tracked via Git/GitHub, and orchestrated locally using a resource-optimized Kubernetes cluster (Minikube).

---

## 🛠️ Tech Stack & Architecture
*   **Frontend Base:** HTML5, CSS3, JavaScript
*   **Web Server Engine:** Nginx (Alpine Linux Distribution)
*   **Container Engine:** Docker Desktop (WSL 2 Backend)
*   **Container Orchestration:** Kubernetes v1.35.1 (via Minikube)

---

## 🚀 Local Deployment Pipeline

### 1. Build & Package the Container
The application environment is built into an isolated image using a lightweight web server footprint:
```bash
docker build -t my-portfolio:v1 .

2. Cluster Initialization (Eco-Mode Optimization)To protect system memory and processing bandwidth on shared-resource development machines, the cluster is configured with strict compute boundaries ($2\text{ CPUs}$, $2048\text{MB}$ RAM):Bash

minikube start --driver=docker --cpus=2 --memory=2048mb

3. Image Sideloading & OrchestrationTo avoid external registry delays, the local container target is cached inside the Minikube registry before creating a deployment controller:Bash# Sideload image to cluster

minikube image load my-portfolio:v1

# Create Deployment Controller

minikube kubectl -- create deployment portfolio-app --image=my-portfolio:v1

4. Service Networking & AccessExposing the application internally using a NodePort layer and tunneling a direct local route to render the active endpoint:Bash# Expose Port Forwarding

minikube kubectl -- expose deployment portfolio-app --type=NodePort --port=80

# Retrieve Dynamic Service Route URL
minikube service portfolio-app --url

🔋 Resource Management & TeardownTo reclaim memory allocations ($2\text{ GB}$ RAM) and conserve power when not active, the environment uses a safe runtime teardown mechanism:
Bash

minikube stop

---

Save that file! Once you save it, your code repo is ready to be committed and pushed up to GitHub for good. 

Do you want to run the quick Git commands to push this finalized documentation up to your GitHub rep