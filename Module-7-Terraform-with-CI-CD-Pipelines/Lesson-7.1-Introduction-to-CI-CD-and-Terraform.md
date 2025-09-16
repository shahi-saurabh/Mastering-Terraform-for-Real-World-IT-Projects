# Lesson 7.1: Introduction to CI/CD and Terraform

## Theory

**CI/CD (Continuous Integration/Continuous Deployment)** automates the process of testing, building, and deploying code. Integrating Terraform with CI/CD ensures infrastructure changes are tested, reviewed, and deployed automatically.

**Why Integrate Terraform with CI/CD?**
- Automated, repeatable deployments
- Reduced manual errors
- Improved collaboration and review

**Popular CI/CD Tools:**
- Jenkins
- GitLab CI
- GitHub Actions

## Practical Example

**Basic GitHub Actions workflow for Terraform:**
```yaml
name: Terraform
on:
	push:
		branches: [ main ]
jobs:
	terraform:
		runs-on: ubuntu-latest
		steps:
			- uses: actions/checkout@v2
			- name: Set up Terraform
				uses: hashicorp/setup-terraform@v2
			- name: Terraform Init
				run: terraform init
			- name: Terraform Plan
				run: terraform plan
			- name: Terraform Apply
				run: terraform apply -auto-approve
```

## Real Case Scenario

**Scenario:**
A fintech company wants to automate infrastructure deployment and ensure all changes are reviewed.

**Solution:**
They use GitHub Actions to run Terraform plan and apply on every pull request and merge, with required approvals.

**Outcome:**
- Faster, safer deployments.
- Full audit trail of changes.
- Improved team collaboration.

---
