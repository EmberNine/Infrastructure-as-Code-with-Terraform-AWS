#  Secure Terraform AWS Infrastructure

This project provisions a secure, production-ready AWS environment using Terraform with a remote S3 backend, DynamoDB state locking, IAM least privilege, and GitHub Actions CI/CD.

---

##  Features

- **VPC** with public/private subnets
- **EC2 instance** (Amazon Linux 2 or 2023)
- **IAM roles** with least-privilege security
- **Encrypted S3 bucket** for remote Terraform state
- **DynamoDB** table for state locking
- **Secure defaults** (no public S3, locked-down SG)
- **GitHub Actions pipeline** for CI/CD
- **CloudTrail / GuardDuty / AWS Config** (optional)

---

## Folder Structure

```
terraform/
├── backend.tf               # Remote S3 backend
├── main.tf                  # VPC, EC2, SG, IAM
├── outputs.tf               # Outputs (e.g., EC2 IP)
├── providers.tf             # AWS provider setup
├── security.tf              # Security groups
├── variables.tf             # Input vars
├── terraform.tfvars.example# Safe example vars
.github/
└── workflows/
    └── terraform.yml        # GitHub Actions CI/CD
```

---

## Prerequisites

- Terraform CLI
- AWS CLI configured (or GitHub Secrets set)
- AWS Free Tier account
- S3 bucket & DynamoDB table for remote state

---

##  Setup

1. Clone the repo
2. Copy `terraform.tfvars.example` → `terraform.tfvars`
3. Run:
```bash
terraform init
terraform apply
```

---

##  GitHub Secrets Required

For CI/CD via GitHub Actions:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

---

## Remote State Config

State is stored in:
- S3 bucket: `terraform-state-armando`
- DynamoDB table: `terraform-locks`

---

##  .gitignore

See `.gitignore` to prevent committing:
- Terraform state
- Local `.terraform` cache
- Private SSH keys

---

##  Next Steps

- Add Checkov or tfsec for security scanning
- Promote to multiple environments (dev/stage/prod)
- Add auto-tagging or cost allocation tags
- Export CloudTrail logs to encrypted S3
