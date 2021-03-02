# Project 1

##### Select a city and scrape as many observations as possible from zillow. Try to obtain at least 400 observations from your selected location. Clean the housing data you obtained and create a number of usable features (independent variables) and targets (dependent variables). Set price as the response variable, and then set numbers of beds, number of bathrooms and total square footage as the predictors. Following the previous model you specified (6 houses in Mathews), import your new data set and train a new model on your target and features. Write a one and a half to two page report on your results and include the following:
- A description of the housing data you scraped from zillow
- A description of your model architecture
- An analysis of your model output
- An analysis of the output that assesses and ranks all homes from best to worst deal
- Include at least three plots that support your project report
- Stretch goal: add a spatial variable to your feature set and compare with the original model. Did this improve the predictive power of your model? If so, how?

##### Data Description

City selected: Atlanta

Original number of observations: 400

Final number of observations: 350

To obtain my data, I first used the BeautifulSoup library to scrape Zillow home postings from Atlanta, GA. The data I collected contained information on the address of each posting, as well as the number of bedrooms, the number of bathrooms, and the square footage of each house. I also obtained the listing price. 
After scraping this information, I exported the data in a table and imported it into ArcGIS Pro. I used a geoprocessing tool to geolocate the addresses on a map, and then added a shapefile of the Atlanta City Council districts to the map. Using the spatial join tool, I determined which district each house was in. Unfortunately as you can see from the map below, some of the homes fell outside of these districts. These homes were excluded from the final sample. I then exported the data into a .csv file and re-imported it into PyCharm. Below the map is a table of descriptive statistics summarizing the final 350 observations. 

![image](https://user-images.githubusercontent.com/78189165/109401451-d97fab00-791c-11eb-9acc-52d5ef3d9386.png)

|   |Asking Price|Beds|Baths|Sqft|
|---|-----|----|----|------|
|count|3.500000e+02|350.000000|350.000000|350.000000|
|mean|7.725935e+05|3.137143|2.862857|2298.097143|
|std|1.513848e+06|1.364109|1.709083|2651.213030|
|min|1.500000e+04|1.000000|1.000000|552.000000|
|25%|2.249250e+05|2.000000|2.000000|1150.000000|
|50%|3.274500e+05|3.000000|3.000000|1889.000000|
|75%|5.986250e+05|4.000000|3.000000|2732.000000|
|max|1.395000e+07|9.000000|18.000000|33000.000000|


##### Model Description

In addition to including variables on number of bedrooms, number of bathrooms, and square footage, I wanted my model to have a spatial element. To do this, I added data on the district that each house was located in (see Data Description section for more details). In order to include this in my model, I had to create twelve dummy variables for the twelve districts, giving a house a 1 value for the district it is located in and a 0 value for all other districts. The code below shows how I approached this:

```dummies = pd.get_dummies(atl_homes['District'])
atl_homes['d1']=np.asarray(dummies[1])
atl_homes['d2']=np.asarray(dummies[2])
atl_homes['d3']=np.asarray(dummies[3])
atl_homes['d4']=np.asarray(dummies[4])
atl_homes['d5']=np.asarray(dummies[5])
atl_homes['d6']=np.asarray(dummies[6])
atl_homes['d7']=np.asarray(dummies[7])
atl_homes['d8']=np.asarray(dummies[8])
atl_homes['d9']=np.asarray(dummies[9])
atl_homes['d10']=np.asarray(dummies[10])
atl_homes['d11']=np.asarray(dummies[11])
atl_homes['d12']=np.asarray(dummies[12])
```

![image](https://user-images.githubusercontent.com/78189165/109555679-d6fb8d80-7aa3-11eb-8113-7fa5617d980c.png)

![image](https://user-images.githubusercontent.com/78189165/109556082-5721f300-7aa4-11eb-8ffd-ee08c3accc16.png)



MSE with just beds, baths, and sqft: 2205958780709.3184 

MSE with beds, baths, sqft, and city council district: 1805440807305.1465

