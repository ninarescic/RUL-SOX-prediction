# RUL / SOX Prediction Project

## Overview

This project introduces **Remaining Useful Life (RUL)** and **SOX prediction** using time-series sensor data.
It is designed for students who are **new to Python, Jupyter notebooks, and machine learning**.

The project follows a **shared data pipeline** (preprocessing, feature engineering, windowing) and then branches into two modeling approaches:

- **Classical Machine Learning** (feature-based models)
- **Deep Learning (LSTM)** using PyTorch

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
      00_Classical_ML_Demo.ipynb
      05_Classical_Model.ipynb

    deep_learning/
      00_LSTM_TimeSeries_Demo.ipynb
      05_LSTM_Model.ipynb

    06_Evaluation_Comparison.ipynb
```

---

## Installing Conda (first-time setup)

This project uses **Conda** to manage Python and all required packages.

### Step 1: Download Miniconda (recommended)

Download Miniconda from:
https://docs.conda.io/en/latest/miniconda.html

Choose:
- **Windows** → Miniconda3 (64-bit)
- **macOS / Linux** → Miniconda3

### Step 2: Install Miniconda

During installation:
- Allow Conda to initialize your shell
- Use default installation options

Restart your terminal after installation.

### Step 3: Verify installation

```bash
conda --version
```

---

## Environment setup

From the project root directory:

```bash
conda env create -f environment.yml
conda activate rul-sox
```

---

## Deep learning framework

For deep learning and LSTM models, this project uses **PyTorch**.

PyTorch was chosen because:
- it is robust and reliable on Windows systems
- it integrates well with Conda environments
- it provides transparent control over training loops
- it avoids common TensorFlow DLL issues on student machines

No prior PyTorch experience is required.

> Note: The LSTM demo notebook uses **PyTorch**, even though the filename does not include the framework name.

---

## Starting Jupyter

Always start Jupyter from an activated environment:

```bash
conda activate rul-sox
jupyter notebook
```

In Jupyter, ensure the selected kernel is:
**Python (rul-sox)**

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
   → Learn how Jupyter notebooks work and basic Python usage

2. `01_Data_Overview.ipynb`  
   → Explore synthetic (and optionally private) data

3. `02_Preprocessing_Shared.ipynb`  
   → Cleaning, scaling, and train/validation/test split  
   ⚠️ Split is done **by unit**, not by time step

4. `feature_preparation/03_Feature_Engineering.ipynb`  
   → Feature creation per time step (shared by all models)

5. `feature_preparation/04_Windowing.ipynb`  
   → Sliding windows and label assignment

### Example notebooks (warm-up)

Before working on the RUL/SOX models, complete these examples:

- `classical_ml/00_Classical_ML_Demo.ipynb`  
  → Typical classical ML workflow (baseline, linear model, tree-based model)

- `deep_learning/00_LSTM_TimeSeries_Demo.ipynb`  
  → Basic LSTM example on synthetic time-series data (PyTorch)

### Main modeling notebooks

- `classical_ml/05_Classical_Model.ipynb`
- `deep_learning/05_LSTM_Model.ipynb`

6. `06_Evaluation_Comparison.ipynb`  
   → Compare classical ML and LSTM approaches on the same test set

---

## Important rules

- **No data leakage** (fit scalers on training data only)
- **No random shuffling** of time series
- Keep notebooks runnable **top-to-bottom**
- **Do not use the base Anaconda environment**

---

## Troubleshooting

### Conda environments and kernels

If you encounter import errors:
- ensure `rul-sox` environment is activated
- restart Jupyter
- select kernel **Python (rul-sox)**

### Git: dubious ownership (Windows)

```bash
git config --global --add safe.directory "<repo_path>"
```

---

## Learning outcomes

By the end of this project, students should be able to:
- explain the full ML pipeline
- justify preprocessing and feature choices
- train and evaluate classical ML and LSTM models
- compare feature-based and sequence-based approaches
