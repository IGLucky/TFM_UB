# Algorithmic Fairness in ICU Mortality Prediction

A Multi-Model Analysis of Racial Disparities, Structural Bias, and Mitigation Strategies Using MIMIC-IV

## Overview

This repository contains the code for a Master's thesis investigating algorithmic fairness in ICU mortality prediction. The study compares four model architectures (XGBoost, a deep feedforward neural network, a bidirectional LSTM, and a Transformer) across an ICU cohort, seeing whether performance disparities exist across race groups, where they come from, and whether they can be mitigated.


## Dataset

This work uses MIMIC-IV (version 3.1), a database of de-identified ICU patient records. Access requires credentialing through PhysioNet, so no patient data is included in this repository. Code here assumes the user has independently obtained credentialed access and built the relevant cohort tables.

## Repository structure

```
icu-fairness-thesis/
├── README.md
├── thesis/
│   └── thesis.tex
├── notebooks/
│   ├── 01_baseline_cv/
│   ├── 02_missingness_imputation/
│   ├── 03_measurement_bias_simulation/
│   ├── 04_sample_size_subsampling/
│   ├── 05_transformer_as_fourth_model/
│   ├── 06_adversarial_debiasing/
│   └── 07_survival_vs_mortality/
```

## Experiments

1. **Baseline cross validation.** Out of fold performance for all four architectures across demographic groups.
2. **Missingness and imputation.** Tests whether the missingness mask itself carries predictive signal, and whether imputation can resolve structural bias.
3. **Measurement bias simulation.** Simulates pulse oximetry offsets to test sensitivity to known clinical measurement bias together with a simulated run of removing temperature measurements for Black patients and adding heart rate noise.
4. **Sample size subsampling.** Isolates how much of the observed performance gap is explained by group sample size alone.
5. **Transformer as fourth model.** Trains the Transformer and runs the same four-model performance and fairness comparison as the other architectures.
6. **Adversarial debiasing.** Tests whether adversarial training closes fairness gaps by lifting underperforming groups or by degrading better performing ones.
7. **Survival vs. mortality framing.** Tests whether the fairness gap is sensitive to outcome prevalence by reframing the prediction target.
