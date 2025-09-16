# Assignments

Each module includes an assignment to reinforce your learning. Complete the tasks and submit your solutions for feedback or peer review.

## Assignment Template

**Module:**
**Lesson:**
**Objective:**

### Task
- Describe the task or problem to solve.

### Submission
- Provide your Terraform code or answers below.

---

## Example Assignment (Module 1)

**Module:** 1 - Introduction to IaC and Terraform
**Lesson:** 1.4 - Basic Terraform Configuration
**Objective:** Write and apply a basic Terraform script.

### Task
Write a Terraform configuration to launch a t2.micro EC2 instance in AWS us-east-1. Use variables for the AMI and instance type.

### Submission
```hcl
variable "ami" {}
variable "instance_type" { default = "t2.micro" }

provider "aws" {
	region = "us-east-1"
}

resource "aws_instance" "example" {
	ami           = var.ami
	instance_type = var.instance_type
}
```
---
