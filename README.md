# Codveda Data Analytics Internship

This repository contains the projects completed as part of my
**Data Analytics Internship at Codveda Technology**.

The projects cover different stages of the data analytics workflow,
including data preprocessing, exploratory data analysis, time series
analysis, regression, natural language processing, and business
intelligence dashboard development.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- NLTK
- TextBlob
- WordCloud
- Statsmodels
- Power BI
- DAX
- Jupyter Notebook

---

## Level 1 – Basic

### Task 1: Data Cleaning and Preprocessing

The objective of this task was to prepare a raw dataset for further analysis.

Main steps included:

- Loading and inspecting the dataset
- Checking missing values
- Identifying duplicate records
- Cleaning textual and categorical data
- Standardizing data formats
- Preparing the dataset for further analysis

**Tools:** Python, Pandas

---

### Task 2: Exploratory Data Analysis – Iris Dataset

Exploratory Data Analysis was performed on the Iris flower dataset to
understand feature distributions and relationships between variables.

The analysis included:

- Summary statistics
- Histograms
- Boxplots
- Scatter plots
- Species comparison
- Correlation analysis
- Correlation heatmap

#### Key Findings

- Petal measurements showed stronger separation between flower species than sepal measurements.
- Setosa generally had the smallest petal dimensions.
- Virginica generally had the largest petal dimensions.
- Petal length and petal width showed a very strong positive correlation of approximately **0.96**.

**Tools:** Python, Pandas, Matplotlib, Seaborn

---

## Level 2 – Intermediate

### Task 1: Regression Analysis – House Prices

A simple linear regression model was developed to analyze the relationship
between the average number of rooms and median house value.

#### Model

**Independent Variable:** Average Number of Rooms (`RM`)  
**Target Variable:** Median House Value (`MEDV`)

The dataset was divided into training and testing sets before fitting a
Linear Regression model.

#### Model Results

- Regression Coefficient: **9.35**
- R² Score: approximately **0.37**
- Mean Squared Error: approximately **46.14**
- RMSE: approximately **6.79**

#### Key Finding

The model showed a positive relationship between the average number of
rooms and house value. However, the R² score indicates that room count
alone is not sufficient to explain most of the variation in house prices.

**Tools:** Python, Pandas, Scikit-learn, Matplotlib

---

### Task 2: Time Series Analysis – Apple Stock Price

Time series analysis was performed on historical Apple stock price data.

The analysis included:

- Date preprocessing
- Filtering Apple stock records
- Closing-price visualization
- 20-day moving average
- 50-day moving average
- Monthly resampling
- Seasonal decomposition

#### Key Findings

The stock price demonstrated an overall upward trend during the analyzed
period, while moving averages helped smooth short-term fluctuations.

Seasonal decomposition was also used to separate the series into:

- Trend
- Seasonal component
- Residual component

**Tools:** Python, Pandas, Matplotlib, Statsmodels

---

## Level 3 – Advanced

### Task 2: Customer Churn Analysis Dashboard – Power BI

An interactive Power BI dashboard was developed to analyze customer
churn patterns in a telecommunications dataset.

#### Dashboard KPIs

- **Total Customers:** 3,333
- **Churned Customers:** 483
- **Overall Churn Rate:** 14.5%
- **Average Customer Service Calls:** 1.56

#### Dashboard Visualizations

- Churn Rate by International Plan
- Churn Rate by Customer Service Calls
- Churned Customers by Voice Mail Plan
- Churn Rate by State
- Interactive slicers for customer segmentation

#### Key Insights

- Customers with an international plan had a significantly higher churn rate: **42.4% vs 11.5%**.
- Customer churn increased sharply after approximately **4 or more customer service calls**.
- Customers without a voice mail plan showed a higher churn rate (**16.7%**) compared with customers with a voice mail plan (**8.7%**).
- Churn rates varied across different U.S. states.

#### Dashboard Preview

![Customer Churn Dashboard](Level-3-Advanced/Task-2-Power-BI-Dashboard/dashboard_preview.png)

**Tools:** Power BI, Power Query, DAX

---

### Task 3: NLP Sentiment Analysis

Natural Language Processing techniques were applied to a social media
text dataset to analyze sentiment and word usage.

#### Text Preprocessing

The preprocessing pipeline included:

- Lowercasing
- Removing unnecessary characters
- Tokenization
- Stopword removal
- Lemmatization

Sentiment polarity was calculated using **TextBlob**, and texts were
classified into three categories:

- Positive
- Neutral
- Negative

#### Sentiment Results

- **Neutral:** 341
- **Positive:** 272
- **Negative:** 119

#### Additional Analysis

- Word frequency analysis
- Top frequently used words
- Word cloud visualization

Frequently occurring words included terms such as:

`new`, `life`, `day`, `joy`, `dream`, `feeling`, `moment`, and `heart`.

**Tools:** Python, Pandas, NLTK, TextBlob, WordCloud, Matplotlib

---

## Repository Structure

```text
codveda-data-analytics-internship/
│
├── README.md
├── requirements.txt
│
├── Level-1-Basic/
│   ├── Task-1-Data-Cleaning/
│   └── Task-2-Exploratory-Data-Analysis/
│
├── Level-2-Intermediate/
│   ├── Task-1-Regression-Analysis/
│   └── Task-2-Time-Series-Analysis/
│
└── Level-3-Advanced/
    ├── Task-2-Power-BI-Dashboard/
    └── Task-3-NLP-Sentiment-Analysis/
```

---

## Skills Demonstrated

This internship project demonstrates practical experience in:

- Data Cleaning
- Data Preprocessing
- Exploratory Data Analysis
- Statistical Analysis
- Data Visualization
- Linear Regression
- Model Evaluation
- Time Series Analysis
- Natural Language Processing
- Sentiment Analysis
- Business Intelligence
- Dashboard Development
- DAX Measures
- Data Storytelling

---

## Author

**Ali Ahmad Khanbeigi**

Data Analytics | Business Intelligence | Python | SQL | Power BI
