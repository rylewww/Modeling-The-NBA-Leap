# Modeling the NBA Leap
<img src="https://specials-images.forbesimg.com/imageserve/6039162297e0c18b3c836174/960x0.jpg?cropX1=276&cropX2=2296&cropY1=51&cropY2=1188" alt= "NBA HOF Image" width="800" height="400"> 
Author: Ryan Lewis

## Overview
This project applies machine learning classification to predict whether NBA players will make 'All NBA' teams in seasons 4 - 6, based upon thier first 3 season statistics. The structure of our model will be based upon inference, as the goal is to educate front offices on what player statistics correlate the most with future NBA stars. The model will focus on the 'recall' metric as we are aiming to minimize our false positives (predicting an NBA star when the player is not.)

## Business Problem
Each year 60 NBA players are drafted into the league and many others are signed as non-drafted free agents. Dependent on what round players are drafted in, rookie contracts can stretch from 2 to 4 years, with team options in the 3rd and 4th year. Its imperative for NBA front offices to be able identify if their recently drafted players will make the leap from productive NBA player to All NBA star. 

Why is this important? Salary cap for the NBA in 2020-21 season is at $109M and first round draft picks who sign a 'max rookie scale extension' can demand contracts up to 25% of the salary cap. Meaning its so important to correctly identify these players, as you don't want such a large percentage of your team's salary cap tied to a player who is not living up to expectations. This is a quick way to lose your job as a team's General Manager. 

## Data
I used Selenium webdriver to scrape both 'standard' and 'advanced' seasonal statistics of all NBA players dating back to 1947 from stathead.com. I then merged datasets containing NBA draft history, All NBA selections, All Rookie teams and All Defensive teams and began to aggregate all data down to one row representing the first 3 years of a players career. 

Final Data Set was subset to players who's rookie year was 1977 and later, advanced statistics such as Win-Share and VORP were not tracked prior to 1977. Furthermore, qualified players need to play a minumum of six years in the league as our target variable is All NBA selections in seasons 4 through 6. This left us with the following population breakdown:

<insert bar chart>
  
  
