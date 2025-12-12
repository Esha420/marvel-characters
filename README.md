# End-to-End MLOps Pipeline with Databricks — Marvel Characters Project

This repository provides a complete, production-ready **MLOps pipeline** built on **Databricks Lakehouse**, including data ingestion, feature engineering, model training, model deployment, CI/CD, monitoring, and automation.

The project uses:
- **Databricks Workflows**
- **Databricks Model Serving**
- **uv (Python package manager)**
- **Databricks Bundles**
- **GitHub Actions for CI/CD**

---

## 🚀 Project Overview

This project trains and deploys a classification model to predict attributes of Marvel characters based on structured features such as identity, gender, universe, origin, etc.

The full MLOps flow includes:

- Reproducible environment setup with **uv**
- Managed storage using **Unity Catalog**
- Model training & evaluation
- Model registration in **MLflow Model Registry**
- Deployment to **Databricks Model Serving**
- Drift detection & monitoring
- Automated CI/CD deployment via GitHub Actions

---

## 📦 1. Clone the Repository

```bash
git clone https://github.com/Esha420/marvel-characters.git
cd marvel-characters
```

## 2. Install uv (if not installed)
Install uv:
```
pip install uv
```
Set up project environment:
```
uv sync --extra dev
```
This:
* Creates a virtual environment
* Installs all dependencies
* Generates a lockfile for reproducibility

## 3. Create a Databricks Account

If you don’t have a Databricks workspace yet, create one using the Databricks Free Trial:

 https://www.databricks.com/try-databricks

You will receive a workspace URL like:
```
https://dbc-1cfe64a4-0242.cloud.databricks.com/
```
## 4. Configure Databricks Authentication
Update databricks.yml

Replace the host value with your Databricks host URL.

## Create .env File

Inside the project root, create a .env file containing:
```
PROFILE=<your databricks CLI profile name>
DBR_TOKEN=<your personal access token>
DBR_HOST=<your workspace host (no https://)>
```
## Configure .databrickscfg

Install Databricks CLI extension:
```databricks auth login
```
## 5. Running the Pipeline Notebooks

You can run the notebooks individually to test each pipeline stage.
```
/notebooks/*
```
## 6. Run the Full MLOps Pipeline (Databricks Bundle)
Validate the bundle:
```
databricks bundle validate
```
Deploy the entire pipeline:
```
databricks bundle deploy
```
This will:
* Execute all pipeline tasks
* Register and log the model
* Deploy to model serving
* Configure monitoring workflows

What This Repo Contains
* src/marvel_characters/ — Model & pipeline source code
* notebooks/ — Development notebooks
* databricks.yml — Databricks bundle definition
* .github/workflows/ — CI/CD pipelines
* project_config_marvel.yml — Environment-specific configuration
* mlops/ — Monitoring, drift detection, workflows
