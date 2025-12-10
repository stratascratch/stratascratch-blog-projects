# Missing Data Imputation Comparison

Companion code for [KDN 5: We Tried 5 Missing Data Imputation Methods — The Simplest Method Won (Sort Of)](#).

## Overview

We tested 5 imputation methods on the Crop Recommendation dataset to see which best preserves predictive signal after introducing 20% missing values. The surprise: simple methods (Mean, Median) beat sophisticated ones (KNN, MICE) for prediction accuracy — but lost on correlation preservation.

## Key Findings

| Method | Accuracy | Correlation MAE |
|--------|----------|-----------------|
| Mean | 94.4% | 0.030 |
| Median | 94.4% | 0.029 |
| KNN | 93.0% | 0.005 |
| MICE | 92.9% | 0.008 |
| Random Sample | 87.5% | 0.048 |

**The trade-off:**
- Prediction accuracy → Mean/Median win
- Correlation preservation → KNN wins (6× better than Mean)

## Methodology

- **Validation**: 10-fold cross-validation × 5 random seeds
- **Missing rate**: 20% MCAR (Missing Completely at Random)
- **No data leakage**: Imputers fit only on training folds
- **Feature scaling**: Applied for distance-based methods (KNN, MICE)
- **Statistical testing**: Paired t-tests with Bonferroni correction

## Dataset

[Crop Recommendation](https://platform.stratascratch.com/data-projects/agricultural-data-analysis) from StrataScratch.

- 2,200 samples, 7 features, 22 crop classes
- Perfectly balanced (100 samples per class)
- Baseline accuracy: 99.6% (Random Forest on complete data)

## Files

```
missing-data-imputation/
├── README.md
├── requirements.txt
├── missing_data_imputation.ipynb
└── datasets/
    └── Crop_recommendation.csv
```

## Usage

```bash
pip install -r requirements.txt
jupyter notebook missing_data_imputation.ipynb
```