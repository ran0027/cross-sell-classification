![Cartoon Picture of a House with a Car in Driveway](Images/house_and_car.jpg)

# Cross-Sell Lead Generator & Market Insights

Author: Rebecca Neel

## Overview

This project uses a slew of machine learning classification algorithms to build a predictive model to generate leads for the sales team and insights for the marketing and product-development teams of a large insurance provider.

## Business Problem

Insurance companies usually offer a suite of products to help people protect the things that matter through life's ups and downs. Health insurance, vehicle insurance, life insurance all operate on the same basic principles of insurance. However, people think about these insurance products differently and shop for them individually. It becomes the job of the insurance provider to consider if their customers with one type of policy might be interested in another type of policy as well, and the practice of reaching out to a customer who has already purchased one type of insurance policy (health) from the company and offering them another type of insurance policy (in this case, vehicle insurance) is known as a "cross-sell."

We aim to help companies with this area of business in two ways:

1. The primary goal of this project is to **predict** who will convert when contacted with the cross-sell offer. There are too many existing health insurance customers for any individual employee or even team of employees to go through them all and classify them as a lead or not, especially when you consider the mental fatigue this could induce on top of needing to actually make the sales contact. Not to mention that the list of health insurance customers is changing everyday! Allowing machine learning to take over this task frees up salespeople to make sales.

2. The secondary goal of this project is to examine model artefacts (coefficients in parametric models, feature importances in tree-based models) and perform quality data analysis to understand *why* some cross-sells are or are not successful. This understanding needs to be discussed with the marketing team and the product-development team to help inform their departmental dicussions related to marketing campaigns (what considerations are driving customers to purchase or not purchase insurance? how can we respond to these pre-emptively with the right marketing?) and product offerings (if younger customers don't want vehicle insurance, is it because they have to purchase via phone and not a website? via a website and not an app? is there anything in our policy that could be profitably tweaked to appeal more to younger customers? I am focusing on age as a single example, but there are many more.) Our approach is data-driven, allowing teams to learn from real data rather than guessing what could be influencing customer behavior.

## Data

This project uses data from [this Kaggle posting](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction) regarding the responses of ~380,000 health insurance customers to an offer to buy vehicle insurance from the company to build a predictive model to recommend leads to the sales team.

## Methods

The following classification algorithms were considered for classifying health insurance customers as potential vehicle insurance customers:

Single Model
- Logistic Regression
- K Nearest Neighbors
- Decision Tree

Ensemble Methods / Other
- Random Forest
- AdaBoost
- XGBoost
- Voting Classifier with AdaBoost and Logistic Regression

Because our data was imbalanced, we tried several methods of increasing minority class detection:

- Random Under Sampling
- SMOTE
- Class Weights within the Model

## Results

Our best classifier was able to nearly triple the conversion rates that would be experienced by the sales team were they to randomly choose a customer from the database to contact. Contacting every lead generated by the model would result in capturing 85% of the 12% of our health insurance customers who are interested in purchasing vehicle insurance from us.

## Conclusion

We've successfully more than doubled the conversion rates of our sales team (within the context of cross-sells from health to vehicle) without increasing the time and energy output of our salespeople.

## Next Steps

**Regional Cross-Sells Dashboard**

Performing data analysis in preparation for modeling was rich with insights, and I hope to build a dashboard to present further insights by region related to overall conversion rates, conversion rates by policy sales channel, and customer profiles by region. The ideal dashboard would also include monitoring of any initiatives introduced to increase sales, to objectively review their effectiveness and learn from customer responses.

**Model Deployment**

Lead generator integration - connecting our model to the current system used by the sales team to track customer contacts and sales will hopefully allow the system to select a random customer from the leads generated by the model and display the customer information necessary to make a call on the salesperson's desktop or virtual machine when they log in to the app. The system can automatically move to the next recommendation after the contact with the current customer is marked complete, implementing any data entry checks at this stage as appropriate, as long as the salesperson is in contact mode. The lead generator can also be accessed by the system to generate email lists for general marketing emails.

Monitoring model performance - connecting to the current system used by the sales team to track customer contacts and sales should allow us to pull new data on customer responses to cross-sell offers. We can check the model's performance on this new data as often as every day, and we can assess the model's performance over the last day, week, month and quarter to determine if and when the model needs to be updated to reflect changes in our customer base or in our customers' thinking about vehicle insurance. This information could also be displayed in a dashboard format, with automatic checks in place to alert (via email?) key employees if model metrics over a certain period of time indicate that the model's performance has fallen below an acceptable threshold. A possible threshold for the alert is falling below the 12% conversion rate we expect from randomly selecting customers for more than a day or two in a row (urgent: model needs to be inspected and possibly re-trained now), or if the model's performance is within 2 or 3 points of 12% for a month or more (model is not necessarily costing us anything, but it is not performing significantly better than random chance, either.)


## For More Information

See the full analysis in this [Jupyter Notebook](notebook.ipynb) or review the [Google Slides presentation](presentation.pdf).

For additional information, contact Rebecca Neel at rebecc.clark@gmail.com.

## Repository Structure

```
├── Images
├── rawData
├── zippedData
├── EDA.ipynb
├── Presentation.ipynb
├── README.md
└── Presentation.pdf
```