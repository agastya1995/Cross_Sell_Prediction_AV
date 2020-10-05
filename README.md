# Cross_Sell_Prediction for Vehicle Insurance
Cross-selling identifies products or services that satisfy additional, complementary needs that are unfulfilled by the original product that a customer possesses. As an example, a mouse could be cross-sold to a customer purchasing a keyboard. Oftentimes, cross-selling points users to products they would have purchased anyways; by showing them at the right time, a store ensures they make the sale.

Our client is an Insurance company that has provided Health Insurance to its customers now they need help in building a model to predict whether the policyholders (customers) from past year will also be interested in Vehicle Insurance provided by the company.

Building a model to predict whether a customer would be interested in Vehicle Insurance is extremely helpful for the company because it can then accordingly plan its communication strategy to reach out to those customers and optimise its business model and revenue.

Now, in order to predict, whether the customer would be interested in Vehicle insurance, we have information about demographics (gender, age, region code type), Vehicles (Vehicle Age, Damage), Policy (Premium, sourcing channel) etc.

This project was done as a part of the Hackathon we participated in Analytics Vidhya.
Link : https://datahack.analyticsvidhya.com/contest/janatahack-cross-sell-prediction/#ProblemStatement

Methodology:
1. Did some basic data cleaning (removed the id column, set the correct data types etc)
2. Tried different ways of converting the region and sales channels to categories. Since there were 155 sales channels and 50 regions, creating dummies would not have worked. We tried to manually create  bins for these channels based on the response rate, but the final results were unsatisfactory. Eventually, we settled on WOE encoding, which gave some good results.
3. Created new variables by interacting certain other binary variables. This eventually helped increase the ROC AUC score by 2 percentage points.
4. Since the dataset was heavily imbalanced, we used the imblearn package to first balance it. Oversampling and artificial oversampling methods (like SMOTE and ADASYN) did not work at all, but undersampling as well as Balanced Bagging Classifier worked well. 
5. The best solution was that of XGBoost on the undersampled dataset. The final score was 0.85 (***The winner's score was 0.86***) 
