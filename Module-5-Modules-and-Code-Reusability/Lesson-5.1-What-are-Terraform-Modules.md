# Lesson 5.1: What are Terraform Modules?

## Theory

**Modules** are containers for multiple resources that are used together. A module can be local (within your repo) or remote (from the Terraform Registry or a Git repo). Modules enable code reuse, organization, and sharing.

**Benefits:**
- DRY (Don't Repeat Yourself) principle
- Easier maintenance and updates
- Standardization across projects

## Practical Example

**Create and use a local module:**
1. Create a folder `modules/vpc` with a `main.tf` that defines a VPC resource.
2. In your root configuration:
```hcl
module "vpc" {
	source = "./modules/vpc"
	cidr_block = "10.0.0.0/16"
}
```

## Real Case Scenario

**Scenario:**
A cloud consultancy manages dozens of client projects, each needing a similar VPC setup.

**Solution:**
They create a reusable VPC module and use it in all client projects, customizing only the input variables.

**Outcome:**
- Faster project delivery.
- Fewer errors and inconsistencies.
- Easier updates and bug fixes across all clients.

---
