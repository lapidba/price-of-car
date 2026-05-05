# Used Car Price Analysis Report

## Executive Summary
This report identifies the key factors that influence used car prices using a dataset of 426K vehicles. Our goal is to provide actionable recommendations for a used car dealership to optimize their inventory.

### Key Findings
- **Brand Power:** Premium and luxury brands like **Tesla, Ferrari, and Porsche** have the highest positive impact on price.
- **Fuel Efficiency & Type:** **Diesel** vehicles command a significant premium over gasoline and electric vehicles in the used market.
- **Vehicle Type:** **Off-road** and specialized vehicle types maintain their value better than hatchbacks or economy sedans.
- **Depreciation Drivers:** **Vehicle age** is a stronger driver of price depreciation than odometer reading alone, although both are highly significant.

---

## Technical Analysis (CRISP-DM)

### 1. Business Understanding
The primary objective is to determine what makes a car more or less expensive. This information allows dealerships to fine-tune their inventory to maximize profit margins and turnover.

### 2. Data Understanding
The initial dataset contained significant quality issues:
- **Extreme Outliers:** Prices ranging from $0 to $3.7 Billion.
- **Missing Data:** Over 70% of entries for vehicle size were missing.
- **Cardinality:** The 'model' and 'region' columns had thousands of unique values, requiring careful handling or removal for general modeling.

### 3. Data Preparation
- **Outlier Removal:** Filtered prices to $500 - $100,000 and odometer to < 300,000 miles.
- **Feature Engineering:** Calculated vehicle **age** from the manufacture year.
- **Dimensionality Reduction:** Used **PCA** to capture 63% of variance with 10 components.
- **Segmentation:** Applied **KMeans Clustering** to identify 5 distinct car segments.

### 4. Modeling & Evaluation
We utilized **Ridge Regression** with **GridSearchCV** for hyperparameter tuning.
- **Best Model:** Ridge Regression (Alpha=10.0)
- **Performance:** R-squared of **0.69**, meaning the model explains 69% of the price variance.
- **Mean Absolute Error (MAE):** ~$5,500.

#### Top Positive Drivers of Price:
1. Manufacturer: Tesla (+ $14,364)
2. Manufacturer: Ferrari (+ $12,995)
3. Fuel Type: Diesel (+ $11,795)
4. Manufacturer: Porsche (+ $10,826)

#### Top Negative Drivers of Price:
1. Manufacturer: Fiat (- $8,426)
2. Manufacturer: Mitsubishi (- $6,682)
3. Vehicle Age (- $5,867 per unit of age)
4. Manufacturer: Kia (- $5,330)

### 5. Visualizations
Detailed plots can be found in the `images/` directory:
- `price_distribution.png`: Shows the majority of used cars are priced under $30,000.
- `price_by_condition.png`: Illustrates the premium paid for 'new' and 'like new' conditions.
- `price_vs_odometer.png`: Demonstrates the non-linear relationship between mileage and value.

---

## Recommendations for the Dealership
1. **Acquire Diesel Inventory:** There is a clear market premium for diesel vehicles.
2. **Prioritize Luxury Brands:** Tesla, Porsche, and Ferrari hold their value exceptionally well.
3. **Avoid Economy High-Depreciation Brands:** Limit inventory of brands like Fiat, Mitsubishi, and Kia unless purchased at a significant discount.
4. **Focus on Newer Models:** Age depreciates value faster than mileage; a newer car with higher miles may be a better investment than an older car with low miles.

---

## Project Structure
- `used_car_analysis.ipynb`: The complete technical analysis and modeling process.
- `README.md`: This report.
- `data/vehicles.csv`: The raw dataset (locally stored).
- `images/`: Generated visualizations.

---
*For a detailed look at the code and methodology, please refer to the [Jupyter Notebook](used_car_analysis.ipynb).*
