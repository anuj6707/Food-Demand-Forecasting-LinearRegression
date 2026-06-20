# 🍽️ Food Demand Forecasting using Machine Learning

## 📌 Project Overview

This project focuses on forecasting food demand using multiple machine learning regression algorithms.

The objective is to predict the number of meal orders (`num_orders`) based on historical ordering patterns, pricing strategies, promotional campaigns, and fulfillment center characteristics.

The project compares traditional regression models with advanced ensemble learning techniques to determine the most effective approach for real-world demand forecasting.

---

# 🎯 Business Problem

Accurate demand forecasting plays a crucial role in the food delivery and restaurant industry.

Poor demand estimation can result in:

- Food wastage
- Inventory shortages
- Increased operational costs
- Inefficient workforce allocation
- Poor customer experience

The objective of this project is to build predictive models capable of accurately estimating future meal demand, enabling businesses to optimize inventory, pricing strategies, and promotional campaigns.

---

# 📊 Dataset Description

The dataset contains historical food ordering data from multiple fulfillment centers.

### Features

### Time

- Week Number

### Pricing

- Base Price
- Checkout Price

### Promotions

- Homepage Featured
- Emailer Promotion

### Product Information

- Meal ID

### Fulfillment Center

- Center ID

### Target Variable

```text
num_orders
```

Number of meal orders placed during a given week.

---

# 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- XGBoost
- Matplotlib
- Seaborn

---

# ⚙️ Data Preprocessing

The following preprocessing steps were performed before model training.

### Data Cleaning

- Missing value inspection
- Data validation
- Consistency checks

---

## Feature Engineering

### Discount Percentage

A new feature was created to represent the effective discount.

```python
discount = (base_price - checkout_price) / base_price
```

---

### Promotional Discount

Another engineered feature captured the interaction between pricing and promotions.

```python
promo_discount = (
    discount *
    homepage_featured *
    emailer_for_promotion
)
```

This feature models the idea that discounts become more effective when supported by marketing campaigns.

---

## One-Hot Encoding

High-cardinality categorical variables were converted into numerical features.

```python
pd.get_dummies(
    df,
    columns=["meal_id","center_id"]
)
```

Final Dataset:

```
456,548 rows
134 features
```

---

# 📈 Exploratory Data Analysis

The following analyses were performed:

- Correlation Heatmap
- Weekly Demand Trends
- Demand vs Discount
- Demand vs Promotional Discount
- Promotion Impact Analysis
- Feature Importance Analysis

---

# 🤖 Machine Learning Models

## 1. Linear Regression

Used as the baseline regression model.

### Performance

```
R² ≈ 0.50
```

### Observations

- Established baseline performance
- Unable to model complex nonlinear relationships

---

## 2. Ridge Regression

Applied L2 Regularization to reduce model complexity.

Best Alpha:

```
5
```

### Performance

```
R² ≈ 0.49
```

### Observations

- Reduced coefficient variance
- Similar performance to Linear Regression

---

## 3. Lasso Regression

Applied L1 Regularization for automatic feature selection.

### Performance

```
R² ≈ 0.50
```

### Observations

- Eliminated less useful features
- Similar predictive performance to Ridge Regression

---

## 4. K-Nearest Neighbors Regression

Demand was predicted using neighboring historical observations.

Feature scaling was performed using StandardScaler.

### Performance

```
R² ≈ 0.76
MSE ≈ 36,875
```

### Observations

- Significant improvement over linear models
- Captured local nonlinear demand patterns

---

## 5. Random Forest Regression

Random Forest was implemented to model complex nonlinear interactions between pricing, promotions, and meal characteristics.

### Performance

```
Training R² ≈ 0.98

Testing R² ≈ 0.83

MSE ≈ 25,482
```

### Observations

- Strong predictive performance
- Successfully modeled nonlinear relationships
- Slight overfitting observed due to very high training performance

---

## 6. XGBoost Regression ⭐

Extreme Gradient Boosting was implemented to further improve prediction accuracy using sequential boosting.

### Performance

```
Training R² ≈ 0.89

Testing R² ≈ 0.84
```

### Observations

- Best-performing model
- Better generalization than Random Forest
- Highest prediction accuracy among all tested models
- Demonstrated the effectiveness of boosting for structured tabular datasets

---

# 📊 Model Comparison

| Model | Test R² |
|---------|---------:|
| Linear Regression | 0.50 |
| Ridge Regression | 0.49 |
| Lasso Regression | 0.50 |
| KNN Regression | 0.76 |
| Random Forest Regression | 0.83 |
| ⭐ XGBoost Regression | **0.84** |

---

# 📌 Feature Importance Analysis

Random Forest feature importance revealed the primary demand drivers.

| Feature | Importance |
|----------|-----------:|
| Checkout Price | 0.17 |
| Promotional Discount | 0.08 |
| Meal ID 2290 | 0.08 |
| Discount | 0.06 |
| Week | 0.06 |
| Base Price | 0.06 |

---

# 💡 Key Business Insights

### Pricing Strongly Influences Demand

Checkout Price was the most influential feature in predicting customer demand.

This suggests pricing strategy has a major impact on order volume.

---

### Promotions Increase Demand

The engineered **Promotional Discount** feature ranked among the most important predictors.

Marketing campaigns significantly amplify the effectiveness of discounts.

---

### Popular Meals Drive Consistent Orders

Certain meal categories consistently generated higher demand regardless of promotional activity.

These meals can be prioritized for inventory planning and promotional campaigns.

---

### Ensemble Models Outperformed Traditional Regression

Linear Regression, Ridge, and Lasso captured only basic trends.

Tree-based ensemble methods learned complex nonlinear relationships between pricing, promotions, meals, and customer demand.

XGBoost achieved the strongest predictive performance.

---

# 🚀 Business Applications

The final forecasting model can be used for:

- Inventory Planning
- Demand Forecasting
- Workforce Scheduling
- Supply Chain Optimization
- Promotion Planning
- Menu Optimization
- Reducing Food Waste

---

# 🧠 Machine Learning Concepts Demonstrated

- Regression Analysis
- Linear Regression
- Ridge Regression
- Lasso Regression
- KNN Regression
- Random Forest Regression
- XGBoost Regression
- Ensemble Learning
- Feature Engineering
- Hyperparameter Tuning
- GridSearchCV
- Feature Importance Analysis
- Model Comparison
- Business Analytics

---

# 🔮 Future Improvements

Potential future enhancements include:

- LightGBM
- CatBoost
- Time Series Forecasting (ARIMA, Prophet, LSTM)
- SHAP Feature Importance
- Hyperparameter Optimization using Optuna
- Flask Deployment
- Real-Time Demand Forecasting Dashboard

---

# 🏆 Conclusion

This project compared six regression algorithms for forecasting food demand using historical sales, pricing, and promotional data.

Traditional linear models provided useful baseline performance but struggled to capture nonlinear demand behavior. K-Nearest Neighbors significantly improved prediction accuracy by leveraging local relationships within the data.

Tree-based ensemble methods achieved the strongest performance. Random Forest produced a test **R² score of approximately 0.83**, while **XGBoost delivered the highest predictive performance with a test R² score of approximately 0.84**.

The project demonstrates how feature engineering, ensemble learning, and model comparison can substantially improve forecasting accuracy for real-world demand prediction problems in the food delivery industry.

---

## 👨‍💻 Author

Built as part of a machine learning portfolio focused on:

- Predictive Analytics
- Demand Forecasting
- Feature Engineering
- Ensemble Learning
- Applied Machine Learning

