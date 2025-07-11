Noooo


<h1 align="center">
 Monolithic Application Deployment 🚀
</h1>

<p align="center">
  DevOps Project – End-to-End CI/CD on AWS
</p>


> The project is designed with industry standards, following best practices for infrastructure provisioning, configuration management, CI/CD, and monitoring.

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


    <details> <summary>Click to Expand Diagram</summary>

    graph TD
    
         A[Developer Pushes Code] --> B[Jenkins CI/CD Pipeline]
    
         B --> C [Build & Test]
    
         C --> D [SonarQube Quality Gate]
    
         D --> E [Generate Artifact (.war)]
    
         E --> F [Upload to S3 Bucket]
    
         F --> G [Deploy using Ansible]
    
         G --> H [Tomcat App Server]
</details>


### 4. Verification
 - Verify application accessibility via ELB DNS.

- Ensure all services like tomcat or httpd are running.

### 5. Monitoring

- Prometheus collects metrics from EC2 and apps.

- Grafana visualizes health dashboards for CPU, memory, and disk usage.


## 🛠️ Common Issues & Resolutions

#### 🔴 Pipeline Failures
- Cause: Misconfigurations, missing plugins, wrong credentials.

- Fix:

     Check Jenkins logs

     Validate plugin setup and credentials

     Debug dependencies

#### ⚠️ Infrastructure Errors

- Cause: Terraform syntax, module errors, provisioner failures.

- Fix:

     Review .tf files and module structure

     Use terraform plan before apply

#### ⚠️ Code Failures
- Cause: SonarQube violations, failed unit tests.

- Fix:

     Check SonarQube dashboard

     Share detailed logs with the development team

#### 🔄 Production Issue Handling
- Scenario	Action
  
     * App not working after deploy	- **Perform rollback from S3**
     * App running slow	- **Auto Scaling / Edge Location**
     * App not loading for users	- **Check Tomcat / HTTPD status**


## ✅ Conclusion

- This project helped me gain strong experience in:

- Automating infrastructure with Terraform

- Configuring servers using Ansible

- Building and deploying apps using Jenkins pipelines

- Monitoring infrastructure and services with Grafana/Prometheus

- Handling real-world issues and rollback mechanisms

- The project demonstrates a real-time DevOps CI/CD lifecycle from scratch to production — infrastructure to monitoring.
