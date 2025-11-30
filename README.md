Microservices Deployment on Amazon EKS using GitHub Actions & Argo CD**

---

## 📝 **Overview**

This project demonstrates a complete CI/CD and GitOps-based deployment workflow for a Go-based microservice.
The application is containerized with Docker, pushed to Docker Hub through GitHub Actions CI, and deployed to an Amazon EKS cluster using Argo CD.
An AWS Application Load Balancer (ALB), created by the AWS Load Balancer Controller, provides public access.

---

## 🏗️ **Architecture**

<img width="1342" height="501" alt="image" src="https://github.com/user-attachments/assets/eb14f12e-65e8-486f-8f39-66e007f0ead8" />

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

![ci](https://github.com/user-attachments/assets/61282b21-5b00-4af3-b50a-8d5adea36457)

</details>

---

<details>
  <summary><strong>2️⃣ Docker Hub – Image Pushed</strong></summary>

Docker image built and pushed to Docker Hub.

<br>

![dockerhub](https://github.com/user-attachments/assets/f769bd63-e0d6-44d6-b388-53bf45674903)


</details>

---

<details>
  <summary><strong>3️⃣ Argo CD – Application Synced</strong></summary>

Argo CD successfully pulled and synced Kubernetes manifests.

<br>

![argocd](https://github.com/user-attachments/assets/20c8ba87-750b-4d13-9feb-af4ebf4b0adb)


</details>

---

<details>
  <summary><strong>4️⃣ EKS Workloads – Pod Status</strong></summary>

Application pod created in the EKS cluster.
Pending state confirms the deployment reached Kubernetes.

<br>

![workload-pods](https://github.com/user-attachments/assets/37e0d2eb-daca-44de-8840-3020378cec2c)


</details>

---

<details>
  <summary><strong>5️⃣ Application Load Balancer (Ingress)</strong></summary>

Ingress successfully created an Internet-facing ALB.

<br>

![alb](https://github.com/user-attachments/assets/ee462b5d-c820-4213-b0e7-ea3c7df16f3f)


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



