# RUL / SOX Prediction Project

## Overview

This project introduces **Remaining Useful Life (RUL)** and **SOX prediction** using time-series sensor data.
It is designed for students who are **new to Python, Jupyter notebooks, and machine learning**.

The project follows a **shared data pipeline** (preprocessing, feature engineering, windowing) and then branches into two modeling approaches:

- **Classical Machine Learning** (feature-based models)
- **Deep Learning** (LSTM sequence models)

The goal is not only to build models, but to understand **how data preparation and representation affect results**.

---

## Project structure

```
rul-sox-project/
  README.md
  environment.yml
  .gitignore

  data/
    synthetic/
      README.md
      synthetic_data.csv
    private/
      README.md

  notebooks/
    00_Jupyter_Basics.ipynb
    01_Data_Overview.ipynb
    02_Preprocessing_Shared.ipynb

    feature_preparation/
      03_Feature_Engineering.ipynb
      04_Windowing.ipynb

    classical_ml/
      05_Classical_Model.ipynb

    deep_learning/
      05_LSTM_Model.ipynb

    06_Evaluation_Comparison.ipynb
```

---

## Data

### Synthetic data (included)
Synthetic data is provided to:
- allow everyone to run the notebooks immediately
- illustrate degradation behavior and ground truth RUL/SOX
- debug preprocessing and modeling logic safely

Location:
```
data/synthetic/
```

### Private data (not included)
Real data must be placed **locally** and is **not committed to GitHub**.

Expected location:
```
data/private/
```

⚠️ Do not commit private data — it is excluded via `.gitignore`.

---

## Environment setup

### Option 1: Conda (recommended)

```
conda env create -f environment.yml
conda activate rul-sox
```

### Option 2: pip + venv
Use the packages listed in `environment.yml`.

---

## Starting Jupyter

From the project root:

```
jupyter notebook
```

or

```
jupyter lab
```

---

## Notebook execution order

1. `00_Jupyter_Basics.ipynb`
2. `01_Data_Overview.ipynb`
3. `02_Preprocessing_Shared.ipynb`
4. `feature_preparation/03_Feature_Engineering.ipynb`
5. `feature_preparation/04_Windowing.ipynb`

Choose one track:

### Classical ML
6. `classical_ml/05_Classical_Model.ipynb`

### Deep Learning
6. `deep_learning/05_LSTM_Model.ipynb`

Finally:
7. `06_Evaluation_Comparison.ipynb`

---

## Why feature engineering is shared

Feature engineering is applied per time step and shared across models.
Classical ML aggregates features; LSTMs consume sequences directly.

This ensures fair comparison and clearer learning outcomes.

---

## Important rules

- No data leakage
- No random shuffling of time series
- Keep notebooks runnable top-to-bottom

---

## Troubleshooting

### Git dubious ownership (Windows)
```
git config --global --add safe.directory "<repo_path>"
```

---

## Learning outcomes

Students will:
- understand the full ML pipeline
- implement feature engineering and windowing
- compare classical ML and LSTM approaches
