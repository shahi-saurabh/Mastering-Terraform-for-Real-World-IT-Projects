# Lesson 1.2: Introduction to Terraform

## Theory

**What is Terraform?**
Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It allows you to define, provision, and manage infrastructure across multiple cloud providers and services using a declarative configuration language (HCL - HashiCorp Configuration Language).

**Key Concepts:**
- **Providers:** Plugins that allow Terraform to interact with APIs of cloud providers (AWS, Azure, GCP, etc.) and other services.
- **Resources:** The basic building blocks in Terraform, representing infrastructure components (e.g., servers, databases, networks).
- **State:** Terraform keeps track of the infrastructure it manages using a state file, which maps resources in your configuration to real-world objects.
- **Modules:** Reusable groups of resources, allowing you to organize and share code.

**Terraform Workflow:**
1. **Write:** Author your infrastructure as code in `.tf` files.
2. **Plan:** Preview changes Terraform will make to your infrastructure.
3. **Apply:** Execute the planned changes to provision or update resources.
4. **Destroy:** Remove resources managed by Terraform.

## Practical Example

Suppose you want to create an S3 bucket in AWS using Terraform:
```hcl
provider "aws" {
	region = "us-east-1"
}

resource "aws_s3_bucket" "example" {
	bucket = "my-unique-bucket-name-12345"
	acl    = "private"
}
```
Steps:
- Save this code in a file (e.g., `main.tf`).
- Run `terraform init` to initialize the project and download the AWS provider.
- Run `terraform plan` to see what will be created.
- Run `terraform apply` to create the S3 bucket.

## Real Case Scenario

**Scenario:**
A startup needs to quickly deploy and manage cloud resources for multiple projects and environments.

**Solution:**
They use Terraform to define all infrastructure as code. Each project has its own set of Terraform files, and modules are used for common patterns (e.g., VPC, EC2, S3). The state is stored remotely for collaboration.

**Outcome:**
- Rapid, consistent deployments across environments.
- Easy rollback and change tracking.
- Reduced manual errors and improved team productivity.

---
