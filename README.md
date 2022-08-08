# Neural_Network_Charity_Analysis

## Overview

With my knowledge of machine learning and neural networks, I'll use the features in a provided dataset to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, I have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years.

I will use a deep learning neural network to create a classification model that can predict if an Alphabet Soup–funded organization will be successful. My goal is to make a model that achieves at least 75% accuracy. So if my initial model does not meet this requirement I will then find ways to optimize the model in order to reach that goal.

## Results

### Data Preprocessing

In order to prepare the dataset for deep learning I began by inspecting the data and discovering it's general shape and content. I found the following charateristics:
- 12 columns
- 34299 rows
- 4 integer columns 
- 8 string columns
- IS_SUCCESSFUL column which will be my target

In looking at a sample of the table and calculating the number of unique values in each column, it looked like the EIN and NAME columns would be extra noise and have little value for our model. Though the NAME column did have repeated values that might be worth binning together, I dropped both of these columns to start.

![nunique](https://github.com/Olibabba/Neural_Network_Charity_Analysis/blob/main/resources/nunique.png)

A closer look at the APPLICATION TYPE and CLASSIFICATION columns showed that these would benifit from binning.

After calculating the value_counts of the APPLICATION TYPE column and plotting the denisty of it's values, I decided to cutoff and replace the values with less than 100 occurances. This kept the most unique groups and left the total number of bins at the prefered maximum of 10.

![App Type Counts](https://github.com/Olibabba/Neural_Network_Charity_Analysis/blob/main/resources/app_type_count.png)
![App Type Density](https://github.com/Olibabba/Neural_Network_Charity_Analysis/blob/main/resources/app_type_density.png)

After calculating the value_counts of the CLASSIFICATION column and plotting the denisty of it's values, I decided to cutoff and replace the values with less than 200 occurances. 

![Classification Density](https://github.com/Olibabba/Neural_Network_Charity_Analysis/blob/main/resources/classification_density.png)
![Classificaiton Binning Complete](https://github.com/Olibabba/Neural_Network_Charity_Analysis/blob/main/resources/classification_binning.png)

Next I made a list of all the catigorical variables and encoded them using one-hot-encoder. These were stored in a sepearte dataframe which I merged with the original dataframe while dropping the original unencoded columns.

After this I split the preprocessed data into features and target arrays, then further into training and testing datasets.

And finally I scaled the data in order to standardize the variables.

### Compiling, Training, and Evaluating the Model

With the data successfully preprocessed, I proceeded with the creation of a neural network with the following charateristics:

- Using TensorFlow Keras I initialized a Sequential Model
- Two hidden Layers with a ReLu activation function
- The first hidden layer with 8 neurons
- The second hidden layer with 5 neurons
- An output layer with a Sigmoid activation function
- A callback that saves the model's weights every 5 epochs
- 100 epochs

I selected this configuration as a basic starting point for a lightweigh model and it came close to my goal reaching 72.5% accuracy.

### Optimizing the MOdel

Since my initial model did not reach my goal I attempted several options to optimize the model for better accuracy.

First I added neurons to the hidden layers. With a modest boost I hoped for better reults
- The first hidden layer with 10 neurons
- The second hidden layer with 8 neurons

![]()

These changes gave me very similar results as my initial model

![]()

Next I added a hidden layer. Keeping the additional neurons from attempt one:
- The first hidden layer with 10 neurons
- The second hidden layer with 8 neurons
- The third hidden layer with 5 neurons

![]()

These changes did not give me better results

![]()

For my third attempt I processed the data again, but this time I removed two more columns. These were binary columns which I suspected were not adding to the classification. Since the third hidden layer did not offer any improvements I reverted to only two hidden layers.

![]()

These changes did not give me better results

In a last ditch attempt I added the NAME column back in and choose to bin everything with less than 50 occurnaces into an "other" group. This brought the number of unique variables down from 19,568 to 52. This was far more than the recommended maximum of 10 bins, but Google was so kinf to le tme use their compute power, so I one-hot-encoded all 52 values and built the same model as my first optimization. 

![]()

To my surprise, this successfully pushed the accuracy above my goal

![]()
![]()
![]()

I celebrated by saving the model to a HDF5 file in order to share it with you.

## Summary