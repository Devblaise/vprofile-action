## GitOps CI/CD Pipeline with AWS EKS

## Overview
This repository implements a **GitOps-based CI/CD pipeline** for deploying applications on **AWS EKS** using **Terraform, GitHub Actions, Docker, Maven, Helm, and SonarCloud**.

## Architecture
![GitOps Pipeline](path-to-your-image)

### Key Components
- **Visual Studio Code (VS Code)**: Local development environment.
- **GitHub Actions**: Automates CI/CD workflows.
- **Terraform**: Infrastructure as Code (IaC) for provisioning AWS resources.
- **Amazon ECR**: Stores Docker images.
- **Amazon EKS**: Hosts Kubernetes workloads.
- **Docker**: Containerizes the application.
- **Helm Charts**: Manages Kubernetes deployments.
- **Apache Maven**: Builds the application.
- **SonarCloud**: Ensures code quality.

## Workflow
### 1. **Terraform Workflow (Infrastructure Deployment)**
1. Developers push infrastructure code to a **stage branch**.
2. **GitHub Actions** fetches the branch and runs:
   - `terraform plan` (preview infrastructure changes)
   - `terraform apply` (apply changes upon approval)
3. Changes are merged into the **main branch**.
4. AWS resources are provisioned, including **EKS and ECR**.

### 2. **Build, Test & Deploy Workflow**
1. Developers push application code to GitHub.
2. **GitHub Actions** fetches the code and executes:
   - **Maven** to build the application.
   - **SonarCloud** for code quality checks.
   - **Docker** to containerize the application.
3. The Docker image is pushed to **Amazon ECR**.
4. The application is deployed on **EKS using Helm Charts**.

## Prerequisites

- AWS Account with necessary permissions
- Terraform installed locally
- GitHub repository with Actions enabled
- Docker installed
- Kubernetes CLI (`kubectl`)
- Helm installed
- JDK 11
- Maven 3
- MySQL 8 

# Technologies 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- MySQL
# Database
Here,we used Mysql DB 
MSQL DB Installation Steps for Linux ubuntu 14.04:
- $ sudo apt-get update
- $ sudo apt-get install mysql-server

Then look for the file :
- /src/main/resources/db_backup.sql
- db_backup.sql file is a mysql dump file.we have to import this dump to mysql db server
- > mysql -u <user_name> -p accounts < db_backup.sql

## Setup Instructions
1. Clone this repository:
   ```sh
   git clone  https://github.com/Devblaise/vprofile-action.git
   ```
2. Configure AWS credentials:
   ```sh
   aws configure
   ```
3. Initialize Terraform:
   ```sh
   cd infrastructure
   terraform init
   ```
4. Run Terraform plan:
   ```sh
   terraform plan
   ```
5. Apply Terraform configuration:
   ```sh
   terraform apply --auto-approve
   ```
6. Push application code to trigger CI/CD workflow:
   ```sh
   git push origin main
   ```

## Repository Structure
```
├── .github/workflows    # GitHub Actions CI/CD workflows
├── infrastructure       # Terraform code for AWS EKS setup
├── src                  # Application source code
├── Dockerfile           # Docker containerization
├── helm                 # Helm charts for Kubernetes deployment
└── README.md            # Documentation
```

## Monitoring & Logs
- **GitHub Actions**: Check CI/CD pipeline status.
- **AWS Console**: Monitor EKS and ECR resources.
- **SonarCloud Dashboard**: Analyze code quality.
- **Kubernetes Logs**:
  ```sh
  kubectl logs -f <pod-name>
  ```

## Contributing
Feel free to submit issues or pull requests to improve this repository.






