# Lesson 4.2: Locals and Constants

## Theory

**Locals** in Terraform are named values that you can use to simplify expressions and avoid repetition. They are evaluated within the module and cannot be set from outside.

**Use Cases:**
- Calculating derived values
- Simplifying complex expressions
- Centralizing constants

## Practical Example

**Define and use locals:**
```hcl
locals {
	environment = "production"
	instance_count = 3
}

resource "aws_instance" "web" {
	count         = local.instance_count
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
	tags = {
		Environment = local.environment
	}
}
```

## Real Case Scenario

**Scenario:**
A SaaS provider needs to tag all resources with a consistent environment label and calculate resource counts based on business logic.

**Solution:**
They use locals to centralize environment names and compute values, reducing duplication and errors.

**Outcome:**
- Cleaner, more maintainable code.
- Easier updates to environment-wide settings.
- Fewer mistakes from hardcoded values.

---
