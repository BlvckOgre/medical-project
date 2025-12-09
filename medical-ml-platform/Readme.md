# medical-ml-platform

## Overview
This repository contains code for model training, feature engineering, SageMaker Pipelines, and model deployment for TB and other disease forecasts.

## Architecture
- Data source: Snowflake gold training dataset
- Preprocessing & FE: `preprocess.py`, `feature_engineering.py`
- Training: `train.py` (scikit-learn / XGBoost)
- CI/CD: GitHub Actions triggers SageMaker Pipeline or builds Docker image for training

## Run locally (dev)
1. Setup venv and install requirements
2. Use `snowflake-connector-python` to pull gold dataset
3. Test training locally with `python training/train.py --local`

## SageMaker CI/CD (example)
- `sagemaker-pipeline.yml` will start a pipeline run when `main` updates
- Uses GitHub Actions + AWS credentials in secrets

## Model governance
- All experiments logged to SageMaker Experiments
- Model metadata (version, dataset snapshot, metrics) stored in `model_registry` table (Snowflake or SageMaker Model Registry)

## Retraining schedule
- EventBridge triggers retrain monthly (can be configured)
