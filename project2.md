# Project 2 - Kenyan DHS Data

For this project, I am interested in predicting wealth based on DHS data from Kenya. Below is a summary of observations as they are distributed across the five wealth categories: 

![image](https://user-images.githubusercontent.com/78189165/112401182-59acec80-8ce0-11eb-8487-07ff153828bf.png)


## Model 1 - Penalized Logistic Regression

See below for a summary of the top_models: 

```python:
      penalty .metric .estimator  mean     n std_err .config              
      <dbl> <chr>   <chr>      <dbl> <int>   <dbl> <chr>                
 1 0.0001   roc_auc hand_till  0.643     1      NA Preprocessor1_Model01
 2 0.000127 roc_auc hand_till  0.643     1      NA Preprocessor1_Model02
 3 0.000161 roc_auc hand_till  0.643     1      NA Preprocessor1_Model03
 4 0.000204 roc_auc hand_till  0.643     1      NA Preprocessor1_Model04
 5 0.000259 roc_auc hand_till  0.643     1      NA Preprocessor1_Model05
 6 0.000329 roc_auc hand_till  0.642     1      NA Preprocessor1_Model06
 7 0.000418 roc_auc hand_till  0.642     1      NA Preprocessor1_Model07
 8 0.000530 roc_auc hand_till  0.642     1      NA Preprocessor1_Model08
 9 0.000672 roc_auc hand_till  0.642     1      NA Preprocessor1_Model09
10 0.000853 roc_auc hand_till  0.641     1      NA Preprocessor1_Model10
11 0.00108  roc_auc hand_till  0.641     1      NA Preprocessor1_Model11
12 0.00137  roc_auc hand_till  0.641     1      NA Preprocessor1_Model12
13 0.00174  roc_auc hand_till  0.640     1      NA Preprocessor1_Model13
14 0.00221  roc_auc hand_till  0.640     1      NA Preprocessor1_Model14
15 0.00281  roc_auc hand_till  0.639     1      NA Preprocessor1_Model15
```

And below is a plot of penalty values versus the area under the ROC curve:

![image](https://user-images.githubusercontent.com/78189165/112401665-6da51e00-8ce1-11eb-8fef-91272b232bd4.png)

Based on the above information, I selected model 7 as the model that performed the best because it had very close to the highest ROC, and is the model before a slight drop off in the graph. This model has a penalty of 0.000418. That said, I'm not convinced that it is significantly better than other models - based on the available information there is very little difference bewteen them, especially the first nine. 

Below are the ROC plots, showing how well this model predicted the wealth categories: 

![image](https://user-images.githubusercontent.com/78189165/112402323-ba3d2900-8ce2-11eb-92d8-a2392d45cdc2.png)

The dotted 45 degree line through each of the graphs shows what the curve would look like if our model was no better than random guessing. The higher the curve is above that line, the better this model is at predicting that particular wealth category. As you can see, the most prominent curves can be seen on graph 1 and graph 5. This makes sense - the model is good at predicting those with very high, and very low, incomes. It does not fare as well with those in the middle ranges. This is to be expected, as predicting the distinctions between these is likely much more complicated and nuanced, and would likely require more variables.


## Model 2 - Random Forest

Below, you can see the AUC - ROC values for the randomly selected predictors, and the minimal node size. 

![image](https://user-images.githubusercontent.com/78189165/112403190-561b6480-8ce4-11eb-921c-6fdeeb465712.png)

In general, the results were very comparable to the linear regression. You can see this in this graph, comparing the AUC of the linear regression model to the AUC of the random forest model: 

![image](https://user-images.githubusercontent.com/78189165/112403293-85ca6c80-8ce4-11eb-8d27-e7ff29faa2cb.png)

While the results are almost identical, based on this image we can see that the random forest model performs slightly better. Below, we can see the ROC plots for the random forest, showing how well this model predicted the wealth categories: 

![image](https://user-images.githubusercontent.com/78189165/112403455-d17d1600-8ce4-11eb-98de-7f983d62689f.png)

Again, we see that the model does significantly better with predicting those with very high or very low wealth, and does not fare as well with those in the middle. 

Interestingly, in this model, gender is weighted significantly lower than other predictors. This is interesting, because I expected it to be higher. In this model, at least, age is the most important feature. Below, we can see the relative importance of each feature included in the model: 

![image](https://user-images.githubusercontent.com/78189165/112403521-efe31180-8ce4-11eb-885f-d395bdd16ff3.png)



## Model 3 - Logistic Regression with Linear Classifier

#### Wealth 1:

```python:
{'accuracy': 0.7522943, 'average_loss': 0.5178214, 'loss': 0.51782596, 'global_step': 35960}
```

ROC curve:

![image](https://user-images.githubusercontent.com/78189165/112410097-0abb8300-8cf1-11eb-976b-dc15cd1ee17a.png)

#### Wealth 2:  

```python:
{'accuracy': 0.7949473, 'average_loss': 0.4964159, 'loss': 0.4964591, 'global_step': 35960}
```


#### Wealth 3: 

```python:
{'accuracy': 0.81241524, 'average_loss': 0.4743538, 'loss': 0.4743492, 'global_step': 35960}
```


#### Wealth 4: 

```python:
{'accuracy': 0.8247471, 'average_loss': 0.45209032, 'loss': 0.45204842, 'global_step': 35960}
```

#### Wealth 5: 

```python:
{'accuracy': 0.8644541, 'average_loss': 0.36294478, 'loss': 0.36292008, 'global_step': 35960}
```



## Model 4 - Gradient Boosting Model


#### Wealth 1:


```python:
accuracy                  1.000000
accuracy_baseline         0.713109
auc                       1.000000
auc_precision_recall      1.000000
average_loss              0.000022
label/mean                0.286891
loss                      0.000022
precision                 1.000000
prediction/mean           0.286901
recall                    1.000000
global_step             100.000000
```


#### Wealth 2:



#### Wealth 3:



#### Wealth 4: 



#### Wealth 5:


## Best Model??? 


