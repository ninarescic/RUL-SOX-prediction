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

## Installing Conda (first-time setup)

This project uses **Conda** to manage Python and all required packages.
If you do not already have Conda installed, follow the steps below.

### Step 1: Download Miniconda (recommended)

Miniconda is a minimal Conda installer.

Download from:
- https://docs.conda.io/en/latest/miniconda.html

Choose:
- **Windows** → Miniconda3 (64-bit)
- **macOS / Linux** → Miniconda3

### Step 2: Install Miniconda

During installation:
- ✅ Allow Conda to initialize your shell (recommended)
- ✅ Use default installation settings

After installation, **restart your terminal**.

### Step 3: Verify installation

Open a new terminal (or PowerShell) and run:

```
conda --version
```

If Conda is installed correctly, you should see a version number.

---

## Environment setup

Once Conda is installed, create the project environment.

From the project root directory:

```
conda env create -f environment.yml
conda activate rul-sox
```

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

Make sure the **correct Conda environment (`rul-sox`)** is selected as the kernel.

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

## Notebook execution order

Run notebooks **in order**:

1. `00_Jupyter_Basics.ipynb`
2. `01_Data_Overview.ipynb`
3. `02_Preprocessing_Shared.ipynb`
4. `feature_preparation/03_Feature_Engineering.ipynb`
5. `feature_preparation/04_Windowing.ipynb`

Choose one track:

### Classical Machine Learning
6. `classical_ml/05_Classical_Model.ipynb`

### Deep Learning (LSTM)
6. `deep_learning/05_LSTM_Model.ipynb`

Finally:
7. `06_Evaluation_Comparison.ipynb`

---

## Why feature engineering is shared

Feature engineering is applied **per time step** and shared across all models.

- Classical ML aggregates features over time windows
- LSTM models consume full feature sequences

This ensures:
- fair comparison
- reduced code duplication
- clearer learning outcomes

---

## Important rules

- **No data leakage** (fit scalers on training data only)
- **No random shuffling** of time series
- Keep notebooks runnable **top-to-bottom**

---

## Troubleshooting

### Git: dubious ownership (Windows)

If you see a "dubious ownership" error:

```
git config --global --add safe.directory "<repo_path>"
```

---

## Learning outcomes

By the end of this project you should be able to:
- explain the full ML pipeline
- justify preprocessing and feature choices
- train and evaluate a model correctly
- compare classical ML and LSTM tradeoffs
