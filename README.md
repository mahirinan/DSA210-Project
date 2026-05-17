# DSA210 Term Project

## The Correlation Between Domestic Player Representation in Domestic Leagues and National Team Success (1986-2024)

This repository contains the final project for the **DSA 210: Introduction to Data Science** course at Sabancı University.

---

## Motivation
The central motivation of this project is to investigate a long-standing debate in international football: Does a national team's success depend on the "Domesticity Index" of its local league? Traditionally, it has been argued that a strong national team is built upon the foundation of domestic clubs consistently fielding local players to maintain tactical cohesion and national identity.

However, the rapid globalization of football since the late 1990s, catalyzed by the Bosman Ruling and the financial concentration in elite European leagues (the "Top 5"), has challenged this conventional wisdom. This project tests whether "staying local" still provides a competitive edge in the modern era or if it has become a nostalgic myth, by determining:
* **The Impact of Globalization:** Whether a squad's success is more closely tied to the "Top 5 League Ratio" rather than domestic representation.
* **Financial vs. Demographic Indicators:** If quantitative metrics such as Market Value and FIFA Rankings have surpassed the "Domesticity Index" as the primary predictors of tournament performance.

---

## Data Sources & Collection
A hybrid methodology was used to construct the dataset (**160 primary observations from 1986 to 2024**):
* **National Team Data:** Historical tournament results from Kaggle (International Football Results).
* **Squad Demographics & Market Values:** Custom automated pipeline using Python's `Requests` and `BeautifulSoup` to scrape Transfermarkt archives — extracting full squad lists, club affiliations, league of each player, and historical market values.
* **Club Performance:** International club trophy data (UCL, UEL) manually curated and merged using Pandas.
* **Data Processing:** Raw data was merged and standardized using Pandas. Key steps included feature engineering (Domesticity Index, Top 5 League Ratio), handling missing historical values via trend-based estimation, and normalizing Success Scores by tournament stage (Winner = 100, Runner-up = 80, etc.).

---

## Key Features

| Variable | Description |
| :--- | :--- |
| **Success Score** | Quantitative metric for tournament progress |
| **Domesticity Index** | Percentage of squad players competing in their home country's league |
| **Top 5 League Ratio** | Proportion of squad playing in elite European leagues |
| **Market Value (€M)** | Total squad market value |
| **FIFA Rank** | Pre-tournament FIFA ranking |
| **Club Trophy Count** | International trophies (UCL/UEL) won by domestic clubs that year |
| **Average Age** | Mean age of the squad |
| **Squad Size** | Total number of players in the squad |

---

## Methodology

### Exploratory Data Analysis (EDA)
Correlation analysis and visualization of all metrics against Success Score using scatter plots, heatmaps, and time-series line plots to reveal the globalization trend (1986–2024).

### Hypothesis Testing
* **Pearson Correlation** to measure the linear relationship between Domesticity Index and Success Score.
* **T-Tests** to compare mean success scores of high-domesticity vs. low-domesticity squads.

### Machine Learning Framework
To evaluate predictive capacity on a small dataset constraint, a robust evaluation framework was deployed side-by-side:
* **Baseline Model:** Linear Regression to capture global baseline linear trends.
* **Non-Linear Models:** K-Nearest Neighbors (KNN) Regressor and Random Forest Regressor.
* **Overfitting Mitigation:** Given the small dataset size (160 rows), **5-Fold Cross-Validation** was applied to all models. Train MAE, Test MAE, CV Train MAE, and CV Test MAE are reported side-by-side to explicitly evaluate generalization and detect potential memorization.

---

## Key Findings

* **Domesticity Hypothesis Rejected:** Pearson $r \approx -0.048$, T-test p-value $> 0.05$. Having a high concentration of local players is no longer a prerequisite for international success.
* **Strongest Predictors:** FIFA Rank ($r = -0.27$) and Market Value ($r = 0.21$) are the most reliable indicators of tournament progression.
* **Globalization Trend:** Top 5 League Ratio shows a positive correlation ($r = 0.19$). Since the 1990s, the ratio of elite-league players in successful squads has increased by **~12.63%**.

### Model Evaluation Summary

| Model | Train MAE | Test MAE | CV Train MAE | CV Test MAE |
| :--- | :---: | :---: | :---: | :---: |
| **Linear Regression (Baseline)** | 16.64 | 18.00 | 16.72 | 17.72 |
| **KNN Regressor** | 16.16 | 19.25 | 15.38 | 19.18 |
| **Random Forest Regressor** | 12.24 | 18.21 | 11.82 | 18.10 |

> **Analysis:** Random Forest achieved the highest predictive power. The close convergence between CV train and test scores confirms the model successfully generalizes global trends rather than overfitting despite the small dataset.

---

## Limitations & Future Work

### Limitations
* **League Quality:** The Domesticity Index does not account for the quality/UEFA coefficient of the domestic league — all domestic leagues are treated equally.
* **Historical Financial Data:** Market values from the late 1980s–early 1990s were estimated from historical records, introducing a minor margin of error.
* **External Factors:** Coaching philosophy, injuries, and squad psychology were not quantifiable and are excluded from the models.

### Future Work
* **Weighted Domesticity Index** incorporating league strength (UEFA/FIFA coefficients).
* **Player Fatigue Analysis** using minutes played prior to the tournament.
* **Managerial Influence** metric based on coach experience and win rates.
* **Broader Geographical Scope** including AFC and CAF tournaments.

---

## How to Run

1. **Clone the repository:**
```bash
   git clone https://github.com/mahirinan/DSA210-Project.git
```

2. **Install required libraries:**
```bash
   pip install pandas numpy seaborn matplotlib scikit-learn beautifulsoup4 requests
```

3. **Open the Jupyter Notebook:**
```bash
   jupyter notebook "world_cup_data.ipynb"
```

---

## Repository Structure

DSA210-Project/
├── world_cup_data.ipynb                  # Main analysis notebook (Most recent)
├── ml_results.png                        # Side-by-side Train vs Test MAE comparison graph
├── world_cup_data_with_trophies.csv      # Primary dataset (with Club_Trophy_Count)
├── world_cup_data.csv                    # Base dataset
├── results.csv                           # Results data
└── README.md                             # Project documentation

---

## AI Disclosure
AI-assisted tools (LLMs) were used in a limited capacity for code debugging, documentation refinement, and statistical logic verification. All core data collection, hypothesis formulation, feature engineering, and model selection were designed and executed by the student.
