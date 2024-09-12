# Premier League Match Result Prediction

This repository contains an implementation aimed at predicting the results of Premier League matches based on match characteristics and statistics. The objective is to test various classification models and optimize the best-performing model using hyperparameter tuning to improve the accuracy of predictions.

## Project Overview

1. **Data Preprocessing**:  
   The dataset is cleaned by removing irrelevant columns such as date, time, match reports, and captain information. Columns like "goals for" and "goals against" are also removed to avoid leaking the target outcome into the model. Missing values are checked using a matrix, confirming no need for data imputation.

2. **Categorical Variable Encoding**:
   - **Round**: The matchweek number (1 to 38) is extracted from the "Matchweek" column, as the timing of a match can be crucial, especially late in the season.
   - **Day**: The day of the week might impact the match outcome, with most matches played between Friday and Sunday.
   - **Venue**: Matches are labeled as home (1) or away (0), as the home team often has an advantage.
   - **Formation**: The formation is a key factor in football strategy, with more frequent formations assigned higher values.
   - **Referee**: Referees are ranked based on frequency, with more common referees given higher values.
   - **Teams**: Teams are ranked, with stronger teams in recent years assigned higher values.

3. **Model Comparison**:  
   Several classification models are imported and compared:
   - Logistic Regression
   - Random Forest Classifier
   - Support Vector Machine (SVM)
   - K-Nearest Neighbors (KNN)
   - Decision Tree Classifier
   - Gradient Boosting Classifier
   - Ada Boost Classifier
  
   These models are trained on the processed data, and their performance is stored in a DataFrame for comparison.

4. **Best Model Optimization**:  
   The model with the highest accuracy, precision, recall, and F1 score was the **Random Forest Classifier**. A grid search was then performed to fine-tune its hyperparameters, leading to the following optimal settings:
   - Max depth: 40
   - Min samples leaf: 1
   - Min samples split: 2
   - Estimators: 400

5. **Results**:  
   The optimized Random Forest model showed improvements across all key metrics, including accuracy, precision, recall, and F1 score. Confusion matrices were printed to visualize performance, showing improved prediction accuracy for wins and losses, though both models struggled with predicting draws.

## Files

- `matches_classification.ipynb`: Contains the implementation of the models and hyperparameter tuning.
- `Explicación Código.pdf`: A detailed explanation of the project, including data preprocessing steps, model comparison, and hyperparameter tuning results.
 
## How to Run
1. Clone the repository.
2. Install the necessary dependencies:
pip install -r requirements.txt

3. Run the Jupyter notebook to see the full implementation and results.
