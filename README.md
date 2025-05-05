# Reproduce_physioMTL

PhysioMTL Reproduction and Interpretability Extension

This repository contains our reproduction and extension of the paper:

PhysioMTL: Personalizing Physiological Patterns Using Optimal Transport Multi-Task RegressionJoshua Ray, Vishnu Suresh, Jukka-Pekka OnnelaarXiv:2203.12595


## Overview

The goal of this project is to:

Reproduce the RMSE performance results reported in the original paper.

Replicate counterfactual analysis visualizations.

Extend the model by adding interpretability techniques using SHAP and Attention mechanisms.


## Repository Structure
.

├── PhysioMTL.ipynb                # Main notebook with training, evaluation, and analysis

└── README.md                      # You're here

## Dependencies
* Python 3.9
* Mutar (0.0.1)
* Numpy (1.22.4)
* Pandas (1.5.3)
* Matplotlib (3.7.1)
* Pot (0.9.0)
* Scipy (1.10.1)
* PyTorch (2.6.0)
* SHAP (0.47.2)


## How to Run

Run the main notebook directly in Colab utilizing the colab link attached on the top of the notebook.

Or download it to local:

    jupyter notebook PhysioMTL.ipynb


## Reproduced Results

We reproduced the RMSE comparision results from the original paper across 20%, 40%, 60%, and 80% training data. The results match closely, especially under low-data regimes, confirming the benefit of optimal transport regularization. However, the reproduced counterfactual plots showed deviations: HRV did not consistently decrease with age as seen in the paper, possibly due to different hyperparameter choices, input scaling, or optimization variance.


## Reproducibility Notes

Some variance in results due to lack of random seed control.

Counterfactual visualizations generally follow expected trends, but do not always align in magnitude or direction.

Age-dependent HRV decrease seen in the paper was weaker or reversed in some reproduction plots.


## Interpretability Extensions

SHAP (Local Feature Attribution)

SHAP values show per-subject feature influence:

Stress had the strongest negative contribution to HRV.

Age and weight contributed negatively, while activity effects varied.

Attention Mechanism (Global Attribution)

We added an attention layer over demographic inputs:

Attention weights confirmed stress and sleep as high-impact features.

Features with low attention weight (e.g., height) aligned with low SHAP importance.

Visualization

We compared SHAP and attention side-by-side to validate consistency across instance-level and model-level interpretations.


## Counterfactual Analysis

We simulated changes in demographic features (e.g., increasing age or reducing sleep) and visualized how predicted HRV curves shift over a 24-hour period. While general trends were visible, some deviations from the original paper's plots were observed, particularly for age and stress. This suggests sensitivity to model initialization, feature scaling, or data preprocessing differences.


## Authors

Meilin Liu


## 📂  Original Work
The following code was created by the original authors (Zhu, Jiacheng et al.), and was used as reference when creating our code. https://proceedings.mlr.press/v174/zhu22a/zhu22a-supp.zip

