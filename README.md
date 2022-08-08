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

## Summary