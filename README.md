# OSA Anomaly Detection Methodology

A methodology for detecting anomalous hourly sales drops in retail data, developed as a graduation thesis at a technical university.

## Problem Statement

The core problem addressed is **On-Shelf Availability (OSA)**: identifying moments when a product is present in warehouse stock but its sales have unexpectedly collapsed. This pattern strongly indicates a shelf availability failure — a product is not physically placed on the shelf despite being available for distribution.

## Data

The methodology was developed and tested on a dataset of hourly sales records across approximately **10,000 product SKUs** from a single store of a mid-tier grocery retail chain, provided by **Imredi**.

- **Training period:** January–July 2025
- **Test period:** August 2025
- **Features per observation:** date, product identifier, category, sales volume, stock level, price
- **Note:** Product identifiers are anonymised. The dataset is proprietary and not included in this repository.

## Repository Structure

```text
osa-anomaly-detection-methodology
├── OSA Data Analysis EDA.ipynb
├── Manual Anomaly Injection on Stable Sales.ipynb
├── LightGBM Methodology Test.ipynb
├── Typology Features Impact on LightGBM.ipynb
└── OSA Anomaly Detection Model Comparison
    ├── LightGBM for Sales Drop Detection.ipynb
    ├── TCN for Sales Drop Detection.ipynb
    ├── Isolation Forest for Sales Drop Detection.ipynb
    ├── Anomaly Detection Model Selection via Statistical Diagnostics.ipynb
    └── README.md
```

## Research Pipeline

The study follows a sequential pipeline across five notebooks:

### 1. `OSA Data Analysis EDA.ipynb`
Exploratory data analysis of the full hourly dataset. Covers demand distribution, zero-sales rate, stock availability patterns, intraday and weekly seasonality, and product heterogeneity across categories. Establishes the statistical properties that inform all downstream modelling decisions.

### 2. `Manual Anomaly Injection on Stable Sales.ipynb`
Construction of the controlled evaluation benchmark. **synthetic zero-sales anomalies** are manually injected into stable high-selling products during business hours, with stock confirmed available. These labelled events serve as the primary recall benchmark, compensating for the absence of real ground-truth labels.

### 3. `OSA Anomaly Detection Model Comparison/`
Comparative study of three fundamentally different anomaly detection approaches on the top-500 products by August sales volume. See the folder README for details.

### 4. `LightGBM Methodology Test.ipynb`
Extension of the winning LightGBM architecture to the full product catalogue. Introduces an enriched **feature product profile** and a systematic four-configuration benchmark (RMSE / Huber loss × conservative / strong regularisation) evaluated at z-score thresholds. Constitutes the final, deployable anomaly detection pipeline.

### 5. `Typology Features Impact on LightGBM.ipynb`
External validation of the final pipeline against anomalies independently detected by Imredi on the same August 2025 test period. Applies an identical statistical evaluation framework to both sets, enabling a direct metric-consistent comparison of signal quality, stock filter compliance, and operational alert volume.


## Data Availability

The dataset is proprietary and **not included** in this repository. It was provided by Imredi under a data sharing agreement for academic research purposes.
