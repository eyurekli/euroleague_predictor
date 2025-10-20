# 🏀 Euroleague Match Winner Predictor

This project builds an end-to-end **data-engineering + machine-learning pipeline** using open Euroleague datasets (2007 – 2026).  
It prepares, cleans, integrates, and models basketball data to predict whether the **home team wins** a game — and includes a fun rivalry analysis: *Fenerbahçe vs Panathinaikos.*

---

## 📁 Project Structure
| Folder / File | Purpose |
|----------------|----------|
| `data/` | Raw Euroleague CSVs from Kaggle |
| `clean_data/` | Cleaned and integrated datasets |
| `01_data_cleaning_and_exploration.ipynb` | Standardizes columns, parses dates, validates keys |
| `02_data_integration_and_features.ipynb` | Joins tables, aggregates boxscores, builds features |
| `03_modeling_and_evaluation.ipynb` | Trains Logistic Regression & Random Forest models |
| `README.md` | Project summary & usage guide |

---

## 🧹 Stage 1 — Data Cleaning & Exploration
- Unified column naming (`snake_case`)
- Parsed and validated dates (`NaT` for invalid entries)
- Verified relational keys (`game_id`, `team_id`, `season_code`)
- Separated raw vs. cleaned data (`data/` → `clean_data/`)

---

## 🧩 Stage 2 — Data Integration & Feature Building
- Aggregated player boxscores → **team totals per game**
- Engineered metrics (FG2%, FG3%, FT%, rebounds, AST/TOV)
- Created **home vs away** feature sets
- Generated `home_win` binary label
- Exported modeling-ready dataset `games_features.csv`
- Added **Fenerbahçe vs Panathinaikos head-to-head** extractor (34 games found)

---

## 🧠 Stage 3 — Modeling & Evaluation
- Split data into training/testing sets  
- Trained **Logistic Regression** (baseline) and **Random Forest** (non-linear) models  
- Evaluated accuracy & confusion matrices  
- Visualized **feature importance** (key predictors: rebounds, assists, shooting %)  
- Produced **rivalry charts** for Fenerbahçe vs Panathinaikos wins per season  

> ⚠️  Perfect accuracy on the first run revealed **data leakage** (post-game stats).  
>  This was used as a learning example to highlight feature selection and predictive validity.

---

## 🔍 Example Output
```text
Fener vs Panathinaikos — Head-to-Head Summary
Total games: 34
Fener wins:  16
PAO wins:    18
