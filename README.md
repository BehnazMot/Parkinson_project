Parkinson's Disease Severity Prediction Using Hybrid Machine Learning 
📌 Project Overview: This repository contains code and analysis for predicting Parkinson’s disease (PD) severity using optimized ensemble machine learning models. Parkinson’s disease is a progressive neurological disorder affecting motor and non-motor functions, making early and precise diagnosis critical for effective treatment. This project leverages the UCI Parkinson’s Telemonitoring dataset and focuses on predicting Total UPDRS and Motor UPDRS scores. 

📖 Related Publication: 
Motamedi, B., & Villányi, B. J. (2025).
A novel hybrid machine learning approach for early prediction of Parkinson’s disease severity using optimized feature selection and ensemble learning.
Intelligence-Based Medicine, 100276. 
👉https://doi.org/10.1016/j.ibmed.2025.100276

📊 Primary Dataset:
Source: https://doi.org/10.24432/C5ZS3N
License: Creative Commons Attribution 4.0 International (CC BY 4.0)
Patients: 42 early-stage PD patients 
Number of Samples: 5,875 voice recordings 
Recording Environment: Audio recordings systematically acquired in patients’ residences over six months 
Objective: Predict motor_UPDRS and total_UPDRS using voice features 
Features:
Demographic / Temporal: Age, Sex, test_time (duration since baseline recruitment) 
Motor & Total UPDRS Scores: motor_UPDRS, total_UPDRS 
Biomedical Voice Metrics (16 features): 
Jitter measures: Jitter(%), Jitter(Absolute), Jitter: RAP, Jitter: PPQ5, Jitter: DDP 
Shimmer measures: Shimmer, Shimmer(dB), Shimmer: APQ3, Shimmer: APQ5, Shimmer: APQ11, Shimmer: DDA 
Noise-to-harmonics / complexity metrics: NHR, HNR, RPDE, DFA, PPE 

The primary goal is to investigate the relationship between vocal biomarkers and the progression of PD, thereby facilitating remote monitoring of motor symptom development. 

🚀 Key Features of the Approach:
🔹 Data Preprocessing:
Outlier Removal: Interquartile range (IQR) filtering 
Normalization: Min–Max scaling for all features 
Feature Selection: Three strategies to reduce redundancy and multicollinearity: All features, Pearson Correlation Coefficient (PCC,) Variance Inflation Factor (VIF) 
Feature Optimization:
Algorithms: Minimum Redundancy Maximum Relevance (mRMR) and Robust ReliefF (RRF). Purpose: Rank features and improve model performance 
Ensemble Learning Models:
Bagged Ensembles (BE) optimized using Bayesian Optimization and Random Search. Hyperparameters tuned: learning rate, number of weak learners. Validation: 10-fold cross-validation 

🔹 Proposed Models:
VIF-BOBE-RRF: Bayesian-optimized Bagged Ensemble with RRF and VIF VIF-RSOBE-RRF: Random Search-optimized Bagged Ensemble with RRF and VIF 
Benchmarked against: MLR, GPR, SVR, MLP, DTR, Boosting ensembles 

Evaluation Metrics:
coefficient of determination (R²)
Root Mean Squared Error (RMSE) 
Mean Absolute Error (MAE) 

Total UPDRS Performance: 
VIF-BOBE-RRF → R² = 0.97, RMSE = 0.0400, MAE = 0.0169 
VIF-RSOBE-RRF → R² = 0.97, RMSE = 0.0405, MAE = 0.0169 
Motor UPDRS Performance: 
VIF-BOBE-RRF →  R² = 0.96, RMSE = 0.0454, MAE = 0.0190 
VIF-RSOBE-RRF →  R² = 0.96, RMSE = 0.0492, MAE = 0.0198
Interpretability:
SHAP analysis identifies key predictors such as age, DFA, and test duration 
Helps understand feature contributions and model decisions 

📊 External Validation on Kaggle Dataset:
Source: https://www.kaggle.com/datasets/rohanpurohit0705/clinical-parkinson-dataset/data
To evaluate generalizability, models were validated on an independent Kaggle Clinical Parkinson Dataset. 
Dataset Characteristics:
Samples: 23,841 
Features: 9 (voice-based biomarkers + demographics) including fundamental_freq_hz, max_freq_hz, min_freq_hz, spread_2, detrended_fluctuation, rpde, dfa, age, gender, test_time 
Clinical targets: motor_updrs_score, total_updrs_score 
Validation Findings 
VIF-BOBE-RRF & VIF-RSOBE-RRF: R² = 1.00 (train & test) → excellent generalization 
Baseline models: R² ≈ 0.96–0.98 
RMSE (Total UPDRS): 
VIF-RSOBE-RRF → train: 0.18797, test: 0.18861 
VIF-BOBE-RRF → train: 0.30585, test: 0.27778 
MAE (Total UPDRS): 
VIF-RSOBE-RRF → train: 0.11745, test: 0.11478 
VIF-BOBE-RRF → train: 0.22343, test: 0.20626 
Motor UPDRS: Similar trends with lower RMSE and MAE for proposed models 
These results demonstrate robustness and superior predictive performance of the proposed models across diverse datasets.
