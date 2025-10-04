# 🎯 Audience Scoring for Direct Mail Marketing

## Project Overview

This project focuses on building a predictive model to identify customers most likely to be influenced by a **Direct Mail (DM)** marketing campaign. The primary goal is to optimize customer targeting by predicting their **influence probability** to maximize the campaign's Return on Investment (ROI).

## The Business Problem

How do we efficiently allocate marketing resources? The core problem was to identify customers who are likely to respond to a Direct Mail campaign. We achieved this by developing a robust classification model to score each customer's likelihood of making a purchase following the mailing.

## 🧪 Data Science Lifecycle

This project followed a standard data science lifecycle, from understanding the business objective to model deployment:

1.  **Identifying Problems & Understanding Business** 
2.  **Data Collection** 
3.  **Data Processing**
4.  **Data Analysis** 
5.  **Data Modeling**
6.  **Model Deployment**

---

## 🏗️ Feature Engineering & Target Definition

### Data Sources
The analysis utilized two main datasets, joined on `Gold_Cust_ID`:
* `Sales_Data.csv`: Transaction-level data including price, units, and channel.
* `DM_Dates.csv`: Direct Mail send dates per customer.

### Target Variable: Influenced (1/0)
A customer was marked as **Influenced (1)** if they made a purchase transaction within **30 days** after the `DM Mail Date`. The 30-day window was defined as the business's assumption for measuring influence.

Target=1 if (Tran_Dt>Last_Mailing_Date) AND (Tran_Dt≤Last_Mailing_Date+30)

### Key Features
Aggregated transaction-level data to create customer-level features.

* **RFM Metrics**: Constructed **Recency, Frequency, and Monetary** features from transaction history.
    * *Insight*: Frequent customers tended to spend more.
* **Last Mailing Recency**: Created a feature for the 'Recency of Last Mailing'.
* Missing values were handled using a max+1 strategy.

---

## 🤖 Modeling & Evaluation

### Models Trained
Several classification models were trained and evaluated on the engineered features:
* Logistic Regression 
* Decision Tree
* Random Forest 
* Gradient Boosting 
* Gradient Boosting (Tuned)

### Performance Summary
Models were evaluated using **Area Under the Curve (AUC)**, precision, and recall.

| Model | AUC Score | Notes |
| :--- | :--- | :--- |
| **Gradient Boosting (Tuned)** | **0.9935** | **Best Performer** |
| Logistic Regression | 0.9999 | Excellent baseline |
| Random Forest | 0.9871 | Strong performance |
| Decision Tree | 0.9448 | Reasonable performance |

---

## 🚀 Strategic Recommendations

Based on the model scoring, the following recommendations were made to the marketing team:

* **Targeting Threshold**: Prioritize customers with a predicted influence probability **greater than 0.3**.
* **Customer Prioritization**: Focus marketing spend on **high-frequency and high-monetary** customers.
* **Personalization**: Deploy personalized campaigns based on customers' historical transaction patterns.

## 📈 Future Enhancements

Potential improvements to the model and analysis include:
* **External Data**: Incorporate demographic or other external data sources.
* **Advanced Modeling**: Explore deep learning or advanced time-series models.
* **Channel Data**: Integrate channel interaction data for more granular targeting insights.
