# medical-security-config

This repo holds security configuration for Snowflake and AWS required for the Medical Data Platform.

## Snowflake
- Role definitions
- Row-level security (RLS)
- Masking policies for PII

## AWS
- S3 bucket policies (block public access)
- KMS key policies
- IAM role templates for Lambda, Glue, SageMaker, and Snowflake STS access

## Deploying Snowflake security
Run `deploy_snowflake.sh` (requires `snowsql` configured or use Terraform provider)
