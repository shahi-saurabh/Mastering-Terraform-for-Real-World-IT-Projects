# Lesson 4.3: Dynamic Blocks

## Theory

**Dynamic Blocks** in Terraform allow you to generate repeatable nested blocks within resources, based on variable input or complex logic. This is useful for resources that require a variable number of sub-blocks (e.g., security group rules).

**Conditional Resource Creation:**
You can use `count` or `for_each` to conditionally create resources or blocks.

## Practical Example

**Dynamic block for security group rules:**
```hcl
variable "ingress_ports" {
	type    = list(number)
	default = [80, 443]
}

resource "aws_security_group" "web" {
	name        = "web-sg"
	description = "Allow web traffic"

	dynamic "ingress" {
		for_each = var.ingress_ports
		content {
			from_port   = ingress.value
			to_port     = ingress.value
			protocol    = "tcp"
			cidr_blocks = ["0.0.0.0/0"]
		}
	}
}
```

## Real Case Scenario

**Scenario:**
An enterprise needs to manage security groups with a variable set of allowed ports for different environments.

**Solution:**
They use dynamic blocks and variables to generate the correct rules for each environment, reducing code duplication and manual errors.

**Outcome:**
- Highly flexible and DRY (Don't Repeat Yourself) code.
- Easy updates for new requirements.
- Consistent security group management across environments.

---
