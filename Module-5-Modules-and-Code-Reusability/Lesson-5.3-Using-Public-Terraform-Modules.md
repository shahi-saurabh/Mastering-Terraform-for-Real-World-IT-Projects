# Lesson 5.3: Using Public Terraform Modules

## Theory

**Public Modules** are reusable modules published on the Terraform Registry or other sources. They help you avoid reinventing the wheel for common infrastructure patterns.

**Finding Modules:**
- Use the [Terraform Registry](https://registry.terraform.io/) to search for modules by provider and resource type.

**Implementing Modules:**
- Reference the module source and required variables in your configuration.

## Practical Example

**Use a public VPC module:**
```hcl
module "vpc" {
	source  = "terraform-aws-modules/vpc/aws"
	version = "4.0.2"
	name    = "my-vpc"
	cidr    = "10.0.0.0/16"
	azs     = ["us-east-1a", "us-east-1b"]
	public_subnets  = ["10.0.1.0/24", "10.0.2.0/24"]
}
```

## Real Case Scenario

**Scenario:**
A startup needs to quickly deploy a production-ready VPC with best practices.

**Solution:**
They use the official AWS VPC module from the Terraform Registry, customizing only the required variables.

**Outcome:**
- Rapid, secure infrastructure deployment.
- Leverage community best practices.
- Focus on business logic instead of boilerplate code.

---
