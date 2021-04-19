# Project 3


# Data

#### Country: Kenya

![image](https://user-images.githubusercontent.com/78189165/115153654-280c1480-a045-11eb-96f6-46cb6f643065.png)

Kenya as a whole had too much data for my computer to process, so I chose a much smaller area to look at - Kisumu. Kisumu is an area next to Lake Victoria, located in southwest Kenya. Below is an image that shows where Kisumu is located (shown in red), followed by a close up of the region: 

![image](https://user-images.githubusercontent.com/78189165/115153601-e54a3c80-a044-11eb-9531-43285afadfa8.png)

![image](https://user-images.githubusercontent.com/78189165/115153683-43771f80-a045-11eb-9c60-8ec00c3fb67e.png)

#### Raster Files

In addition to the shapefile of Kisumu, we have 12 raster files with information on important features of the region, as well as a population raster dataset. 


# Linear Regression

Plot of predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115168267-4b0be800-a088-11eb-82cb-4333d4196034.png)

Plot that shows the difference between actual and predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115168315-7393e200-a088-11eb-8c98-2b19f3c3ff6f.png)

As you can see, the linear regression model underpredicts the population in one area of Kisumu. This area is a highly populated area. The model likely underpredicts population in this area because it does not take into account building height, so does not realize that some buildings are tall and can house many people. 

3D plot of ME: 

![image](https://user-images.githubusercontent.com/78189165/115168740-e94c7d80-a089-11eb-8773-c66487046853.png)

All in all, this plot shows that the model is relatively good. It could probably be improved by increasing the number of variables that can be used to determine population density in more urban areas. 

# Random Forest

Plot of the model: 

![image](https://user-images.githubusercontent.com/78189165/115168900-860f1b00-a08a-11eb-95ee-f5907f5cc6cc.png)


Plot of the variable importance: 

![image](https://user-images.githubusercontent.com/78189165/115168923-98895480-a08a-11eb-8466-5dac87c1d8ba.png)


Plot of predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115169059-fae25500-a08a-11eb-91a4-5702a82348d5.png)

Plot that shows the difference between actual and predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115169071-06358080-a08b-11eb-94f5-ba8f7fcd3da7.png)

3D plot that shows the difference between actual and predicted population sums: 

![image](https://user-images.githubusercontent.com/78189165/115169132-2feea780-a08b-11eb-8545-931f5a4640a4.png)

3D plot of ME: 

![image](https://user-images.githubusercontent.com/78189165/115169197-59a7ce80-a08b-11eb-863b-439daf6c82de.png)

Again, the model is relatively good but could probably be improved by increasing the number of variables that can be used to determine population density in more urban areas. That said, it is **not quite as good as the linear model, with higher ME in urban areas. Therefore, the linear regression model is the best out of the two.**
