---
name: cloud
description: "Manage cloud resources, infrastructure, and services across AWS, GCP, or Azure. Use when provisioning resources, configuring cloud services, or working with cloud-native tools."
---

# Cloud Skill

Configure and manage cloud infrastructure and services.

## When to Use

Use this skill when the user wants to:
- Provision cloud resources (AWS, GCP, Azure)
- Configure cloud services (compute, storage, databases)
- Set up cloud infrastructure as code
- Manage deployment pipelines
- Work with serverless functions
- Configure networking and security
- Optimize cloud costs

## Cloud Providers & Services

### AWS (Amazon Web Services)
- **Compute**: EC2 (VMs), Lambda (Serverless), ECS/EKS (Containers).
- **Storage**: S3 (Object), EBS (Block), EFS (File).
- **Database**: RDS (Relational), DynamoDB (NoSQL), ElastiCache (In-memory).
- **Networking**: VPC, Route 53 (DNS), CloudFront (CDN), ELB (Load Balancer).

### GCP (Google Cloud Platform)
- **Compute**: Compute Engine, Cloud Run (Serverless Containers), App Engine.
- **Storage**: Cloud Storage, Persistent Disk.
- **Database**: Cloud SQL, BigQuery (Data Warehouse), Firestore (NoSQL).
- **Networking**: VPC, Cloud DNS, Cloud Load Balancing.

### Azure (Microsoft Azure)
- **Compute**: Virtual Machines, Azure Functions, App Service.
- **Storage**: Blob Storage, Azure Files, Disk Storage.
- **Database**: Azure SQL, Cosmos DB, Azure Cache for Redis.
- **Networking**: VNet, Azure DNS, Application Gateway.

## Infrastructure as Code (IaC)

- **Terraform**: Multi-cloud, declarative configuration.
- **CloudFormation**: AWS-native infrastructure provisioning.
- **Pulumi**: Using general-purpose programming languages for IaC.
- **ARM Templates / Bicep**: Azure-native infrastructure provisioning.

## Common Tasks

### Compute & Scaling
- Provisioning virtual machines and auto-scaling groups.
- Setting up serverless functions (Lambda, Cloud Functions).
- Managing container orchestration (EKS, GKE, AKS).

### Networking & Security
- Configuring VPCs, subnets, and routing tables.
- Setting up firewalls and security groups.
- Implementing Identity and Access Management (IAM) roles and policies.

### Storage & Data
- Configuring object storage buckets and lifecycle policies.
- Setting up managed database instances.
- Implementing Content Delivery Networks (CDNs).

## Common Pitfalls

- **Unmanaged Costs**: Forgetting to turn off unused resources (e.g., idle NAT gateways, large DB instances).
- **Manual Configuration (\"Snowflake\" Infrastructure)**: Making manual changes in the cloud console instead of using IaC, leading to drift.
- **Over-permissioned IAM Roles**: Granting `AdministratorAccess` when only specific permissions are needed.
- **Insecure Networking**: Leaving SSH (22) or RDP (3389) open to the entire internet.
- **Lack of Tagging**: Not using tags, making it impossible to track costs and ownership.

## Deliverables

- Cloud infrastructure configuration (Terraform, CloudFormation, etc.).
- Deployment scripts and automation.
- Cost estimation and optimization reports.
- Infrastructure architecture diagrams.
- Security and compliance checklists.

## Quality Checklist

- [ ] Resources are properly tagged for cost tracking and ownership.
- [ ] Security groups/firewalls follow the principle of least privilege.
- [ ] Monitoring (CloudWatch, Stackdriver) and logging are enabled.
- [ ] Cost optimization measures are applied (e.s. Reserved Instances, Spot Instances).
- [ ] Infrastructure is reproducible through IaC.
- [ ] Follows cloud provider best practices (Well-Architected Framework).
