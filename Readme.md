# Problem ID-9: Effect of Feedback on Affective and Cognitive Measures

This project (IITB, Problem ID-9) investigates how feedback (Correct / Incorrect / Skip) influences engagement, confusion, and EEG band powers over time.

## Dataset Instructions
The raw dataset files (`PSY.csv`, `TIVA.csv`, `EEG.csv`) are **not included** in this repository due to size and privacy concerns.

To run the notebooks:

1. Download the dataset from [Google Drive / IITB portal link].  
2. Place the CSV files in the `data/` folder:
project/
data/
PSY.csv
TIVA.csv
EEG.csv



## Project Structure
project/
│── data/ # PSY.csv, TIVA.csv, EEG.csv
│── notebooks/           # Jupyter notebooks
│ ├── 01_preprocessing_time_series.ipynb
│ ├── 02_anova_analysis.ipynb
│ ├── 03_time_series_modeling.ipynb
│── results/            # Metrics + Plots
│── models/             # Saved BiLSTM+Attention weights
│── README.md           # Project overview


## Approach
1. Step 1 & 2 – Data preprocessing and feature engineering  
   - Synchronize EEG and affective data per trial  
   - Compute band powers and temporal derivatives  
   - Encode feedback (Correct/Incorrect/Skip)  

2. Step 3.1 (Statistical Baseline) – Repeated Measures ANOVA  
   - Tested effect of feedback type on engagement and confusion  

3. Step 3.2 (ML Regression) – Predict affective states  
   - Models: Linear Regression, Random Forest  
   - Metrics: MAE, RMSE, R²  

4. Step 3.3 (Deep Learning) – Temporal modeling  
   - BiLSTM with Attention  
   - Captures sequential influence of feedback across trials  

## Key Results
- Random Forest (ML Baseline)  
  - MAE ≈ 0.15  
  - RMSE ≈ 0.93  
  - R² ≈ 0.86  

- BiLSTM with Attention (DL)  
  - MAE ≈ 8–9  
  - RMSE ≈ 22–23  
  - R² < 0 (needs larger dataset and tuning)  

## Outputs
- anova_summary.csv – Statistics from ANOVA  
- ml_baseline_metrics.csv – ML results  
- dl_metrics.csv – DL results  
- ml_predictions.png – Predicted vs Actual (ML)  
- dl_predictions.png – Predicted vs Actual (DL)  
- attention_weights.png – Attention visualization  

## Run Instructions
1. Preprocess data

jupyter notebook notebooks/01_preprocessing_time_series.ipynb

2. Run ANOVA

jupyter notebook notebooks/02_anova_analysis.ipynb

3. Train ML and DL models

jupyter notebook notebooks/03_time_series_modeling.ipynb## IITB Alignment
- Step 3.1: ANOVA baseline  
- Step 3.2: ML regression (Linear, Random Forest)  
- Step 3.3: DL with Attention (BiLSTM)
- 
## 4. Evaluation & Interpretation
- ANOVA: p-values to assess statistical significance of feedback on engagement, confusion, and EEG metrics
- ML/DL Models:
  - MAE (Mean Absolute Error)
  - RMSE (Root Mean Squared Error)
  - R² (Coefficient of Determination)
- Interpretability:
  - ANOVA → F-statistics and p-values show effect size of feedback
  - Attention models → Visualize attention weights to identify which past trials most influence current affective/EEG states

## 5. Experimentation & Visualization
- Hypothesis Testing: Examine if negative feedback increases confusion or decreases engagement
- Feature Engineering: Temporal derivatives and lagged features (e.g., previous trial engagement)
- Visualizations:
  - Average engagement/confusion across trials for each feedback type
  - Predicted vs Actual plots for ML and DL models
  - Attention weights visualization from BiLSTM+Attention

## 6. Outputs
- anova_summary.csv – Statistics from ANOVA
- ml_baseline_metrics.csv – ML regression metrics
- dl_metrics.csv – DL regression metrics
- final_summary.csv – Consolidated trial-level predictions
- ml_predictions.png – Predicted vs Actual (ML)
- dl_predictions.png – Predicted vs Actual (DL)
- attention_weights.png – Attention visualization

