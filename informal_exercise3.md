# Informal Exercise 3

#### Last time you did an exercise (convolutions and pooling) where you manually applied a 3x3 array as a filter to an image of two people ascending an outdoor staircase. Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times. Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size. What are you functionally accomplishing as you apply the filter to your original array (see the following snippet for reference)? 

##### Original Image:
![original staircase](https://user-images.githubusercontent.com/78189165/108776436-65b25c80-7530-11eb-9775-f5416816d885.png)

##### Filter #1: `filter1 = [ [1, 0, 1], [0, 0, 0], [-1, 0, -1]]`

![image](https://user-images.githubusercontent.com/78189165/108777564-fb9ab700-7531-11eb-95c2-0084eacf6a0c.png)

Filter 1 highlighted the vertical and horizontal lines while darkening everything else. This is because of the placement of the zeros in the filter matrix. While it appears that the left part of the image is brighter than the right, this is not because of this filter, but a reflection of the original image (see above). 

##### Filter #2: `filter2 = [ [0, 0, -1], [0, 0, 2], [0, 0, -1]]`

![Filter 2](https://user-images.githubusercontent.com/78189165/108777392-be362980-7531-11eb-860d-6cc4e0aa6abe.png)

Filter 2 highlights the vertical lines as a product of the placement of the zeros. It also made the rest of the image significantly darker. 

##### Filter #3: `filter3 = [ [-1, 0, 0], [2, 0, 0], [-1, 0, 0]]`

![Filter 3](https://user-images.githubusercontent.com/78189165/108777454-d148f980-7531-11eb-9182-872c3b8737f0.png)

Filter 3 is the same as filter 2, but with the order of each line reversed. I wanted to see if this made a difference in the image produced, and it appears that it does not. Again, the vertical lines are emphasized because of the zeros. 

#### Why is the application of a convolving filter to an image useful for computer vision? 

Applying a convolving filter enhances some features of an image while dulling/darkening others. This can make it easier for the computer to "see" identifying features of an image, which can help it to classify the image. 

#### Stretch goal: instead of using the misc.ascent() image from scipy, can you apply three filters and weights to your own selected image? Again describe the results.

#### Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result. In effect what have you accomplished by applying this filter? Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? Did the resulting image increase in size or decrease? Why would this method be useful? Stretch goal: again, instead of using misc.ascent(), apply the pooling filter to one of your transformed images.

#### Convolve the 3x3 filter over the 9x9 matrix and provide the resulting matrix.
