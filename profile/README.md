# 📚 Book Vault

Welcome to Book Vault - A Modern Book Management System

## 🏗️ Project Architecture

```mermaid
graph TB
    subgraph "Frontend [GitHub Pages]"
        A[React Application]
    end

    subgraph "Backend Infrastructure"
        subgraph "AWS Cloud"
            B[VPC]
            C[EC2 Instance]
            
            subgraph "Kubernetes Cluster"
                D[Backend Deployment]
                E[Backend Service]
                F[Ingress Controller]
            end
        end
    end

    subgraph "CI/CD"
        G[GitHub Actions]
        H[GitHub Container Registry]
    end

    A -->|API Calls| F
    F --> E
    E --> D
    G -->|Push Container| H
    D -->|Pull Container| H
```

## 🌐 Project Overview
Book Vault is a comprehensive book management system split across three main repositories, each serving a specific purpose in the application architecture.

## 📂 Repository Structure

```
book-vault/
├── frontend/          # React frontend application
├── backend/           # Node.js backend service
└── infra/            # Infrastructure as Code (Terraform)
```

### Frontend Repository
[![Deploy to GitHub Pages](https://github.com/book-vault/frontend/workflows/Deploy%20to%20GitHub%20Pages/badge.svg)](https://github.com/book-vault/frontend/actions)
- **Tech Stack**: React.js
- **Hosting**: GitHub Pages
- **URL**: [https://bookvault.maniish.in](https://bookvault.maniish.in)
- **CI/CD**: Automated deployment via GitHub Actions

### Backend Repository
[![Container Build](https://github.com/book-vault/backend/workflows/Container%20Build/badge.svg)](https://github.com/book-vault/backend/actions)
- **Tech Stack**: Node.js
- **Container Registry**: GitHub Container Registry
- **Image**: `ghcr.io/book-vault/backend`
- **API Endpoint**: [https://backend.bookvault.maniish.in](https://backend.bookvault.maniish.in)

### Infrastructure Repository
- **Tech Stack**: Terraform
- **Cloud Provider**: AWS
- **Components**:
  - VPC Configuration
  - EC2 Instance
  - Kubernetes Cluster

## 🔧 Infrastructure Architecture

```mermaid
flowchart TB
    subgraph AWS["AWS Cloud"]
        subgraph VPC["VPC"]
            subgraph Public["Public Subnet"]
                EC2["EC2 Instance"]
                
                subgraph K8S["Kubernetes Cluster"]
                    D["Deployment"]
                    S["Service"]
                    I["Ingress"]
                end
            end
            NAT["NAT Gateway"]
            IGW["Internet Gateway"]
        end
    end
    
    Client-->|HTTPS|I
    I-->S
    S-->D
    D-->|Pull Image|CR["GitHub Container Registry"]
```

## 🚀 Deployment Flow

1. **Frontend Deployment**
   - Push to `main` branch triggers GitHub Actions
   - Build React application
   - Deploy to GitHub Pages
   - Available at `bookvault.maniish.in`

2. **Backend Deployment**
   - Push to `main` branch triggers GitHub Actions
   - Build Docker container
   - Push to GitHub Container Registry
   - Kubernetes pulls latest image
   - Exposed via Ingress at `backend.bookvault.maniish.in`

3. **Infrastructure Deployment**
   ```mermaid
   graph LR
       A[Terraform Init] -->|Initialize| B[Terraform Plan]
       B -->|Review| C[Terraform Apply]
       C -->|Create| D[AWS Resources]
       D -->|Configure| E[Kubernetes]
       E -->|Deploy| F[Applications]
   ```

## 🛠️ Local Development Setup

### Prerequisites
- Node.js 16+
- Docker
- Kubernetes CLI (kubectl)
- Terraform
- AWS CLI

### Frontend Setup
```bash
git clone https://github.com/book-vault/frontend.git
cd frontend
npm install
npm start
```

### Backend Setup
```bash
git clone https://github.com/book-vault/backend.git
cd backend
npm install
npm run dev
```

### Infrastructure Setup
```bash
git clone https://github.com/book-vault/infra.git
cd infra
terraform init
terraform plan
terraform apply
```

## 📡 Endpoints

- **Frontend**: `https://bookvault.maniish.in`
- **Backend API**: `https://backend.bookvault.maniish.in`
  - Protected with SSL certificates
  - Managed through Kubernetes Ingress

## 🔐 Security Features

- SSL/TLS encryption for all endpoints
- Container security scanning
- Infrastructure security through AWS VPC
- Kubernetes security policies

## 📝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## 👥 Contact

Project Link: [https://github.com/book-vault](https://github.com/book-vault)


---
---
### Reference 
- [Customizing your organization's profile](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/customizing-your-organizations-profile)