# Kazakhstan-Macroeconomic-Data-Pipeline-Data-Engineerg-Analytics-pet-project

# 🇰🇿 Kazakhstan Macroeconomic Data Pipeline

An end-to-end **ETL Data Engineering project** built with **Apache Airflow (Docker Compose)**, **PostgreSQL**, and **Power BI**, using public data from the [National Bank of Kazakhstan API](https://data.nationalbank.kz/api-docs).

---

## Project Overview

This project demonstrates a modern **Data Engineering workflow**:
1. **Extract** currency exchange data (USD/KZT) from NBRK’s open API  
2. **Transform** the data with Python & Pandas  
3. **Load** it into a PostgreSQL warehouse  
4. **Visualize** in Power BI dashboards  

---

## Tech Stack

| Layer | Technology |
|-------|-------------|
| **Orchestration** | Apache Airflow (Docker Compose) |
| **Storage / Warehouse** | PostgreSQL |
| **Processing** | Python (Pandas, SQLAlchemy) |
| **Visualization** | Power BI |
| **Infrastructure** | Docker Compose |

---

## Architecture
1. NBRK API  →  Airflow DAG (Extract → Transform → Load)
2. Data Lake (CSV files)
3. PostgreSQL Database
4. Power BI Dashboard

---

## Setup Instructions

### 1 Prerequisites

- Docker & Docker Compose installed  
- Minimum 4 GB RAM allocated to Docker  
- Port `8080` (Airflow) and `5432` (Postgres) available  

---

### 2 Clone the Repository

```bash
git clone https://github.com/<your-username>/kazakhstan-macro-pipeline.git
cd kazakhstan-macro-pipeline

### Project Structure

.
├── dags/
│   └── nbrk_currency_pipeline.py     # Main ETL DAG
├── data/
│   ├── raw/                          # Raw extracted data
│   └── processed/                    # Cleaned data
├── docker-compose.yaml               # Airflow + PostgreSQL setup
├── logs/                             # Airflow logs
├── plugins/                          # (Optional) custom operators/hooks
└── README.md                         # This file
