# Lesson 6.1: Dependencies and Inter-Resource Connections

## Theory

**Dependencies** in Terraform determine the order in which resources are created, updated, or destroyed. Terraform automatically infers dependencies based on references, but you can also use the `depends_on` argument for explicit control.

**Implicit Dependencies:**
Created when one resource references another (e.g., using an output or attribute).

**Explicit Dependencies:**
Use `depends_on` to force Terraform to create or destroy resources in a specific order.

## Practical Example

**Implicit dependency:**
```hcl
resource "aws_vpc" "main" {
	cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "subnet" {
	vpc_id     = aws_vpc.main.id
	cidr_block = "10.0.1.0/24"
}
```

**Explicit dependency:**
```hcl
resource "null_resource" "example" {
	depends_on = [aws_vpc.main]
}
```

## Real Case Scenario

**Scenario:**
A company needs to ensure a database is created before an application server is deployed.

**Solution:**
They use implicit references and, where needed, `depends_on` to guarantee the correct order.

**Outcome:**
- Reliable, predictable deployments.
- Fewer race conditions and errors.
- Easier troubleshooting and maintenance.

---
