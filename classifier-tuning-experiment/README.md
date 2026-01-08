# Classifier Tuning Experiment

Companion code for the article "We Tuned 4 Classifiers on the Same Dataset — None Improved".

## Overview

We tuned hyperparameters for four classifiers on Portuguese student performance data to predict pass/fail status (G3 ≥ 10). Despite proper nested cross-validation and grid search, none showed statistically significant improvement over default parameters.

## Key Findings

| Model | Baseline F1 | Tuned F1 | Change |
|-------|-------------|----------|--------|
| Random Forest | 0.9249 | 0.9239 | -0.0010 |
| SVM | 0.9229 | 0.9155 | -0.0074 |
| Logistic Regression | 0.9226 | 0.9185 | -0.0040 |
| XGBoost | 0.9192 | 0.9296 | +0.0104 |

Statistical tests (McNemar's) confirmed no significant differences between models.

## Methodology

- **Validation**: Nested cross-validation (5-fold outer, 5-fold inner)
- **Metric**: F1 score (dataset is imbalanced: 85% pass, 15% fail)
- **Preprocessing**: Inside pipelines to prevent data leakage
- **Statistical testing**: McNemar's test for model comparison

## Dataset

Portuguese student performance data from [StrataScratch project](https://platform.stratascratch.com/data-projects/student-performance-analysis).

- 649 students, 30 features
- Target: Pass/Fail (G3 ≥ 10)

## Files

```
classifier-tuning-experiment/
├── README.md
├── requirements.txt
├── classifier_tuning_experiment.ipynb
└── datasets/
    └── student-por.csv
```

## Usage

```bash
pip install -r requirements.txt
jupyter notebook classifier_tuning_experiment.ipynb
```
