# Over_Under_Totals
## Background
In sports betting, a bettor can bet if the total score of a game is going to be over or under a certain amount of points. The certain amount of points is given by a sportsbook with odds associated with under the total score and under the total score. In the sports betting world is called Totals betting. 

## Objective: 
I want to particularly take a look at NFL Totals betting. Intutitively, I thought that game conditions, such as weather or playing surface, would have an effect how teams score. If it rains or snows, teams should have a tougher time to score than a nice sunny day, right? Odds from bookmakers are also a good indication if they think the game is going to go one way or not.

For this project, I would like to predict whether or not the total of NFL game would be over or under based on game conditions and odds. 

## Data: 
My first dataset that contains the weather conditions and other miscellaneous features was scraped from https://www.rotowire.com/betting/nfl/archive.php. The dataset has 9113 rows, where each row is a game, and 33 columns of features.The games range from 1983 to 2019.  My second dataset contains odds from http://www.aussportsbetting.com/data/historical-nfl-results-and-odds-data/. The dataset has 3738 rows and 45 columns.The odds are for games from 2006 to 2020.

## EDA

### Game Conditions Conditions

#### Playing Surface 
Surface      |      Over     |      Under
------------ | ------------- | -------------
Dome | 50.19% | 49.81%
Grass| 48.71% | 51.29%
Turf| 50.60 % | 49.40%

The playing surface doesn't look like it has an effect on a game being over or under. 

#### Weather
The types of weather conditions include Wind, Snow, Sleet, Rain, Partly Cloudy Night, Partly Cloudy Day, Fog, Dome, Cloudy, Clear Night, and Clear Day. The over and under percentage for each weather condition were close to 50/50. Three conditions that stood out were Rain, Wind, and Fog. 


Weather     |      Over     |      Under
------------ | ------------- | -------------
Rain | 41.69% | 58.31%
Wind| 42.35% | 57.65%
Fog|42.86 % | 57.14%


It seems that bad weather might have an effect on the score of the game. 

#### Odds

Closing Odds    |      Over     |      Under
------------ | ------------- | -------------
Min | 1.74| 1.81
Max| 2.11 | 2.22
Mean|1.93 | 1.94

The closing odds are the final odds before the games start. I wanted to take a look at this feature because the closing odds takes everything into account like news, injuries, etc. For the most part, the average for over or under odds is around 1.90. Odds of 1.90 means that the bet is even between the over wager and under wager. When the odds are lower than 1.90, it means that that wager is favored to happen. Above 1.90, means the wager is less likely to happen, therefore, you get paid more if the wager. 

## Models

### Logistic Regression 
Model    |      F1 Score          
------------ | ------------- 
Base| .4996
Trained| .5407
Test|.5382

### Gradient Boosting Classifier
Model    |      F1 Score          
------------ | ------------- 
Base| .5249
Trained| .5438
Test|.5304

## Results
The F1 score was chosen as the metric to evaluate the models because both the false positive and false negative are equally important. I want to predict the correct outcome, so I'm able to place the correct bet. 

Out of the box, the Logistic Regression model did not perform as well as the Gradient Boosting Classifier model, but after feature engineering the performance was comparable. The final test performance for the Logistic Regression model was slightly better than Gradient Bossting Classifier model. The winning model is the Logistic Regression model, not only because of the higher score, but while running multiple tests, the Logistic Regession model consistently performed around 0.53. The Gradient Boosting Classifier was more sporadic with results indicating that it was underfit, which isn't good for placing bets. 

## Next Steps

* Get more data for odds
  * Sites started collecting odds around 2006, so I was limited in the amount of odds available to me. In the future, if I had more odds, the models might be able to pick up more signal.

* Add more features
  * In this project, I only looked at game conditions and odds, so I'd like to add features that are team and player related stats. 
  
* Neural Network Classfier
  * If I had time, I would like to run a Neural Network Classifier to see if I can get a better score.
