# Lead-Scoring-Classification-Problem
# Problem Statement:
An education company named X Education sells online courses to industry professionals. On any given day, many professionals who are interested in the courses land on their website and browse for courses. 

The company markets its courses on several websites and search engines like Google. Once these people land on the website, they might browse the courses or fill up a form for the course or watch some videos. When these people fill up a form providing their email address or phone number, they are classified to be a lead. Moreover, the company also gets leads through past referrals. Once these leads are acquired, employees from the sales team start making calls, writing emails, etc. Through this process, some of the leads get converted while most do not. The typical lead conversion rate at X education is around 30%. 

Now, although X Education gets a lot of leads, its lead conversion rate is very poor. For example, if, say, they acquire 100 leads in a day, only about 30 of them are converted. To make this process more efficient, the company wishes to identify the most potential leads, also known as ‘Hot Leads’. If they successfully identify this set of leads, the lead conversion rate should go up as the sales team will now be focusing more on communicating with the potential leads rather than making calls to everyone

X Education has appointed you to help them select the most promising leads, i.e. the leads that are most likely to convert into paying customers. The company requires you to build a model wherein you need to assign a lead score to each of the leads such that the customers with higher lead score have a higher conversion chance and the customers with lower lead score have a lower conversion chance. The CEO, in particular, has given a ballpark of the target lead conversion rate to be around 80%.

# Approach:
### Data Prepration:
1. The Dataset have 9340 rows and 37 features.
2. The problem is supervised binary classification problem
3. "Select" category in some categorical columns is treated as missing value as Select is the tab which is left unfilled while filling the form by a lead.
4. The columns which have missing values greater than 30%, combining "Select" and NaN values, we drop these columns.
5. For the features with less than 30%, if we drop these missing values we will end up loosing large amount of data so we can impute the data using mode and median.
6. There are some categorical features which have only one category which has to be dropped as they will become redundant during modelling.
7. Low occuring categories can be segregated iwn one category to reduce the number of features we will get when we form dummy variables.
8. EDA to find patterns in data
9. Label Encoding for features having two categories and dummy variables for categorical features having more than 2 categories
10. Recursive feature elimination technique is used to get 15 most important variables for modelling.

### Modelling:
1. Statsmodels api is used instead of scikit learn as statsmodels give the summary of statistical parameters 
2. High multicolinear variables were dropped using variance inflation factor. Features which have variance inflation factor is higher than 3.0
3. For our problem statement we have to predict Leads more correctly. So, we need high sensitivity for that we have to tweak the cut-off probability.
4. We get 0.3 as optimal cutoff probability through ROC curve.
5. We get train accuracy as 0.82 and test accuracy as 0.81
6. Precision recall curve and plot of probability vs sensitivity, specificity and accuracy indicates good probability at 0.45
7. For business problem we have to set a probability so that the conversion rate is more than 80%. We use hit and trial method to check at which probability we can reach 80% conversion rate.
