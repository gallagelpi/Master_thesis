# Early Warning Signals for Conflict Allocation

**Master Project — Barcelona School of Economics (BSE)**
Data Science for Decision Making

**Authors:** Erika Yazmín Blanco, Gal·la Gelpí, María Victoria Suriel

---

## Overview

This project develops an early warning system to anticipate whether a country will accumulate the conditions necessary to become eligible for a CERF (Central Emergency Response Fund) allocation related to conflict-induced displacement, two months ahead of time. The model is a Random Forest classifier trained on a monthly panel of 176 countries (January 2018 – April 2026), combining data on conflict dynamics, displacement, structural vulnerability, and humanitarian risk.

The full methodology, literature review, and results are detailed in the accompanying thesis document.

## Repository Structure

The pipeline is organized into five sequential notebooks:

| Notebook | Description |
|---|---|
| `1_preprocessing.ipynb` | Loads and cleans the six raw data sources (CERF allocations, IDMC, ACLED, HDX Signals, EconAI, INFORM Index), standardizing each to a common `iso3` + `month` format. |
| `2_EDA.ipynb` | Exploratory analysis of the integrated dataset: structure, temporal/geographic coverage, missing values, and the distribution of the target variable. |
| `3_feature_engineering.ipynb` | Merges all cleaned sources into a single country-month panel, defines the target variable, and constructs the engineered feature groups (humanitarian dynamics, conflict dynamics, structural vulnerability, conflict risk signals, and specialized early-warning signals). |
| `4_model.ipynb` | Defines the temporal cross-validation strategy (PanelSplit), trains the Random Forest model, and runs the full grid of feature-group experiments. |
| `5_results.ipynb` | Evaluates experiment results, selects the final feature set, trains the final model, and reports metrics, feature importance, SHAP values, and robustness checks. |

## Data Sources

- **CERF allocations** — United Nations Central Emergency Response Fund
- **IDMC** — Internal Displacement Monitoring Centre
- **ACLED** — Armed Conflict Location & Event Data Project
- **HDX Signals** — Humanitarian Data Exchange
- **EconAI** — Text-based conflict risk forecasts
- **INFORM Risk Index** — Structural vulnerability indicators

Raw data files are expected under `data_raw/`, and cleaned/processed outputs are saved to `data_clean/`.

## Setup

```bash
pip install -r requirements.txt
```

Key dependencies: `pandas`, `numpy`, `scikit-learn`, `panelsplit`, `shap`, `matplotlib`, `seaborn`, `ipywidgets`, `pycountry`, `country_converter`.

## Usage

Run the notebooks in order, from `1_preprocessing.ipynb` through `5_results.ipynb`. Each notebook reads the outputs saved by the previous one (`data_clean/` for preprocessed data, `results/` for model outputs).

## Notes

A few minor cleanups are pending across the notebooks: a handful of inline comments are still in Spanish/Catalan (mostly in `4_model.ipynb` and `5_results.ipynb`), and there's a leftover comment in `EDA.ipynb` referencing a Spanish-language variable rename. These don't affect functionality but should be translated before the final submission.