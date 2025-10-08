
# Assignments

Each module includes assignments that progress from beginner to advanced. Complete the tasks and submit your solutions for feedback or peer review.

## Assignment Template

**Module:**
**Lesson:**
**Objective:**

### Task
- Describe the task or problem to solve.

### Submission
- Provide your Terraform code or answers below.

---

## Beginner to Advanced Assignments

### Module 1: Introduction to IaC and Terraform
**Beginner:**
- Write a Terraform configuration to launch a t2.micro EC2 instance in AWS us-east-1. Use variables for the AMI and instance type.
**Intermediate:**
- Add tags to your EC2 instance and output the instance ID after creation.
**Advanced:**
- Configure remote state storage using an S3 backend for your Terraform project.

### Module 2: Working with Providers and Resources
**Beginner:**
- Configure a provider for AWS and create a basic resource (e.g., S3 bucket).
**Intermediate:**
- Add version constraints to your provider and enable versioning on the S3 bucket.
**Advanced:**
- Create multiple resources (EC2, S3, IAM) and manage dependencies between them.

### Module 3: Managing State and Outputs
**Beginner:**
- Use Terraform outputs to display resource attributes after apply.
**Intermediate:**
- Reference data sources to fetch existing AWS resources.
**Advanced:**
- Implement remote state locking and state file encryption.

### Module 4: Variables and Dynamic Configuration
**Beginner:**
- Use input variables to parameterize your configuration.
**Intermediate:**
- Use local values and constants to simplify expressions.
**Advanced:**
- Implement dynamic blocks to create multiple similar resources.

### Module 5: Modules and Code Reusability
**Beginner:**
- Use a public Terraform module to deploy an AWS VPC.
**Intermediate:**
- Create a custom module for EC2 deployment and use it in your configuration.
**Advanced:**
- Refactor your infrastructure using multiple custom modules and manage module versions.

### Module 6: Advanced Terraform Concepts
**Beginner:**
- Use resource dependencies to control creation order.
**Intermediate:**
- Manage multiple environments using Terraform workspaces.
**Advanced:**
- Use provisioners to run scripts on your resources after creation.

### Module 7: Terraform with CI/CD Pipelines
**Beginner:**
- Version control your Terraform code using Git.
**Intermediate:**
- Set up a basic CI pipeline to lint and validate Terraform code.
**Advanced:**
- Automate Terraform plan and apply using a CI/CD tool (e.g., GitHub Actions).

### Module 8: Troubleshooting and Best Practices
**Beginner:**
- Debug a simple syntax error in a Terraform script.
**Intermediate:**
- Identify and fix resource drift using Terraform commands.
**Advanced:**
- Implement best practices for team collaboration and code reviews in Terraform projects.
---
