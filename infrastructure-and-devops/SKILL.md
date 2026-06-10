---
name: infrastructure-and-devops
description: "Automate infrastructure provisioning, CI/CD pipelines, and cloud deployments. Manage containerized environments using Docker and Kubernetes."
---

# Infrastructure and DevOps Skill

Automate and scale applications through efficient infrastructure management and continuous integration/delivery.

## When to Use

Use this skill when the user wants to:
- Set up CI/CD pipelines (GitHub Actions, GitLab CI, Jenkins).
- Implement Infrastructure as Code (IaC) (Terraform, Ansible, Pulumi).
- Containerize applications using Docker.
- Orchestrate containers with Kubernetes.
- Deploy to cloud providers (AWS, Azure, GCP).
- Implement GitOps workflows (ArgoCD, Flux).
- Manage deployment strategies (Blue-Green, Canary, Rolling).

## Core Pillars

### 1. CI/CD (Continuous Integration & Continuous Deployment)
- **CI (Continuous Integration)**: Automatically build and test code on every commit to ensure quality and catch bugs early.
- **CD (Continuous Delivery/Deployment)**: Automate the release process to various environments (Staging, Production) after successful testing.
- **Pipelines**: Orchestrate the entire lifecycle from commit to production using automated workflows.

### 2. Infrastructure as Code (IaC)
- **Declarative Configuration**: Define the desired state of infrastructure in code files (e.g., Terraform, CloudFormation).
- **Immutable Infrastructure**: Instead of changing existing servers, replace them with new ones from a standard image to ensure consistency.
- **Version Control**: Treat your infrastructure configuration exactly like application code, enabling audits and easy rollbacks.

### 3. Containerization & Orchestration
- **Docker**: Package applications and their dependencies into lightweight, portable containers for consistent environments across dev/prod.
- **Kubernetes (K8s)**: Automate deployment, scaling, and management of containerized applications at scale.
- **Microservices**: Use containers to decouple services and allow them to scale independently.

### 4. Cloud Management
- **Compute**: Manage virtual machines (EC2), serverless functions (Lambda), or managed container services (ECS, GKE).
- **Networking**: Configure Virtual Private Clouds (VPCs), subnets, load balancers, and DNS.
- **Storage**: Manage object storage (S3), block storage (EBS), and managed databases (RDS).
- **Security**: Manage Identity and Access Management (IAM) roles, policies, and secrets management.

## Implementation Examples

### Docker: Simple Web App Dockerfile
```dockerfile
# Use an official lightweight Python image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy requirements file first to leverage Docker cache
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 8000

# Run the application
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### Terraform: Provisioning an S3 Bucket (AWS)
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "my_app_data" {
  bucket = "my-unique-app-data-bucket-2023"

  tags = {
    Name        = "App Data Bucket"
    Environment = "Production"
  }
}

resource "aws_s3_bucket_public_access_block" "example" {
  bucket = aws_s3_bucket.my_app_data.id

  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}
```

## Deployment Strategies

- **Rolling Update**: Gradually replace old instances with new ones, ensuring zero downtime.
- **Blue-Green Deployment**: Run two identical production environments. Route traffic from "Blue" (old) to "Green" (new) once verified.
- **Canary Release**: Roll out the new version to a small subset of users first to monitor stability before full deployment.

## Common Pitfalls

- **Manual Configuration (Snowflake Servers)**: Making changes directly on servers instead of using IaC, leading to configuration drift.
- **Hardcoding Secrets**: Storing API keys or passwords in Dockerfiles or IaC files instead of using a secret manager.
- **Lack of Automation**: Relying on manual steps for deployments, which increases human error and downtime.
- **Over-provisioning**: Allocating too many resources to cloud services, leading to unnecessary costs.

## Deliverables

- CI/CD pipeline configurations (YAML files).
- IaC scripts (Terraform, Ansible, etc.).
- Dockerfiles and container orchestration manifests (Kubernetes YAML, Helm charts).
- Deployment automation scripts.
- Infrastructure architecture diagram/documentation.

## Quality Checklist

- [ ] Infrastructure is defined as code (IaC).
- [ ] CI/CD pipelines are automated, reliable, and tested.
- [ ] Automated testing is an integral part of the pipeline.
- [ ] Deployment strategies (e.g., rolling updates) are configured.
- [ ] Application is containerized and portable.
- [ ] Infrastructure follows the principle of least privilege.
- [ ] Monitoring and alerting are integrated into the deployment process.
- [ ] Rollback procedures are automated and tested.
