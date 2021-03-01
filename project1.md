# Project 1

##### Select a city and scrape as many observations as possible from zillow. Try to obtain at least 400 observations from your selected location. Clean the housing data you obtained and create a number of usable features (independent variables) and targets (dependent variables). Set price as the response variable, and then set numbers of beds, number of bathrooms and total square footage as the predictors. Following the previous model you specified (6 houses in Mathews), import your new data set and train a new model on your target and features. Write a one and a half to two page report on your results and include the following:
- A description of the housing data you scraped from zillow
- A description of your model architecture
- An analysis of your model output
- An analysis of the output that assesses and ranks all homes from best to worst deal
- Include at least three plots that support your project report
- Stretch goal: add a spatial variable to your feature set and compare with the original model. Did this improve the predictive power of your model? If so, how?

##### Data Overview

City selected: Atlanta

Original number of observations: 400

Final number of observations: 350

|   |District|Price|Beds|Baths|Sqft|
|---|---------|-----|----|----|------|
|count|350.000000|3.500000e+02|350.000000|350.000000|350.000000|
|mean|6.540000|7.725935e+05|3.137143|2.862857|2298.097143|
|std|3.147264|1.513848e+06|1.364109|1.709083|2651.213030|
|min|1.000000|1.500000e+04|1.000000|1.000000|552.000000|
|25%|4.000000|2.249250e+05|2.000000|2.000000|1150.000000|
|50%|7.000000|3.274500e+05|3.000000|3.000000|1889.000000|
|75%|9.000000|5.986250e+05|4.000000|3.000000|2732.000000|
|max|12.000000|1.395000e+07|9.000000|18.000000|33000.000000|


![image](https://user-images.githubusercontent.com/78189165/109401451-d97fab00-791c-11eb-9acc-52d5ef3d9386.png)




MSE with just beds, baths, and sqft: 2205958780709.3184 
MSE with beds, baths, sqft, and city council district: 1805440807305.1465

![image](https://user-images.githubusercontent.com/78189165/109555679-d6fb8d80-7aa3-11eb-8113-7fa5617d980c.png)
