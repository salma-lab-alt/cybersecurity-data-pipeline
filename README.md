# Cybersecurity Data Engineering & Analytics Pipeline

A modular and reproducible data pipeline prototype for cybersecurity
analytics and intrusion detection, built with PySpark, Delta Lake,
scikit-learn, XGBoost, MLflow, and Power BI.

Based on the CIC-IDS2017 network intrusion detection dataset, using
DistriNet, a corrected version of the original release. The same dataset
version was used in my final-year project on deep-learning-based
intrusion detection.

---

## Project Goals

This project has two parallel objectives:

### Learning Objective

Develop hands-on experience in modern Data Engineering and MLOps:

- PySpark DataFrame API and Window functions
- Bronze / Silver / Gold data architecture
- Databricks and Delta Lake
- Data quality and automated testing with pytest
- Machine Learning with scikit-learn and XGBoost
- Experiment tracking with MLflow
- Business intelligence and visualization with Power BI

### Portfolio Objective

- Demonstrate an end-to-end cybersecurity data pipeline
- Apply Data Engineering practices to a real-world dataset
- Build modular, tested, and documented Python code
- Provide a reproducible project setup

---

## Architecture Overview

```text
                    CIC-IDS2017 (DistriNet)
                              |
                              v
                           Raw CSV
                              |
                              v
                       PySpark Ingestion
                              |
                              v
                           Bronze
                              |
                              v
                    Cleaning & Validation
                              |
                              v
                           Silver
                              |
                              v
                    Feature Engineering
                              |
                              v
                            Gold
                           /    \
                          /      \
                         v        v
                   ML Training  Power BI
                         |
                         v
                       MLflow
````

---

## Development Progress

| Phase   | Description                   | Visible Deliverable                                      |
| ------- | ----------------------------- | -------------------------------------------------------- |
| J3      | Project setup + raw ingestion | Repository structure, `src/ingestion.py`, Bronze Parquet |
| J4      | Cleaning & validation         | `src/cleaning.py`, Silver Parquet                        |
| J5      | Feature engineering           | `src/transformation.py`, Gold Parquet                    |
| J6      | Data quality                  | Automated tests and quality report                       |
| J7–J8   | Databricks + Delta Lake       | Databricks notebooks and Delta tables                    |
| J9–J10  | ML training & evaluation      | ML pipeline and evaluation metrics                       |
| J11–J12 | MLflow tracking               | Experiment comparison                                    |
| J13     | Power BI dashboard            | Dashboard screenshots                                    |

**Current status:** J3 in progress

---

## Technologies

| Category              | Technologies           |
| --------------------- | ---------------------- |
| Data Processing       | PySpark, Pandas        |
| Storage               | Parquet, Delta Lake    |
| Machine Learning      | scikit-learn, XGBoost  |
| Data Engineering      | Databricks             |
| Experiment Tracking   | MLflow                 |
| Business Intelligence | Power BI               |
| Testing & CI          | pytest, GitHub Actions |
| Configuration         | YAML, python-dotenv    |

---

## Dataset

### DistriNet — Corrected CIC-IDS2017

The project uses **DistriNet**, a corrected version of CIC-IDS2017
that addresses labeling issues present in the original dataset.

This is the same dataset version used in my final-year project
on deep-learning-based intrusion detection.

* **Original dataset:** CIC-IDS2017
* **Corrected version:** DistriNet
* **Source:** Canadian Institute for Cybersecurity, University of New Brunswick
* **Format:** Network-flow records in CSV
* **Preprocessing:** Project-specific cleaning, validation, and transformation

Official CIC-IDS2017 reference:

[https://www.unb.ca/cic/datasets/ids-2017.html](https://www.unb.ca/cic/datasets/ids-2017.html)

---

## Project Structure

```text
cybersecurity-data-pipeline/
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
│
├── data/
│   ├── raw/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── notebooks/
│
├── src/
│   ├── __init__.py
│   ├── ingestion.py
│   ├── cleaning.py
│   ├── transformation.py
│   ├── quality.py
│   └── ml/
│       ├── train.py
│       ├── predict.py
│       └── mlflow_utils.py
│
├── tests/
├── config/
├── docs/
└── .github/
    └── workflows/
```

---

## Quickstart

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/cybersecurity-data-pipeline.git
cd cybersecurity-data-pipeline
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

#### Linux / macOS

```bash
source .venv/bin/activate
```

#### Windows

```powershell
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Generate a synthetic dataset

For local development and testing, a small synthetic dataset can be
generated without downloading the full CIC-IDS2017 dataset:

```bash
python -m src.ingestion --generate-sample --sample-rows 10000
```

### 5. Run the Bronze ingestion

```bash
python -m src.ingestion \
    --input data/raw/ \
    --output data/bronze/
```

The generated Bronze data is stored in Parquet format.

---

## Data Pipeline

The project follows a layered data architecture:

### Bronze

Raw data ingested from CSV files and stored in Parquet format.

### Silver

Cleaned and validated data with standardized columns and data quality
checks.

### Gold

Transformed and feature-engineered data prepared for Machine Learning
and Business Intelligence use cases.

---

## Reproducibility

The project is designed to provide a reproducible development
environment through:

* Version-controlled source code
* Dependency management with `requirements.txt`
* Configuration through YAML files
* Git-based version control
* Automated testing with pytest
* Clear separation between raw data, processed data, and source code

Dataset files are excluded from Git through `.gitignore`.

---

## License

MIT
