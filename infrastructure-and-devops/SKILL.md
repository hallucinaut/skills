---
name: infrastructure-and-devops
description: "Automate infrastructure provisioning, CI/CD pipelines, and cloud deployments. Manage containerized environments using Docker and Kubernetes."
---

# Infrastructure and DevOps Skill

Automate and scale applications through efficient infrastructure management and continuous integration/delivery.

## When to Use

Use this skill when the user wants to:
- Set up CI/CD pipelines (GitHub Actions, GitLab CI, Jenkins).
- Implement Infrastructure as Code (IaC) (Terraform, Ansible).
- Containerize applications using Docker.
- Orchestrate containers with Kubernetes.
- Deploy to cloud providers (AWS, Azure, GCP).
- Implement GitOps workflows (ArgoCD, Flux).
- Manage deployment strategies (Blue-Green, Canary, Rolling).

## Core Pillars

### 1. CI/CD (Continuous Integration & Continuous Deployment)
- **CI**: Automatically build and test code on every commit to ensure quality.
- **CD**: Automatically deploy code to various environments (Staging, Production) after successful testing.
- **Pipelines**: Automate the entire lifecycle from commit to production.

### 2. Infrastructure as Code (IaC)
- **Declarative Configuration**: Define the desired state of infrastructure in files (Terra-form, CloudFormation).
- **Immutable Infrastructure**: Instead of changing existing servers, replace them with new ones from a standard image.
- **Version Control**: Treat your infrastructure configuration exactly like application code.

### 3. Containerization & Orchestration
- **Docker**: Package applications and their dependencies into lightweight, portable containers.
- **Kubernetes (K8s)**: Automate deployment, scaling, and management of containerized applications.
- **Microservices**: Use containers to decouple services and scale them independently.

### 4. Cloud Management
- **Compute**: Manage virtual machines, serverless functions, or container services.
- **Networking**: Configure VPCs, subnets, load balancers, and DNS.
- **Storage**: Manage object storage (S3), block storage, and managed databases.
- **Security**: Manage IAM (Identity and Access Management) roles and policies.

## Best Practices

- **Automate everything**: If you have to do it twice, write a script or a pipeline for it.
- **Pipeline as Code**: Store all CI/CD configurations in version control.
- **Immutability**: Prefer replacing infrastructure over modifying it in place.
- **Idempotency**: Ensure that applying the same configuration multiple times results in the same state without side effects.
- **Observability**: Integrate logging, monitoring, and alerting into your deployment process.
- **Least Privilege**: Use the minimum necessary permissions for service accounts and CI/CD runners.

## Deliverables

- CI/CD pipeline configurations (YAML files).
- IaC scripts (Terraform, Ansible, etc.).
- Dockerfiles and container orchestration manifests (Kubernetes YAML, Helm charts).
- Deployment automation scripts.
- Infrastructure architecture diagram/documentation.

## Quality Checklist

- [ ] Infrastructure is defined as code.
- [ ] CI/CD pipelines are automated and reliable.
- [ ] Automated testing is an integral part of the pipeline.
- [ ] Deployment strategies (e.g., rolling updates) are configured.
- [ ] Application is containerized and portable.
- [ ] Infrastructure follows the principle of least privilege.
- [ ] Monitoring and alerting are integrated into the deployment.
- [ ] Rollback procedures are automated and tested.
