---
name: data-analysis
description: "Analyze data, create visualizations, and generate actionable insights. Use when working with data manipulation, statistical analysis, data visualization, or data reporting."
---

# Data Analysis Skill

Analyze data, create visualizations, and generate actionable insights.

## When to Use

Use this skill when the user wants to:
- Analyze data from datasets
- Create data visualizations
- Perform statistical analysis
- Clean and transform data
- Generate data reports
- Find patterns and trends

## Data Analysis Workflow

### 1. Data Understanding
- Examine data structure and content (schema, types, distributions).
- Identify relationships between variables (correlation, causation).
- Understand the context of the data collection process.

### 2. Data Cleaning & Preprocessing
- **Handling Missing Values**: Imputation (mean/median), deletion, or flagging.
- **Removing Duplicates**: Identifying and merging duplicate records.
- **Standardizing Formats**: Ensuring consistent date formats, units, and categorical values.
- **Outlier Detection**: Identifying anomalies that might skew analysis.
- **Feature Engineering**: Creating new variables from existing ones to improve model/analysis quality.

### 3. Data Exploration (EDA)
- Calculate summary statistics (mean, median, mode, variance, standard deviation).
- Find correlations and dependencies between features.
- Detect patterns, trends, and seasonalities in time-series data.

### 4. Statistical Analysis
- **Descriptive Statistics**: Summarizing the main characteristics of a dataset.
- **Inferential Statistics**: Making predictions or inferences about a population based on a sample (e.g., p-values, confidence intervals).
- **Hypothesis Testing**: Validating assumptions (e.s. t-tests, chi-square tests).

### 5. Visualization & Reporting
- Create charts and graphs that tell a story.
- Build interactive dashboards for real-time monitoring.
- Present findings with clear, actionable insights.

## Tools & Libraries

### Python (The Data Science Standard)
- **Pandas**: Powerful data manipulation and analysis.
- **NumPy**: Fundamental package for scientific computing.
- **Matplotlib / Seaborn**: Static plotting and statistical visualization.
- **Plotly**: Interactive, web-based visualizations.
- **Scikit-learn**: Machine learning and predictive modeling.

### JavaScript
- **D3.js**: Low-level, powerful data-driven document manipulation.
- **Chart.js / Recharts**: Easy-to-use charting libraries for web apps.
- **Plotly.js**: Interactive plots for the web.

### R
- **ggplot2**: The gold standard for grammar of graphics visualization.
- **dplyr / tidyr**: Data manipulation and tidying.

## Implementation Example (Python/Pandas)

```python
import pandas as pd

# Load data
df = pd.read_csv('sales_data.csv')

# 1. Data Cleaning: Handle missing values and duplicates
df = df.drop_duplicates().fillna({'revenue': 0, 'customer_id': 'Unknown'})

# 2. Feature Engineering: Create a 'profit' column
df['profit'] = df['revenue'] - df['cost']

# 3. Aggregation: Monthly revenue per region
monthly_revenue = df.groupby(['region', 'month'])['revenue'].sum().reset_index()

# 4. Statistical Summary
print(df.describe())
print(f"Correlation between Price and Quantity: {df['price'].corr(df['quantity'])}")
```

## Common Pitfalls

- **Correlation vs. Causation**: Assuming that because two things happen together, one caused the other.
- **Selection Bias**: Analyzing data that isn's representative of the whole population.
- **Overfitting**: Creating models that are too complex and capture noise instead of the underlying signal.
- **Ignoring Outliers**: Not checking if extreme values are errors or important signals.
- **Visualization Misrepresentation**: Using truncated axes or inappropriate chart types to mislead the viewer.

## Deliverables

- Analysis report with key findings and insights.
- Data visualizations (charts, graphs, dashboards).
- Data cleaning and transformation pipelines.
- Statistical analysis results (p-values, coefficients, etc.).
- Actionable recommendations based on data.

## Quality Checklist

- [ ] Data is properly cleaned and validated.
- [ ] Analysis is statistically sound and avoids common fallacies.
- [ ] Visualizations are clear, accurate, and tell a story.
- [ ] Findings are actionable and directly answer the business question.
- [ ] Code is reproducible and well-documented.
