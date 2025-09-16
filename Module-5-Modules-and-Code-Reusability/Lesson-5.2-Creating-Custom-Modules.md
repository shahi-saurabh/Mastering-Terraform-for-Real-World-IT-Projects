# Lesson 5.2: Creating Custom Modules

## Theory

**Custom Modules** allow you to encapsulate and reuse infrastructure code. A module typically consists of `main.tf`, `variables.tf`, and `outputs.tf` files. Modules accept input variables and return outputs.

**Best Practices:**
- Use clear input/output variables
- Document module usage
- Keep modules focused and composable

## Practical Example

**Create a custom EC2 module:**
1. In `modules/ec2/main.tf`:
```hcl
resource "aws_instance" "this" {
	ami           = var.ami
	instance_type = var.instance_type
}
```
2. In `modules/ec2/variables.tf`:
```hcl
variable "ami" {}
variable "instance_type" {}
```
3. In `modules/ec2/outputs.tf`:
```hcl
output "instance_id" {
	value = aws_instance.this.id
}
```
4. Use the module in your root config:
```hcl
module "web" {
	source        = "./modules/ec2"
	ami           = "ami-0c55b159cbfafe1f0"
	instance_type = "t2.micro"
}
```

## Real Case Scenario

**Scenario:**
An enterprise wants to standardize EC2 instance creation across teams.

**Solution:**
They build a custom EC2 module with required variables and outputs, and share it across all projects.

**Outcome:**
- Consistent, secure EC2 deployments.
- Simplified code reviews and audits.
- Faster onboarding for new teams.

---
