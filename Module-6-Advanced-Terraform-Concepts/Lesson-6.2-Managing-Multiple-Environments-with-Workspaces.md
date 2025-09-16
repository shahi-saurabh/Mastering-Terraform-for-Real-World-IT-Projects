# Lesson 6.2: Managing Multiple Environments with Workspaces

## Theory

**Workspaces** in Terraform allow you to manage multiple distinct versions of infrastructure from a single configuration. Each workspace has its own state file, making it ideal for managing dev, test, and prod environments.

**Best Practices:**
- Use workspaces for truly parallel environments (not for feature branches).
- Name workspaces clearly (e.g., `dev`, `staging`, `prod`).

## Practical Example

**Create and switch workspaces:**
```bash
terraform workspace new dev
terraform workspace new prod
terraform workspace select dev
terraform apply
```
Each workspace will have its own state and resources.

## Real Case Scenario

**Scenario:**
A SaaS company needs to maintain separate infrastructure for development, staging, and production.

**Solution:**
They use Terraform workspaces to isolate environments, ensuring changes in dev do not affect prod.

**Outcome:**
- Safe, isolated deployments.
- Easier testing and validation.
- Simplified environment management.

---
