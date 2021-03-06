# Project 1

### Data Description

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


### Model Description

In addition to including variables on number of bedrooms, number of bathrooms, and square footage, I wanted my model to have a spatial element. To do this, I added data on the district that each house was located in (see Data Description section for more details). In order to include this in my model, I had to create twelve dummy variables for the twelve districts, giving a house a 1 value for the district it is located in and a 0 value for all other districts. The code below shows how I approached this:

```
dummies = pd.get_dummies(atl_homes['District'])

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

I used a Keras Sequential model, with stochastic gradient descent as the optimizer and mean squared error as the loss function. The code below shows my model:

```
model = keras.Sequential([keras.layers.Dense(units = 1, input_shape=[15])])
model.compile(optimizer = 'sgd', loss = 'mean_squared_error')

x1 = np.asarray(atl_homes['Beds'])
x2 = np.asarray(atl_homes['Baths'])
x3 = np.asarray(atl_homes['sqft_scale'])
x4 = np.asarray(atl_homes['d1'])
x5 = np.asarray(atl_homes['d2'])
x6 = np.asarray(atl_homes['d3'])
x7 = np.asarray(atl_homes['d4'])
x8 = np.asarray(atl_homes['d5'])
x9 = np.asarray(atl_homes['d6'])
x10 = np.asarray(atl_homes['d7'])
x11 = np.asarray(atl_homes['d8'])
x12 = np.asarray(atl_homes['d9'])
x13 = np.asarray(atl_homes['d10'])
x14 = np.asarray(atl_homes['d11'])
x15 = np.asarray(atl_homes['d12'])

xs = np.stack([x1, x2, x3, x4, x5, x6, x7, x8, x9, x10, x11, x12, x13, x14, x15], axis=1)
ys = np.asarray(atl_homes['prices_scale'])

model.fit(xs, ys, epochs=500)
```

When training my model, I used 500 epochs. However, I probably could have used less and gotten the same result, as the plot below shows that my loss function did not improve significantly (if at all) as they ran. 

![image](https://user-images.githubusercontent.com/78189165/109555679-d6fb8d80-7aa3-11eb-8113-7fa5617d980c.png)

### Model Analysis

![image](https://user-images.githubusercontent.com/78189165/109556082-5721f300-7aa4-11eb-8ffd-ee08c3accc16.png)


Based on this model, the “best deals” are located in the upper left hand quarter of the graph above, and the “worst deals” are located in the lower right hand corner of the graph above. But, as you can see from the graph, my model does a pretty bad job of predicting the asking prices of homes in Atlanta. The MSE of this model (that includes bedrooms, bathrooms, square footage, and city council district) is 1805440807305.1465. This is an improvement over the MSE of the same model but excluding the city council districts, which was 2205958780709.3184. The improvement on the MSE indicates that including data on the city council district makes the model better. Including the city council district improves the model by serving as an imperfect proxy for other spatial variables such as school district or crime rate. 

There are several factors contributing to the inaccuracy of the model, the most apparent of which is the small sample size. However, even with a significantly larger sample size, I am not confident that the model - with these variables - could ever do a decent job of predicting the asking prices. First of all, there is a lot more that goes into the asking price of a home than just bedrooms, bathrooms, square footage, and general location. Additional variables that could contribute to the accuracy of the model include, but are not limited to:
- Time elapsed since the home was initially put up for sale (since we are trying to estimate asking price, the longer the home is on the market, the lower the asking price may be)
- School district 
- Local crime rate
- Neighborhood-level variables, such as average home value and racial composition
- Distance to downtown
- Acreage (size of yard)



