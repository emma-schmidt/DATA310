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

This model is trained as a logistic regression model using the tensorflow estimator API and the DHS data from Kenya. 

### Wealth 1:

```python:
accuracy            0.753285
average_loss        0.515050
loss                0.515025
global_step     35960.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112539402-5587da00-8d87-11eb-8fc5-feb6d5197820.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112539373-4d2f9f00-8d87-11eb-9efb-b0d8520c03db.png)


### Wealth 2:  

```python:
accuracy            0.793826
average_loss        0.496922
loss                0.496950
global_step     35960.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112539020-de524600-8d86-11eb-9875-bd65a95a03f5.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112539000-d72b3800-8d86-11eb-92d2-97de21fad51c.png)


### Wealth 3: 

```python:
accuracy            0.810512
average_loss        0.478042
loss                0.478025
global_step     35960.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112538618-713eb080-8d86-11eb-982f-41629a77d977.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112538597-6b48cf80-8d86-11eb-84ca-ab84464d45bc.png)

### Wealth 4: 

```python:
accuracy            0.821097
average_loss        0.455290
loss                0.455296
global_step     35960.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112538242-0b522900-8d86-11eb-9a0f-c6a9f1db76c8.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112538205-01c8c100-8d86-11eb-8a44-81553182a7ac.png)


### Wealth 5: 

```
accuracy            0.863307
average_loss        0.365876
loss                0.365920
global_step     35960.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112537781-764f3000-8d85-11eb-80f5-ff5e90c00f4c.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112537741-6c2d3180-8d85-11eb-9602-9ec4a26fe2b0.png)


## Model 4 - Gradient Boosting Model

For this model, I trained a gradient boosting model using decision trees with the tensorflow estimator. Below are the results for each wealth bin. As with the other models, it does a much better job of predicting very high and very low wealth, and a pretty bad job of predicting more middle wealth levels. Wealth 1 is an interesing (and suspicious) category for this one - it appears to have 100% accuracy. I can't find an issue with the code, but I'm also not convinced that is right so we should be cautious of that particular result. 


### Wealth 1:


```python:
accuracy                  1.000000
accuracy_baseline         0.712066
auc                       1.000000
auc_precision_recall      1.000000
average_loss              0.000022
label/mean                0.287934
loss                      0.000022
precision                 1.000000
prediction/mean           0.287944
recall                    1.000000
global_step             100.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112536423-d3e27d00-8d83-11eb-8485-aee6d7ef6c63.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112536392-cd540580-8d83-11eb-85fc-c1c2f1791766.png)

### Wealth 2:


```
accuracy                  0.794947
accuracy_baseline         0.795052
auc                       0.766762
auc_precision_recall      0.375286
average_loss              0.408367
label/mean                0.204948
loss                      0.408367
precision                 0.409091
prediction/mean           0.204926
recall                    0.001145
global_step             100.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112535882-28d1c380-8d83-11eb-8984-eddbf5fb48ed.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112535851-22434c00-8d83-11eb-80da-43bcdf49c626.png)


### Wealth 3:

```
accuracy                  0.809808
accuracy_baseline         0.809782
auc                       0.714789
auc_precision_recall      0.299503
average_loss              0.408735
label/mean                0.190218
loss                      0.408735
precision                 1.000000
prediction/mean           0.187240
recall                    0.000137
global_step             100.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112531658-346ebb80-8d7e-11eb-885b-b880d33b34f2.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112536650-1f952680-8d84-11eb-8cca-f64791160a63.png)


### Wealth 4: 

```
accuracy                  0.821514
accuracy_baseline         0.821332
auc                       0.714486
auc_precision_recall      0.298418
average_loss              0.397650
label/mean                0.178668
loss                      0.397650
precision                 0.606061
prediction/mean           0.175882
recall                    0.002918
global_step             100.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112494443-6cafd300-8d59-11eb-81c4-73a78ddfaf8d.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112494408-64579800-8d59-11eb-86c4-1c3d606a539a.png)


### Wealth 5:

```
accuracy                  0.861873
accuracy_baseline         0.853869
auc                       0.791587
auc_precision_recall      0.397457
average_loss              0.331681
label/mean                0.146131
loss                      0.331681
precision                 0.594345
prediction/mean           0.144980
recall                    0.172525
global_step             100.000000
```

#### ROC Plot:

![image](https://user-images.githubusercontent.com/78189165/112493193-548b8400-8d58-11eb-917b-43898d9279bf.png)

#### Predicted Probabilities Plot:

![image](https://user-images.githubusercontent.com/78189165/112492946-18f0ba00-8d58-11eb-9333-8c1fae9627a7.png)


## So, which model is best? 



