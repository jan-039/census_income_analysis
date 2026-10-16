# Census Income Classification Model

## Table of Contents

1. [Project Background and Overview](#project-background-and-overview)
2. [Data and Methodology](#data-and-methodology)
3. [Results](#results)

## Project Background and Overview

This project uses demographic and employment data from the 1994 U.S. Census to predict whether an individual's annual income is greater than $50,000.

The goal is to develop and compare machine learning models for binary income classification while also examining class imbalance, feature relationships, model interpretability, and potential ethical concerns associated with demographic data.

The project utilizes a traditional Logistic Regression model evaluates its performance using accuracy and F1 score.

## Data and Methodology

- **Dataset Used:**
  - Census Income dataset containing demographic, employment, education, and income-related characteristics
  - Target variable: `income_binary`
  - Income classes: `<=50K` and `>50K`

- **Exploratory Data Analysis:**
  - Checked missing values, duplicate records, data types, and dataset dimensions
  - Examined class imbalance in the income target
  - Reviewed summary statistics and numeric distributions
  - Used z-scores to identify potential outliers
  - Explored correlations between numeric variables and income
  - Examined relationships between categorical characteristics and income

- **Data Cleaning:**
  - Removed records containing missing values
  - Removed duplicate records
  - Dropped irrelevant or redundant columns including `fnlwgt`, `relationship`, and `education`
  - Winsorized `capital-gain` and `capital-loss` to reduce the influence of extreme values

- **Feature Engineering:**
  - One-hot encoded categorical variables
  - Grouped less common native-country values after encoding the most frequent countries
  - Label encoded the income target into binary values
  - Standardized model features before training

- **Model Development:**
  - Split the cleaned dataset into training and testing sets
  - Trained a Logistic Regression classifier
  - Applied class weighting to address target imbalance
  - Used GridSearchCV with 5-fold cross-validation to optimize Logistic Regression hyperparameters

- **Model Evaluation:**
  - Evaluated model using accuracy and F1 score
  - Used log loss when evaluating Logistic Regression

- **Ethical Considerations:**
  - Considered potential bias related to protected demographic characteristics
  - Evaluated limitations caused by unequal representation among demographic groups
  - Considered how incorrect predictions could disproportionately affect underrepresented groups

## Results

- **Logistic Regression:**
  - Accuracy: approximately **81%**
  - F1 Score: approximately **0.69**
  - Performed slightly better than the Neural Network
  - Provided interpretable coefficients that helped identify features associated with the income prediction
