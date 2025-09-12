# 🎬 Netflix Clone - DevSecOps CI/CD Pipeline  

A complete **DevSecOps pipeline project** that deploys a Netflix clone on the cloud using **Docker, Jenkins, SonarQube, Trivy, OWASP Dependency-Check, Prometheus, Grafana, and Kubernetes**.  

This project demonstrates **end-to-end automation with security integration** — covering code quality checks, vulnerability scanning, containerization, CI/CD pipelines, monitoring, and GitOps deployment with ArgoCD.  

---

## 🚀 Project Architecture  

- **Frontend:** React.js (Netflix UI Clone with TMDB API)  
- **Containerization:** Docker  
- **CI/CD Automation:** Jenkins Pipelines  
- **Security Integration:** SonarQube, Trivy, OWASP Dependency-Check  
- **Monitoring:** Prometheus + Grafana  
- **Orchestration:** Kubernetes (EKS) + ArgoCD  
- **Cloud Provider:** AWS EC2 for infra setup 


## 🔑 Features  

✅ Automated CI/CD pipeline with Jenkins  
✅ Code quality & vulnerability checks (SonarQube, OWASP, Trivy)  
✅ Docker containerization and image scanning  
✅ Monitoring with Prometheus & Grafana dashboards  
✅ GitOps deployment using Kubernetes + ArgoCD  
✅ Email/Slack notifications for pipeline status  

---

🛠️ Setup Instructions
Phase 1: Initial Setup & Deployment

Launch an EC2 (Ubuntu 22.04) instance on AWS.

Install Docker and clone this repository:

sudo apt update && sudo apt upgrade -y
sudo apt install docker.io -y
git clone https://github.com/harshita194/Netflix-DevSecOps-CI-CD-Pipeline.git
cd Netflix-DevSecOps-CI-CD-Pipeline


Build & run Docker container with TMDB API key:

docker build --build-arg TMDB_V3_API_KEY=<your_api_key> -t netflix .
docker run -d --name netflix -p 8081:80 netflix:latest

Phase 2: Security Integration

SonarQube for code quality:

docker run -d --name sonar -p 9000:9000 sonarqube:lts-community


Access at: http://<public-ip>:9000 (default login: admin/admin)

Trivy for container scanning:

trivy image netflix:latest


OWASP Dependency-Check integrated into Jenkins pipeline for dependency scanning.

Phase 3: Jenkins CI/CD Pipeline

Install Jenkins and required plugins:

SonarQube Scanner

NodeJS Plugin

OWASP Dependency-Check

Docker Pipeline

Email Extension

Pipeline stages include:

Clean workspace

Checkout from GitHub

Code quality scan (SonarQube)

OWASP dependency check

Trivy file system + image scan

Docker build & push to DockerHub

Deployment to container

Phase 4: Monitoring (Prometheus + Grafana)

Install Prometheus & Node Exporter for metrics.

Install Grafana and connect it with Prometheus as a data source.

Import dashboards for container & pipeline monitoring.

Phase 5: Notifications

Jenkins pipeline configured for email/Slack notifications on build & deployment status.

Phase 6: Kubernetes + ArgoCD

Setup EKS Kubernetes cluster on AWS.

Install Prometheus Node Exporter with Helm.

Deploy Netflix app with ArgoCD GitOps.

Access the app via NodePort/Ingress.

Phase 7: Cleanup

Terminate unused EC2 instances & release cloud resources.
