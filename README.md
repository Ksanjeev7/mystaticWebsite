# Static Website Deployment with Terraform

## Overview
Automated deployment of a portfolio website to AWS S3 using Terraform.

## Architecture
- AWS S3 for static hosting
- Terraform for infrastructure provisioning.

## What it does
- Creates an S3 bucket (name from `variables.tf`)
- Configures bucket ownership & public-access settings
- Uploads `index.html` and `error.html`
- Configures S3 website hosting.

## Website endpoint
- Example endpoint for this project:
  http://sanjubucket07.s3-website.ap-south-1.amazonaws.com/
- To get the deployed endpoint dynamically after apply:
  ```powershell
  cd C:\TerraformScripts\mystaticWebsite
  terraform output -raw website_endPoint
  ```
  
## Files
- `Main.tf` — resources (bucket, objects, website config, policies)
- `provider.tf` — AWS provider configuration
- `variables.tf` — region & bucket name variables
- `index.html`, `error.html` — site content
- `.gitignore` — excludes `.terraform`, state files, etc.

## Prerequisites
- Terraform 1.x
- AWS CLI configured or environment AWS credentials
- IAM user/role with S3 permissions to create buckets/objects (or adjust policy)

## How to use
1. Edit `variables.tf` (set `bucket_name` and `aws_region`) or set TF_VAR_* env vars.
2. Initialize and validate:
   ```powershell
   terraform init
   terraform validate
   terraform plan
   ```
3. Apply:
   ```powershell
   terraform apply
   ```

## Notes & best practices
- Do not commit AWS credentials or `*.tfstate` files to Git.
- `.terraform/` and provider binaries must be ignored in `.gitignore`.
- If you need a public site in a production environment, prefer CloudFront + Origin Access Control instead of public ACLs/policies.

## Contact
- Connect with me on [LinkedIn](https://www.linkedin.com/in/sanjeevkadagandla/)
