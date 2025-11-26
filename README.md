# 🚗 Car Price Modeling & Predictive Analytics

## 📌 Project Overview

Purchasing a used car is a complex decision driven by numerous factors such as brand perception, mileage, age, engine type, and fuel efficiency. This project applies data science techniques to determine **what truly drives the price of a car** and builds a predictive model capable of estimating used vehicle prices.

Using a real dataset from a used car dealership, this project explores the relationships between vehicle characteristics and price. By leveraging the **CRISP-DM** methodology, we walk through the complete lifecycle of a machine-learning solution — from business understanding through deployment considerations.

---

## 🧭 CRISP-DM Framework

This project follows the established **Cross-Industry Standard Process for Data Mining**:

1. **Business Understanding**  
   Identify which vehicle attributes most influence price and quantify their predictive power.

2. **Data Understanding**  
   Explore data types, distributions, missing values, outliers, correlations, and domain relevance.

3. **Data Preparation**  
   Encode categorical variables, scale numeric features, engineer new predictors, and ensure data quality.

4. **Modeling**  
   Fit and compare different regression models to estimate car prices.

5. **Evaluation**  
   Analyze performance using MSE, MAE, R², and hold-out validation.

6. **Deployment**  
   Outline steps for operationalizing the model for real-world use.


---

## Business and Data Understanding: 
   - The primary goal was to identify key drivers for used car prices to provide actionable recommendations to a used car dealership.
   - The initial data exploration revealed significant missing values across many columns, as well as outliers in numerical features like price, year, and odometer.

---

## Data Preparation: 
   - **Missing Values:** A comprehensive strategy was implemented, including dropping columns with very high missingness (size, VIN), imputing categorical features with 'unknown' or the mode, and numerical features with the median. This ensured a complete dataset for modeling.
   - **Outlier Handling:** Outliers in price, year, and odometer were addressed by removing erroneous entries (price = 0) and capping extreme values based on IQR bounds. This step helped to create more robust and realistic distributions for these critical features.
   - **Feature Engineering:** A new car_age feature was successfully created from the year column, which is often a strong predictor of vehicle price.

---

## Modeling Approach: 
   - **Feature Selection:** The analysis focused on selected categorical (condition, fuel, drive, cylinders) and numerical (year, odometer, car_age) features, avoiding high-cardinality ones. 
                            - Two preprocessing pipelines were used:
                               * preprocessor: Standard scaling for numeric features and one-hot encoding for categorical features.
                               * preprocessor_Poly: Similar to preprocessor but with PolynomialFeatures(degree=2) applied to numerical features.
   - **Sequential Feature Selection (SFS):** SFS was applied to both sets of preprocessed features to select a subset of 10 features for some linear regression models.
   - **Models:** Six regression models were built and evaluated:
                        - 1.Linear Regression (on 10 SFS-selected features from preprocessor)
                        - 2.Ridge Regression (on all 28 original features from preprocessor)
                        - 3.Lasso Regression (on all 28 original features from preprocessor)
                        - 4.Linear Regression (on 10 SFS-selected features from preprocessor_Poly)
                        - 5.Ridge Regression (on all 34 original features from preprocessor_Poly)
                        - 6.Lasso Regression (on all 34 original features from preprocessor_Poly)

---