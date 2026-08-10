# Census Income Classification Model

## Table of Contents

1. [Project Background and Overview](#project-background-and-overview)
2. [Data and Methodology](#data-and-methodology)
3. [Results](#results)
4. [Next Steps](#next-steps)

## Project Background and Overview

This project uses demographic and employment data from the 1994 U.S. Census to predict whether an individual's annual income is greater than $50,000.

The goal is to develop and compare machine learning models for binary income classification while also examining class imbalance, feature relationships, model interpretability, and potential ethical concerns associated with demographic data.

The project compares a traditional Logistic Regression model with a Neural Network and evaluates their performance using accuracy and F1 score.

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
  - Built a Neural Network with three hidden layers containing 64, 32, and 16 neurons

- **Model Evaluation:**
  - Evaluated models using accuracy and F1 score
  - Used log loss when evaluating Logistic Regression
  - Compared training and validation performance for the Neural Network
  - Reduced Neural Network training epochs after identifying overfitting

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

- **Neural Network:**
  - Accuracy: approximately **79%**
  - F1 Score: approximately **0.68**
  - Initially showed overfitting when trained for more epochs
  - Reducing training to 15 epochs improved the balance between training and validation performance

- **Model Comparison:**
  - Logistic Regression and the Neural Network produced similar predictive performance
  - Logistic Regression performed slightly better while remaining simpler and easier to interpret
  - Logistic Regression was selected as the preferred model because the additional complexity of the Neural Network did not produce better results
