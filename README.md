## Overview

This project applies supervised machine learning to a real-world petrophysical dataset loaded from a LAS file. Using well log measurements, including Gamma Ray (GR), Sonic (DT), Neutron Porosity (NPHI), Caliper (CALI), and Resistivity (RESD, LLS). A Linear Regression model was trained to predict Bulk Density (RHOB) across 23,000+ depth samples. The workflow covers data ingestion with `lasio`, exploratory data analysis, missing value handling, feature scaling with `StandardScaler`, model training via a `sklearn` Pipeline, and performance evaluation using MAE, RMSE, and R². The model was further applied to fill in missing RHOB values across flagged depth intervals.

## Dataset

- **Format:** LAS file (`Data2.las`)
- **Records:** 23,064 depth samples
- **Depth range:** 10 ft – 11,541.5 ft

### Features (Input Variables)

| Column | Description |
|--------|-------------|
| CALI | Caliper log (borehole diameter) |
| DT | Sonic / Compressional slowness |
| GR | Gamma Ray log |
| RESD | Deep Resistivity |
| LLS | Shallow Laterolog Resistivity |
| NPHI | Neutron Porosity |

### Target Variable

| Column | Description |
|--------|-------------|
| **RHOB** | Bulk Density (g/cm³) |

## Workflow

1. **Data Loading** — LAS file parsed using the `lasio` library and converted to a Pandas DataFrame
2. **Exploratory Data Analysis (EDA)** — Statistical summaries, distribution plots, and correlation analysis
3. **Data Preprocessing** — Handling missing values, feature scaling with `StandardScaler`
4. **Model Training** — A Linear Regression model trained within a `Pipeline` with `StandardScaler` for feature scaling
5. **Model Evaluation** — Performance assessed using:
   - Mean Absolute Error (MAE)
   - Root Mean Squared Error (RMSE)
   - Coefficient of Determination (R²)
