# Lesson 1.4: Basic Terraform Configuration

## Theory

Terraform configurations are written in HCL (HashiCorp Configuration Language) and typically organized into files like `main.tf`, `variables.tf`, and `outputs.tf`. The core of any configuration is the provider and resource blocks.

**Providers:** Define which cloud or service Terraform will interact with (e.g., AWS, Azure, GCP).

**Resources:** Represent the infrastructure components you want to create (e.g., EC2 instance, S3 bucket).

**Terraform Init:** The `terraform init` command initializes the working directory, downloads providers, and prepares the environment for use.

## Practical Example

**Write a simple Terraform script to launch an AWS EC2 instance:**
```hcl
provider "aws" {
	region = "us-east-1"
}

resource "aws_instance" "web" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}
```

**Steps:**
1. Save the above code in `main.tf`.
2. Run `terraform init` to initialize the project.
3. Run `terraform plan` to preview changes.
4. Run `terraform apply` to create the EC2 instance.

## Real Case Scenario

**Scenario:**
A consulting firm needs to quickly spin up demo environments for clients on AWS.

**Solution:**
They use basic Terraform scripts for each demo, allowing them to provision and destroy environments with a few commands. This saves time and ensures consistency across demos.

**Outcome:**
- Rapid, repeatable environment creation.
- Reduced manual setup errors.
- Easy cleanup after demos using `terraform destroy`.

---
