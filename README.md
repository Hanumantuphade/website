# 🚀 Automated CI/CD Pipeline on AWS Using GitHub, Docker & ECS Fargate

A hands-on DevOps project demonstrating how to automate application build and deployment using **GitHub, AWS CodePipeline, AWS CodeBuild, Amazon ECR, and Amazon ECS Fargate**.

The project integrates source code management, Docker containerization, container image storage, and deployment to AWS. Application traffic is routed through Amazon Route 53 and an internet-facing Application Load Balancer (ALB).

## 🏗️ Architecture Diagram

![Automated CI/CD Pipeline on AWS](architecture.png)

**AWS Region:** Asia Pacific (Mumbai) — `ap-south-1`

> To display this diagram, upload your architecture image to the repository root and name it `architecture.png`.

## 📌 Project Overview

This project demonstrates an automated CI/CD workflow for deploying a containerized website on AWS.

When application code is pushed to the configured GitHub repository branch, AWS CodePipeline orchestrates the deployment workflow. AWS CodeBuild builds the Docker image, Amazon ECR stores the container image, and Amazon ECS Fargate runs the application containers.

An Application Load Balancer distributes incoming application traffic to the ECS service, while Amazon CloudWatch Logs provides container log visibility.

## 🛠️ Technologies & AWS Services

| Technology / Service | Purpose |
|---|---|
| GitHub | Source code management and change tracking |
| AWS CodePipeline | CI/CD workflow orchestration |
| AWS CodeBuild | Docker image build and build artifact generation |
| Docker | Application containerization |
| Amazon ECR | Private Docker image registry |
| Amazon ECS | Container orchestration |
| AWS Fargate | Serverless container compute |
| Amazon VPC | Network isolation and subnet organization |
| Application Load Balancer | Routes application traffic to targets |
| Amazon Route 53 | DNS resolution for the application |
| Amazon CloudWatch Logs | Container log collection and troubleshooting |
| Amazon EC2 | Helper/build host for initial manual Docker and ECR setup |

## 🔄 CI/CD Workflow

### 1. Source Code Management — GitHub

The website source code is maintained in GitHub. A push to the configured branch triggers the CI/CD pipeline.

Repository: [Hanumantuphade/website](https://github.com/Hanumantuphade/website)

### 2. Pipeline Orchestration — AWS CodePipeline

AWS CodePipeline coordinates the source, build, and deployment stages, providing visibility into the pipeline execution status.

### 3. Container Image Build — AWS CodeBuild

AWS CodeBuild uses the project's `buildspec.yml` to execute the Docker build workflow and prepare the image definition required for deployment.

### 4. Container Image Registry — Amazon ECR

The Docker image is stored in a private Amazon Elastic Container Registry repository so that ECS can retrieve the image for deployment.

### 5. Container Deployment — Amazon ECS Fargate

Amazon ECS manages the application service and task definitions. AWS Fargate provides compute capacity for running the containers without requiring you to manage the underlying container host instances.

### 6. Application Traffic — Route 53 and Application Load Balancer

Amazon Route 53 resolves the application domain to the Application Load Balancer. The internet-facing ALB forwards incoming requests to the configured target group for the application running on ECS.

### 7. Monitoring — Amazon CloudWatch Logs

CloudWatch Logs provides access to container logs to help troubleshoot application startup, runtime issues, and deployment behavior.

## 🌐 AWS Networking Architecture

The application infrastructure is organized within an AWS VPC across two Availability Zones in the Mumbai region.

- **Public subnets:** Host the internet-facing Application Load Balancer.
- **Private subnets:** Intended for the ECS Fargate tasks, as shown in the architecture.
- **Application Load Balancer:** Provides the entry point for incoming application traffic.
- **Target group:** Routes traffic to the configured application targets.
- **ECS service:** Maintains the desired number of application tasks.

Actual subnet routing, security group rules, and task networking depend on the deployed AWS configuration.

## 📂 Repository Contents

The repository includes website source files and container/deployment configuration.

```text
website/
├── css/
├── fonts/
├── images/
├── js/
├── Dockerfile
├── buildspec.yml
├── cloudbuild.yaml
├── k8s.yaml
├── index.html
├── about.html
├── contact.html
├── guard.html
└── service.html
```

The repository also contains other website pages and supporting assets.

- `Dockerfile` — Defines the container image build instructions.
- `buildspec.yml` — Defines the AWS CodeBuild build workflow.
- `k8s.yaml` — Contains Kubernetes configuration.
- `cloudbuild.yaml` — Contains a Cloud Build configuration.

These additional configuration files are included in the repository; they are not necessarily part of the AWS ECS deployment path described above.

## 🎯 Key Learning Outcomes

Through this hands-on project, I gained practical exposure to:

- Designing a CI/CD workflow using AWS developer tools.
- Integrating GitHub with AWS deployment services.
- Building Docker images using AWS CodeBuild.
- Managing container images with Amazon ECR.
- Deploying containerized applications with Amazon ECS Fargate.
- Understanding VPCs, Availability Zones, and public/private subnet architecture.
- Routing application traffic through Route 53 and an Application Load Balancer.
- Using CloudWatch Logs for container troubleshooting.
- Understanding the difference between automated pipeline stages and initial manual setup tasks.

## 🔐 Security Considerations

For a secure deployment, review the following:

- Use IAM roles with least-privilege permissions for CodePipeline, CodeBuild, and ECS.
- Keep ECS tasks in private subnets where appropriate.
- Restrict security group rules to the required traffic paths.
- Store credentials and secrets securely rather than committing them to GitHub.
- Use HTTPS for public application traffic.
- Review ECR image scanning and image lifecycle policies.
- Configure suitable CloudWatch log retention.

These are recommended security practices and should not be interpreted as claims that every item is already enabled in this project.

## 🚀 Future Enhancements

Potential improvements include:

- Infrastructure provisioning using Terraform.
- Automated testing and quality checks before deployment.
- Image tagging based on Git commit IDs.
- ECS deployment health checks and rollback configuration.
- Container vulnerability scanning.
- Improved IAM permissions and secret management.
- Pipeline notifications and enhanced monitoring.

## 👨‍💻 Author

**Hanumant Uphade**

Aspiring Cloud & DevOps Engineer | AWS | Docker | Terraform | CI/CD

- GitHub: [Hanumantuphade](https://github.com/Hanumantuphade)
- Project Repository: [Automated CI/CD Pipeline — Website](https://github.com/Hanumantuphade/website)


**Tags:** `AWS` `DevOps` `Docker` `ECS` `Fargate` `CodePipeline` `CodeBuild` `CI/CD` `CloudComputing`
