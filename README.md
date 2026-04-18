# world-cup-2026-match-predictor
# ⚽ FIFA World Cup 2026 — Match Outcome Predictor

> **Course Final Project** — Machine Learning  
> Predicting group-stage match outcomes (Home Win / Draw / Away Win) using ELO ratings, historical data, and ensemble machine learning models.

---

## 👥 Team Members & Algorithm Responsibilities

| # | Name | Student ID | Algorithm(s) Implemented |
|---|------|------------|--------------------------|
| 1 | **[STUDENT_1_NAME]** | [ID] | Random Forest Classifier + EDA & Feature Engineering |
| 2 | **[STUDENT_2_NAME]** | [ID] | Gradient Boosting Classifier + Monte Carlo Simulation |
| 3 | **[STUDENT_3_NAME]** | [ID] | XGBoost Classifier + Knockout Stage Simulator |

> **Shared work:** Data loading & preprocessing, final ensemble model, visualizations, presentation.

---

## 📋 Project Overview

This project predicts the outcome of FIFA World Cup 2026 group-stage matches using:

- **Historical international match data** (48,850 matches, 1872–2023)
- **Team ELO ratings** (312 national teams)
- **Monte Carlo simulation** (500 iterations) for tournament probabilities
- **Four ML classifiers** compared head-to-head using Accuracy, F1, Precision, and Recall

**Target variable:** `result` → `1` (Home Win), `0` (Draw), `-1` (Away Win)

---

## 🗂️ Repository Structure

```
world-cup-2026-predictor/
│
├── notebooks/
│   └── world_cup_2026_predictor.ipynb   # Main Kaggle notebook (all cells)
│
├── src/
│   ├── data_loader.py                   # Dataset loading helpers
│   ├── feature_engineering.py           # ELO features, temporal features
│   ├── models/
│   │   ├── random_forest.py             # [STUDENT_1] Random Forest
│   │   ├── gradient_boosting.py         # [STUDENT_2] Gradient Boosting
│   │   └── xgboost_model.py             # [STUDENT_3] XGBoost
│   ├── simulation/
│   │   ├── group_stage.py               # Group stage simulator
│   │   └── knockout_stage.py            # Knockout bracket simulator
│   └── evaluation.py                    # Metrics, confusion matrix, charts
│
├── data/
│   └── world_cup_2026_groups.py         # Confirmed 48-team draw (all 12 groups)
│
├── outputs/
│   ├── qualified_teams_2026.html
│   ├── tournament_bracket_2026.html
│   └── world_cup_2026_final_report.html
│
├── presentation/
│   └── wc2026_presentation.pptx
│
├── requirements.txt
└── README.md
```

---

## ⚙️ How to Run

### Option A — Kaggle (Recommended)

1. Go to [kaggle.com](https://www.kaggle.com) and create a new notebook
2. Add these datasets to your notebook:
   - `international-football-results-from-1872-to-2017`
   - `world-cup-database`
   - `teams-elo`
   - `wc2026-match-probability-baseline-dataset`
   - `group-stage-probabilities`
3. Upload `notebooks/world_cup_2026_predictor.ipynb`
4. Run all cells (**Runtime → Run All**)

### Option B — Local Setup

**Prerequisites:** Python 3.9+

```bash
# 1. Clone the repository
git clone https://github.com/[YOUR_USERNAME]/world-cup-2026-predictor.git
cd world-cup-2026-predictor

# 2. Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Download datasets manually from Kaggle and place in data/raw/
#    (See Dataset section below for links)

# 5. Launch Jupyter
jupyter notebook notebooks/world_cup_2026_predictor.ipynb
```

---

## 📦 Dependencies

See [`requirements.txt`](requirements.txt) for the full pinned list.

Core libraries:

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | ≥2.0 | Data manipulation |
| `numpy` | ≥1.24 | Numerical computing |
| `scikit-learn` | ≥1.3 | Random Forest, Gradient Boosting, Logistic Regression, metrics |
| `xgboost` | ≥2.0 | XGBoost classifier |
| `matplotlib` | ≥3.7 | Static visualizations |
| `seaborn` | ≥0.12 | Statistical plots |
| `plotly` | ≥5.14 | Interactive charts |
| `jupyter` | ≥1.0 | Notebook environment |

---

## 📊 Datasets

| Dataset | Source | Size |
|---------|--------|------|
| International Football Results (1872–2023) | [Kaggle](https://www.kaggle.com/datasets/martj42/international-football-results-from-1872-to-2017) | 48,850 matches |
| World Cup Database | [Kaggle](https://www.kaggle.com/datasets/abecklas/fifa-world-cup) | 900 WC matches |
| Team ELO Ratings | [Kaggle](https://www.kaggle.com/datasets/slehkyi/extended-football-stats-for-european-leagues-xg) | 312 teams |
| WC2026 Match Probability Baseline | [Kaggle](https://www.kaggle.com) | 72 future matches |
| Group Stage Probabilities | [Kaggle](https://www.kaggle.com) | 48 group matches |

---

## 🔑 Key Results

| Model | Test Accuracy | F1-Score | Implemented By |
|-------|:------------:|:--------:|----------------|
| Logistic Regression (baseline) | 56.1% | 55.0% | Shared |
| **Random Forest** | 61.3% | 59.7% | [STUDENT_1_NAME] |
| **Gradient Boosting** | 62.8% | 61.3% | [STUDENT_2_NAME] |
| **XGBoost** | 63.5% | 62.1% | [STUDENT_3_NAME] |
| Voting Ensemble (final) | **64.9%** | **63.8%** | Shared |

> **Best model:** Voting Ensemble combining all three classifiers — 64.9% test accuracy.  
> **Key predictor:** ELO differential (~45% of feature importance).  
> **Hardest class:** Draw (28% recall — consistent with literature on football prediction).

---

## 🏆 2026 World Cup Predictions

**Predicted group winners (top probabilities from 500 Monte Carlo simulations):**

| Group | Predicted Winner | Win Probability |
|-------|-----------------|:--------------:|
| A | Mexico 🇲🇽 | 74.2% |
| B | Switzerland 🇨🇭 | 52.8% |
| C | Brazil 🇧🇷 | 77.0% |
| D | USA 🇺🇸 | 66.0% |
| E | **Germany 🇩🇪** | **88.4%** |
| F | Netherlands 🇳🇱 | 56.2% |
| G | Belgium 🇧🇪 | 67.8% |
| H | Spain 🇪🇸 | 67.0% |
| I | France 🇫🇷 | 66.2% |
| J | Argentina 🇦🇷 | 72.0% |
| K | Portugal 🇵🇹 | 68.0% |
| L | England 🏴󠁧󠁢󠁥󠁮󠁧󠁿 | 65.0% |

**Championship probability:** 🇧🇷 Brazil 22.2% → 🇫🇷 France 17.0% → 🇩🇪 Germany 12.6%

---

## 📌 Important Notes

- All 48 teams confirmed as of **April 1, 2026** (after UEFA & intercontinental playoffs)
- ELO ratings sourced from [eloratings.net](https://www.eloratings.net) (April 2026)
- Predictions are probabilistic and for academic/analytical purposes only
- The ML model was trained on historical data only — no future information was used

---

## 📄 License

This project is submitted for academic purposes. All datasets remain property of their respective Kaggle publishers.
