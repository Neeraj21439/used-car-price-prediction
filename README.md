# Used Car Price Prediction

A machine learning project that predicts the selling price of used cars in the Indian market using Python, Pandas and Scikit-learn. It covers the full workflow: data cleaning, exploratory data analysis (EDA), feature engineering, model training and evaluation.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## Problem Statement

Pricing a used car is hard because many factors affect its value, such as age, kilometers driven, engine power and brand. This project builds a regression model that estimates a used car's selling price from these features, which can help buyers and sellers judge whether a price is fair.

## Results at a Glance

| Model | R² Score | MAE (₹) | RMSE (₹) |
|---|---|---|---|
| Linear Regression | 0.69 | 1,33,095 | 2,62,232 |
| **Random Forest** | **0.92** | **73,118** | **1,29,331** |

- **Best model:** Random Forest Regressor, explaining about 92% of the variance in car prices on unseen test data.
- **Top features affecting price:** `max_power`, `age` and `km_driven`.

## Dataset

- **Source:** [Vehicle dataset (CarDekho) on Kaggle](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho)
- **File used:** `Car details v3.csv`
- **Size:** 8,128 rows originally, 6,926 rows after removing 1,202 duplicates
- **Target variable:** `selling_price`

| Column | Description |
|---|---|
| name | Car make and model |
| year | Year of manufacture |
| selling_price | Price the car was sold at (target) |
| km_driven | Total kilometers driven |
| fuel | Fuel type (Petrol, Diesel, CNG, LPG) |
| seller_type | Individual, Dealer or Trustmark Dealer |
| transmission | Manual or Automatic |
| owner | Number of previous owners |
| mileage | Fuel efficiency (kmpl) |
| engine | Engine capacity (CC) |
| max_power | Maximum power (bhp) |
| torque | Engine torque (dropped, inconsistent format) |
| seats | Number of seats |

> The dataset is not included in this repository. Download it from the Kaggle link above and place `Car details v3.csv` in the project folder.

## Tools and Technologies

- **Language:** Python
- **Libraries:** NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn
- **Environment:** Jupyter Notebook
- **Version control:** Git and GitHub

## Project Workflow

### 1. Data Cleaning
- Removed units from `mileage` (kmpl), `engine` (CC) and `max_power` (bhp) and converted them to numeric values.
- Filled missing values in `mileage`, `engine`, `max_power` and `seats` with the column median.
- Removed 1,202 duplicate rows.
- Dropped the `torque` column because of its inconsistent format.

### 2. Feature Engineering
- Created an `age` feature (2026 minus manufacturing year) and dropped `year`.
- Extracted `brand` from the car name and dropped the `name` column.
- Converted categorical columns (`brand`, `fuel`, `seller_type`, `transmission`, `owner`) into numeric form using one-hot encoding, giving 47 input features.

### 3. Exploratory Data Analysis
Visualized with Matplotlib and Seaborn: price distribution, correlation heatmap, average price by brand, price vs age, price vs kilometers driven, price vs max power, and price by fuel type and transmission. A boxplot was also used to inspect outliers in `km_driven`.

**Key insights:**
- `max_power` has the strongest correlation with price (0.69), followed by `engine` (0.44).
- Older cars sell for less: `age` is negatively correlated with price (-0.43).
- Kilometers driven has only a weak negative correlation with price (-0.17).
- Luxury brands such as Lexus, Volvo, BMW, Jaguar, Land Rover, Audi and Mercedes-Benz have the highest average prices, while brands like Peugeot, Opel, Daewoo and Chevrolet are at the lower end.

### 4. Model Building and Evaluation
The data was split into 80% training and 20% testing sets (`random_state=42`). Two models were trained and compared using R², MAE and RMSE. Random Forest clearly outperformed Linear Regression (R² of 0.92 vs 0.69), which suggests the relationship between car features and price is non-linear.

Feature importance from the Random Forest model:
- `max_power` is by far the most important feature (about 0.60).
- `age` comes second (about 0.23).
- `km_driven`, `mileage` and `engine` contribute smaller amounts.

## Visualizations

Add screenshots of your graphs to an `images/` folder and link them here, for example:

```
![Correlation Heatmap](images/heatmap.png)
![Average Price by Brand](images/brand_price.png)
![Feature Importance](images/feature_importance.png)
```

## How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/Neeraj21439/used-car-price-prediction.git
   cd used-car-price-prediction
   ```
2. Install the required libraries
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```
3. Download `Car details v3.csv` from Kaggle and place it in the project folder.
4. Open the notebook and run all cells
   ```bash
   jupyter notebook
   ```

## Project Structure

```
used-car-price-prediction/
├── used-car-price-prediction.ipynb   # Complete analysis and model code
├── README.md                         # Project documentation
└── images/                           # Graphs used in this README
```

## Limitations and Future Improvements

- Results come from a single train-test split; cross-validation would give a more reliable estimate.
- No hyperparameter tuning has been done yet (GridSearchCV or RandomizedSearchCV can be tried).
- Extreme values in `km_driven` and `selling_price` were not removed, so very expensive luxury cars may affect errors.
- Try more models such as Gradient Boosting and XGBoost.
- Build a simple web app (for example with Streamlit) to predict prices from user input.

## Author

**Neeraj Bhardwaj**
B.Tech (Computer Science and Engineering), J.C. Bose University of Science and Technology, YMCA

- LinkedIn: [linkedin.com/in/neeraj-bhardwaj001](https://www.linkedin.com/in/neeraj-bhardwaj001)
- GitHub: [github.com/Neeraj21439](https://github.com/Neeraj21439)
- Email: neeraj.bhardwaj.ds@gmail.com
