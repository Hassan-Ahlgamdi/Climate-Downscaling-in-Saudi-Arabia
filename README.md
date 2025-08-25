# Climate Downscaling in Saudi Arabia

This repository contains the code, data processing scripts, and report for the project:

**Downscaling Future Heat Stress in Jeddah and Riyadh:  
A Comparison of Statistical and Machine Learning Methods**

---

## 📌 Project Overview
Accurate local climate projections are essential for understanding and preparing for future heat stress in Saudi Arabia.  
This project evaluates **statistical vs. machine learning approaches** for downscaling CMIP6 climate model data to city scale:

- **Study area**: Jeddah (coastal) & Riyadh (desert)  
- **Methods**: Quantile Delta Mapping (QDM), Random Forest (RF), and XGBoost (XGB)  
- **Observations**: ERA5-Land reanalysis (1985–2014)  
- **Models**: CMIP6 (ACCESS-CM2, EC-Earth3, MPI-ESM1-2-HR) under SSP126, SSP245, SSP585  
- **Target variables**: Minimum temperature (tasmin, ERA5 proxy t2m at 3AM local time)  
- **Indicators**: Cooling Degree Days (CDD), 95th percentile heat extremes (P95)  

---

## 📂 Repository Structure
```
├── notebooks/ # Jupyter notebooks for analysis & experiments
│ ├── qdm_downscaling.ipynb
│ ├── rf_downscaling.ipynb
│ ├── xgb_downscaling.ipynb
│ └── exploratory_analysis.ipynb
├── data/ # (Not included in repo) ERA5 & CMIP6 city files
├── report/ # Project report (PDF / LaTeX / Word)
├── UTCDW_Guidebook/ # UTCDW guidebook files (reference)
└── README.md
```

## ⚙️ Installation
We provide an environment YAML based on the **UTCDW Guidebook**.

```bash
conda env create -f environment.yml
conda activate UTCDW-env
```
### Main dependencies
Python 3.11+

xarray, pandas, numpy, dask

scikit-learn, xgboost

matplotlib, seaborn, cartopy

xclim, xskillscore

cdsapi, gcsfs

## 🚀 Usage
Place raw ERA5 & CMIP6 city-level files in data/.

Run preprocessing notebooks in notebooks/.

Use src/ scripts to apply downscaling methods:

qdm_utils.py → QDM bias correction & projections

rf_utils.py → Random Forest downscaler

xgb_utils.py → XGBoost downscaler

Generate figures with plotting.py.

## 📊 Results Summary
QDM: Robust statistical baseline, but limited at extremes.

RF: Moderate improvements, still some generalization issues.

XGBoost: Strongest historical fit (RMSE ↓ 83–89% vs QDM) but underperformed for out-of-sample future projections.

Future projections (2070–2100):

Jeddah → Moderate coastal warming (+2–3 °C)

Riyadh → Severe desert amplification (+4–5 °C)

Substantial increases in Cooling Degree Days (CDD) under all SSPs.

## 📖 References
ERA5-Land reanalysis: https://cds.climate.copernicus.eu

CMIP6 data: https://esgf-node.llnl.gov

UTCDW Guidebook (included in this repo)

## 👤 Authors
Hasan Algamdi (University of Toronto, KAUST Academy AI Program)

Supervisors: Paul Kushner, Karen Smith

