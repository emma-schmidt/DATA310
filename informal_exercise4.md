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

#### Why would we include more than one filter? How many filters did you assign as part of your architecture when training a model to learn images of numbers from the mnist dataset?
Different filters extract different features from an image, so we would use multiple filters when we wish to extract multiple features from an image. I think we used one filter for the mnist dataset. 


### MSE Exercise

#### MSE: From your 400+ observations of homes for sale, calculate the MSE for the following.
- The 10 biggest over-predictions: **2343429801.622119**
- The 10 biggest under-predictions: **16028512191.533596**
- The 10 most accurate results (use absolute value): **882901443.9793992**

#### In which percentile do the 10 most accurate predictions reside? Did your model trend towards over or under predicting home values?
The ten most accurate predictions reside in the 70th percentile. This indicates that my model trends towards under-predicting home values.

#### Which feature appears to be the most significant predictor in the above cases?
It seems like square footage might be the most significant predictor in the above cases. Logically, it makes sense that houses with more square footage would have higher listing prices. Two houses could both have three bedrooms and two bathrooms, but if one house is 1,000 sqft and the other is 1,700 sqft, the second one will probably be priced higher due to either larger bedrooms/bathrooms, more rooms that are not counted as bedrooms/bathrooms (e.g. family rooms, offices, etc), or a combination of the two as well as other factors. This logic is mirrored in the ten most accurate predictions - square footage is pretty highly correlated with asking price/predicted price, while number of bedrooms/bathrooms is not quite as accurate a predictor of price. 

