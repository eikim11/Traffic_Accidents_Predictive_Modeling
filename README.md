# Traffic_Accidents_Predictive_Modeling

### Table of Contents

- [Description](#description)
- [Author Info](#author-info)

---

## Description

There are 3.5 million U.S. traffic accident records (2016- June.2020) in the dataset. I focused on the 816,000 accident records from California to build and optimize a multi-class classification model to predict accident severity.

Severity is rated 1-4, based on the impact on traffic (1 = low impact, 4 = high impact).

![Severity Distribution](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/Severity.png)

Severity distribution was very imbalanced - about 70% Severity 2, 28% Severity, and 1% for each of Severity 1 and 4.

To avoid multicolliniearity, I removed columns that showed values resulting from an accident - 'end time', 'end lat/long', 'distance'.

![byhour](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/accs_by_hour.png)

![accidents by day of week](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/accs_by_day_of_week.png)

![Number of Accidents by Year](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/byyear.png)

Also, 94% of Severity 1 accidents were in 2020, so I got rid of all data from 2020. Otherwise, the oversampling method would amplify this disproportion and make 'Year' an unreasonably strong deciding factor in our prediction. Doing so decreased the number of Severity 1 accidents even more, leaving only 235 rows behind.

Because of this, training the model on Severity 1 became less effective, but it is, in most cases, more useful to be able to predict Severity 4 accidents than Severity 1.

There are 72 unique categorical values in the Weather_Condition column, which were simplified into 3 categories (good (0), mild(1), and bad(2)). After this, 54.32% of total was under 'good weather', 36.28% was 'mild', and 9.4% was 'bad'.

![Decision Tree Confusion Matrix](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/dt_CM.png)

I used Decision Tree Classifier and Random Forest Classifier as my initial models to calculate the overall accuracy score as well as per-class accuracy scores. After using imblearn's SMOTE technique, the accuracy scores went down expectedly. 

Lastly, I used GridSearchCV to find the most optimal parameters for the Random Forest model, which resulted in a final accuracy score of 0.76.

![Final RF Confusion Matrix](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/final_RF_CM.png)

And here are the final feature importances:
![feature_importance](https://github.com/eikim11/Traffic_Accidents_Predictive_Modeling/blob/master/img/final_feature_importance.png)

#### Next Steps:

- Try different variations of feature engineering:
  - What if we grouped the 72 Weather Conditions differently instead of 'good', 'mild', and 'bad'?
  - What if we group the severity levels into binary: 'low severity' vs. 'high severity'?


- Zoom in on a focus area, such as the Bay Area, a single county, or city


- Compare accuracy score with different models - XGBoost? Neural Network?

#### Technologies

- Python packages: Pandas, Numpy, Matplotlib, Seaborn, Basemap, Sci-kit learn (sklearn), and Imbalanced-Learn (imblearn)

[Back To The Top](#traffic_accidents_predictive_modeling)

---


#### Data Source
https://arxiv.org/abs/1906.05409
https://arxiv.org/abs/1909.09638


[Back To The Top](#traffic_accidents_predictive_modeling-me-template)


---

## Author Info

- Email - edward.kim9280@gmail.com
- LinkedIn - https://www.linkedin.com/in/edwardkim11/

[Back To The Top](#traffic_accidents_predictive_modeling)
