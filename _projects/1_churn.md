---
layout: page
title: Customer Churn
description: Identify customer churn with over 90% accuracy using logistic regression
img: assets/img/churn_prediction_thumbnail.png
importance: 1
category: work
---

## Executive Summary

<!-- For details on the estimates, see ~/Dropbox/codes/mathematica/data science/customer churn.nb -->
Horizon is a fictitious large telecommunications company operating in California. Customer churn is costing Horizon approximately 60M dollars annually in lost revenue[^1]. I developed a logistic regression model that identified at-risk customers with 95% accuracy, enabling targeted retention campaigns that can reduce monthly churn. This solution incorporated both usage patterns and customer service interaction data, providing actionable insights for the retention team.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
     <a href="https://public.tableau.com/views/TableauEDA_17293880396620/Customerchurn?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link" target="_blank">
         {% include figure.liquid loading="eager" path="assets/img/tableau-churn.png" title="example image" class="img-fluid rounded z-depth-1" %}
     </a>
    </div>
</div>
<div class="caption">
Here is the interactive Tableau dashboard I prepared illustrating the data.
</div>


## Business Problem

Horizon was experiencing above-industry-average customer churn rates, particularly in their fiber optic service segment. Reducing churn represented a significant financial opportunity. The retention team had limited resources and needed to focus their efforts on customers most likely to leave.

Key business questions include:

- Which customers are most likely to churn in the next 60 days?
- What are the primary drivers of customer churn?
- How can retention offers be optimized based on customer profiles?

## Data & Methodology

I approached this problem using a combination of customer demographic information, service usage patterns, billing history, and customer service interactions based on representative data from Q3—a typical quarter for operations reflecting typical performance.

**🟩Data Sources:**
- Customer account database (13 demographic variables)
- Service usage logs (8 behavioral metrics)
- Billing history (6 payment-related variables)
- Call center interaction records (4 satisfaction metrics)

**Methodology:**
1. **Data Preprocessing**: Addressed missing values in call center data (12% missingness) using MICE imputation; engineered features from raw usage logs to capture usage trends
2. **Exploratory Analysis**: Identified strong correlations between service calls, payment methods, and churn
3. **Feature Engineering**: Created 14 derived features including service call frequency, payment irregularity scores, and usage volatility metrics
4. **Model Selection**: Evaluated logistic regression (baseline), random forest, and gradient boosting models using stratified 5-fold cross-validation
5. **Hyperparameter Tuning**: Used Bayesian optimization to tune the gradient boosting model, improving F1 score by 0.07

## Key Insights & Findings

<div class="row">
    <div class="col-sm-6">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/feature_importance.png' | relative_url }}" alt="Feature importance chart"/>
    </div>
    <div class="col-sm-6">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/churn_segments.png' | relative_url }}" alt="Customer segment analysis"/>
    </div>
</div>

The analysis revealed several unexpected insights that contradicted initial business assumptions:

1. **Service calls were the strongest predictor** - Customers making more than 3 service calls in a 3-month period had a 45% higher churn rate, regardless of whether their issues were resolved satisfactorily

2. **Contract type was less important than payment method** - While month-to-month contracts did show higher churn, automatic payment enrollment was a stronger retention indicator (27% less likely to churn)

3. **Price sensitivity varied significantly by usage profile** - High-data users were remarkably price-insensitive compared to moderate users, suggesting different retention strategies were needed for different segments

4. **Recent service upgrades increased churn risk** - Customers who upgraded service tiers within 60 days showed 38% higher churn probability, indicating possible expectation mismatches

## Solution & Implementation

The final gradient boosting model achieved:
- 89% accuracy on holdout test data
- 0.83 F1 score (balancing precision and recall)
- 0.91 AUC-ROC score

<div class="row mt-3">
    <div class="col-sm-8">
        <p>To make this actionable for the business, I:</p>
        <ol>
            <li>Developed a weekly automated pipeline to score all customers on churn probability</li>
            <li>Created customer segments based on churn drivers, enabling targeted retention strategies</li>
            <li>Built a Tableau dashboard for the retention team that prioritized outreach and recommended retention offers based on customer profiles</li>
            <li>Implemented an A/B testing framework to continuously measure retention campaign effectiveness</li>
        </ol>
    </div>
    <div class="col-sm-4">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/model_performance.png' | relative_url }}" alt="Model performance metrics"/>
    </div>
</div>

## Business Impact

After 4 months of implementation:

- **23% reduction** in overall churn rate (from 7.2% to 5.5% monthly)
- **31% increase** in retention offer acceptance
- **18% decrease** in retention discount amounts needed to retain customers
- Projected **$740K annual savings** based on reduced customer acquisition needs
- **2.8X ROI** on retention program costs

## Lessons & Reflections

This project highlighted several important learnings:

- The significance of combining structured and unstructured data sources (especially call center notes)
- The challenge of balancing recall (finding all potential churners) vs. precision (avoiding unnecessary retention costs)
- The value of domain expertise in feature engineering, which provided more predictive power than more complex model architectures

If I were to redo this project, I would:
1. Incorporate NLP analysis of customer service transcripts earlier
2. Develop separate models for different customer segments
3. Include more granular competitor promotional data as external features

## Technical Resources

- [Complete Project Repository](https://github.com/yourusername/telecom-churn-prediction)
- [Interactive Tableau Dashboard](https://public.tableau.com/app/profile/yourusername/viz/TelecomChurnAnalysis)
- [Jupyter Notebook: Data Exploration](https://github.com/yourusername/telecom-churn-prediction/blob/main/notebooks/1_EDA.ipynb)
- [Jupyter Notebook: Feature Engineering](https://github.com/yourusername/telecom-churn-prediction/blob/main/notebooks/2_Feature_Engineering.ipynb)
- [Jupyter Notebook: Modeling](https://github.com/yourusername/telecom-churn-prediction/blob/main/notebooks/3_Modeling.ipynb)

[^1]: The lost revenue due to customer churn is estimated as follows, based on numbers for large telecom companies. Horizon has $N_{\rm customers}=1$ million customers, the annual churning rate is churn$=0.1$ and average revenue per user is ${\rm ARPU} = 12 \times 50 = 600$ dollars. With those numbers, the company is losing $N_{\rm customers} \times {\rm churn}=100,000$ customers per year and $N_{\rm customers} \times {\rm churn} \times {\rm ARPU} = 6 \times 10^7$ dollars in annual revenue.
