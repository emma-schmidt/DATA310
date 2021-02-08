# 2/8 Informal Exercise

### 1. In the video, First steps in computer vision, Laurence Maroney introduces us to the Fashion MNIST data set and using it to train a neural network in order to teach a computer “how to see.” One of the first steps towards this goal is splitting the data into two groups, a set of training images and training labels and then also a set of test images and test labels. Why is this done? What is the purpose of splitting the data into a training set and a test set?

By splitting the data into a training set and a testing set, we can first train the neural network on our data and see how accurate it is with classifying this data, and then we can test the neural network on data it has not seen yet and see how accurate it is with classifying this new data. Because we know the actual classifications of all of the data, we can get a read on how well the neural network is doing with its classification. We can also evaluate whether the model is overfit or underfit, and adjust accordingly. 

### 2. The fashion MNIST example has increased the number of layers in our neural network from 1 in the past example, now to 3. The last two are .Dense layers that have activation arguments using the relu and softmax functions. What is the purpose of each of these functions? Also, why are there 10 neurons in the third and last layer in the neural network?

..* The purpose of the relu function is to ensure that there are no negative numbers in the output of the neurons. If the output of a neuron is less than zero, it sets it to zero.
..* The purpose of the softmax function is to make it easy to get results from your neural network. Neurons on the bottom layer of the model are probabilities, and the softmax function sets the highest probability equal to 1, and all others equal to 0. This way, the user doesn't have to write a function that finds the highest probability - we just have to identify the 1. 

### 3. In the past example we used the optimizer and loss function, while in this one we are using the function adam in the optimizer argument and sparse_categorical- crossentropy for the loss argument. How do the optimizer and loss functions operate to produce model parameters (estimates) within the model.compile() function?

### 4. Using the mnist drawings dataset (the dataset with the hand written numbers with corresponding labels) answer the following questions:
#### What is the shape of the images training set (how many and the dimension of each)?
#### What is the length of the labels training set?
#### What is the shape of the images test set?
#### Estimate a probability model and apply it to the test set in order to produce the array of probabilities that a randomly selected image is each of the possible numeric outcomes (look towards the end of the basic image classification exercises for how to do this — you can apply the same method applied to the Fashion MNIST dataset but now apply it to the hand written letters MNIST dataset).

### 5. Use np.argmax() with your predictions object to return the numeral with the highest probability from the test labels dataset.

### 6. Produce a plot of your selected image and the accompanying histogram that illustrates the probability of that image being the selected number
