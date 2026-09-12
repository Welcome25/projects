Advertising Sales Prediction using Linear Regression

A machine learning project that uses Multiple Linear Regression to predict product sales based on advertising spending across TV, Radio, and Newspaper.

Project Overview

This project demonstrates an end-to-end regression workflow using Python and Scikit-learn.

The project includes:

Loading the Advertising dataset
Data inspection
Handling the unnecessary index column
Exploratory data analysis
Feature-target separation
Train-test split
Multiple Linear Regression
Model coefficient analysis
Sales prediction
Model evaluation
Actual vs predicted visualization
Feature coefficient visualization
Dataset

The dataset contains advertising expenditure across three media channels and the resulting sales.

Columns
Column	Description
Unnamed: 0	Dataset index column; removed before modeling
TV	Advertising budget spent on TV
Radio	Advertising budget spent on Radio
Newspaper	Advertising budget spent on Newspaper
Sales	Product sales; target variable
Machine Learning Problem

This is a supervised regression problem.

Input Features
TV
Radio
Newspaper

Target
Sales


The goal is to learn the relationship between advertising expenditure and sales.

Linear Regression

The model estimates sales using a linear combination of the advertising features:

Sales = β₀ + β₁(TV) + β₂(Radio) + β₃(Newspaper)


Where:

β₀ = intercept
β₁ = TV coefficient
β₂ = Radio coefficient
β₃ = Newspaper coefficient

The coefficients indicate how the predicted sales change as each advertising feature changes while the other features are held constant.

Project Workflow
Advertising Dataset
        ↓
Data Inspection
        ↓
Remove Unnecessary Index
        ↓
Feature Selection
        ↓
Train/Test Split
        ↓
Linear Regression
        ↓
Predictions
        ↓
Model Evaluation
        ↓
Visualization

Dataset Preprocessing

The column:

Unnamed: 0


is treated as an unnecessary index column and removed.

The model uses:

TV
Radio
Newspaper


as input features.

Sales is used as the target variable.

Train-Test Split

The dataset is divided into:

80% → Training data
20% → Testing data


The random state is set to 42 so that the experiment can be reproduced.

Model

The project uses:

LinearRegression()


from Scikit-learn.

This is a multiple linear regression model because there are three independent variables.

Evaluation Metrics

The model is evaluated using four common regression metrics.

Mean Absolute Error — MAE

MAE measures the average absolute difference between actual and predicted sales.

Lower values indicate better performance.

Mean Squared Error — MSE

MSE calculates the average squared prediction error.

Lower values indicate better performance.

Root Mean Squared Error — RMSE

RMSE is the square root of MSE.

It is expressed in the same units as the target variable.

Lower values indicate better performance.

R² Score

R² measures how much of the variation in sales is explained by the model.

A value closer to 1 indicates a stronger fit.

Results

Run the project to generate the exact metrics for your dataset.

The program displays:

MAE
MSE
RMSE
R² Score


It also displays the learned coefficients for:

TV
Radio
Newspaper

Visualizations

The project generates two visualizations.

Actual vs Predicted Sales
results/actual_vs_predicted.png


This plot compares the actual sales values against the model's predictions.

Points closer to the diagonal line indicate more accurate predictions.

Feature Coefficients
results/feature_coefficients.png


This visualization shows the learned coefficient for each advertising channel.

Example Prediction

The project includes an example prediction using:

TV = 150
Radio = 30
Newspaper = 20


The trained model predicts the expected sales for these advertising expenditures.

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/advertising-linear-regression.git


Move into the project directory:

cd advertising-linear-regression


Create a virtual environment:

python -m venv venv

Windows
venv\Scripts\activate

macOS/Linux
source venv/bin/activate


Install dependencies:

pip install -r requirements.txt

Dataset Setup

Place your CSV file here:

data/Advertising.csv


The CSV should contain:

Unnamed: 0
TV
Radio
Newspaper
Sales

Run the Project

From the project root:

python src/train.py

Output

The project creates:

results/
├── actual_vs_predicted.png
├── feature_coefficients.png
└── predictions.csv


It also prints model performance and coefficient information in the terminal.

Example Repository Structure
advertising-linear-regression/
│
├── data/
│   └── Advertising.csv
│
├── notebooks/
│   └── advertising_linear_regression.ipynb
│
├── src/
│   └── train.py
│
├── results/
│   ├── actual_vs_predicted.png
│   ├── feature_coefficients.png
│   └── predictions.csv
│
├── requirements.txt
├── README.md
└── .gitignore

Technologies Used
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Jupyter Notebook
Future Improvements

Possible improvements include:

Exploratory Data Analysis
Correlation heatmap
Individual feature vs sales plots
Residual analysis
Polynomial Regression
Ridge Regression
Lasso Regression
Random Forest Regression
XGBoost Regression
Cross-validation
Hyperparameter tuning
Streamlit deployment
Disclaimer

This project is intended for educational and portfolio purposes.