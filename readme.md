# California Housing — Linear & Ridge Regression (From Scratch)

Short, human-readable repo summary. No long theory — just what matters.

## What this project is

- Implemented linear regression and Ridge (L2) regression from scratch using NumPy and plain Python.
- Built a reproducible preprocessing pipeline (impute → log1p → scale → one-hot) with sklearn's ColumnTransformer.
- Solved numerical issues that arise in DIY gradient descent and tuned lambda (regularization).

## Real problems I faced (and fixed)

- Extra useless file in dataset (removed).
- Heavy skew in many numeric features — used log1p transforms.
- Silent pipeline mismatch: column order + stale pickle caused unscaled columns. Fixed by saving feature order and re-fitting when pipeline changes.
- Gradient descent explosion: fixed by scaling the target (log1p + standardize), clipping extreme ratios, and reducing learning rate.
- Zero coefficients due to printing the wrong variable — fixed with clearer names and an assertion.

## Why Ridge?

- Ridge (L2) prevents large, noisy coefficients and improves generalization.
- It’s simple, effective, and easy to implement from scratch for learning purposes.

## Quick usage (local)

1. Put `california_housing.csv` into `data/raw/`
2. Run notebooks in order:
   - `notebooks/01_eda.ipynb`
   - `notebooks/02_preprocessing.ipynb` (fit & save preprocessor)
   - `notebooks/03_linear_regression.ipynb` (from-scratch baseline)
   - `notebooks/04_ridge_regression.ipynb` (Ridge + lambda experiments)
   - `notebooks/05_model_comparison.ipynb` (validation & final eval)

## Files you will find

- `report/` — final report docx
- `models/` — saved preprocessor, theta, best_lambda, target scaler
- `notebooks/` — step-by-step notebooks
- `data/processed/` — optional npz files with processed arrays

## Final note

This project taught me the practical parts of ML engineering: reproducible pipelines, numerical hygiene, and disciplined validation.