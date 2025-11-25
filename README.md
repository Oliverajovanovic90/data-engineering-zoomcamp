# data-engineering-zoomcamp
Practice work from the Data Engineering Zoomcamp, covering GCP, Docker, Terraform, workflow orchestration, data ingestion, BigQuery, dbt, Spark, and Kafka.

# ⭐ Section 1 (Docker, Postgres, Terraform, GCP)  
Foundation of the entire data engineering stack.  
The focus is on containerization, running databases in Docker, interacting with Postgres, and provisioning cloud infrastructure using Terraform.

---
# 📘 1. Introduction  
Essential tools and concepts required for modern data engineering:

- Docker & containerization  
- Postgres + pgAdmin inside Docker  
- SQL basics  
- Terraform for Infrastructure as Code  
- Google Cloud Platform (VMs, Storage, IAM)  
---

# 🐳 2. Docker + Postgres

### 🎥 **Introduction to Docker**
Topics learned:
- Why we need containers in data engineering  
- Running repeatable pipelines in isolated environments  
- Building a simple Docker-based data ingestion pipeline  

---

### 🎥 **Ingesting NY Taxi Data to Postgres**
Hands-on tasks completed:
- Ran Postgres locally using Docker  
- Connected using **pgcli**  
- Explored NYC Taxi dataset  
- Loaded CSV data into Postgres using a Python ingestion script  

> If pgcli is unavailable, pandas/Jupyter connections were used as an alternative.

---

### 🎥 **Connecting pgAdmin + Postgres**
Concepts covered:
- pgAdmin interface  
- Docker networking  
- Creating a pgAdmin server connection  
- Container-to-container communication  

PgAdmin 4 UI requires:
1. Right-click **Servers**  
2. Register → **Server**  
3. Enter container credentials  

---

### 🎥 **Putting the Ingestion Script into Docker**
Learnings:
- Converted a Jupyter notebook to a Python script  
- Added CLI parameters via **argparse**  
- Built a Docker image for ingestion  
- Ran the script inside the container  

---

### 🎥 **Running Postgres & pgAdmin with Docker-Compose**
Topics:
- Why Docker-Compose is needed  
- Defining multi-container systems  
- Running everything with:

bash: 
docker compose up -d

# ☁️ 3. Google Cloud Platform (GCP)

# 🛠️ 4. Terraform

Located in:
01-docker-terraform/1_terraform_gcp/terraform/terraform_basic

🎥 Terraform Concepts & Overview

Infrastructure as Code (IaC)
Providers
Resources
State management

🎥 Terraform Basics (Simple Deployment)

Created:

main.tf

variables.tf

Ran:

terraform init
terraform plan
terraform apply


→ Successfully created a GCS bucket (olyzoom-data-lake-bucket)

🎥 Deployment with Variables File

Topics:

Variables

Default values

Passing -var="project=..."

🖥️ 5. Cloud VM Setup (GCP)
🎥 GCP VM Setup

Completed steps:

Generated SSH keys

Added public key to GCP Metadata

Created Ubuntu VM (Compute Engine)

Connected using SSH (from Codespaces & local)

Installed on the VM:

Anaconda

Docker + Docker Compose

pgcli

Terraform

Completed configuration:

Created SSH config file

Used VS Code Remote-SSH to edit files on VM

Port-forwarded:

pgAdmin (8080)

Postgres (5432)

File Transfer via SFTP (Course Material)

Learned:

Creating .gcp folder

Uploading service account JSON credentials

Activating service account via:

gcloud auth activate-service-account --key-file <path>

VM Shutdown

To avoid charges:

Stopped/terminated instance through GCP

Terraform resources destroyed when not needed

🎯 Results:
✔ A full cloud-based development environment
✔ Dockerized Postgres + pgAdmin
✔ A functioning ingestion pipeline
✔ SQL joins and data checks
✔ A GCS bucket created with Terraform
✔ SSH + VS Code remote development environment
✔ Working Docker Compose workflow
