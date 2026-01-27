# 🛒 MERN E-Commerce Application with DevOps on AWS

A **production-ready e-commerce web application** built using the **MERN stack**, fully containerized with **Docker**, deployed on **AWS EKS (Kubernetes)**, and automated through a **CI/CD pipeline using Jenkins and Terraform (Infrastructure as Code)**.

This project demonstrates **end-to-end DevOps ownership**, covering application development, cloud infrastructure provisioning, automated deployments, monitoring, logging, and security.

---

## 🚀 Key Features

- Full-stack MERN application (React, Node.js, Express, MongoDB)
- Dockerized frontend and backend services
- Kubernetes orchestration on AWS EKS
- CI/CD pipeline using Jenkins and GitHub Webhooks
- Infrastructure provisioning using Terraform (IaC)
- Monitoring with Prometheus and Grafana
- Centralized logging using AWS CloudWatch
- Secure authentication with JWT and Bcrypt

---

## 🧠 Tech Stack

| Category | Technologies |
|--------|-------------|
| Frontend | React.js |
| Backend | Node.js, Express.js |
| Database | MongoDB |
| Authentication | JWT, Bcrypt |
| Containerization | Docker |
| Orchestration | Kubernetes (AWS EKS) |
| CI/CD | Jenkins, GitHub |
| Infrastructure | Terraform |
| Monitoring | Prometheus, Grafana |
| Logging | AWS CloudWatch |
| Cloud Provider | AWS |

---

## 🔄 CI/CD Pipeline (Jenkins)

1. Code is pushed to GitHub.
2. Jenkins pipeline is triggered via webhook.
3. Docker images for frontend and backend are built.
4. Images are pushed to Docker Hub / AWS ECR.
5. Application is deployed to AWS EKS using Kubernetes manifests.

✔ Fully automated build and deployment  
✔ Zero manual deployment steps

---

## ☁️ Infrastructure Provisioning (Terraform)

Infrastructure is provisioned using Terraform:

- VPC with public and private subnets
- AWS EKS cluster and worker nodes
- EC2 instance for Jenkins
- IAM roles and policies
- Elastic Load Balancer

```bash
cd terraform
terraform init
terraform apply
☸️ Kubernetes Deployment
cd k8s
kubectl apply -f mongo-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-deployment.yaml
Kubernetes best practices applied:

Liveness and Readiness probes

Resource requests and limits

Internal service networking

Restart policies for resilience

📊 Monitoring & Logging
Tool	Purpose
Prometheus	Metrics collection
Grafana	Metrics visualization
AWS CloudWatch	Centralized logging
Monitored metrics include:

CPU and memory utilization

Pod health and restarts

Request latency

Replica scaling

🔐 Security
JWT-based authentication

Password hashing using Bcrypt

Secrets managed via Kubernetes Secrets

MongoDB accessible only as an internal service

IAM roles, security groups, and VPC network isolation

🧪 Local Development
Run the application locally using Docker Compose:

git clone https://github.com/SUHEL782/application.com.git
cd application.com
docker-compose up --build
🔮 Future Enhancements
Convert Kubernetes manifests into Helm charts

Enable HTTPS using Ingress and cert-manager

Push Docker images to AWS ECR

Automate MongoDB backups

Add automated testing to CI/CD pipeline
