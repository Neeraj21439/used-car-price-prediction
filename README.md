# Used Car Price Prediction

A machine learning project that predicts the selling price of used cars in the Indian market using Python, Pandas and Scikit-learn. It covers the full workflow: data cleaning, exploratory data analysis (EDA), feature engineering, model training and evaluation.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## Problem Statement

Pricing a used car is hard because many factors affect its value, such as age, kilometers driven, fuel type, engine power and brand. This project builds a regression model that estimates a used car's selling price from these features, which can help buyers and sellers judge whether a price is fair.

## Dataset

- **Source:** [Vehicle dataset (CarDekho) on Kaggle](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho)
- **File used:** `Car details v3.csv`
- **Size:** `XXXX` rows after cleaning (originally `XXXX`)
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
- Removed duplicate rows.
- Dropped the `torque` column because of its inconsistent format.

### 2. Feature Engineering
- Created an `age` feature (current year minus manufacturing year) and dropped `year`.
- Extracted `brand` from the car name.
- Converted categorical columns (`fuel`, `seller_type`, `transmission`, `owner`, `brand`) into numeric form using one-hot encoding.

### 3. Exploratory Data Analysis
Key questions explored with Matplotlib and Seaborn:
- How is the selling price distributed?
- How do car age and kilometers driven affect price?
- How does engine power relate to price?
- Do fuel type and transmission change the price?
- Which brands have the highest average price?

**Key insights:**
- `INSIGHT 1` (example: price drops as the car gets older)
- `INSIGHT 2` (example: higher max power is linked to a higher price)
- `INSIGHT 3` (example: diesel and automatic cars tend to sell for more)

### 4. Model Building
The data was split into 80% training and 20% testing sets (`random_state=42`). The following models were trained and compared:

- Linear Regression
- Random Forest Regressor
- `ADD ANY OTHER MODEL YOU USED`

## Results

| Model | R² Score | MAE | RMSE |
|---|---|---|---|
| Linear Regression | `X.XX` | `XXXX` | `XXXX` |
| Random Forest | `X.XX` | `XXXX` | `XXXX` |

**Best model:** `MODEL NAME`, with an R² of `X.XX` on the test set.

**Top features affecting price:** `FEATURE 1`, `FEATURE 2`, `FEATURE 3`

## Visualizations

Add 2-3 screenshots of your best graphs here, for example:

```
![Price vs Age](images/price_vs_age.png)
![Correlation Heatmap](images/heatmap.png)
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
├── notebook.ipynb        # Complete analysis and model code
├── README.md             # Project documentation
└── images/               # Graphs used in this README
```

## Limitations and Future Improvements

- Tune hyperparameters with GridSearchCV or RandomizedSearchCV.
- Try more models such as Gradient Boosting and XGBoost.
- Handle outliers in `km_driven` and `selling_price` more carefully.
- Build a simple web app (for example with Streamlit) to predict prices from user input.

## Author

**Neeraj Bhardwaj**
B.Tech (Computer Science and Engineering), J.C. Bose University of Science and Technology, YMCA

- LinkedIn: [linkedin.com/in/neeraj-bhardwaj001](https://www.linkedin.com/in/neeraj-bhardwaj001)
- GitHub: [github.com/Neeraj21439](https://github.com/Neeraj21439)
- Email: neeraj.bhardwaj.ds@gmail.com
