# Adidas Sales Performance Analytics

## Overview
This project analyses and predicts sales performance for Adidas products 
in the U.S. market using marketing analytics techniques. The dataset 
contains 9,648 rows and 13 columns sourced from Kaggle, covering retailer 
information, product types, pricing, units sold, and profit metrics. 
The analysis explores how Units Sold and Price per Unit affect Total Sales, 
and builds regression and classification models to support data-driven 
business decisions.

---

## What Was Done

### 1. Data Dictionary & Exploration
A data dictionary was created in R to document all 13 variables in the 
dataset, including their data types and descriptions. Key variables 
analysed include:

- **Units Sold** — ranges from 0 to 1,275 with a mean of 257
- **Price per Unit** — averages $45.22, ranging mostly from $35 to $55
- **Total Sales** — highly right-skewed with a mean of $93,273
- **Operating Profit** — mean of $34,425, also right-skewed

---

### 2. Data Exploration & Visualisation
Three key visualisations were produced to understand patterns in the data:

- **Histograms** — Units Sold and Total Sales are right-skewed, meaning 
  most transactions are smaller with a few very large ones. Price per 
  Unit follows a near-normal distribution, showing consistent pricing 
  across products.

- **Scatter Plot** — A strong positive linear relationship was found 
  between Units Sold and Total Sales, confirming that volume is the 
  primary driver of revenue.

- **Correlation Heatmap** — Units Sold, Total Sales and Operating Profit 
  show strong positive correlations (above 0.89). Price per Unit has a 
  weaker correlation (r = 0.44) with Total Sales. Operating Margin 
  negatively correlates with Total Sales (-0.36) and Units Sold (-0.31), 
  suggesting profit margins decrease as volume increases, possibly due 
  to bulk discounts or higher operational costs.

---

### 3. Hypotheses
Three hypotheses were developed based on the exploratory analysis:

- **H1** — Units Sold have a significant positive impact on Total Sales 
  (r = 0.91 confirmed this)
- **H2** — Price per Unit has a significant but weaker positive impact 
  on Total Sales (r = 0.44)
- **H3** — Units Sold and Price per Unit have a significant interaction 
  effect on Total Sales

---

### 4. Multivariate Linear Regression

**Main Effects Model:**  
Both Units Sold and Price per Unit were used to predict Total Sales.

- Adjusted R-squared = **0.8744** (model explains 87.4% of variance)
- Units Sold coefficient = **568.5** — each additional unit sold increases 
  Total Sales by ~$568.50
- Price per Unit coefficient = **2,004** — a $1 price increase raises 
  Total Sales by ~$2,004
- Both predictors statistically significant (p < 2e-16)
- Hypotheses 1 and 2 supported

**Interaction Model:**  
An interaction term (Units Sold × Price per Unit) was added to test H3.

- Adjusted R-squared improved to **0.9493** (94.9% of variance explained)
- Interaction coefficient = **12.35**, statistically significant (p < 2e-16)
- Shows that higher prices amplify the effect of volume on revenue
- Hypothesis 3 supported

The interaction plot confirmed that at higher price levels, selling more 
units results in a much steeper increase in Total Sales, suggesting 
Adidas should prioritise premium product lines in large-scale campaigns.

---

### 5. Classification Model
A logistic regression classification model was built to predict whether 
a transaction results in High or Low Total Sales, using Units Sold and 
Price per Unit as predictors. Transactions above the median Total Sales 
were labelled High (1) and those below as Low (0).

| Metric | Result |
|---|---|
| Accuracy | 91% |
| Precision | 92.9% |
| Recall | 88.8% |
| F1 Score | 90.8% |
| AUC | 0.96 |

The model correctly predicted 4,498 low-sales and 4,283 high-sales 
transactions. The ROC curve confirmed strong model performance, with 
the curve bending sharply towards the top-left corner. An AUC of 0.96 
demonstrates the model can effectively distinguish between high and 
low revenue transactions.

---

## Key Takeaway
Volume (Units Sold) is the primary driver of Adidas sales revenue, 
but pricing amplifies this effect significantly. When high-priced 
products are sold in large quantities, revenue growth is at its 
strongest. The classification model proved highly effective at 
identifying high-revenue transactions, which can help Adidas 
prioritise premium product lines and build smarter, data-driven 
marketing and pricing strategies.

---

## Tools Used
- **R** — data cleaning, regression modelling, classification, 
  and all visualisations
- **Dataset** — Adidas Sales Dataset (Kaggle, 2023)
