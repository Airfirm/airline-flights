# Predictive Analytics for Airline Flight Delays

## Project Overview

This data analytics capstone project analyzes historical U.S.
domestic airline flight performance and develops machine learning
models to predict arrival delays of 15 minutes or more.

## Data Source

U.S. Department of Transportation  
Bureau of Transportation Statistics (BTS)  
Reporting Carrier On-Time Performance

[https://www.transtats.bts.gov/]

## Dataset

Period: January–December 2025

Original records: 7,001,619

Final processed records: 6,879,483

Processed attributes: 30

## Tools and Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- Visual Studio Code
- Git and GitHub

## Project Methodology

1. Data collection
2. Data cleaning and preprocessing
3. Exploratory Data Analysis
4. Feature engineering
5. Predictive model development
6. Model evaluation and optimization
7. Final testing and interpretation

## Machine Learning Models

The project evaluated:

- Logistic Regression
- Balanced Logistic Regression
- Decision Tree
- Random Forest

The final selected model was Logistic Regression.

## Final Model Performance

Test period: December 2025

Classification threshold: 0.225

| Metric | Score |

|---|---:|
| Accuracy | 0.5961 |
| Precision | 0.3433 |
| Recall | 0.5572 |
| F1-score | 0.4248 |
| ROC-AUC | 0.6166 |
| Average Precision | 0.3536 |

## Key Findings

Scheduled departure hour was the strongest predictor
identified in the Logistic Regression permutation
importance analysis.

Airline, origin airport, and destination airport
information also contributed to predictive performance.

The selected model identified approximately 56% of
significantly delayed flights in December 2025.

However, its precision remained limited, indicating
a substantial number of false-positive predictions.

## Project Limitations

- Only 2025 flight data was analyzed.
- The prediction model focuses on completed flights.
- Cancelled and diverted flights were excluded.
- Real-time weather and congestion data were not included.
- The final model demonstrated modest discrimination.
- The classification threshold prioritizes delay detection,
  resulting in a relatively high false-positive rate.

## Repository Structure

```text
airline-flights/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_analysis.ipynb
│   └── 04_predictive_modeling.ipynb
├── reports/
│   ├── figures/
│   └── model_results/
├── models/
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```

## Reproducibility

The analysis was conducted using Jupyter Notebook
and Python.

Required Python packages are documented in
requirements.txt.

The trained model and classification threshold
are stored separately to preserve the final
prediction procedure.

## Future Improvements

Future work may incorporate additional years
of flight data, weather conditions, airport
congestion, aircraft rotation information,
and alternative machine learning algorithms.
