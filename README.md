# **Kaggle's Spaceship Titanic Competition - Top 7% Finish**

This repository contains my solution for the [Kaggle Spaceship Titanic competition](https://www.kaggle.com/competitions/spaceship-titanic). The goal of this competition was to predict whether a passenger was transported to an alternate dimension based on personal records recovered from the spaceship's damaged computer system.

This solution achieved a final leaderboard rank of **645**.

## **Project Pipeline**

The project follows a structured machine learning pipeline from data preprocessing to model training and final submission.

### **1. Data Preprocessing & Cleaning**

* **Unified Processing:** The training and test datasets were combined to ensure consistent transformations were applied across all data.
* **Handling Missing Data:** A key part of this project was the imputation strategy.
    * For numerical and related categorical features (`Age`, `RoomService`, `Spa`, etc.), **K-Nearest Neighbors (KNN) Imputer** was used to estimate missing values based on the nearest neighbors.
    * Categorical text columns (`HomePlanet`, `Destination`) were imputed with a placeholder and then **one-hot encoded** to be used in the model.

### **2. Feature Engineering**

New features were created to provide the model with more predictive signals:
* **Cabin Deconstruction:** The `Cabin` feature was split into three distinct features: `Deck`, `Num`, and `Side`.
* **Spending Habits:** The various spending columns (`RoomService`, `FoodCourt`, `ShoppingMall`, etc.) were aggregated to create new features like `amt_spent` (total amount) and `mean_amt_spent`.
* **Composite Features:** Several high-correlation features were combined to create new composite signals for the model.

### **3. Model Selection & Training**

Five different classification models were trained and evaluated to find the best performer:
1.  Logistic Regression (`Accuracy: ~77.0%`)
2.  Decision Tree Classifier (`Accuracy: ~74.7%`)
3.  Random Forest Classifier (`Accuracy: ~79.1%`)
4.  XGBoost Classifier (`Accuracy: ~79.4%`)
5.  **LightGBM (LGBM) Classifier (`Accuracy: ~79.7%`)**

The **LGBM Classifier** provided the highest accuracy on the validation set and was selected to generate the final predictions for the submission file.

## **Key Libraries & Tools**
* **Data Manipulation:** `Pandas`, `NumPy`
* **Machine Learning:** `Scikit-learn`, `XGBoost`, `LightGBM`
* **Data Visualization:** `Matplotlib`, `Seaborn`
