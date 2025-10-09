# Lesson 6.1: Dependencies and Inter-Resource Connections

## Theory

**Dependencies** in Terraform determine the order in which resources are created, updated, or destroyed. Terraform automatically infers dependencies based on references, but you can also use the `depends_on` argument for explicit control.

**Implicit Dependencies:**
Created when one resource references another (e.g., using an output or attribute).

**Explicit Dependencies:**
Use `depends_on` to force Terraform to create or destroy resources in a specific order.

# Best Practices for Managing Dependencies
- Prefer implicit dependencies for simplicity and maintainability.
- Use explicit dependencies (`depends_on`) only when necessary, such as with provisioners or external resources.
- Avoid circular dependencies, which can cause errors and unpredictable behavior.
- Regularly review resource references to ensure correct relationships.
- Document complex dependencies in your code for team clarity.

# Troubleshooting Dependency Issues
- If resources are created in the wrong order, check for missing references or incorrect use of `depends_on`.
- Use `terraform graph` to visualize resource relationships and debug issues.
- For failed deployments, review the plan output for dependency-related errors.

# Advanced Concepts
- Terraform's dependency graph is recalculated on every plan and apply, ensuring up-to-date relationships.
- Modules can have dependencies on other modules; use outputs and inputs to connect them.
- Data sources can also create implicit dependencies when their results are used in resource definitions.

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
