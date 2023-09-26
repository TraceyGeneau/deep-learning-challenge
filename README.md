## Overview


For this assignment, I was tasked with assisting Alphabet Soup, a nonprofit foundation, in developing a machine learning model to aid in the selection of funding applicants with the highest probability of success in their ventures. My objective was to create a binary classifier using machine learning and neural networks to predict whether applicants are likely to be successful if funded by Alphabet Soup.

The aim of this assignement was to build a binary classification model for Alphabet Soup, a nonprofit foundation, to improve funding decisions by identifying organizations likely to succeed. The dataset consisted of metadata for over 34,000 previously funded organizations. Leveraging machine learning and neural networks, I preprocessed data, selected features, and evaluated models, focusing on binary classification (Successful or Not Successful).  This model aims to assist Alphabet Soup in making informed financial decisions.

## Results

### Data Pre Processesing 

The target variables of this model relate to the binary classification of a positive outcome, 'Success,' or a negative outcome, 'Failure'.  The EIN and NAME identification columns were excluded as they are irrelevant for model building.

The following columns were included in the model:

* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special considerations for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively

#### Original Unique Values for each Column 

![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/unique%20values.png)


#### Application Type

The first parameter that was adjust was the application type.  It had a total number of unique values of 17.  Through binning this value was changed on several ocassions throughout the process.  Ultimately, the final cut off values of 16 for binning.  This ultimately lead to 13 uniques values in the model.

##### Unique Values for application type

![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/application%20type.png)

#### Classification type

The number of unique values for classification was 71.  Through optimization it was reduced to 32 unique values with a cutoff of 16 counts. This number was chosen through several runs of the model going both above and below 16 as the cut off.  In the end, this was the number that seems to lead to the best accuracy. 

##### Unique values for Classifciation

![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/Classification%20Unique%20Values.png)

#### Ask Amount

The number of unique values was 8747.  Although the model ran with 73% accuracy if all of the unique values were used, the high number could lead to overfitting of the model.  In order to determine a way of using the ask amount in the model the data was first analyzed and found to have the following values:

![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/min%20max%20ask%20amount.png)

A box plot was also created to get an idea of the distribution of the data. 

![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/Box%20Plot.png)

From this visualization and the statistical values, it was determined to do a logistic ditribution.  

![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/Log%20Dristribution.png)

Ultimately, the data was binned as follows:  [0, 10000, 50000, 100000, 1000000, 10000000]

#### Special Considerations

Due to the fact that the special considerations column was a yes or no field, it was changed to "0" no and "1" for yes.

#### Income Amount

I attempted to cut down income amount into numerical values for each category and this caused the model to be over simplified and was removed.


### Modeling

Using pd.get.dummies, all of the non-numerical data was transformed into 0s and 1s.  The data was originally trained but I checked the value counts and it was slightly imbalanced.  I proceeded to apply random oversampler to have an equal amount of No(0) and Yes(1).  The issue that arrose if that the validation accuracy was higher than the training accuracy indicating that there may be data leakage.  I decided not to use it.  

Parameters such as layer numbers and neurons, epochs, and random state were altered one parameter at a time.  The goal was to acheive a good accuracy and a trend that indicated both the training accuracy and validation accuracy were in line with each other.  Ultimately, the following configuration was acheived:

* Layer 1: 18 neurons Activation Relu
* Layer 2: 2 neurons Activation Tanh
* Epochs: 28
* reandom State: 1
* Strafity:  Yes

##### Model Sequenctial
![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/Model%20Sequenial.png)


##### Final plot of the training accuracy and validation accuracy
![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/70%20accuracy%20final.png). 

##### Final Calculation of the Model Accuracy and Model Loss
![](https://github.com/TraceyGeneau/deep-learning-challenge/blob/main/images/Final%20Config.png)
 
While I wasn't able to achieve an accuracy higher than 75% with this model, reaching a 70% accuracy rate marks a significant milestone and a substantial improvement compared to our initial efforts. I've dedicated considerable time to improving the model's performance, starting from data preprocessing and carefully adjusting model parameters one step at a time. It's a prudent choice to utilize this model for now, and I recommend keeping a watchful eye on its performance over time. At this stage, we already have a robust foundation to build upon.












