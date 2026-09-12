IPL Score Prediction using Random Forest

A machine learning regression project that uses a Random Forest Regressor to predict the total IPL innings score from match and current-innings information.

Project Overview

This project demonstrates an end-to-end machine learning workflow using IPL cricket data.

The project includes:

Data loading
Data inspection
Data cleaning
Feature selection
Missing-value handling
Categorical feature encoding
Train-test splitting
Random Forest Regression
Model evaluation
Actual vs predicted visualization
Feature importance analysis
Example IPL score prediction
Dataset

The dataset contains IPL innings-level information.

Dataset Columns
Column	Description
mid	Match identifier
date	Match date
venue	Stadium/venue
bat_team	Batting team
bowl_team	Bowling team
batsman	Current batsman
bowler	Current bowler
runs	Current innings score
wickets	Current wickets lost
overs	Current over
runs_last_5	Runs scored during the previous 5 overs
wickets_last_5	Wickets lost during the previous 5 overs
striker	Current striker
non-striker	Current non-striker
total	Final innings total
Machine Learning Problem

This is a supervised regression problem.

The goal is to predict:

total


which represents the final score of the innings.

Input Features

The model uses:

venue
bat_team
bowl_team
runs
wickets
overs
runs_last_5
wickets_last_5

Target
total

Important Data Leakage Consideration

The target variable is total.

Therefore, total must not be used as an input feature.

The following columns are also removed from this implementation:

mid
date
batsman
bowler
striker
non-striker


The player-level columns are removed to create a simpler team/innings-state model and avoid unnecessarily high-cardinality categorical features.

Random Forest Regression

Random Forest is an ensemble machine learning algorithm that combines many decision trees.

Training Data
     ↓
 ┌─────────────┐
 ↓             ↓
Tree 1       Tree 2
 ↓             ↓
Tree 3       Tree 4
 ↓             ↓
    ...
     ↓
Combine Predictions
     ↓
Predicted Score


For regression, the predictions from the individual trees are combined to produce the final prediction.

Why Random Forest?

Random Forest is useful for this problem because it can:

Model nonlinear relationships
Capture interactions between features
Handle numerical features
Work with complex feature relationships
Provide feature importance
Usually require less feature engineering than linear models
Preprocessing
Categorical Features

The following columns are categorical:

venue
bat_team
bowl_team


They are converted into numerical representations using One-Hot Encoding.

Numerical Features

The following columns are numerical:

runs
wickets
overs
runs_last_5
wickets_last_5


Missing numerical values are filled using the median.

Project Workflow
IPL Dataset
     ↓
Data Inspection
     ↓
Data Cleaning
     ↓
Remove Unnecessary Columns
     ↓
Separate Features & Target
     ↓
Train/Test Split
     ↓
Categorical Encoding
     ↓
Random Forest Regressor
     ↓
Predictions
     ↓
Model Evaluation
     ↓
Feature Importance

Model Configuration

The default model uses:

RandomForestRegressor(
    n_estimators=200,
    random_state=42,
    n_jobs=-1
)

Number of Trees
n_estimators = 200


The forest contains 200 decision trees.

Increasing the number of trees can improve stability, although training time also increases.

Evaluation Metrics

The model is evaluated using:

MAE

Mean Absolute Error measures the average absolute difference between the actual and predicted scores.

Lower is better.

MSE

Mean Squared Error penalizes larger prediction errors more strongly.

Lower is better.

RMSE

Root Mean Squared Error is the square root of MSE and is expressed in runs.

Lower is better.

R² Score

R² measures how much of the variation in the target score is explained by the model.

A value closer to 1 indicates a stronger fit.

Results

Run the project to calculate the exact results for your version of the dataset.

The program displays:

MAE
MSE
RMSE
R² Score


It also prints the most important features according to the Random Forest model.

Visualizations

The project generates two plots.

Actual vs Predicted
results/actual_vs_predicted.png


This plot compares actual IPL innings totals with the model's predictions.

Predictions closer to the diagonal line represent smaller errors.

Feature Importance
results/feature_importance.png


This plot displays the 15 most important features used by the Random Forest.

Example Prediction

The project includes an example innings state:

Runs = 80
Wickets = 2
Overs = 12
Runs Last 5 Overs = 45
Wickets Last 5 Overs = 1


The model uses the corresponding venue and team information from the dataset to estimate the final innings score.

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/random-forest-ipl-score-prediction.git


Move into the project directory:

cd random-forest-ipl-score-prediction


Create a virtual environment:

python -m venv venv

Windows
venv\Scripts\activate

macOS/Linux
source venv/bin/activate


Install dependencies:

pip install -r requirements.txt

Dataset Setup

Place your dataset at:

data/ipl.csv


The CSV should contain:

mid
date
venue
bat_team
bowl_team
batsman
bowler
runs
wickets
overs
runs_last_5
wickets_last_5
striker
non-striker
total

Run the Project

From the project root:

python src/train.py

Output

The project generates:

results/
├── actual_vs_predicted.png
├── feature_importance.png
└── predictions.csv

Example Repository Structure
random-forest-ipl-score-prediction/
│
├── data/
│   └── ipl.csv
│
├── notebooks/
│   └── random_forest_ipl.ipynb
│
├── src/
│   └── train.py
│
├── results/
│   ├── actual_vs_predicted.png
│   ├── feature_importance.png
│   └── predictions.csv
│
├── requirements.txt
├── README.md
└── .gitignore

Future Improvements

Possible improvements include:

Hyperparameter tuning using GridSearchCV
RandomizedSearchCV
Cross-validation
XGBoost comparison
Gradient Boosting comparison
Linear Regression comparison
Extra Trees Regression
Better time-aware train/test splitting
Player-level feature engineering
Recent batting/bowling form
Venue-specific statistics
Team-specific scoring rates
Streamlit score prediction application
Live IPL score prediction interface
Important Note

This project predicts an innings total from the information available at a particular point in an innings.

For a realistic predictive system, the train/test split should respect match chronology rather than randomly mixing observations from the same matches across training and testing data. Otherwise, the reported test performance may be overly optimistic because observations from the same match can be highly related.

Technologies Used
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Jupyter Notebook
Disclaimer

This project is intended for educational and portfolio purposes. Predictions should not be interpreted as guaranteed cricket outcomes.