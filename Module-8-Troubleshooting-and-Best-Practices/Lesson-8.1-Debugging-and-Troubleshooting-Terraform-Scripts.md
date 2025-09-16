# Lesson 8.1: Debugging and Troubleshooting Terraform Scripts

## Theory

**Debugging** in Terraform involves identifying and resolving errors in configuration files or during execution. Common issues include syntax errors, provider authentication failures, and resource conflicts.

**Debugging Tools:**
- `terraform plan` and `terraform apply` output
- `terraform validate` for syntax checking
- `TF_LOG` environment variable for detailed logs

**Common Errors:**
- Incorrect resource references
- Provider authentication issues
- State file conflicts

## Practical Example

**Enable debug logging:**
```bash
export TF_LOG=DEBUG
terraform apply
```

**Validate configuration:**
```bash
terraform validate
```

## Real Case Scenario

**Scenario:**
A team encounters intermittent errors when applying changes to production infrastructure.

**Solution:**
They enable debug logging and use `terraform plan` to identify dependency issues, then fix resource references and re-apply.

**Outcome:**
- Faster troubleshooting and resolution.
- Fewer production outages.
- Improved team confidence in Terraform workflows.

---
