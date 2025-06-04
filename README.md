# Infrastructure as Code (IaC) with Terraform & AWS

## Overview
This project provisions a secure AWS environment using Terraform, focused on least privilege and secure defaults.

## Stack
- AWS (Free Tier)
- Terraform
- GitHub Actions (CI/CD)

## Resources
- VPC
- EC2 Instance
- S3 Bucket (encrypted)
- IAM Role
- Security Groups

## CI/CD
Deployments are automated via GitHub Actions on each `main` branch push.

## Setup

1. Clone the repo
2. Configure AWS credentials
3. Run:
```bash
cd terraform
terraform init
terraform apply
```

## GitHub Actions Secrets Required
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
