# MovieLens Recommender System

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![License](https://img.shields.io/badge/License-MIT-green)
![Dataset](https://img.shields.io/badge/Dataset-MovieLens%201M-orange?logo=data)

> A Machine Learning project focused on building a simple and reliable recommendation pipeline using the MovieLens 32M dataset.

> (PT) Projeto de Machine Learning focado na construção de um pipeline simples e confiável de recomendação de filmes.

---

## Table of Contents

- [Problem Statement](#problem-statement)
- [Solution Overview](#solution-overview)
- [Pipeline](#pipeline)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Quickstart](#quickstart)
- [Phases & Progress](#phases--progress)
- [Key Results](#key-results)
- [Tech Stack](#tech-stack)
- [License](#license)

---

## Problem Statement

With thousands of movies available, users face difficulty finding content that matches their preferences. Recommendation systems solve this by personalizing content discovery at scale (and are at the heart of companies like Netflix, Spotify, and Amazon).

This project focuses on building a **collaborative filtering pipeline** to predict user ratings and generate personalized movie recommendations using the MovieLens 32M dataset.

The main challenges explored include:

- **Cold start problem** (new users or movies with few ratings)
- **Evaluation beyond accuracy** (RMSE alone is not enough — Precision@K and Recall@K matter)
- **Temporal split** to avoid data leakage when evaluating the model

---

## Solution Overview

```
Raw data -> Data validation -> EDA -> Feature engineering -> Model training
```

The goal is to understand the dataset, explore user and item patterns, and train a baseline collaborative filtering model for movie recommendation.

---

## Pipeline

- Load and validate the MovieLens 32M files (ratings, movies, users)
- Perform exploratory data analysis (EDA)
- Apply feature engineering (normalization, encoding, temporal split)
- Train and evaluate a baseline model (SVD / Matrix Factorization)

---

## Dataset

**MovieLens 32M** — GroupLens Research

[https://grouplens.org/datasets/movielens/32m/](https://grouplens.org/datasets/movielens/32m/)

F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. ACM Transactions on Interactive Intelligent Systems (TiiS) 5, 4: 19:1–19:19. https://doi.org/10.1145/2827872

| Property | Value |
|---|---|
| Source | GroupLens Research, University of Minnesota |
| Ratings | ~32,000,204 |
| Users | 200,948 |
| Movies | 87,585 |
| Rating scale | 0.5 to 5 |
| Time span | ~28 years (1995–2023) |
| Target variable | `rating` (regression) / top-N ranking (recommendation) |

> **Note:** The dataset is not included in this repository. Download it from GroupLens and place the files in `data/raw/`. See [Quickstart](#quickstart).

---

## Project Structure

```
movielens-recommender/
│
├── data/
│   ├── raw/                    # Original .dat files from GroupLens (git-ignored)
│   ├── processed/              # Cleaned and merged data
│   └── curated/                # Feature-engineered, model-ready data
│
├── notebooks/
│   ├── 01_eda.ipynb            # Exploratory Data Analysis
│   ├── 02_feature_engineering.ipynb
│   └── 03_modeling.ipynb
│
├── src/
│   ├── ingestion/
│   │   ├── loader.py           # Load and merge ratings, movies, users
│   │   └── validation.py       # Basic data quality checks
│   ├── features/
│   │   └── pipeline.py         # Feature engineering and train/test split
│   └── models/
│       └── train.py            # Model training and evaluation
│
├── pyproject.toml
├── .gitignore
└── README.md
```

---

## Quickstart

### Prerequisites

- Python 3.11+
- [conda](https://docs.conda.io/) or `venv`

### 1. Clone and set up environment

```bash
git clone https://github.com/CaesarDuarte/Movie-Recommendation-System.git
cd Movie-Recommendation-System

conda create -n recommender python=3.11
conda activate recommender

pip install -e ".[dev]"
```

> ⚠️ **Important dependency**
> This project uses Parquet for efficient storage. Ensure that `pyarrow` is installed, as it is required for Parquet support.

### 2. Download the dataset

```bash
wget https://files.grouplens.org/datasets/movielens/ml-32m.zip
unzip ml-32m.zip -d data/raw/
```

### 3. Run the data pipeline

```bash
python src/ingestion/loader.py
python src/ingestion/validation.py
python src/features/pipeline.py
```

### 4. Train the model

```bash
python src/models/train.py
```

---

## Phases & Progress

| Phase | Description | Status |
|---|---|---|
| 1 | Data Ingestion | 🟥 Not started |
| 2 | Data Validation | 🟥 Not started |
| 3 | EDA | 🟥 Not started |
| 4 | Feature Engineering | 🟥 Not started |
| 5 | Modeling | 🟥 Not started |

---

## Key Results

> *To be updated as the project progresses.*

| Metric | Baseline Model |
|---|---|
| RMSE | — |
| Precision@10 | — |
| Recall@10 | — |

---

## Tech Stack

| Layer | Tools |
|---|---|
| Data validation | pandas, custom checks |
| Data processing | numpy, pandas |
| Data visualization | matplotlib, seaborn |
| Feature engineering | scikit-learn, scikit-surprise |
| Modeling | scikit-surprise (SVD, KNN) |

---

## Notes

This project focuses on building a solid foundation in data understanding and collaborative filtering modeling. A production pipeline (API, Docker, monitoring) is intentionally out of scope for now.

## License

MIT © César Duarte
