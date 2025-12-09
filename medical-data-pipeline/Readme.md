# medical-data-pipeline

## Overview
This repository contains the data ingestion and ETL components of the Medical Data Platform. It pulls public health APIs (WHO, NICD, Africa CDC), lands raw files into AWS S3, runs ETL using AWS Glue, and loads data into Snowflake.

## Architecture
1. API Lambdas (EventBridge scheduled) → S3 raw zone
2. S3 put-event → AWS Glue jobs for bronze → silver transforms
3. Snowflake external stage + COPY INTO → Snowflake raw tables
4. Snowflake Tasks / Stored Procedures → silver/gold tables

> Security: S3 encryption (SSE-KMS), IAM least privilege, and Snowflake RBAC & masking rules.

## Repos & Responsibilities
- `medical-ml-platform` (ML training & deployment)
- `medical-security-config` (Snowflake RBAC, masking, AWS IAM/KMS policies)

## How to use (developer flow)
1. Clone repo
2. Create Python venv and install requirements
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r lambda_functions/requirements.txt
