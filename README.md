# Modeling the NBA Leap
<img src="https://cdn.vox-cdn.com/thumbor/NsPkdWLpxyLkBTL2z2Ycjl0ogYY=/0x16:982x530/fit-in/1200x630/cdn.vox-cdn.com/uploads/chorus_asset/file/13284645/Screen_Shot_2018_10_17_at_1.37.46_AM.png" alt= "Jalen Brown Dunk" width="1000" height="500"> 
Author: Ryan Lewis

## Overview
This project applies machine learning classification to predict whether NBA players will make 'All NBA' teams in seasons four through six, based upon thier first three seasons in the league. The structure of our model will be based upon inference, as the goal is to educate NBA front offices on which player statistics correlate the most with future NBA stars. The model will focus on the 'precision' metric as we are aiming to minimize our false positives (predicting an NBA star when the player is not.)

## Business Problem
Each year 60 NBA players are drafted into the league and many others are signed as non-drafted free agents. Dependent on what round players are drafted in, rookie contracts can stretch from two to four years, with team options in the 3rd and 4th year. Its imperative for NBA front offices to be able identify if their recently drafted players will make the leap from productive NBA player to All NBA star (Top 15 player in the league.)

Why is this important? Salary cap for the NBA in 2020-21 season is set at $109M and first round draft picks who sign a 'max rookie scale extension' at the end of thier rookie deal can demand contracts up to 25% of the salary cap. This can rise up to 28%-30% if these young players make All-NBA teams within thier first four years like Ben Simmons and Pascal Siakam. Meaning its so important to correctly identify these players, as you don't want such a large percentage of your team's salary cap tied to a player who is not living up to expectations.

## Data
I used Selenium webdriver to scrape both 'standard' and 'advanced' seasonal statistics of all NBA players dating back to 1947 from [StatHead](stathead.com). I then merged datasets containing NBA draft history, All NBA selections, All Rookie teams and All Defensive teams and began to aggregate all data down to one row representing the first three years of a players career. 

Final Data Set was subset to players who's rookie year was 1977 and later, advanced statistics such as 'Win-Share' and 'Value Over Replacement Player' were not tracked prior to 1977. Furthermore, qualified players need to play a minumum of six years in the league as our target variable is All NBA selections in seasons four through six. This left us with the following population breakdown:

<div align="center">
<img src="https://github.com/rylewww/Modeling-The-NBA-Leap/blob/main/Images/target_barchart.png" alt= "NBA HOF Image" width="800" height="500"> 
</div>

Only 7% of our qualified population of NBA players are selected to All-NBA teams in seasons four through six in thier careers. This demonstrates out elite of company these players are, highlighted by household names such as LeBron James, Michael Jordan, Larry Bird, ect.
  
 ## Exploratory Data Analysis
Once the data was properly formatted and cleaned, I began to explore and investigate which features correlated the most with our 'All-NBA 4-6' target variable. It became clear that future All-NBA players differentiate themselves from the rest of the league with statistic totals in the first three years.
 
<img src="https://github.com/rylewww/Modeling-The-NBA-Leap/blob/main/Images/nba_pair_plt_basic.png" alt= "NBA HOF Image" width="1000" height="700"> 

By NBA players third season, advanced statistics such as 'Win-Shares' (An estimate of the number of wins contributed by a player*), 'Player Efficiency Rating' (A measure of per-minute production*), and 'Value over Replacement Player (A box score estimate of the points per 100 TEAM possessions that a player contributed above a replacement-level player*). 

<div align="center">
<img src="https://github.com/rylewww/Modeling-The-NBA-Leap/blob/main/Images/Season%203%20Scatter%20updated.png" alt= "NBA HOF Image" width="800" height="600">
</div>

## Modeling Process & Results
After EDA and feature engineering processes it was time to begin our modeling process. I employed recursive feature elimination to reduce our total number of features down from over 200 to 13. Then, in efforts to best understand which statistics highlight young NBA players potential growth to All-NBA stars, the models I focused on were all interpretable. Additionally, they were all grid-searched to best tune our hyperparameters and scored based on the 'precision' metric to best reduce our false positives. 

<div align="center">
<img src="https://github.com/rylewww/Modeling-The-NBA-Leap/blob/main/Images/modeling.jpeg" alt= "NBA HOF Image" width="600" height="300">
</div>

The Random Forest model produced the best results with an Accuracy score of 94.5% and a Precision score of 75%. Below shows the associated confusion matrix and which features the model found most important when identifying future All NBA players.

<p float="left">
  <img src="https://github.com/rylewww/Modeling-The-NBA-Leap/blob/main/Images/RF_CM.png" width="400" height="300" />
  <img src="https://github.com/rylewww/Modeling-The-NBA-Leap/blob/main/Images/feature_importance%20copy.png" width="400" height="300" />
  </p>

## Conclusion
Our Random Forest model performed the best per our business question of identifying and explaining which NBA players were expected to reach All NBA levels in seasons four through six. It scored the highest precision score, meaning that when it identifies a player to be 'making the leap' its correct 75% of the time. It displays the importance a players points total and 3rd season VORP rating relates to the probability they will make an All NBA team in the next three seasons.

## Next Steps
There's plenty of room for improvement in our model, currently it has too high of standards to which it classifies future All NBA players. In the future I hope to add the following:
* Implement additional resampling techniques to better combat class imbalance
* Pull in additional categorial data such as draft pick positions and team win/loss records
* Look into generational trends; did All NBA players look statistically different in the 80's vs 90's
* Expanding into a multiclass classification model - breaking down All NBA teams or classifying All NBA vs All Defense

## Sources
* Player statistics sourced via [StatHead](stathead.com)
* Categorical statistics (e.i. All NBA, Rookie of the Year, ect) sourced via [ESPN](http://www.espn.com/nba/history/awards)

## Insperation
* Zach Lowe's Grantland artice [Look Before You Leap](https://grantland.com/features/the-young-nba-players-looking-make-leap-greatness)

## Repository Structure
```
├── Data
├── Images
├── Notebooks
│   └── 1_Webscrape.ipynb
│   └── 2_Data_Compiling.ipynb
│   └── 3_EDA.ipynb
│   └── 4_Modeling.ipynb
│   └── 5_YoY_Analysis.ipynb
├── README.md
├── Modeling_The_Leap.ipynb
└── Modeling_The_NBA_leap.pdf
