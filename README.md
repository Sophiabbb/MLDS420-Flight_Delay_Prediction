
# Flight Delay Prediction

## Project Overview

Flight delays are a major inconvenience to passengers and a significant challenge for airlines and airports. In this project, we aim to develop predictive models to classify whether a flight will be delayed or not using a real-world dataset from the **Bureau of Transportation Statistics** and **NOAA**.

Given the dataset's strong class imbalance (only ~19% of flights are delayed), we evaluated various classification algorithms with a particular focus on improving **F1-score**. Techniques such as **feature engineering** and **class weighting** were used to enhance model interpretability and performance.

## Approach

### 1. Data Collection

- **Source**: [Kaggle - 2019 Airline Delays and Cancellations](https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations/data)
- **Size**: ~6.5 million rows, 24 columns
- **Key Features**:
  - Flight details (e.g., distance, segment number)
  - Aircraft characteristics (e.g., plane age, number of seats)
  - Temporal information (e.g., month, time block)
  - Weather variables (e.g., precipitation, snowfall, wind)

### 2. Data Preprocessing

- Stratified 1% sampling to manage computation
- One-hot and label encoding for categorical variables
- Transformation of time blocks into numerical hours
- Feature selection via:
  - Logistic regression with `drop1`
  - Variance Inflation Factor (VIF)

### 3. Model Training
We experimented with several machine learning models, including:
- **Logistic Regression**
- **Decision Tree**
- **Random Forest**
- **Gradient Boosting**
- **Generalized Additive Model (GAM)**
- **Neural Networks**
- **K-Nearest Neighbors (KNN)**
- **Extreme Gradient Boosting (XGBoost)**

To handle class imbalance (since only **18.9%** of flights are delayed), we applied **class weighting techniques** and evaluated models based on:
- **Precision**
- **Recall**
- **F1-score** (a priority metric due to class imbalance)

### 4. Model Comparison and Evaluation

| Model                     | Accuracy | Precision | Recall | F1-score |
|---------------------------|----------|-----------|--------|----------|
| Logistic Regression       | 80.92%   | 43.14%    | 0.9%  | 1.75%   |
| Decision Tree (Weighted)  | 65.06%   | 28.47%    | 55.33% | 37.6%    |
| Neural Network  | 81.16%   | 56.45%    | 4.27% | 7.94%    |
| KNN  | 76.9%   | 30.14%    | 16.27% | 21.14%    |
| GAM  | 81.06%   | 56.32%    | 1.99% | 3.85%    |
| Boosted Tree (Weighted)  | 65.85%   | 29.81%    | 58.67% | 39.53%    |
| Random Forest (Weighted)  | 81.12%   | 52.38%    | 8.5%   | 14.63%   |
| XGBoost (Weighted)    | **66.09%** | **29.95%** | **58.46%** | **39.61%** |

**XGBoost with class weighting (4:1)** performed best with a good trade-off between **recall** and **precision** for detecting delayed flights.

## Key Findings

- **Departure time** is the strongest predictor of delays.
- **Weather conditions** (precipitation, snow, wind speed) are crucial factors.
- **Class weighting (4:1 ratio)** significantly improves recall for delayed flights.
- **XGBoost outperformed other models**, providing the best trade-off between detecting delays and maintaining 

## Files Description
- **Modeling.Rmd**: R Markdown file containing the code for model training and evaluation.
- **Modeling.pdf**: PDF version of the Modeling.Rmd file for easier viewing.
- **Project_Report.pdf**: Final report summarizing the entire project.
- **README.md**: Project overview and documentation.
- **data_for_modeling_clean.Rmd**: R Markdown file focused on data cleaning and feature engineering.

## How to Run

1. Clone the repo:
   ```bash
   git clone https://github.com/Sophiabbb/MLDS420-Flight_Delay_Prediction.git
   cd MLDS420-Flight_Delay_Prediction
   ```

2. Ensure you have R and the required libraries installed. Main packages include:
   - `caret`
   - `gbm`
   - `xgboost`
   - `nnet`
   - `rpart`
   - `mgcv`
   - `randomForest`
   - `ALEPlot`
   - `class`
   - `MLmetrics`
   - `yaImpute`
   - `dplyr`
   - `car`

## References

- [Kaggle Dataset](https://www.kaggle.com/datasets/threnjen/2019-airline-delays-and-cancellations/data)
- U.S. Bureau of Transportation Statistics
- NOAA (National Centers for Environmental Information)

---

## Contributors
- Fuqian Zou
- Glenys Lion
- Iris Lee
- Kavya Bhat
- Mingze Bian
