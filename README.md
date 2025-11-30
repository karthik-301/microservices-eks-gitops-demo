Microservices Deployment on Amazon EKS using GitHub Actions & Argo CD**

---

## 📝 **Overview**

This project demonstrates a complete CI/CD and GitOps-based deployment workflow for a Go-based microservice.
The application is containerized with Docker, pushed to Docker Hub through GitHub Actions CI, and deployed to an Amazon EKS cluster using Argo CD.
An AWS Application Load Balancer (ALB), created by the AWS Load Balancer Controller, provides public access.

---

## 🏗️ **Architecture**

<img width="1504" height="451" alt="image" src="https://github.com/user-attachments/assets/5a8015e8-edb6-4985-bc4b-42cf780727ad" />


**End-to-end flow:**

**Developer → GitHub Repo → GitHub Actions CI → Docker Hub → Argo CD → Amazon EKS → AWS ALB → End User**

---

## 🧰 **Tools Used**
* Amazon EKS
* AWS Application Load Balancer (ALB)
* AWS Load Balancer Controller
* GitHub Actions
* Argo CD
* Docker
* Docker Hub
* Go (microservice)
* Kubernetes YAML manifests
---

## 📁 **Folder Structure**
```
├── src/
│   └── product-catalog/          # Go microservice source code
│       ├── main.go
│       ├── go.mod
│       └── go.sum
│
├── docker/
│   └── Dockerfile                # Docker image build file
│
├── k8s/
│   ├── deployment.yaml           # Kubernetes Deployment
│   ├── service.yaml              # Kubernetes Service
│   └── ingress.yaml              # Kubernetes Ingress (ALB)
│
│
├── terraform/                    # Infrastructure as Code (IaC)
│   ├── main.tf                   # EKS cluster, VPC, IAM, Nodes
│   ├── variables.tf              # Input variables
│   ├── outputs.tf                # Terraform outputs (EKS, LB, nodes)
│   ├── provider.tf               # AWS provider configuration
│
├── .github/
│   └── workflows/
│       └── ci.yaml                 # GitHub Actions CI pipeline
│
├── docs/
│   ├── architecture.png            # Architecture diagram
│   └── screenshots/                # CI/EKS/ALB screenshots
│       ├── ci.png                  # GitHub Actions pipeline screenshot
│       ├── dockerhub.png           # Docker Hub image screenshot
│       ├── argocd.png              # Argo CD sync screenshot
│       ├── eks-pods.png            # EKS pod status screenshot
│       └── alb.png                 # ALB details screenshot
│
└── README.md


```
-----
### 🔄 **CI/CD Pipeline Flow**

1. Developer pushes code → GitHub triggers GitHub Actions
2. GitHub Actions builds & tests the Go application
3. GitHub Actions builds Docker image and tags it with commit SHA
4. Pushes image to Docker Hub
5. Argo CD detects manifest updates and syncs them to EKS
6. Amazon EKS pulls the latest image and updates the Deployment
7. AWS Load Balancer Controller creates ALB from Ingress
8. End user accesses the application through the ALB DNS / custom domain

---
## ⭐ **Features**

* Full CI/CD pipeline using GitHub Actions & Argo CD
* GitOps-based deployment model
* Kubernetes-native application deployment
* Automatic ALB provisioning using Ingress
* Immutable Docker image tagging using commit SHA
* Clean microservice deployment on Amazon EKS
* Clear separation of CI (image build) and CD (manifest sync)

---

# 🖼️ **Screenshots**

Below are the key screenshots for the CI/CD and deployment process.
Click each section to expand.

---

<details>
  <summary><strong>1️⃣ CI Pipeline Run (GitHub Actions)</strong></summary>

GitHub Actions workflow executed successfully.

<br>

![ci](https://github.com/user-attachments/assets/be851f84-07d7-485a-8a9e-2be511496cfc)

</details>

---

<details>
  <summary><strong>2️⃣ Docker Hub – Image Pushed</strong></summary>

Docker image built and pushed to Docker Hub.

<br>

![docker](https://github.com/user-attachments/assets/1e5dce39-28a0-4454-bf2a-00fcc441d4c6)

</details>

---

<details>
  <summary><strong>3️⃣ Argo CD – Application Synced</strong></summary>

Argo CD successfully pulled and synced Kubernetes manifests.

<br>

![argocd](https://github.com/user-attachments/assets/819c6352-e9cd-46aa-b884-7a7bafc57c95)

</details>

---

<details>
  <summary><strong>4️⃣ EKS Workloads – Pod Status</strong></summary>

Application pod created in the EKS cluster.
Pending state confirms the deployment reached Kubernetes.

<br>

<img width="900" src="https://github.com/user-attachments/assets/d4f2ae79-7c5a-4cc8-b288-80e9f7c9aebd" />

</details>

---

<details>
  <summary><strong>5️⃣ Application Load Balancer (Ingress)</strong></summary>

Ingress successfully created an Internet-facing ALB.

<br>

<img width="900" src="https://github.com/user-attachments/assets/ca973646-1b6a-4a2b-9ba1-04a564d6c475" />

</details>

---

🎉 **Conclusion**

This project demonstrates a complete end-to-end DevOps workflow using modern tools and best practices:

* **GitHub Actions** for continuous integration
* **Docker** for containerization
* **Argo CD** for continuous delivery using GitOps
* **Amazon EKS** for Kubernetes orchestration
* **AWS Application Load Balancer (ALB)** for external exposure via Ingress

This setup reflects a real-world production-style CI/CD pipeline and can serve as a strong portfolio project or reference implementation.

If you have any questions or suggestions for improvements, feel free to explore, customize, or extend the project based on your needs!



