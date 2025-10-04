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

[cite_start]$$\text{Target} = 1 \text{ if } (\text{Tran\_Dt} > \text{Last\_Mailing\_Date}) \text{ AND } (\text{Tran\_Dt} \le \text{Last\_Mailing\_Date} + 30)$$ [cite: 17, 18, 19]

### Key Features
[cite_start]Aggregated transaction-level data to create customer-level features[cite: 53].

* [cite_start]**RFM Metrics**: Constructed **Recency, Frequency, and Monetary** features from transaction history[cite: 8, 12].
    * [cite_start]*Insight*: Frequent customers tended to spend more[cite: 9].
* [cite_start]**Last Mailing Recency**: Created a feature for the 'Recency of Last Mailing'[cite: 14].
* [cite_start]Missing values were handled using a $\text{max} + 1$ strategy[cite: 15].

---

## 🤖 Modeling & Evaluation

### Models Trained
[cite_start]Several classification models were trained and evaluated on the engineered features[cite: 21, 22]:
* [cite_start]Logistic Regression [cite: 21]
* [cite_start]Decision Tree [cite: 21]
* [cite_start]Random Forest [cite: 21]
* [cite_start]Gradient Boosting [cite: 21]
* [cite_start]Gradient Boosting (Tuned) [cite: 21]

### Performance Summary
[cite_start]Models were evaluated using **Area Under the Curve (AUC)**, precision, and recall[cite: 23].

| Model | AUC Score | Notes |
| :--- | :--- | :--- |
| **Gradient Boosting (Tuned)** | **0.9935** | [cite_start]**Best Performer** [cite: 28] |
| Logistic Regression | 0.9999 | [cite_start]Excellent baseline [cite: 25] |
| Random Forest | 0.9871 | [cite_start]Strong performance [cite: 26] |
| Decision Tree | 0.9448 | [cite_start]Reasonable performance [cite: 27] |

---

## 🚀 Strategic Recommendations

[cite_start]Based on the model scoring, the following recommendations were made to the marketing team[cite: 29]:

* [cite_start]**Targeting Threshold**: Prioritize customers with a predicted influence probability **greater than 0.3**[cite: 30].
* [cite_start]**Customer Prioritization**: Focus marketing spend on **high-frequency and high-monetary** customers[cite: 31].
* [cite_start]**Personalization**: Deploy personalized campaigns based on customers' historical transaction patterns[cite: 32].

## 📈 Future Enhancements

[cite_start]Potential improvements to the model and analysis include[cite: 33]:

* [cite_start]**External Data**: Incorporate demographic or other external data sources[cite: 34].
* [cite_start]**Advanced Modeling**: Explore deep learning or advanced time-series models[cite: 36].
* [cite_start]**Channel Data**: Integrate channel interaction data for more granular targeting insights[cite: 37].

***

Does this look like the kind of clear, results-focused summary you were hoping for?
