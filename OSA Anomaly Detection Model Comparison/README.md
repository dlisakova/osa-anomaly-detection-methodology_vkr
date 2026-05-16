# Anomaly Detection Model Comparison

**Part of Diploma Thesis** — Development of a methodology for detecting anomalous sales drops in hourly retail data.

## Overview

This folder contains the implementation and comparison of three different models for identifying sudden **sales drops** (anomalies) in hourly sales data across retail products.

All models were trained and evaluated under **identical conditions**:
- Same product subset
- Same data preprocessing pipeline
- Same evaluation period

## We deliberately chose three fundamentally different approaches to obtain a comprehensive and fair comparison:

- **LightGBM (Gradient Boosting)**  
  Excellent at handling highly intermittent demand (≈97% zero-sales observations), supports categorical features natively, offers high interpretability through feature importance, and is very fast to train and deploy.

- **Temporal Convolutional Network (TCN)**  
  A modern deep learning architecture specifically designed for time series data. Uses dilated causal convolutions to effectively capture long-term temporal dependencies with a large receptive field. Implemented as a global model with product and category embeddings.

- **Isolation Forest**  
  Classic unsupervised anomaly detection algorithm. Does not require a target variable, making it robust for cold-start products and previously unseen anomaly patterns. Serves as a strong baseline for pure outlier detection.

This combination allows us to compare **supervised forecasting-based** methods (LightGBM and TCN) with a pure **unsupervised** method (Isolation Forest).

## Contents

- `LightGBM for Sales Drop Detection.ipynb` — LightGBM with multiple thresholding strategies (z-score and sigma)
- `TCN for Sales Drop Detection.ipynb` — Temporal Convolutional Network
- `Isolation Forest for Sales Drop Detection.ipynb` — Isolation Forest
- `Anomaly Detection Model Selection via Statistical Diagnostics.ipynb` — Statistical diagnostics, model comparison and final selection

## Key Conclusion

After comprehensive statistical evaluation (signal strength, historical z-scores, zero-sale ratio, product coverage, and operational alert volume), **LightGBM** demonstrated the best overall performance
