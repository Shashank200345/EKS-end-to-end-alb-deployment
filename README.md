# 🚀 End-to-End Deployment of 2048 Game on Amazon EKS using AWS Load Balancer Controller

![AWS](https://img.shields.io/badge/AWS-EKS-orange?style=for-the-badge&logo=amazonaws)
![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.33-blue?style=for-the-badge&logo=kubernetes)
![Ingress](https://img.shields.io/badge/Ingress-ALB-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

# 📌 Project Overview

This project demonstrates an **end-to-end deployment** of the **2048 Game Application** on **Amazon Elastic Kubernetes Service (EKS)** using Kubernetes.

The application is exposed to the internet through an **AWS Application Load Balancer (ALB)** managed by the **AWS Load Balancer Controller**.

The project also demonstrates:

- Amazon EKS Cluster creation
- Managed Node Groups
- IAM Roles for Service Accounts (IRSA)
- AWS Load Balancer Controller installation
- Kubernetes Deployment
- Kubernetes Service
- Kubernetes Ingress
- Automatic ALB provisioning
- Target Group Health Checks
- Public Application Exposure

---

# 🏗 Architecture

```text
                               Internet
                                   │
                                   │
                          DNS (ALB Endpoint)
                                   │
                                   ▼
                 ┌────────────────────────────┐
                 │ Application Load Balancer  │
                 │        (AWS ALB)           │
                 └─────────────┬──────────────┘
                               │
                     HTTP Listener (Port 80)
                               │
                               ▼
                     Kubernetes Ingress
                               │
                               ▼
                  Kubernetes Service (ClusterIP)
                               │
                ┌──────────────┴──────────────┐
                │                             │
        2048 Pod Replica 1            2048 Pod Replica 2
                │                             │
                └──────────────┬──────────────┘
                               ▼
                     Amazon EKS Worker Nodes
                               │
                               ▼
                           Amazon EKS
```

---

# 🛠 AWS Services Used

| Service | Purpose |
|----------|---------|
| Amazon EKS | Managed Kubernetes Cluster |
| EC2 | Worker Nodes |
| IAM | Authentication & Authorization |
| IAM Roles for Service Accounts (IRSA) | Secure AWS access for Kubernetes Pods |
| VPC | Networking |
| Internet Gateway | Internet Connectivity |
| Security Groups | Traffic Control |
| Elastic Load Balancer (ALB) | Public Load Balancer |
| Target Groups | Route traffic to Pods |
| Route Tables | Network Routing |
| CloudFormation | IAM Service Account Stack |
| AWS CLI | Cluster Management |
| eksctl | EKS Cluster Creation |
| kubectl | Kubernetes Management |

---

# ☸ Kubernetes Resources Used

- Namespace
- Deployment
- ReplicaSet
- Pods
- Service (ClusterIP)
- Ingress
- Service Account
- Labels & Selectors

---

# 📁 Project Structure

```
eks-2048-alb-deployment/

│── manifests/
│     ├── deployment.yaml
│     ├── service.yaml
│     └── ingress.yaml
│
│── iam/
│     └── iam_policy.json
│
│── screenshots/
│
│── README.md
│── .gitignore
```

---

# 🚀 Deployment Workflow

### Step 1

Create an Amazon EKS Cluster

↓

### Step 2

Create Managed Node Group

↓

### Step 3

Associate IAM OIDC Provider

↓

### Step 4

Create IAM Policy

↓

### Step 5

Create IAM Role

↓

### Step 6

Create IAM Service Account (IRSA)

↓

### Step 7

Install AWS Load Balancer Controller

↓

### Step 8

Deploy the Application

```bash
kubectl apply -f deployment.yaml
```

↓

### Step 9

Create Kubernetes Service

```bash
kubectl apply -f service.yaml
```

↓

### Step 10

Create Ingress

```bash
kubectl apply -f ingress.yaml
```

↓

### Step 11

AWS Load Balancer Controller automatically creates:

- Application Load Balancer
- Target Group
- Listener
- Security Group Rules

↓

### Step 12

Access the application using the ALB DNS Name.

---

# 📦 Components Used

## Deployment

Creates the 2048 application Pods.

## Service

Provides a stable endpoint inside Kubernetes.

Type:

```
ClusterIP
```

## Ingress

Routes external HTTP traffic to the Service.

Ingress Class:

```
alb
```

Target Type:

```
IP
```

Scheme:

```
internet-facing
```

---

# 🔐 Security

This project uses **IAM Roles for Service Accounts (IRSA)** instead of attaching permissions to EC2 worker nodes.

Advantages:

- Least Privilege Access
- Better Security
- Fine-grained IAM Permissions
- Recommended AWS Practice

---

# 📊 Deployment Flow

```
User

↓

Application Load Balancer

↓

Ingress

↓

Service

↓

Pods

↓

Application
```

---

# 🧪 Validation Commands

Check Pods

```bash
kubectl get pods -A
```

Check Services

```bash
kubectl get svc -A
```

Check Ingress

```bash
kubectl get ingress -A
```

Check AWS Load Balancer Controller

```bash
kubectl get pods -n kube-system
```

Describe Ingress

```bash
kubectl describe ingress ingress-2048 -n game-2048
```

---

# 📸 Screenshots

Add screenshots here.

```
screenshots/

application.png

alb.png

target-group.png

pods.png

ingress.png
```

Example:

```markdown
## Running Application

![Application](screenshots/application.png)
```

---

# 🐞 Challenges Faced

During the implementation, the following issues were encountered and resolved:

- AWS Load Balancer Controller installation issues
- IAM Service Account recreation
- ALB Target Group health verification
- ALB accessibility troubleshooting
- Ingress reconciliation
- Security Group validation
- Webhook errors during controller setup

---

# 📚 What I Learned

- Amazon EKS Architecture
- Kubernetes Deployments
- Kubernetes Services
- Kubernetes Ingress
- AWS Load Balancer Controller
- IAM Roles for Service Accounts (IRSA)
- Target Groups
- Application Load Balancer
- EKS Networking
- Kubernetes Troubleshooting

---

# 🛠 Tools Used

- Amazon Web Services
- Amazon EKS
- EC2
- IAM
- kubectl
- eksctl
- AWS CLI
- Kubernetes
- Git
- GitHub

---

# 👨‍💻 Author

**Shashank**

If you found this project useful, feel free to ⭐ the repository.