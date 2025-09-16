# Lesson 4.1: Using Variables

## Theory

**Variables** in Terraform allow you to parameterize your configuration, making it reusable and flexible. Variables can have types, default values, and validation rules.

**Types:**
- string, number, bool, list, map, object

**Validation:**
You can add custom validation rules to variables for stricter input control.

**tfvars Files:**
Variable values can be set in `.tfvars` files, environment variables, or via the CLI.

## Practical Example

**Define and use variables:**
```hcl
variable "instance_type" {
	description = "EC2 instance type"
	type        = string
	default     = "t2.micro"
}

resource "aws_instance" "web" {
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = var.instance_type
}
```

**Use a tfvars file:**
`terraform.tfvars`:
```hcl
instance_type = "t3.micro"
```

## Real Case Scenario

**Scenario:**
A consulting company needs to deploy the same infrastructure for multiple clients, each with different requirements.

**Solution:**
They use variables and tfvars files to customize deployments for each client without changing the core code.

**Outcome:**
- Highly reusable and flexible codebase.
- Faster, error-free deployments for new clients.
- Simplified maintenance and updates.

---
