# Mini Project 1

Link to input video: [Input](https://youtu.be/rxEkGZRav0g)

Link to output video: [Output](https://youtu.be/VnRDmG9oNUc)

#### Was your social distance detector effective at detecting potential violations? 

This social distance detector was effective at detecting potential violations. 

#### Are you able to describe how the distance detector is applying its calculations of either being safe or noting a violation?

The detector utilizes three different functions: Check, Setup, and ImageProcess. 

- The **Check** function takes two inputs, a and b. I assume that these are two things in the image that the detector determined to be people. It then calculates the distance between the two. If the distance is less than a given amount, the function returns True. If the distance is larger than that amount, the function returns False.
- The **Setup** function appears to separate the layers in the video. I am not completely sure what is happening, but I assume it is some sort of preprocessing necessary for the other functions to run properly. 
- The **ImageProcess** function takes an image as an input (one frame from the input video). This function does the bulk of the work for the detector, determining where there are people in the frame, uses the Check function to determine whether they are too close to each other, and puts a box around them. I think that the box around the people is red or green, based on whether the Check function returned True (which results in a red box) or False (which results in a green box). 


#### Do you think this approach would be effective for estimating new infections in real time? How would you implement such an approach in response to the COVID-19 pandemic we are currently experiencing?

#### What limitations or improvements might you include in order to improve your proposed design?
