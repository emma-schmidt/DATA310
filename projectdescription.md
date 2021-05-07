# Emma Schmidt Final Project Description

### Rugby World Cup 2019 Game Outcomes

For my final project, I am interested in training a machine learning model to predict whether a team won or lost their game in the 2019 Rugby World Cup by inputting various other stats from the game. Sports are starting to use machine learning analysis in their game analysis, but I was not able to find any of this online for rugby. So, I am interested in seeing if I can come up with a preliminary model that predicts game wins based on other game statistics. Below is the first ten rows of my data (which contains 90 observations in total) so you can see the variables I am working with: 

| Game | Pool | Team         | Win or Loss | Point Differential | Meters Run | Runs | Clean Breaks | Offloads | Turnovers Conceded | Possession Pct | Territory Pct | Scrums Won | Scrums Won Pct | Lineouts Won | Lineouts Won Pct | Red Cards | Yellow Cards | Penalties Conceded |
| ---- | ---- | ------------ | ----------- | ------------------ | ---------- | ---- | ------------ | -------- | ------------------ | -------------- | ------------- | ---------- | -------------- | ------------ | ---------------- | --------- | ------------ | ------------------ |
| 1    | A    | Japan        | 1           | 20                 | 653        | 141  | 16           | 9        | 21                 | 50             | 48            | 4          | 100            | 13           | 92               | 0         | 0            | 5                  |
| 1    | A    | Russia       | 0           | \-20               | 289        | 112  | 11           | 4        | 17                 | 50             | 52            | 13         | 100            | 8            | 88               | 0         | 0            | 5                  |
| 2    | D    | Australia    | 1           | 18                 | 490        | 151  | 8            | 7        | 14                 | 67             | 72            | 3          | 100            | 19           | 90               | 0         | 0            | 9                  |
| 2    | D    | Fiji         | 0           | \-18               | 341        | 66   | 7            | 3        | 12                 | 33             | 28            | 4          | 100            | 11           | 100              | 0         | 1            | 12                 |
| 3    | C    | France       | 1           | 2                  | 435        | 120  | 15           | 13       | 16                 | 42             | 38            | 2          | 66             | 4            | 66               | 0         | 0            | 15                 |
| 3    | C    | Argentina    | 0           | \-2                | 308        | 113  | 7            | 8        | 14                 | 58             | 62            | 6          | 85             | 13           | 100              | 0         | 0            | 5                  |
| 4    | B    | New Zealand  | 1           | 10                 | 367        | 110  | 12           | 8        | 13                 | 47             | 41            | 8          | 100            | 7            | 77               | 0         | 0            | 4                  |
| 4    | B    | South Africa | 0           | \-10               | 370        | 104  | 7            | 2        | 18                 | 53             | 59            | 5          | 83             | 9            | 100              | 0         | 0            | 9                  |
| 5    | B    | Italy        | 1           | 25                 | 537        | 122  | 22           | 11       | 17                 | 57             | 63            | 9          | 100            | 14           | 82               | 0         | 0            | 5                  |
| 5    | B    | Namibia      | 0           | \-25               | 317        | 80   | 7            | 6        | 15                 | 43             | 37            | 11         | 100            | 17           | 75               | 0         | 0            | 9                  |


I will play with including different variables in the model to get the highest accuracy. In doing so, I will be able to see which of these variables have the greatest impact on game success. For example, we might not expect that the number of lineouts won would be important and that percent of lineouts won is a much better measure of game success. But, perhaps this is wrong -- by playing around with what variables I include in the model, I will hopefully be able to make some interesting discoveries. It's also possible that I won't be able to come up with a good model, which whould also be an interesting result and would indicate that important predictors of game success might not be the traditional markers we look to, such as meters run or penalties conceded. To make my model, I will need to start with doing some dimensionality reduction (possibly using TSNE). After that, I will run different models and see which one makes the best predictions. 

I don't have a working model yet -- once I have a script as a jumping off point, I will get started. 

Data sources: 

https://www.japantimes.co.jp/rugby-world-cup-2019-schedule/  

https://www.espn.com/rugby/matchstats?gameId=292888&league=164205
