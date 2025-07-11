<h1 align="center">
 Monolithic Application Deployment 🚀
</h1>

<p align="center">
  DevOps Project – End-to-End CI/CD on AWS
</p>


> This is a real-time monolithic application deployment project, implemented with complete DevOps practices using open-source tools and AWS Cloud infrastructure.



## 🏗️ Architecture Overview

We follow a **3-Tier Architecture** hosted on **AWS Cloud**:

- **Web Tier**: Public-facing web servers (Nginx/Apache)
- **Application Tier**: Application servers (Tomcat)
- **Database Tier**: Private RDS or EC2-based MySQL/PostgreSQL

All tiers are isolated using proper VPC, Subnets, Route Tables, and Security Groups.



## 🔧 Tools & Technologies

  
| Category               | Tool/Service            |
|------------------------|-------------------------|
| Cloud Provider         | AWS                     |
| Infrastructure as Code | Terraform (modular)     |
| Source Code Mgmt       | Git & GitHub            |
| CI/CD Pipeline         | Jenkins                 |
| Config Management      | Ansible                 |
| Artifact Storage       | S3                      |
| App Server             | Apache Tomcat           |
| Monitoring             | Prometheus & Grafana    |
| Code Quality           | SonarQube               |

---

## 📌 Project Flow: End-to-End Lifecycle

### 1. Infrastructure Provisioning
- Terraform is used to create AWS 3-tier architecture (modular approach).
- Includes EC2, VPC, Subnets, Internet Gateways, S3, Security Groups, etc.

### 2. Configuration Management
- Ansible installs required packages on EC2 instances.
- Roles and playbooks are created for reusability and automation.

### 3. Continuous Integration & Continuous Deployment
- Developers push code to GitHub.
- Jenkins is triggered for CI pipeline:
  - **Build**: Compile source code
  - **Test**: Run unit tests
  - **SonarQube**: Static code analysis
  - **Package**: Generate `.war` file
  - **Store Artifact**: Save to S3 bucket
  - **Deploy**: Automatically deploy to target EC2 (Dev → Test → UAT → Prod)

```mermaid
graph LR
A[Developer Pushes Code] --> B[Jenkins CI/CD Pipeline]
B --> C[Build & Test]
C --> D[SonarQube Quality Gate]
D --> E[Artifact (.war)]
E --> F[S3 Artifact Storage]
F --> G[Ansible Deployment]
G --> H[Target Servers (Tomcat)]
