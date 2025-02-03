## Premier League 23/24 Analysis
#### Summary:
In this project I investigated data from the Premier League season 2023/2024 to see what trends or insights I could extrapolate. This project is segmented into three sections: 
1. Data Cleaning
2. Exploratory Data Analysis
3. Machine Learning

Following is a outline of each section with key findings.

1. Data Cleaning:
- Match day data used: https://www.kaggle.com/datasets/mertbayraktar/english-premier-league-matches-20232024-season?resource=download
- Made a few changes like dropping unneccesary columns, mapping values to be more legible (e.g. 'LutonTown' -> 'Luton Town')
- The table originally had two rows for every match; one from the perspective of the home team and one from the perspective of the away team. I joined the table to itself to see all match information is on one row

2. Exploratory Data Analysis:
- The number of goals scored in a game is fairly independent of the individual responsible for refereeing. There were some outliers, but these people generally managed only a handful of games. Generally, the average goals of most referees is close to the mean of 3.28 games, indicating a high level of conformity to standards
- The factors with the highest correlation to points were: Goals For, xG, Shots on Target, and Possession. I was surprised to find that Avg Distance Covered actually had a negative correlation of -0.3. This may be explained by the possibility that teams out of possession may have to run more (and we have seen that less possession correlates to less points)
- Despite placing 15th, Everton actually had a top-four quality defense, only conceding 51 goals behind Man City (1st), Arsenal (2nd) and Liverpool (3rd)
- Newcastle had a fairly poor point-to-goal return, achieving the same points (60) as Manchester United with 85 goals scored to MU's 57
- By a large way, Liverpool had the most shots in the league with 781. Man City were the closest behind with 683 (87.5% as many shots). Despite this, Manchester City actually had more shots _on target_ (264 vs. 263)
- Final table rankings seem completely independent of average distance covered. Sheffield United covered the most ground but still finished bottom of the table. Man City still won the league despite being outran by teams like Liverpool, Chelsea, and Manchester United
- Man City didn't lose a single game at home all season
- Tottenham didn't draw a single game at home all season
- Burnley were the only team in the league to take more points away than at home (14 away, 10 home)

3. Machine Learning:
- Attempted to predict win/draw/loss based on features 
Features used in ML:
    - Home Team
    - Away Team
    - Home Possession
    - Shots of Target For
    - Shots on Target Against
- One-hot encoded team names worked better than label-encoded, I suspect because the model was not trying to interpret some sort of ordinal relationship between the values
- I developed a base model using KNN and found the best value for k to be 3 (which makes sense considering we are predicting for 3 potential outcomes) and found my best test accuracy to be 60.53%
- I developed a comparison model using Random Forest Classifier. Despite tuning the model, the best accuracy I could achieve was 63.81%
