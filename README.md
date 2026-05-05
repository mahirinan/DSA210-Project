# DSA210 Term Project
**The Correlation Between Domestic Player Representation in Top Clubs and National Team Success (1986-2024)**

This repository contains the final project for the DSA 210: Introduction to Data Science course at Sabancı University.

## Project Overview
The objective of this project is to investigate the relationship between the performance of national football teams and the demographics of their domestic leagues. Specifically, the project focuses on the "Domesticity Index"—the ratio of local players in top clubs—and its impact on national team success in major tournaments (FIFA World Cup and UEFA EURO).

## Motivation
While a strong domestic league is often assumed to benefit the national team, the globalization of football has led to an influx of foreign players in top European leagues. This project explores whether maintaining a high ratio of local players in domestic clubs actually leads to better national team results or if success is now driven by other global factors.

## Data Sources & Collection
A hybrid methodology was used to construct the dataset (160 primary observations from 1986 to 2024):
- **National Team Data:** Sourced from Kaggle (International Football Results).
- **Squad Demographics:** Automated extraction from Transfermarkt and digital archives using Python (Requests & BeautifulSoup).
- **Market Values & FIFA Ranks:** Retrieved from historical official records.
- **Club Performance:** International club trophy data (UCL, UEL) was manually curated and merged using Pandas.

## Key Features
The analysis revolves around the following variables:
- **Success Score:** Quantitative metric for tournament progress.
- **Domesticity Index:** Percentage of local players in top domestic clubs.
- **Top 5 League Ratio:** Concentration of players in elite European leagues.
- **Market Value (€M):** Total squad market value.
- **Club Trophy Count:** Number of international trophies won by domestic clubs in that year.

## Methodology
- **Exploratory Data Analysis (EDA):** Correlation analysis and visualization of metrics against success.
- **Hypothesis Testing:** Pearson Correlation and T-Tests to verify the initial "Domesticity" hypothesis.
- **Machine Learning (Regression):** Multiple models trained to predict Success Score:
  - Linear Regression, Ridge, Lasso
  - Support Vector Regression (SVR)
  - K-Nearest Neighbors Regressor (best k selected via 5-fold CV)
  - Random Forest Regressor
  - Gradient Boosting Regressor
- **Machine Learning (Classification):** Success Score binned into 3 classes (Low / Mid / High):
  - Logistic Regression
  - K-Nearest Neighbors Classifier
  - Random Forest Classifier
  - Gradient Boosting Classifier
  - Support Vector Classifier (SVC)
- **Model Evaluation:** R², MAE, RMSE for regression; Accuracy & Classification Report for classification; 5-Fold Cross-Validation for all key models.

## Key Findings
- The initial hypothesis regarding the Domesticity Index was not supported; no significant linear correlation (r≈-0.04) was found.
- FIFA Rank and Market Value remain the strongest predictors of success.
- A clear Globalization Trend was observed: Successful modern squads are increasingly composed of players competing in the "Top 5" European leagues.
- Among ML models, Random Forest achieved the best regression performance; cross-validation confirmed results are stable.

## How to Run
Clone the repository:
```bash
git clone https://github.com/mahirinan/DSA210-Project.git
```
Install required libraries:
```bash
pip install pandas seaborn matplotlib scikit-learn xgboost beautifulsoup4
```
Open the Jupyter Notebook:
```bash
jupyter notebook world_cup_data.ipynb
```

## Repository Structure
```
DSA210-Project/
├── world_cup_data.ipynb                  # Main analysis notebook
├── world_cup_data_with_trophies.csv      # Primary dataset
├── results.csv                           # Results data
├── DSA210 progress proposal.pdf          # Progress report
└── README.md
```
