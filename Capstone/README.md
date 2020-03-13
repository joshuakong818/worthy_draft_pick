# Worthy Draft Pick or Bust? (WR Edition)

By [Joshua Kong](https://github.com/joshuakong818)

## Executive Summary

Through webscraping, merging dataframes, feature selection, feature engineering and classification models this project aims to identify wide receivers who are worth their draft stock.

---

## Problem Statement

Year after year, general managers, coaches, and scouts in the NFL are tasked with the seemingly impossible task of identifying standout talent. Sometimes NFL teams hit on their players, but often times, drafted players do not live up to their larger than life hype preceding the pros.

__How might data science improve the scouting and drafting processes by shedding competitive advantage granting insights?__

---
## Data

For this project, BeautifulSoup was used to scrape college stats, NFL stats, and combine stats from 'https://www.pro-football-reference.com/'. The scrape was filtered down for wide receivers, and those receivers having all three aforementioned stats. Code for the webscraping and data cleaning can be found here: [Scraping & Cleaning](./code/capstone_scraping_data_cleaning.ipynb)


|Stat Types|Years|
|:---|:---|
|College Receiving|2017, 2018, 2019|
|NFL Receiving|2017, 2018, 2019|
|Combine|2017, 2018, 2019|


Per year, nearly 450 players were scraped. After cleaning (notebook linked above), the 450 was reduced to around 20. 

---
## EDA

Missing data was noted in the college and combine stats. Yards per carry is total rushing yards divided by total rush attemps, so 0 was entered for those without neither rushing yards nor rush attempts. Binary features for being drafted, invited to the Combine, being in a power five conference, and being taller than six feet were created to strategically reduce the number of features. I manually labeled whether a player was a worthy pick or not depending on their NFL stats.

---
## Limitations

---

Several limitations were noted throughout the course of the project. These limitations include not all players being invited to the Combine, so these individuals were not included in my model. Additionally, there is limited access to advanced/sophisticated stats data. This data exists, but are only availble through purchase. My model was trained on three years worth of data only. The history of the NFL spans 100 years. A ordinal injury feature in particular would have been interesting to use in model. The use of interaction terms to increase model accuracy. Not all conferences are tracked, so vital draft worthy players like Cooper Kupp are missing from model.

replace drafted with projected draft round (can use that information to determine whether a player will be drafted or not), could also try doing a nlp model where the scouts' analyses on players become features

---

## Modeling
---

Logistic Regression, K-Nearest Neighbors, Decision Trees, Bagged Decision Trees, Random Forests, AdaBoosts, and Support Vector Machines ('SVM') models were used to get to the best accuracy score. The baseline model performed with 70% accuracy if all players were designated as busts. The model with the best blend of good test scores, training scores, and true positives was logistic regression. 

The most important features, based on the weights of the coefficients for each word were help, relief, donate, assistance, donations, impacted, center, efforts, supplies, bahamas, affected, victims, need, free, support, fund, tomorrow, Healdsburg, donated, donating, thank, proceeds, helping, today, food, doing, donation, contained, Sunday, and aid.  The top two models had the exact same top words, in the same order. Based on this list, it may be desirable to utilize a lemmatizer or stemmer to shorten words into their stem so that words like donations/donated/donating/donation are combined into one.  This may or may not improve model performance. 

In order to test our best performing model, SVM with Count Vectorizer, with data that had not been previoulsy labeled, we ran the built in model prediction function on the remaining 50,000+ tweets. The model predicted 'needs help' for 8,306 of those tweets. The first 150 of these tweets were examined and labeled, and the model correctly predicted needs help for 85% of these tweets.


---
# Conclusion

The pace of change in social media, like all technology, is increasing rapidly. New platforms, like TikTok, Lasso, Vero, Steemit and Caffeine, are introduced constantly. Likewise, in our ever-changing world, natural and man-made disasters are an ever constant threat. Disaster response and relief must evolve to keep pace with these changes to be as fast and efficient as possible. Drone delivery, autonomous vehicles, machine learning and satellite 5G communications must be leveraged along with these new social media communications tools to minimize the loss of life and property. While privacy of users data is of utmost importance, in the domain of disaster repsonse all data must be leveraged, including location data, to achieve these goals. Since 2012, there has been a Wireless Emergency Alert ('WEA') system in the United States. This system provides geographically targeted alerts during emergency situations. We recommend further study and development of our machine learning algorithm to detect requests for emergency assistance via social media and all other forms of communication. In conjunction with the WEA, our API could greatly enhance disaster preparedness, providing a tool for victims to efficiently and easily communicate their needs during and after an emergency situation, allowing for the most rapid response possible in the delivery of medical assistance and life sustaining supplies.
