---
layout: page
title: Fast surrogate models
description: TBD
img: assets/img/surrogate_model-cover.jpg
importance: 1
category: work
---


<div class="alert alert-info"><h4>Executive Summary</h4><p>
Horizon is a fictitious large telecommunications company operating in California. Customer churn is costing Horizon approximately 60M dollars annually in lost revenue. I developed a logistic regression model that identified at-risk customers with 95% accuracy, enabling targeted retention campaigns that can reduce monthly churn. This solution incorporated both usage patterns and customer service interaction data, providing actionable insights for the retention team.
</p></div>

<!-- 
Data and analysis: Dropbox/codes/jupyter/data-science/kaggle/telco-customer-churn
Order-of-magnitude telecom estimates: /Dropbox/codes/mathematica/data science/customer churn.nb 
-->




## Business Problem

Horizon was experiencing above-industry-average customer churn rates[^1], particularly in their fiber optic service segment. Reducing churn represented a significant financial opportunity. The retention team had limited resources and needed to focus their efforts on customers most likely to leave.

Key business questions include:

- Which customers are most likely to churn in the next 60 days?
- What are the primary drivers of customer churn?
- How can retention offers be optimized based on customer profiles?



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
     <a href="https://public.tableau.com/views/TableauEDA_17293880396620/Customerchurn?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link" target="_blank">
         {% include figure.liquid loading="eager" path="assets/img/churn-tableau.png" title="example image" class="img-fluid rounded z-depth-1" %}
     </a>
    </div>
</div>
<div class="caption">
Interactive Tableau dashboard illustrating the data.
</div>




## Data & Methodology

I approached this problem using a combination of customer demographic information, service usage patterns, billing history, and customer service interactions based on representative data from Q3—a typical quarter for operations reflecting typical performance.

#### Data Sources

- Customer account and services (27 variables including payment, plans and behavioral)
- Customer location (5 variables)
- Customer churn status (satisfaction metrics)

Data for a fictional company for Q3, with numbers taken to be representative of the California business. [Source.](https://accelerator.ca.analytics.ibm.com/bi/?perspective=authoring&pathRef=.public_folders%2FIBM%2BAccelerator%2BCatalog%2FContent%2FDAT00148&id=i9710CF25EF75468D95FFFC7D57D45204&objRef=i9710CF25EF75468D95FFFC7D57D45204&action=run&format=HTML&cmPropStr=%7B%22id%22%3A%22i9710CF25EF75468D95FFFC7D57D45204%22%2C%22type%22%3A%22reportView%22%2C%22defaultName%22%3A%22DAT00148%22%2C%22permissions%22%3A%5B%22execute%22%2C%22read%22%2C%22traverse%22%5D%7D)

#### Methodology

1. **Data Preprocessing**: Converted 10 categorical features using ordinal encoder.
1. **Exploratory Analysis**: Identified where churn is concentrated and strong correlations between number of referrals, type of contract, monthly charge and churn.
<!--2. **Feature Engineering**: Created 14 derived features including service call frequency, payment irregularity scores, and usage volatility metrics-->
3. **Model Selection**: Evaluated logistic regression (baseline), random forest, and gradient boosting models on validation set.
<!--4. **Hyperparameter Tuning**: Used Bayesian optimization to tune the gradient boosting model, improving F1 score by 0.07-->





## Key Insights & Findings

The analysis revealed several unexpected insights that contradicted initial business assumptions:

<!--
TODO: quantify the impact of charge, e.g. 10% larger bill => 45% higher churn rate

70% below: odds ratio exp(beta) given beta=-1.4 for corresponding feature
-->

1. **Monthly charge was the strongest predictor**: Customers with larger monthly bills are more likely to churn. This suggests retention strategies targeted at customers with larger bills.

2. **Referrals and tenure are the strongest predictor that customer will stay**.

3. **Customers appreciate the online security package**, much more than online backup and streaming service. Customers with online security plans are 70% less likely to churn.

4. **New competitor strongly correlated with churn**: This is particularly apparent in San Diego.





## Solution & Implementation

The final logistic regression model achieved 95% accuracy on validation data.

<!-- 
- 0.83 F1 score (balancing precision and recall)
- 0.91 AUC-ROC score
-->

To make this actionable for the business, I could:
- Develop a weekly automated pipeline to score all customers on churn probability.
- Create customer segments based on churn drivers, enabling targeted retention strategies.
- Build a Tableau dashboard for the retention team to prioritize outreach and recommended retention offers based on customer profiles
- Implement an A/B testing framework to continuously measure retention campaign effectiveness



<!--
## Business Impact

After 4 months of implementation:

- **23% reduction** in overall churn rate (from 7.2% to 5.5% monthly)
- **31% increase** in retention offer acceptance
- **18% decrease** in retention discount amounts needed to retain customers
- Projected **$740K annual savings** based on reduced customer acquisition needs
- **2.8X ROI** on retention program costs


## Lessons 

This project highlighted several important learnings:

- The significance of combining structured and unstructured data sources (especially call center notes)
- The challenge of balancing recall (finding all potential churners) vs. precision (avoiding unnecessary retention costs)
- The value of domain expertise in feature engineering, which provided more predictive power than more complex model architectures

If I were to redo this project, I would:
1. Incorporate NLP analysis of customer service transcripts earlier
2. Develop separate models for different customer segments
3. Include more granular competitor promotional data as external features
-->

## Technical Resources

- [Project Repository](https://github.com/rsnemmen/telco-churn)
- [Interactive Tableau Dashboard](https://public.tableau.com/views/TableauEDA_17293880396620/Customerchurn?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
- [Jupyter Notebook: Data Exploration](https://github.com/rsnemmen/telco-churn/blob/9991af96ae1d4642492b24a26881089559a9ffb4/notebooks/eda.ipynb)
- [Jupyter Notebook: Modeling](https://github.com/rsnemmen/telco-churn/blob/9991af96ae1d4642492b24a26881089559a9ffb4/notebooks/model.ipynb)

[^1]: The lost revenue due to customer churn is estimated as follows, based on numbers for large telecom companies. Horizon has $N_{\rm customers}=1$ million customers in California, the annual churning rate is churn$=0.1$ and average revenue per user is ${\rm ARPU} = 12 \times 50 = 600$ dollars. With those numbers, the company is losing $N_{\rm customers} \times {\rm churn}=100,000$ customers per year and $N_{\rm customers} \times {\rm churn} \times {\rm ARPU} = 6 \times 10^7$ dollars in annual revenue.
