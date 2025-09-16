# Lesson 7.2: Automating Terraform with CI/CD Tools

## Theory

**Automation** in CI/CD pipelines ensures Terraform commands (plan, apply, destroy) are executed consistently and securely. Secrets and credentials must be managed carefully to avoid leaks.

**Managing Secrets:**
- Use environment variables, secret managers, or CI/CD tool integrations to store sensitive data.

**Typical Pipeline Steps:**
1. Checkout code
2. Set up Terraform
3. Authenticate to cloud provider
4. Run `terraform init`, `plan`, and `apply`

## Practical Example

**GitLab CI pipeline for Terraform:**
```yaml
stages:
	- validate
	- plan
	- apply

validate:
	script:
		- terraform init
		- terraform validate

plan:
	script:
		- terraform plan

apply:
	script:
		- terraform apply -auto-approve
	when: manual
```

## Real Case Scenario

**Scenario:**
A healthcare company must ensure all infrastructure changes are reviewed and approved before deployment.

**Solution:**
They use GitLab CI to automate Terraform, with manual approval required for `apply` jobs and secrets stored in GitLab's secret manager.

**Outcome:**
- Secure, auditable deployments.
- Reduced risk of unauthorized changes.
- Compliance with industry regulations.

---
