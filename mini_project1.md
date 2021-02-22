# Mini Project 1

Link to input video: [Input](https://youtu.be/rxEkGZRav0g)

Link to output video: [Output](https://youtu.be/VnRDmG9oNUc)

#### Was your social distance detector effective at detecting potential violations? 

This social distance detector appears to be effective at detecting potential violations. The boxes are green when it looks like people are sufficiently distanced, and red when they come into closer contact with each other. 

#### Are you able to describe how the distance detector is applying its calculations of either being safe or noting a violation?

The detector utilizes three different functions: Check, Setup, and ImageProcess. 

- The **Check** function takes two inputs, a and b. I assume that these are two things in the image that the detector determined to be people. It then calculates the distance between the two. If the distance is less than a given amount, the function returns True. If the distance is larger than that amount, the function returns False.
- The **Setup** function appears to separate the layers in the video. I am not completely sure what is happening, but I assume it is some sort of preprocessing necessary for the other functions to run properly. 
- The **ImageProcess** function takes an image as an input (one frame from the input video). This function does the bulk of the work for the detector, determining where there are people in the frame, uses the Check function to determine whether they are too close to each other, and puts a box around them. I think that the box around the people is red or green, based on whether the Check function returned True (which results in a red box) or False (which results in a green box). 


#### Do you think this approach would be effective for estimating new infections in real time? How would you implement such an approach in response to the COVID-19 pandemic we are currently experiencing?

While this detector could not estimate whether people were infected or not, it could be very useful in contact tracing once we have determined that someone is positive for COVID-19. Implementing this for contact tracing could be tricky, because it would require facial recognition to trace the movements of an infected individual, and this could be seen as a breach of privacy. That said, it has other applications in reducing the spread of COVID that would require much less in terms of privacy breaches. If someone - for example, a store manager - wanted to better enforce social distancing, this detector could be utilized to see which areas of their store have the most breaches of social distancing. This information could be used to better enforce social distancing in that area, perhaps by re-arranging shelves to allow for more distancing, or by strategically placing an employee near that area to remind customers to maintain social distancing. 

#### What limitations or improvements might you include in order to improve your proposed design?

If used in the context that I suggest above - to determine areas with frequent social distancing breaches - I would add a function to the detector that divides the video frames into a grid, and then counts the number of social distance violations within each grid square in each frame. The function would then return an output indicating which grid squares had significantly more violations than the others. This would help the user to easily identify problem areas. 
