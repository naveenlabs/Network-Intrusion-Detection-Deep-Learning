# Network Intrusion Detection: Deep Learning Approach

[![Python](https://img.shields.io/badge/python-3.9%2B-blue)]()
[![TensorFlow](https://img.shields.io/badge/tensorflow-2.10%2B-orange)]()
[![License](https://img.shields.io/badge/license-MIT-green)]()
[![Status](https://img.shields.io/badge/status-complete-success)]()

## Overview

A comprehensive deep learning solution for network intrusion detection using the CIC-IDS2017 dataset. Implements binary classification to distinguish benign from malicious network traffic across 2.5M flow records with 52 network features. Follows DLWP 4.5 (Deep Learning with Python) universal workflow for rigorous cybersecurity model development.

**Module:** CM3015 Machine Learning and Neural Networks  
**Dataset:** CIC-IDS2017 (2.5M rows, 52 features, 717 MB)  
**Task:** Binary Classification (Benign vs Attack)  
**Methodology:** Deep neural networks with stratified validation

## Key Results

| Aspect | Value | Notes |
|--------|-------|-------|
| **Dataset Scale** | 2.5M flows | 52 network features per flow |
| **Class Distribution** | 83.11% / 16.89% | Benign / Attack (imbalanced) |
| **Data Split** | 70% / 15% / 15% | Train / Validation / Test (stratified) |
| **Primary Metrics** | Precision, Recall, F1 | Not raw accuracy (class imbalance) |
| **Scaling** | StandardScaler | Z-score normalization applied post-split |

## What's Inside

**Jupyter Notebook** (`notebooks/Network_Intrusion_Detection_DLWP_Report_2.ipynb`):
- 70 cells: 47 markdown sections + 23 code implementations
- **Sections 1-3:** Problem definition, success metrics, evaluation protocol (DLWP foundation)
- **Section 4:** Data preparation with stratified splitting, integrity verification, feature scaling
- **Section 5:** Deep neural network architecture with Dropout and L2 regularization
- **Section 6:** Model training with validation monitoring (loss, accuracy, early stopping)
- **Section 7:** Systematic hyperparameter investigation and model comparison
- **Section 8:** Final test set evaluation with confusion matrix, precision/recall/F1 analysis

**Data Directory** (`data/README.md`):
- Download instructions for CIC-IDS2017 dataset from Kaggle (717 MB, too large for GitHub)
- Dataset documentation and preprocessing notes

## Quick Start

```bash
pip install -r requirements.txt

# Download dataset from https://www.kaggle.com/datasets/cicdataset/cicids2017
# Extract cicids2017_cleaned.csv to data/ folder

jupyter notebook notebooks/Network_Intrusion_Detection_DLWP_Report_2.ipynb
```

## Tech Stack

- **Deep Learning:** TensorFlow 2.10+, Keras
- **Data Processing:** Pandas, NumPy, Scikit-learn
- **Visualization:** Matplotlib, Seaborn
- **Evaluation:** Scikit-learn metrics (precision, recall, F1, confusion matrix, ROC-AUC)
- **Language:** Python 3.9+, Jupyter

## Methodology

**DLWP 4.5 Workflow:** Industry-standard deep learning development pipeline covering problem definition, metric selection, evaluation protocol, data preparation, model architecture, training strategy, hyperparameter tuning, and final validation.

**Data Integrity:** Programmatic verification confirms zero NaN/Inf values across all 2.5M rows. Stratified splitting preserves exact class distribution (16.89% attacks) across train/validation/test sets, preventing distribution shift.

**Evaluation Strategy:** Hold-out validation with separate unseen test set. Primary metrics (precision, recall, F1-score) chosen to handle class imbalance; raw accuracy rejected due to accuracy trap (naive model predicting all-benign achieves 83% accuracy while detecting zero attacks).

**Regularization:** Dropout layers and L2 penalties prevent overfitting. Early stopping monitors validation loss. Hyperparameter space systematically explored (architecture depth, width, dropout rates, learning rates).

## Data

**CIC-IDS2017 Dataset**

The dataset (717 MB) exceeds GitHub's 25 MB file limit and is hosted on Kaggle.

**Download:** https://www.kaggle.com/datasets/cicdataset/cicids2017  
**Setup:** Extract `cicids2017_cleaned.csv` to `data/` folder before running notebook

**Characteristics:**
- 2.5 million network flow records
- 52 preprocessed numerical features (original 78 reduced via multicollinearity, zero-variance, and statistical filtering)
- Binary target: Benign (0) vs Attack (1)
- Severe class imbalance: 83.11% benign, 16.89% attacks
- Source: Canadian Institute for Cybersecurity (CIC); Kaggle-preprocessed variant

## Key Insights

1. **Imbalanced Data Trap:** Naive accuracy (predicting all samples as benign) = 83%; F1-score and confusion matrix required for fair evaluation
2. **Feature Engineering Complete:** Dataset authors already applied Kruskal-Wallis and Random Forest feature selection; 52 remaining features are highly informative
3. **Stratification Validates:** Stratified splitting maintains 16.89% attack ratio perfectly across all three splits, ensuring unbiased evaluation
4. **Deep Learning Rationale:** Neural networks capture non-linear behavioral signatures in network traffic better than shallow models; captures temporal and statistical patterns
5. **Precision-Recall Trade-off:** Cybersecurity context requires balanced approach—high recall catches attacks (avoids catastrophic misses), high precision prevents alert fatigue in SOC operations

## Author

**Dhanarasu Naveen**  
Computer Science | University of London (via SIM Singapore)  
Specialization: Artificial Intelligence & Machine Learning

## License

MIT License
