# Enterprise Pipeline Optimization (EPO-064)

[![Project Status](https://img.shields.io/badge/Status-Production-success)](https://github.com/Github-SG03/enterprise-pipeline-optimization)
[![Technology](https://img.shields.io/badge/Stack-Snowflake%20%7C%20Airflow%20%7C%20PySpark%20%7C%20dbt-blue)](https://github.com/Github-SG03/enterprise-pipeline-optimization-64squares)
[![Author](https://img.shields.io/badge/Author-Shivam%20Gupta-orange)](https://github.com/Github-SG03)

## 📋 Overview

**Enterprise Pipeline Optimization (EPO-64)** is a production-grade ELT platform .The system automates data ingestion from REST APIs and S3, transforms 10M+ rows/day using PySpark, and delivers analytics-ready marts via dbt on Snowflake—achieving >99% pipeline reliability and 35% cost reduction through incremental models and auto-suspend warehouses.

### Business Problem
Unified subscription analytics (product usage, billing, support) to enable:
- Daily KPIs: MRR/ARR, gross/net churn, cohort LTV, SLA compliance
- ML-ready features for churn prediction
- Self-service BI with published dbt docs lineage

---

## 🏗️ Architecture

REST APIs + S3 (CSV/JSON/Parquet)
↓
Apache Airflow (hourly/daily orchestration)
↓
Snowflake Bronze (raw landing, COPY INTO)
↓
PySpark (bronze → silver: dedupe, normalize, sessionize)
↓
dbt (silver → gold: staging → marts, tests, incremental)
↓
Gold Layer: dim_customer, fact_usage_daily, kpi_mrr_arr_churn
↓
Power BI / Tableau (dashboards) + ML Feature Store

text

**Tech Stack:**
- **Data Warehouse:** Snowflake (auto-suspend, partitioning/clustering)
- **Orchestration:** Apache Airflow 2.9 (SLA monitoring, Slack alerts)
- **Transform:** PySpark 3.5 (heavy normalization), dbt 1.7 (SQL marts, tests)
- **Cloud:** AWS S3, EKS (Airflow deployment), Secrets Manager
- **CI/CD:** GitHub Actions (lint, dbt compile/test, docs publish)
- **Governance:** RBAC roles, audit columns (load_id, landed_at), reject capture

---

## 📂 Repository Contents

| File/Folder | Description |
|-------------|-------------|
| **[Project_Document_Shivam_Gupta.pdf](.Project_Document_Shivam_Gupta.pdf)** | **Complete 85-page project report** (architecture, code, testing, user manual) |
| `airflow/` | DAGs for ingestion, orchestration, backfills |
| `spark/` | PySpark jobs (bronze → silver transforms) |
| `dbt/` | dbt project (staging/marts models, tests, macros) |
| `infra/` | Snowflake DDL (roles, warehouses, schemas, stages) |
| `ci/` | GitHub Actions workflows (CI/CD, dbt docs) |
| `docker/` | docker-compose for local dev environment |

---

## 📖 Full Documentation

📄 **[Download Complete Project Report (PDF)](.Project_Document_Shivam_Gupta.pdf)**

The 85-page document includes:
- ✅ Company profile & business problem
- ✅ System architecture & data model (bronze/silver/gold)
- ✅ UML diagrams (use case, activity, sequence, deployment)
- ✅ Complete code samples (Airflow DAGs, PySpark jobs, dbt models)
- ✅ Test cases & results (56/56 passed, 100% success)
- ✅ User manuals (data engineers, analysts, data scientists)
- ✅ Runbook for production operations
- ✅ Cost optimization checklist

---

## 🚀 Key Features

### Data Pipelines
- **Hourly:** Usage events via REST API → S3 → Snowflake COPY (SLA: 15 min)
- **Daily:** Billing (CSV), Support (JSON) → PySpark transforms → dbt marts (SLA: 06:00 IST)
- **Backfills:** Reprocess any date range via Airflow CLI

### Data Quality & Governance
- dbt tests: unique, not_null, relationships (block deployment on failure)
- COPY reject capture tables with error samples
- RBAC: EPO_INGESTOR (bronze), EPO_TRANSFORMER (silver/gold), EPO_ANALYST (read-only)
- Audit lineage: load_id, source_file, landed_at on all tables

### Observability
- Airflow SLAs with Slack/email alerts on miss
- Row count metrics and task duration exported to CloudWatch
- Published dbt docs lineage (GitHub Pages)

### Cost Optimization
- Auto-suspend warehouses (1 min idle)
- Incremental dbt models for large facts
- Partitioning/clustering on date columns
- Result: Snowflake credits < ₹25K/month (35% reduction)

---

## 📊 Deliverables & Impact

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Manual ETL time | 10 hrs/week | 0 hrs/week | **100% automated** |
| Pipeline reliability | ~85% | >99% | **+14% uptime** |
| Dashboard load time | 45 sec | 15 sec | **-67% latency** |
| Snowflake cost | ₹38K/month | ₹24K/month | **-37% savings** |
| Data freshness | Daily (manual) | Hourly (auto) | **24x faster** |

**Business Value:**
- Enabled self-service analytics for 15+ analysts (dbt docs + BI dashboards)
- Reduced churn by 5% via ML features (projected ₹2M+ annual revenue protection)
- Leadership KPI dashboards refreshed daily by 06:00 IST for planning

---

## 🛠️ Technologies Used

**Languages & Frameworks:**
- Python 3.10, SQL, Bash
- pandas, PySpark, PyArrow, NumPy

**Data Engineering:**
- Apache Airflow, Apache Spark, dbt, Snowflake
- AWS S3, Secrets Manager, EKS, CloudWatch

**DevOps & CI/CD:**
- Git, GitHub Actions, Docker, Kubernetes (Helm)
- Terraform (Snowflake + AWS infra as code)

**BI & Analytics:**
- Power BI, Tableau, Apache Superset
- dbt docs (lineage visualization)

---

## 📸 Screenshots

### 1. Airflow DAG Graph (orchestrator_daily)
![Airflow DAG](https://via.placeholder.com/800x400?text=Airflow+DAG+Graph+View)
*Replace with actual screenshot from your Airflow UI*

### 2. dbt Docs Lineage
![dbt Lineage](https://via.placeholder.com/800x400?text=dbt+Lineage+DAG)
*Replace with actual screenshot from dbt docs site*

### 3. Snowflake Schema Browser
![Snowflake Schema](https://via.placeholder.com/800x400?text=Snowflake+Schema+Browser)
*Replace with actual screenshot showing RAW/REFINED/MARTS databases*

---

## 🎓 Project Context

**Organization:** None 
**Role:** Data Engineer
**Duration:** March 2024-Present
**Guide:** None

---

## 📞 Contact

**Shivam Gupta**  
- 📧 Email: [sgs.shivam99@outlook.com](mailto:sks.shivam339@zohomail.in)
- 💼 LinkedIn: [linkedin.com/in/shivamgupta0303]()
- 🐙 GitHub: [github.com/Github-SG03](https://github.com/Github-SG03)
- 📱 Phone: +91 9404495690
- 🔗 Portfolio: [linktr.ee/shivamgupta99]()

---

## 📜 License

This project is part of academic coursework and professional Wxperience. Code samples and architecture patterns are available for reference under strict License.

---

## ⭐ Acknowledgements

- **64 Squares LLC** for providing the opportunity and production infrastructure
- Open-source communities: Apache Airflow, dbt Labs, Snowflake

---

**⭐ If you found this project helpful, please consider starring the repository!**
