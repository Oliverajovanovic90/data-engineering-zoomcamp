# data-engineering-zoomcamp
Practice work from the Data Engineering Zoomcamp, covering GCP, Docker, Terraform, workflow orchestration, data ingestion, BigQuery, dbt, Spark, and Kafka.

# ⭐ Docker, Postgres, Terraform, GCP 
Foundation of the entire data engineering stack.  
The focus is on containerization, running databases in Docker, interacting with Postgres, and provisioning cloud infrastructure using Terraform.

## 🚀 1. Environment Overview

Cloud & Architecture

Docker fundamentals

Running Postgres in Docker

Ingesting NYC Taxi data

Terraform (Infrastructure as Code)

GCP VM setup & configuration

## 🐳 2. Docker + Postgres
✔️ Run Postgres & pgAdmin using Docker Compose
## docker-compose.yml
services:
  pgdatabase:
    image: postgres:13
    environment:
      - POSTGRES_USER=root
      - POSTGRES_PASSWORD=root
      - POSTGRES_DB=ny_taxi
    ports:
      - "5432:5432"

  pgadmin:
    image: dpage/pgadmin4
    environment:
      - PGADMIN_DEFAULT_EMAIL=admin@admin.com
      - PGADMIN_DEFAULT_PASSWORD=root
    ports:
      - "8080:80"


Run:

docker compose up -d
docker ps

✔️ Ingest NY Taxi CSV into Postgres

Converted from notebook → Python script → Docker image.

python ingest_data.py \
  --user=root \
  --password=root \
  --host=localhost \
  --port=5432 \
  --db=ny_taxi \
  --table_name=yellow_taxi_data \
  --url=<csv_url>

✔️ Connected to DB using pgcli
pgcli -h localhost -u root -d ny_taxi

## ☁️ 3. Google Cloud Platform (GCP)

Created:

A Compute Engine VM (Ubuntu 22.04, SSH access)

Installed:

Anaconda

Docker

Docker Compose

pgcli

Terraform

Connected via VS Code Remote SSH

SSH:

ssh de-zoomcamp

## 🛠️ 4. Terraform on GCP
✔️ Provider + Resource Creation

Created a GCS “data lake” bucket.

provider "google" {
  project = var.project_id
  region  = var.region
}

resource "google_storage_bucket" "data-lake-bucket" {
  name     = "olyzoom-data-lake-bucket"
  location = "US"
}


Commands used:

terraform init
terraform plan
terraform apply


Result: GCS bucket successfully provisioned.

## 🎯 5. Skills Demonstrated
Infrastructure

Docker, Docker Compose

Terraform (provider blocks, resources, variables)

GCP IAM, Storage, Compute Engine

Data Engineering

Dataset ingestion to Postgres

SQL joins, aggregations, schema creation

Python scripting + argparse

DevOps

Remote VM setup

SSH configuration

VS Code Remote SSH

Running containers and databases on cloud VM

## 📦 6. Repository Contents:

docker-compose.yml

Dockerfile.ingest

ingest_data.py

pipeline.py

Terraform files (main.tf, variables.tf)

Jupyter notebooks (pg-test-connection.ipynb, Upload_data.ipynb)


## ✅ Summary

Full foundation for cloud-based data engineering:

✔ Dockerized Postgres & pgAdmin
✔ Automated ingestion pipeline
✔ SQL exploration
✔ Terraform deployment
✔ Full GCP VM environment with Python, Docker & Terraform
✔ Infrastructure ready for (GCS + BigQuery ingestion)
