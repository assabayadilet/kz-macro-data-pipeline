# Kazakhstan Macroeconomic Data Pipeline

An end-to-end **ETL pipeline** that extracts currency exchange data (USD/KZT) from the National Bank of Kazakhstan API, transforms it with Python, loads into PostgreSQL, and visualizes in Power BI.

## Architecture

```
┌──────────────┐     ┌─────────────────────────┐     ┌────────────┐     ┌───────────┐
│  NBRK API    │────▶│   Apache Airflow DAG    │────▶│ PostgreSQL │────▶│ Power BI  │
│ (USD/KZT)    │     │  Extract → Transform →  │     │ Warehouse  │     │ Dashboard │
│              │     │  Load                    │     │            │     │           │
└──────────────┘     └─────────────────────────┘     └────────────┘     └───────────┘
                              │
                              ▼
                     ┌─────────────────┐
                     │   CSV Data Lake  │
                     │  raw/ processed/ │
                     └─────────────────┘
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Orchestration | Apache Airflow (Docker Compose) |
| Storage | PostgreSQL |
| Processing | Python (Pandas, SQLAlchemy) |
| Visualization | Power BI |
| Infrastructure | Docker Compose |

## Project Structure

```
├── dags/
│   └── nbrk_currency_pipeline.py   # Main ETL DAG
├── data/
│   ├── raw/                         # Raw extracted data
│   └── processed/                   # Cleaned data
├── docker-compose.yaml              # Airflow + PostgreSQL setup
├── logs/                            # Airflow logs
├── plugins/                         # Custom operators (optional)
└── README.md
```

## Quick Start

### Prerequisites

- Docker & Docker Compose
- Minimum 4 GB RAM for Docker
- Ports `8080` (Airflow) and `5432` (PostgreSQL) available

### Run

```bash
git clone https://github.com/assabayadilet/kz-macro-data-pipeline.git
cd kz-macro-data-pipeline
docker-compose up -d
```

Airflow UI: http://localhost:8080

## Pipeline Steps

1. **Extract** — Fetch USD/KZT exchange rate data from [NBRK Open API](https://data.nationalbank.kz/api-docs)
2. **Transform** — Clean and process data with Pandas
3. **Load** — Insert into PostgreSQL via SQLAlchemy
4. **Visualize** — Connect Power BI to PostgreSQL for dashboards
