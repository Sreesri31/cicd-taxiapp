Taxi Booking CI/CD Pipeline & Kubernetes Deployment

Overview
This project demonstrates a complete CI/CD pipeline implementation for a Taxi Booking Application using modern DevOps tools and cloud technologies:

Code analysis & quality checks with SonarCloud

Artifact management & Docker registry with JFrog Artifactory

Continuous Integration & Delivery using Jenkins pipelines

Containerization with Docker

Infrastructure as Code with Terraform to provision AWS EKS Kubernetes Cluster

Application Deployment on Kubernetes with Helm charts

Monitoring using Prometheus & Grafana on Kubernetes

Project Roadmap / Steps Completed
1. Code Quality Analysis with SonarCloud
Created SonarCloud organization and project linked to GitHub repo

Integrated SonarCloud token with Jenkins credentials

Added SonarQube analysis stage in Jenkins pipeline for automated static code analysis

2. Artifact Management with JFrog Artifactory
Created Maven and Docker repositories in JFrog Cloud

Generated scoped access token for Jenkins integration

Configured Jenkins to publish JAR artifacts to Artifactory

3. Docker Image Build and Publish
Created Dockerfile for Taxi Booking app based on Tomcat image

Jenkins pipeline stages added for Docker image build and push to JFrog Docker repo

Verified image availability in Artifactory and deployed locally on build slave

4. Kubernetes Cluster Provisioning with Terraform
Created Terraform modules for EKS cluster and security groups

Applied Terraform to provision fully managed EKS cluster on AWS

Verified cluster and node groups on AWS Console

5. Build Slave Configuration
Installed AWS CLI, kubectl, helm on Jenkins build slave

Configured AWS credentials and kubeconfig for cluster access

6. Kubernetes Deployment with Helm
Created Helm chart for taxiapp deployment (namespace, deployment, service, secrets)

Deployed the application on EKS using Helm

Verified Kubernetes resources and accessed app via LoadBalancer DNS

7. Monitoring Setup with Prometheus & Grafana
Installed kube-prometheus-stack Helm chart in monitoring namespace

Accessed Grafana dashboard with default credentials

Edited services from LoadBalancer to ClusterIP for security

8. Pipeline Automation for Deployment
Added deploy stage in Jenkins pipeline to run deployment scripts

Automated full CI/CD from code commit to deployment on Kubernetes

9. Cleanup & Destroy Infrastructure
Provided terraform destroy commands to clean up resources after project completion

How to Use / Run
Clone this repository

Configure Jenkins with necessary credentials (SonarCloud token, JFrog credentials)

Push your code to trigger the Jenkins pipeline

Terraform scripts will provision EKS cluster and required resources

Jenkins pipeline will build, analyze, publish artifacts and deploy on Kubernetes

Access the application via the Kubernetes LoadBalancer URL

Monitor the application health with Prometheus and Grafana dashboards

Tools & Technologies
Category	Tools Used
Source Code Analysis	SonarCloud
CI/CD	Jenkins
Artifact Repository	JFrog Artifactory
Containerization	Docker
Infrastructure as Code	Terraform
Cloud Platform	AWS (EKS, VPC, IAM, etc.)
Kubernetes Package Manager	Helm
Monitoring	Prometheus, Grafana
+-----------------------+
|   Developer           |
| - Code Push to GitHub |
+----------+------------+
           |
           v
+-----------------------+
|   GitHub Repository   |
+----------+------------+
           |
           v
+-----------------------------+
|   Jenkins CI/CD Pipeline    |
|-----------------------------|
| 1. Checkout Code            |
| 2. Build & Unit Tests       |
| 3. SonarCloud Code Analysis |
| 4. Package Jar Artifact     |
| 5. Publish Jar to JFrog     |
| 6. Docker Build & Publish   |
| 7. Deploy to Kubernetes     |
+-----------------------------+
           |
           v
+-----------------------+             +---------------------+
|  JFrog Artifactory    |<------------|   Jenkins            |
| - Maven Artifacts     |             | - Artifactory Plugin |
| - Docker Registry     |             +---------------------+
+-----------------------+
           |
           v
+-------------------------+
| Kubernetes EKS Cluster  |
| - Deployed Taxi App     |
| - Managed via Helm      |
+-------------------------+
           |
           v
+-----------------------+
| Monitoring & Alerts   |
| - Prometheus          |
| - Grafana             |
| - Running on EKS      |
+-----------------------+
           |
           v
+-----------------------+
| Terraform Infrastructure |
| - AWS EKS Cluster       |
| - Security Groups       |
| - Networking (VPC/Subnets)|
+-----------------------+


Additional Notes
Make sure to add Jenkins credentials for SonarCloud and JFrog tokens

Use Terraform to manage the infrastructure lifecycle

Adjust Docker image names and versions according to your JFrog URLs

Helm charts are customizable for different environments

Clean up resources with terraform destroy after finishing the project

Project Status
✅ Complete and fully automated CI/CD pipeline with Kubernetes deployment and monitoring setup.
