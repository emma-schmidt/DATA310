# Project 3

### Using two machine learning methods predict population values at 100 x 100 meter resolution throughout your selected country


### Validate the two models using different methods presented in this class


### Write a report assessing the two approaches and which of the two models was more accurate. Be sure to account for spatial variation throughout your selected location and provide substantive explanations for why those variations occurred. 




# Data

#### Country: Kenya

![image](https://user-images.githubusercontent.com/78189165/115153654-280c1480-a045-11eb-96f6-46cb6f643065.png)



Kenya as a whole had too much data for my computer to process, so I chose a much smaller area to look at - Kisumu. Below is an image that shows where Kisumu is located (shown in red), followed by a close up of the region: 

![image](https://user-images.githubusercontent.com/78189165/115153601-e54a3c80-a044-11eb-9531-43285afadfa8.png)


![image](https://user-images.githubusercontent.com/78189165/115153683-43771f80-a045-11eb-9c60-8ec00c3fb67e.png)

#### Raster Files

In addition to the shapefile of Kisumu, we have 12 raster files with information on important features of the region, as well as a population raster dataset. Not all features are equally important. Below, you can see the relative importance of each feature: 

(insert graph of this -- found in projthree_takeone line 162)


# Linear Regression

Plot of predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115168267-4b0be800-a088-11eb-82cb-4333d4196034.png)

Plot that shows the difference between actual and predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115168315-7393e200-a088-11eb-8c98-2b19f3c3ff6f.png)

As you can see, the linear regression model underpredicts the population in one area of Kisumu. This area is a highly populated area. The model likely underpredicts population in this area because it does not take into account building height, so does not realize that some buildings are tall and can house many people. 

3D plot of ME: 

![image](https://user-images.githubusercontent.com/78189165/115168740-e94c7d80-a089-11eb-8773-c66487046853.png)





