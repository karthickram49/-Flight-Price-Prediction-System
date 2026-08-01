# ✈️ Flight Price Prediction using Machine Learning

## 📌 Project Overview
Flight ticket prices can be highly dynamic and unpredictable due to factors like departure timings, routes, number of stops, and airlines. This project applies Exploratory Data Analysis (EDA) and Machine Learning techniques to predict airfare based on historical travel features.

The objective is to help passengers estimate future travel costs and assist airlines in optimizing price strategy through accurate data-driven forecasts.

---

## 📊 Dataset Description
The dataset contains key travel features used to analyze and predict flight prices:

| Column Name | Description |
| :--- | :--- |
| **Airline** | Name of the airline operating the flight (e.g., IndiGo, Jet Airways, Air India) |
| **Date_of_Journey** | Date on which the passenger's journey starts |
| **Source** | Origin location of the flight |
| **Destination** | Final destination location |
| **Route** | Route path taken by the flight from source to destination |
| **Arrival_Time** | Time at which the flight reaches the destination |
| **Duration** | Total duration taken to complete the journey |
| **Total_Stops** | Number of intermediate stops during the flight |
| **Additional_Info** | Information on amenities, meal inclusion, etc. |
| **Price** | Target Variable: Total ticket price for the journey |

---

## 🛠️ Project Workflow

1. **Exploratory Data Analysis (EDA):**
   - Analyzed relationships between airlines, stops, routes, and pricing trends.
   - Handled missing values and identified outliers.

2. **Feature Engineering & Preprocessing:**
   - Extracted `Day`, `Month`, and `Year` from `Date_of_Journey`.
   - Extracted hours and minutes from `Departure_Time`, `Arrival_Time`, and `Duration`.
   - Categorical encoding: Target/Frequency Encoding and One-Hot Encoding for high-cardinality features (`Airline`, `Source`, `Destination`).
   - Encoded ordinal variables like `Total_Stops`.

3. **Model Training & Evaluation:**
   - Evaluated multiple machine learning models:
     - **Linear Regression**
     - **Decision Tree Regressor**
     - **Random Forest Regressor**
     - **XGBoost Regressor** / **Extra Trees Regressor**
   - Metrics used for evaluation: **Root Mean Squared Error (RMSE)**, **Mean Absolute Error (MAE)**, and **$R^2$ Score**.

4. **Model Comparison & Selection:**
   - Evaluated models using cross-validation to prevent overfitting.
   - Selected the optimal model based on generalization performance and low error variance for production deployment.

---

## ⚠️ Challenges Faced & Solutions

| Challenge | Impact | Technique / Solution Used & Reason |
| :--- | :--- | :--- |
| **Complex Temporal Data Formats** | Raw `Duration`, `Arrival_Time`, and `Date_of_Journey` were in string formats unsuitable for numerical modeling. | Applied regex-based feature extraction to convert timestamps into separate numerical features (`Duration_hours`, `Duration_mins`, `Journey_day`, etc.). |
| **High Cardinality Categorical Data** | Features like `Route` and `Airline` introduced sparse matrices if standard One-Hot Encoding was applied directly. | Used **Ordinal Encoding** for `Total_Stops` and a combination of **One-Hot Encoding** and feature reduction/grouping for high-cardinality categorical features. |
| **Non-Linear Relationships & Skewness** | Ticket prices exhibit non-linear patterns depending on advance booking windows, flight timing, and seasonal spikes. | Deployed tree-based ensemble algorithms (**Random Forest**, **XGBoost**) that inherently capture non-linear feature interactions without strict distribution assumptions. |

---

## 📈 Model Comparison Report Summary

* **Baseline Models:** Linear Regression provided a baseline $R^2$ score but struggled with non-linear feature interactions.
* **Tree-Based Models:** Decision Trees captured complex routes better, but showed signs of overfitting on training data.
* **Ensemble Models (Best Performers):** **Random Forest** / **XGBoost Regressor** achieved the lowest RMSE/MAE and the highest $R^2$ score on test data.
* **Production Recommendation:** The tuned **Random Forest / XGBoost model** is recommended for deployment due to high accuracy, robustness against outliers, and stability across diverse flight routes.

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/flight-price-prediction.git](https://github.com/your-username/flight-price-prediction.git)
