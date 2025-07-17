### 1. **Imports and Setup**

This imports essential libraries:

* `pandas` and `numpy` for data manipulation
* `matplotlib.pyplot` and `seaborn` for visualization

---

### 2. **Exploratory Data Analysis (EDA)**

* Loads California housing dataset from CSV
* Displays first few rows, structure, and statistics of all columns

---

### 3. **Missing Value Detection**

Checks how many missing values each column has

```python
df[df['total_bedrooms'].isna()][['longitude', 'latitude']]
```

---

### 4. **Missing Value Handling**

Options:

* Drop missing rows: `df.dropna(subset=['total_bedrooms'])`
* Fill with median: safer against skew

```python
df['total_bedrooms'] = df['total_bedrooms'].fillna(df['total_bedrooms'].median())
df.isna().sum()
```

---

### 5. **Correlation Analysis**

* Drop non-numeric column (`ocean_proximity`) for correlation
* Plot heatmap to visualize linear relationships
* Observes that `median_income` correlates strongly with `median_house_value`

---

```
sns.scatterplot(data=strat_train_set, x="median_income", y="median_house_value")
```
---
### 6. **Models Used**

* Linear Regression, achieveing 61% accuracy
* Polynomial Regression, achieving 64% accuracy
* Random Forest Regressor, achieving 81% accuracy
---

### 7. Evaluation
- **Visual Prediction Plot**:
  - True vs predicted values were plotted.
  - Points closely clustered around the identity line indicate good performance.
  - Overpredictions (points above the line) and underpredictions (below) are evenly distributed, suggesting low bias.

- **Interpretation**:
  - The model successfully captures the linear trend between features and house value.
  - Although not perfect, the model provides a strong baseline with interpretable results.
---

### 8. Summary:

The notebook carefully preprocesses the California housing dataset:

* Handles missing values
* Performs correlation analysis
* Uses several models to improve accuracy
* Plots a Residual Distribution graph to show how models improve
* Finally achieves over 80% accuracy
