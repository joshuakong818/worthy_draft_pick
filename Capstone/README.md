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
## Limitations & Next Steps

---

Several limitations were noted throughout the course of the project. These limitations include not all players being invited to the Combine, so these individuals were not included in my model. Additionally, there is limited access to advanced/sophisticated stats data. This data exists, but are only availble through purchase. My model was trained on three years worth of data only. The history of the NFL spans 100 years. A ordinal injury feature in particular would have been interesting to use in model. The use of interaction terms to increase model accuracy. Not all conferences are tracked, so vital draft worthy players like Cooper Kupp are missing from model. Gridsearching on hyperparameters to achieve higher accuracy scores and more true positives.  

An NLP model transforming scouts' analyses on players to features could be an interesting future project. I also need to replace drafted feature with projected draft round and that information can be used to project whether a player will be drafted or not.

---

## Modeling
---

Logistic Regression, K-Nearest Neighbors, Decision Trees, Bagged Decision Trees, Random Forests, AdaBoosts, and Support Vector Machines ('SVM') models were used to get to the best accuracy score. The baseline model performed with 70% accuracy if all players were designated as busts. The model with the best blend of good test scores, training scores, and true positives was logistic regression. Interpretability was extremely important, so a model with coefficients was a must. 

Features that were determined to make a player less likely to be a worthy draft pick were reception touchdowns, weight, rush yards, yards per reception, rush attempts, games played, and power five. The strongest of these was the power five. This feature makes sense because players from the power five conferences make up the bulk of the 'strong' wide receiver pool, and by nature of the draft, hitting on players is extremely difficult. Therefore, the fact the model deemed that feature one that made a player less likelier to be worth their draft stock makes sense because there are many players from the power five who do not pan out.

Rushing touchdowns, being drafted, being invited to the Combine, yards per carry, being taller than six feet, age, receptions, and reception yards were determined to make a player more likely to be a worthy pick. Age being included sheds light on older players being more mature and more refined in their technique than their younger counterparts.

---
# Conclusion

After the project, the draft process remains mostly a mystery. No ground-breaking insights were drawn to help teams draft more worthy picks. However, the use of data science and advanced football analytics can absolutely give a team a competitive edge.
