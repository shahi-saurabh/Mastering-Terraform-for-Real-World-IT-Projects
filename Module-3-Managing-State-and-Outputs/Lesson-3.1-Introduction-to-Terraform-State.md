# Lesson 3.1: Introduction to Terraform State

## Theory

**What is Terraform State?**
Terraform state is a file that maps your configuration to the real infrastructure resources. It keeps track of resource metadata and attributes, enabling Terraform to manage and update your infrastructure efficiently.

**Local vs Remote State:**
- **Local State:** Stored on your local machine as `terraform.tfstate`.
- **Remote State:** Stored in a remote backend (e.g., S3, Azure Storage) for collaboration and security.

**Benefits and Drawbacks:**
- **Benefits:** Enables tracking, collaboration, and automation.
- **Drawbacks:** Sensitive data may be stored in state; must be protected and managed carefully.

## Practical Example

**Local state file creation:**
1. Run `terraform apply` on a new project.
2. Terraform creates `terraform.tfstate` in your working directory.
3. This file contains the current state of your infrastructure.

**Inspect state:**
```bash
terraform show
terraform state list
```

## Real Case Scenario

**Scenario:**
A team is working on a shared infrastructure project. Using local state leads to conflicts and lost changes.

**Solution:**
They migrate to remote state in AWS S3 with state locking enabled, allowing safe collaboration and preventing simultaneous changes.

**Outcome:**
- Improved team collaboration.
- Reduced risk of state file corruption.
- Enhanced security and auditability.

---
