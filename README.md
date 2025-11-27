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

# 🚀 Kestra ETL Workflows

This repository contains Kestra workflow orchestration pipelines built in GitHub Codespaces (VS Code) as part of the DataTalksClub Data Engineering Zoomcamp, focusing on:

ETL orchestration with Kestra

Loading NYC Taxi trip data into Postgres

Cloud integration with GCP (GCS + BigQuery)

Analytics engineering using dbt + BigQuery

Infrastructure preparation using KV & scheduling

🧰 Tools & Technologies Practiced

Kestra — orchestration & workflow automation

Docker Compose — service deployment in Codespaces

PostgreSQL — staging & final ETL load target

Google Cloud Storage (GCS) — cloud file storage

BigQuery — data warehouse & table creation

dbt (Data Build Tool) — SQL transformation (Analytics Engineering)

Git/GitHub — version control & workflow storage

📂 Workflow Files Included

All workflows used by Kestra are stored in the:

/Workflow


And include the following flows:

 01_getting_started_data_pipeline.yml
 02_postgres_taxi_scheduled.yml
 03_postgres_dbt.yml
 04_gcp_kv.yml
 05_gcp_setup.yml
 06_gcp_taxi_scheduled.yml
 07_gcp_dbt.yml

These pipelines demonstrate my ability to orchestrate ETL workloads, integrate cloud services, prepare data warehouse tables, and run analytics transformations with dbt.

▶️ How to Run the Project (Local / Codespaces)
1️⃣ Start Kestra services
docker compose up -d

2️⃣ Verify Kestra is running

Open UI (automatically exposed by Codespaces):

http://localhost:8080

3️⃣ Run a workflow from namespace

Use the Kestra UI to execute any of the workflow IDs listed above.

🧠 What This Project Demonstrates

✅ Building reproducible Docker-based data environments
✅ Automating data ingestion using shell + Python task runners
✅ Safe Postgres staging & merge logic using hashed unique IDs
✅ Provisioning GCP cloud resources from KV store variables
✅ Creating structured, partitioned BigQuery tables
✅ Running dbt builds & dependency resolution inside containers
✅ Understanding real-world ETL orchestration patterns

💼 Real-World Usage Context

In production environments, companies use tools like Kestra for workflow orchestration, but data is explored and visualized using:

Business Intelligence (Power BI / Looker / Metabase)

Database clients (DBeaver / DataGrip / Postgres CLI)

Cloud data warehouse UI (BigQuery Console, Data products, etc.)

Kestra does not render tables visually — it runs the pipelines, while other tools display the data.
