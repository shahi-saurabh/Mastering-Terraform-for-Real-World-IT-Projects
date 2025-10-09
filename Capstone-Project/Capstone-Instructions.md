
# Capstone Project Options

Choose one of the following capstone projects to apply your Terraform skills:

## 1. Scalable Web Application Infrastructure (Azure or AWS)
Design and deploy a production-grade, scalable web application infrastructure on Azure or AWS. Include networking, compute, storage, database, and serverless components.

## 2. Multi-Cloud Disaster Recovery Solution
Build a disaster recovery setup using both AWS and Azure. Use Terraform to provision resources in both clouds, configure remote state, and automate failover.

## 3. Automated Data Analytics Pipeline (GCP)
Provision a data pipeline on Google Cloud Platform using Terraform. Include storage buckets, BigQuery datasets, scheduled Cloud Functions, and monitoring resources.

## 4. Secure DevOps Environment
Create a secure DevOps environment with Terraform, including CI/CD pipelines, secrets management, monitoring, and role-based access control for a team.

## 5. Hybrid Cloud Networking
Set up a hybrid cloud network connecting on-premises infrastructure to Azure/AWS using VPNs, subnets, and security groups. Automate the setup and management with Terraform modules.

# Capstone Project: Build a Complete, Scalable Web Application Infrastructure with Azure


## Objective
Apply all learned Terraform concepts to design, build, and deploy a production-grade, scalable infrastructure for your chosen project.

## Theory

This project simulates a real-world scenario where you must provision, secure, and automate a cloud environment for a web application. You will use modules, variables, remote state, CI/CD, and best practices.

## Practical Steps
1. **Set up a VPC (Virtual Network) with subnets, route tables, and security groups.**
2. **Provision Azure VMs (or EC2 if AWS) with autoscaling and load balancing.**
3. **Deploy storage (Azure Blob or S3), a managed database (Azure SQL or RDS), and a serverless function (Azure Functions or Lambda).**
4. **Configure remote state and version control for collaboration.**
5. **Integrate with a CI/CD pipeline for automated deployment.**

## Example Directory Structure
```
capstone/
	main.tf
	variables.tf
	outputs.tf
	modules/
		vnet/
		vm/
		db/
		storage/
		function/
```

## Real Case Scenario

**Scenario:**
A SaaS company needs to launch a new product with high availability, scalability, and security requirements. The team must collaborate, automate deployments, and ensure disaster recovery.

**Solution:**
They use Terraform to define all infrastructure, store state remotely, and automate deployments with CI/CD. Modules are used for each component, and best practices are followed for security and collaboration.

**Outcome:**
- Rapid, reliable product launch
- Easy scaling and updates
- Secure, auditable infrastructure
- Effective team collaboration

---
