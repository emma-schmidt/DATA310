# 2/5 Informal Exercise

### 1. According to Maroney, what is the difference between traditional programming and machine learning?

In traditional programming, the user inputs data and the rules by which to classify that data, and the machine returns answers. In machine learning, the user inputs data and the answers to the data (labels), and the machine figures out what the rules of classification are.

### 2. With the first basic script that Maroney used to predict a value output from the model he estimated (he initially started with 10 that predicted ~31. Modify the predict function to produce the output for the value 7. Do this twice and provide both answers. Are they the same? Are they different? Why is this so?

The first time I ran the script and produced the output value for 7, my code returned a value of 22.000097, while the second time I ran the script my code returned a value of 21.988254. While these are technically different numbers, they are very close to each other in value (and also very close to the value I would have predicted without the machine learning -- 22). The values were different because the neural network is trained on just six data points and deals in probabilities -- each time it ran the script, it produced slightly different probabilities due to the lack of training data. However, this discrepancy may be solved by running more epochs in an attempt to get the loss value down to zero.

### 3. Using the script you produced to predict housing price, take the provided six houses from Mathews, Virginia and train a neural net model that estimates the relationship between them. Based on this model, which of the six homes present a good deal? Which one is the worst deal? Justify your answer.

To predict housing prices, I used data from these six house postings to train a neural network. For my x variables, I inputted number of bedrooms (x1), number of bathrooms (x2), and square footage (x3). Price was my y variable. After training the neural network, I predicted the cost of each of the six houses. Below is a table of my results, comparing predicted price to actual price:

| House        | Predicted Price | Actual Price |
| ------------ |:---------------:| ------------:|
| Church       | $4.115K         | $3.99K       |
| Hudgins      | $1.358K         | $0.97K       |
| Mathews      | $2.830K         | $3.475K      |
| Mobjack      | $3.140K         | $2.89K       |
| Moon         | $1.568K         | $2.5K        |
| Mewptcomfort | $2.953K         | $2.29K       |

Based on this information, Mathews and Moon are both bad deals, while Hudgins and Newptcomfort are both good deals. Mobjack and Church are marginally good deals. However, this model does not take into consideration factors other than number of bedrooms, number of bathrooms, and square footage, and is therefore likely a poor indicator of actual house value.
