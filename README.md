# Terraform AWS S3 GRC Controls

## Overview

This Terraform project enforces NIST controls SC-28, AC-3, CM-6, and AU-3 on AWS S3. It configures AES-256 encryption at rest, blocks all four public-access paths, enables versioning on the primary bucket, applies standardized tags, and sends access logs to a dedicated logging bucket.

The Terraform plan is exported to `evidence/plan.json` as machine-readable proof that the controls are configured.

## Controls Implemented

- **SC-28:** AES-256 encryption at rest
- **AC-3:** All four S3 public-access block settings enabled
- **CM-6:** Versioning enabled and required tags applied
- **AU-3:** Access logging sent to a dedicated log bucket

## Files

- `main.tf` — AWS resources and security controls
- `variables.tf` — Input variable definitions
- `outputs.tf` — Terraform outputs, including the SC-28 attestation
- `terraform.tfvars.example` — Example configuration values
- `evidence/plan.json` — Machine-readable Terraform plan evidence
- `verify.sh` — Live AWS verification checks after deployment

## How to Verify

Run:

```bash
terraform init
terraform fmt
terraform validate
terraform plan -out=tfplan
terraform show -json tfplan > evidence/plan.json
