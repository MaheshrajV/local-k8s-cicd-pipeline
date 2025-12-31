🧑‍💻 Local Kubernetes CI/CD Pipeline — GitHub Actions + Docker + Minikube
📌 Overview

This project implements a full CI/CD pipeline for a Node.js application using:

✔ GitHub Actions
✔ Docker
✔ Docker Hub
✔ Kubernetes (Minikube)
✔ Self-Hosted GitHub Runner

Whenever code is pushed to GitHub, the pipeline:

1️⃣ Runs build & tests
2️⃣ Builds a Docker image
3️⃣ Pushes the image to Docker Hub
4️⃣ Deploys the app automatically to Minikube

This simulates real-world DevOps pipelines in a fully local environment.

🏗 Architecture
Developer → Push Code → GitHub Repo
                │
                ▼
        GitHub Actions (Self-Hosted Runner)
                │
                ▼
        Build & Push Docker Image
                │
                ▼
        Deploy to Kubernetes (Minikube)
                │
                ▼
        Application Running

🧠 Technologies Used
Tool	Purpose
Node.js	Sample web application
Docker	Containerization
Docker Hub	Image registry
Kubernetes	Orchestration
Minikube	Local Kubernetes cluster
GitHub Actions	CI/CD automation
Self-Hosted Runner	Local job execution
📁 Project Structure
.
├── app.js
├── package.json
├── Dockerfile
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
└── .github/workflows/ci-cd.yml

🚀 Application

Simple Node.js server listening on port 5000
Container exposes port 5000 → 80 via Kubernetes Service

🐳 Docker Build
docker build -t <user>/cicd-demo:latest .
docker push <user>/cicd-demo:latest


This is automated via CI/CD.

☸ Kubernetes Deployment
Deployment

Runs Pods for the app

Service

Exposes app via NodePort

Access using:

minikube service cicd-demo-service

🔐 GitHub Secrets
Secret	Purpose
DOCKERHUB_USERNAME	Docker login
DOCKERHUB_TOKEN	Access token
KUBE_CONFIG	Base64 encoded kubeconfig
⚙️ CI/CD Workflow — Key Steps

✔ Checkout code
✔ Install Node
✔ Run tests
✔ Build Docker image
✔ Push to Docker Hub
✔ Apply Kubernetes manifests

Runs on self-hosted runner:

runs-on: self-hosted

🧪 Self-Hosted Runner

Installed locally so the pipeline can reach Minikube.

Steps:

Settings → Actions → Runners → New Runner


Then:

./config.sh
./run.sh


Now CI runs on your laptop.

🏁 Final Result

✔ Push code
✔ Pipeline runs automatically
✔ Image built
✔ Image pushed
✔ App redeployed
✔ Pods updated

Full local CI/CD 🎯

🧩 Challenges & Solutions
❌ Issue — Wrong file paths

✔ Fixed manifest path

❌ Issue — Invalid base64 kubeconfig

✔ Regenerated clean string

❌ Issue — cert files missing in CI

✔ Used embedded cert kubeconfig

kubectl config view --minify --flatten --raw

❌ Issue — GitHub runner couldn’t reach Minikube

Cloud → Local network blocked

✔ Solution: Self-Hosted Runner

Now Minikube is reachable 🎉

🏆 Key Learnings

✔ CI/CD automation
✔ Docker & containerization
✔ Kubernetes deployment
✔ GitHub Actions
✔ Secret management
✔ Networking constraints
✔ Self-hosted runners
✔ Debugging real-world failures

🎯 Why This Matters

This project replicates enterprise DevOps pipelines, but locally and free.

Your workflow now:

🚀 Builds
🚀 Tests
🚀 Packages
🚀 Publishes
🚀 Deploys automatically


