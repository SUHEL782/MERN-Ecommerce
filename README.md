#  MERN E-commerce with DevOps on AWS

A cloud-native, scalable, and secure e-commerce web application built using the MERN stack, fully containerized with Docker, deployed to AWS EKS using Kubernetes, and managed through a robust CI/CD pipeline with Jenkins and Infrastructure as Code (IaC) using Terraform.
---
## Prometheus Architecture

![Prometheus Architecture](./prometheus-architecture.gif)

-----
#  Common Problems & Solutions
# Docker
Problem	Solution
Container exits immediately	Ensure the main process runs in the foreground.
Port binding errors	Check for conflicts using docker ps and free up ports.
Can't connect between containers	Use Docker Compose with proper service names and networks.
Large image size	Use multi-stage builds and Alpine-based images.
---
#  Kubernetes
Problem	Solution
CrashLoopBackOff	Check container logs and probe configurations.
ImagePullBackOff	Verify image name, tag, and Docker registry credentials.
Pending pods	Check node capacity or scheduling constraints.
DNS issues	Ensure CoreDNS is running and correctly configured.
Node Not Ready	Check EKS worker config, IAM roles, and node health.
-----
 Terraform
Problem	Solution
Resource exists already	Use terraform import or terraform state rm.
Inconsistent state in team	Use remote backend with state locking (S3 + DynamoDB).
terraform destroy deletes important infra	Use prevent_destroy = true on critical resources.
-----
Jenkins CI/CD
Problem	Solution
Docker commands fail	Ensure Jenkins agent has Docker installed and socket access.
Webhooks not triggering	Verify GitHub webhook settings and Jenkins endpoint availability.
Env variables missing	Set them in pipeline or Jenkins system config.
------
# App-Level (React, Node, MongoDB)
Problem	Solution
CORS errors	Enable cors in Express backend with correct origin.
MongoDB connection fails	Ensure MongoDB is accessible via correct URI or service.
JWT expires too soon	Extend expiry time and implement refresh tokens.
React app not loading on refresh	Configure fallback routes for React Router.
------
#  Monitoring & Logging
Problem	Solution
No data in Grafana	Ensure Prometheus is scraping the right targets.
CloudWatch logs missing	Check FluentBit config and IAM permissions.
Log clutter	Use log levels (info, warn, error) and structured logs.
---
##  Monitoring Stack

![Monitoring and Observability Stack](./Stack-Architech.gif)

---------
#  Security & Networking
Problem	Solution
JWT easily decoded	Use strong secrets and rotate regularly.
MongoDB exposed	Keep MongoDB behind internal services only.
HTTPS not working	Configure cert-manager and Ingress properly.
Secrets in code	Use Kubernetes Secrets or Sealed Secrets instead of plaintext.
----------
##  Project Overview

-  End-to-end CI/CD pipeline with **Jenkins & GitHub**
-  Fully containerized **frontend/backend using Docker**
-  **Kubernetes** deployment on **AWS EKS**
-  Infrastructure provisioning with **Terraform**
-  Monitoring using **Prometheus & Grafana**
-  Centralized logging with **AWS CloudWatch**
-  Secure login/signup with **JWT Authentication**

---

##  Tech Stack

| Category        | Technologies Used                                 |
|----------------|----------------------------------------------------|
| Frontend        | React.js                                           |
| Backend         | Node.js, Express.js                                |
| Database        | MongoDB                                            |
| Authentication  | JWT, Bcrypt, Express Middleware                    |
| Containerization| Docker                                             |
| Orchestration   | Kubernetes (AWS EKS)                               |
| CI/CD           | Jenkins, GitHub                                    |
| Infrastructure  | Terraform (EC2, VPC, EKS, IAM, ELB)                |
| Monitoring      | Prometheus, Grafana, AWS CloudWatch               |
| Cloud Provider  | AWS                                                |

---

#  Project Structure

.
├── frontend/ # React frontend
├── backend/ # Express backend API
├── docker/ # Dockerfiles
├── k8s/ # Kubernetes manifests
├── terraform/ # Infrastructure definitions
├── Jenkinsfile # Jenkins pipeline config
├── images/ # Screenshots (UI)
└── README.md # Project documentation

yaml
Copy
Edit

---

##  CI/CD Pipeline

- **Source Control:** GitHub  
- **CI/CD Tool:** Jenkins

### Flow:
1. Code pushed to GitHub triggers Jenkins pipeline.
2. Jenkins builds Docker images.
3. Pushes images to Docker Hub or AWS ECR.
4. Deploys the app to AWS EKS using `kubectl`.

---

##  Infrastructure Provisioning with Terraform

Provision infrastructure components:

cd terraform/
terraform init
terraform apply
Resources:

VPC with public/private subnets

EC2 instance for Jenkins (and optionally MongoDB)

AWS EKS cluster and worker nodes

IAM roles and policies

Elastic Load Balancer
----
# Kubernetes Deployment
Apply K8s manifests:

bash
Copy
Edit
cd k8s/
kubectl apply -f mongo-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-deployment.yaml
 Monitoring & Logging
Tool	Purpose
Prometheus	Scrapes metrics from Kubernetes
Grafana	Visualizes application metrics
AWS CloudWatch	Collects and stores logs from services

Dashboards Show:

CPU/Memory usage

Request latency

Pod health

Replica counts

 Security
JWT-based authentication with Bcrypt-hashed passwords

Environment secrets stored using Kubernetes Secrets

Security groups, IAM roles, and VPC for network isolation

Plans for enabling HTTPS using Ingress and cert-manager

 Future Enhancements
Convert manifests to Helm Charts

Enable HTTPS with Ingress + cert-manager

Push images to AWS ECR

Automate MongoDB backups

Add frontend route protection with JWT

Integrate tests into CI/CD

Add architecture diagrams using Mermaid or draw.io

 Local Development
Run locally using Docker Compose:

bash
Copy
Edit
git clone https://github.com/SUHEL782/application.com.git
cd application.com
docker-compose up --build
 Container Best Practices
Use Liveness/Readiness Probes in Kubernetes

Enable restartPolicy: Always for resilience

Gracefully handle SIGTERM in backend

Stream logs to stdout/stderr only

Watch resource usage to avoid memory leaks



 Contributing
Contributions are welcome! Fork the repo, create a feature branch, and submit a PR.
------

 Author
Suhel Khan
Uttar Pradesh, Lucknow
📧 workwithsuhel@gmail.com
📞 +91 8931004042
🌐 https://workwithsuhel.netlify.app
🔗 LinkedIn
💻 GitHub
