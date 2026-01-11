# 🐾 Spring PetClinic: Enterprise DevSecOps on GKE

This project demonstrates a modern **Shift-Left Security** approach for a Java Spring Boot application. It moves beyond simple deployment by integrating automated security gates, container hardening, and real-time observability.



## 🏗️ Architecture Overview
* **Application:** Spring Boot (Java) with H2/MySQL.
* **Infrastructure:** Google Kubernetes Engine (GKE).
* **CI/CD:** GitHub Actions (YAML-based pipelines).
* **Security Gating:** SonarQube (Static Analysis) & Trivy (Image Scanning).
* **Containerization:** Docker (Multi-stage builds for security and size).
* **Notifications:** Slack Webhooks & SMTP Email Integration.

## 🚀 The Pipeline Workflow
1.  **Code Analysis:** SonarQube checks for code smells, bugs, and vulnerabilities.
2.  **Filesystem Scan:** Trivy scans the source code for misconfigurations.
3.  **Build:** Docker builds a hardened, slim image using multi-stage builds.
4.  **Image Scan:** Trivy scans the Docker image for Critical/High CVEs. (Pipeline fails if found).
5.  **GCP Auth:** Secure authentication to GCP via Workload Identity Federation.
6.  **GKE Deploy:** Manifests applied to the cluster.
7.  **Alerting:** Real-time status sent to Slack and Email.

## 🛠️ Tools & Technologies
| Category | Tool |
| :--- | :--- |
| **Cloud** | GCP (GKE, GCR, IAM) |
| **IaaC** | Terraform |
| **Security** | Trivy, SonarQube, Checkov |
| **CI/CD** | GitHub Actions |
| **Orchestration** | Kubernetes (GKE) |
| **Alerting** | Slack, SendGrid/SMTP |

## 📁 Repository Structure
```bash
├── .github/workflows/   # GHA Pipeline Definitions
├── k8s/                 # Kubernetes Manifests (Deployment, Service, Ingress)
├── src/                 # Spring PetClinic Source Code
├── Dockerfile           # Multi-stage Dockerfile
├── pom.xml              # Maven Dependencies
└── README.md
