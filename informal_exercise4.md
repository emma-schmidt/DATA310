### Convolution Exercise

##### Original matrix:

| |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
|-1|-1| 1|-1|-1|-2|-1|1|-1|
|1|0|-1|-2|0|-2|0|0|1|
|0|0|1|2|0|0|-1|-1|-1|
|-1|0|1|-2|-2|-2|-1|0|0|
|0|1|0|2|0|1|-1|1|1|
|0|1|0|-2|-2|1|-1|-1|0|
|-1|1|1|1|-2|-2|0|1|1|
|-1|0|0|-2|1|2|1|-1|-1|
|1|-1|0|1|-1|2|-1|1|1|

###### Filter #1:

| | | |
|---|---|---|
|0|1|0|
|0|0|0|
|1|1|0|


###### Filter #2:

| | | |
|---|---|---|
|0|1|1|
|1|1|1|
|0|0|0|

##### New matrix, filter #1 applied:

| |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|-1|2|2|1|-2|-2|-1|
|-1|0|-3|-4|-6|-3|-1|
|1|2|4|2|1|-1|-1|
|1|2|-4|-6|-3|-1|-2|
|1|2|4|-1|-3|-3|-2|
|0|0|-4|-3|4|2|-1|
|1|0|2|-2|-1|1|1|


##### New matrix, filter #2 applied:


| |  |  |  |  |  |  |
|---|---|---|---|---|---|---|
|0|-3|-5|-7|-5|-2|1|
|0|0|1|0|-3|-2|-2|
|1|2|-1|-6|-6|-5|-3|
|2|2|-2|-1|-3|0|1|
|2|1|-2|-2|-2|-1|0|
|2|1|-4|-4|-4|-3|-1|
|1|0|-2|-3|2|3|-1|

#### What is the purpose of using a 3x3 filter to convolve across a 2D image matrix?
The purpose of using a 3x3 filter to convolve across a 2D image matrix is to extract different features from the image (for example, by emphasizing horizontal lines).

#### Why would we include more than one filter? 
Different filters extract different features from an image, so we would use multiple filters when we wish to extract multiple features from an image. 

#### How many filters did you assign as part of your architecture when training a model to learn images of numbers from the mnist dataset?
One. 


### MSE Exercise

#### MSE: From your 400+ observations of homes for sale, calculate the MSE for the following.
- The 10 biggest over-predictions
- The 10 biggest under-predictions
- The 10 most accurate results (use absolute value)

#### In which percentile do the 10 most accurate predictions reside? Did your model trend towards over or under predicting home values?

#### Which feature appears to be the most significant predictor in the above cases?

#### Stretch goal: calculate the MAE and compare with your MSE results