# Bank Marketing Campaign Analysis
## Overview
![StockSnap_YITM2SKVWI](https://github.com/ZERARKAH/Bank-Marketing/assets/130615319/6fd0f2b4-24c5-4d79-907e-13495f49cef4)


## 1. Understanding the Business Problem
The dataset comes from a Portuguese banking institution and contains the results of multiple telephone marketing campaigns. The primary business problem is to identify the best predictive model that can efficiently predict whether a client will subscribe to a bank term deposit or not. By doing so, the bank can optimize its marketing strategies to target the right customers, thereby improving the success rate and reducing costs.

## Objective
To compare the performance of various machine learning classifiers (Logistic Regression, KNN, Decision Trees, and Support Vector Machines) in predicting the outcome of the marketing campaign.

- #### All of the work done, including observations and comments, is contained within the following Jupyter Notebook, which provides a comprehensive analysis.[Jupyter notebook](https://github.com/ZERARKAH/Amazon_coupons/blob/da30e4371936c06cc978ae41f135aadb3d0f6969/prompt.ipynb)


## 2. Data Understanding and Preprocessing
**Basic Statistics Summary**

**Numeric Features:**

**age:** Ranges from 17 to 98, with a mean age of approximately 40.  
**duration:** The duration of calls varies widely.  
**campaign:** On average, clients were contacted around 2.5 times during the campaign.  
**pdays:** Most values are 999, indicating that many clients were not contacted before.  
**previous:** Most clients were not contacted before this campaign.  
emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed: These are economic indicators with varying ranges and scales. 

**Categorical Features:**

**job**, **marital**, **education**, **default**, **housing**, **loan**,**contact**, **month**, **day_of_week**, **poutcome**: These have a limited set of possible values.
**y:** The target variable, it's binary (**"yes"**/**"no"**).

## 3. Visual Analysis:

![Screenshot 2023-09-14 at 12 21 17 PM](https://github.com/ZERARKAH/Bank-Marketing/assets/130615319/18125f86-9813-4b91-93c8-d94842f76cc8)

![Screenshot 2023-09-14 at 12 23 43 PM](https://github.com/ZERARKAH/Bank-Marketing/assets/130615319/5766f71d-2069-4926-a0d4-83c6fc031247)
**Key Categorical Features:**    
1. **Job:** The job type appears to have some influence on subscription rates. For example, students and retired individuals seem more likely to subscribe compared to blue-collar workers.  

2. **Marital Status:** Married individuals are the largest group in both subscribed and not subscribed categories. However, the proportion of single individuals who subscribe seems slightly higher.  

3. **Education:** Those with a university degree are both the largest group and seem slightly more likely to subscribe.  

4. **Default:** People with no credit in default are far more likely to subscribe, which is expected.  

5. **Housing:** The presence of a housing loan does not seem to significantly affect the subscription rate.  

6. **Loan:** Similarly, personal loan status does not show a clear trend in affecting subscriptions.  

7. **Contact:** Cellular contact seems to be more effective in gaining subscriptions compared to telephone contact.  

8. **Previous Outcome:** If the previous marketing campaign was a 'success,' there is a very high likelihood of the client subscribing again. 




![Screenshot 2023-09-14 at 12 28 59 PM](https://github.com/ZERARKAH/Bank-Marketing/assets/130615319/7d8b5a80-c5cb-420f-a34b-2edd6088a83f)

![Screenshot 2023-09-14 at 12 29 42 PM](https://github.com/ZERARKAH/Bank-Marketing/assets/130615319/0f5ad213-eafe-4b0e-9897-faee79b665b6)

![Screenshot 2023-09-14 at 12 30 48 PM](https://github.com/ZERARKAH/Bank-Marketing/assets/130615319/78f6e9e6-a702-45da-8f7b-8cac09e4dc23)


**Age:** Most clients are between 30 and 40 years old.  
**Duration:** The majority of last contact durations are below 500 seconds.  
**Campaign:** Most clients have been contacted fewer than 10 times in the current campaign.  
**Pdays:** A large majority of clients have a pdays value of 999, indicating they were not previously contacted.  
**Previous:** Most clients have not been contacted in previous campaigns.  
**Emp.var.rate:** The employment variation rate is mostly concentrated around values like -1.8, 1.1, and 1.4.  
**Cons.price.idx:** The consumer price index seems to have a few peaks, indicating certain recurring values.  
**Cons.conf.idx:** The consumer confidence index is fairly normally distributed but has a long tail towards the lower end.  
**Euribor3m:** The Euribor 3-month rate has peaks at around 1 and 4.5.  
**Nr.employed:** The number of employees has peaks around 5099 and 5228.

Data preprocessing involved multiple steps:
- Handling missing values
- Removing outliers
- Feature engineering, including one-hot encoding and normalization

### 4. Modeling

Three types of regression models were employed:
- Linear Regression
- Ridge Regression
- LASSO Regression

Hyperparameters were tuned using GridSearchCV.



### 5. Evaluation

Models were evaluated based on:


![Screenshot 2023-09-14 at 12 36 36 PM](https://github.com/ZERARKAH/Used-Car-Price-Prediction/assets/130615319/4a9c4016-751c-4333-afee-e866c6a261e7) 

![Screenshot 2023-09-14 at 12 37 24 PM](https://github.com/ZERARKAH/Used-Car-Price-Prediction/assets/130615319/f0800dae-83ed-45c3-8e55-8a987bc1b574)



**The best Logistic Regression model, with an accuracy of **0.914989** turned out to the best model. This model gave the following results.**



![Screenshot 2023-09-14 at 12 38 01 PM](https://github.com/ZERARKAH/Used-Car-Price-Prediction/assets/130615319/04289c72-6a2e-4f3b-86a8-28f965611424)

![Screenshot 2023-09-14 at 12 40 44 PM](https://github.com/ZERARKAH/Used-Car-Price-Prediction/assets/130615319/dc5af263-e633-4caa-a9e2-44606dbd85b9)

![Screenshot 2023-09-14 at 12 41 18 PM](https://github.com/ZERARKAH/Used-Car-Price-Prediction/assets/130615319/45fbd12a-be6d-42e5-863a-d4a5562c592b)

The model is adept at identifying instances where a negative result is likely to occur. While it has a tendency to err on the side of caution, often predicting a negative outcome even when the client ends up subscribing, it rarely gives false positives. This makes it a somewhat conservative but reliable tool for forecasting negative scenarios.


## Findings and Actionable Insights:

1. **Key Drivers of Success:** The variables poutcome_success, duration, and job_student are the strongest predictors of a successful marketing campaign. These variables should be considered closely in future marketing strategies.

2. **Positive vs Negative Impact:**

- **Positive Impact:** High values of poutcome_success and duration are strong indicators of a likely positive outcome.
- **Negative Impact:** Features with negative coefficients, like Feature: 44 (which might be a specific job role, marital status, or other categorical variable), are strong indicators of a likely negative outcome.
3. **Less Influential Features:** Features like education_unknown, age, and education_illiterate have low importance and might be candidates for feature reduction in future models.

4. **Demographics:** Job roles like 'student' and 'retired' seem to be more responsive to the campaign, while others like 'unknown' are less responsive.

## Next Steps:

1. **Focus on Previous Success:** Given the high importance of poutcome_success, future campaigns could prioritize customers who had a successful outcome in the past.

2. **Duration Matters:** Since duration is a key variable, monitoring the length of interactions with customers could yield insights into potential success.

3. **Target Specific Demographics:** The job role of 'student' seems to positively impact the campaign. Consider targeting this demographic more aggressively in future campaigns.

4. **Feature Reduction:** Less important features could be dropped in future models to simplify the model without sacrificing performance.

5. **Further Investigation:** For features that have strong negative coefficients, a deeper dive is needed to understand why they are acting as strong negative indicators.


## Recommendations:

1. **Resource Allocation:** Allocate more resources to engage with customers who had a successful previous outcome and fall under the 'student' and 'retired' job roles.

2. **Personalize Campaigns:** Customize the messaging and offers for different job roles based on their responsiveness to past campaigns.

3. **Performance Monitoring:** Continuously monitor the duration of customer interactions and set alerts for interactions that fall below a certain threshold.

4. **Model Reiteration:** As new data is collected, the model should be retrained to keep it up-to-date. Consider using automated machine learning pipelines for this.

 **By focusing on these areas, the bank can improve the effectiveness of its future marketing campaigns and make better use of its resources.**





## Usage

The Jupyter notebook in this repository contains all the code for data preprocessing, modeling, and evaluation.

## Contributing

Contributions are welcome. Feel free to fork the repository and submit pull requests.

## License

Hamza ZERARKA
