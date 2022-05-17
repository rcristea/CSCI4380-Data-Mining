# CSCI4380-Data-Mining
## Predicting Monthly Rent Using a Regression Tree

* Stephanie Breed
* Ruben Cristea
* Jack Solomon


I focused on creating the model and fitting the data to get our pedictions.


### Problem Statment
* Most of the people in this class are graduate students or will be graduating soon
* During this period in our lives, many of us will be moving and searching for housing
* We wanted to know which factors would have the most impact on our housing search
* So we decided to design an algorithm to make searching for housing easier

### Proposed Solution
Use a regression tree to predict rent prices and determine which factors may have the biggest impact on monthly rent.

### What is a Regression Tree?
* Tree-based machine learning model (not a deep learning model)
* Very similar to the kind of decision tree we studied in class, but differs from classification trees in that it does not slot results into predefined labels like "yes/no" or "cat/dog/bird"
  * Outputs are continuous values
* Uses the minimum MSE (Mean Squared Error) to split data rather than the maximum information gain

### Why a Regression Tree?
* Good fit for our problem
* Quick to train
  * O(num. Samples x num. Features x log(num. samples))
* Rules for decision-making are similar to the human decision-making process
* Other considerations: GAN, RNN
  * But we are using structured data, which is better suited for deterministic models like decision trees

### Limitations of Regression Trees
* Take longer to train than classification trees
* Tends to overfit (large, complex trees need to be pruned)
* The tree becomes more complex as it gets deeper
* The interpretability decreases as the depth of the tree increases.

### Dataset 
* The Dataset we used is from Kaggle created by Austin Reese
* The dataset received a score of 10/10 in usability. 
* It is comprised of data scraped from Craigslist retail sales using a python scraper 
* The data is from 2020 and was initially scraped every two months, but has since not been updated in 2 years
* The data contains statistics about Craigslist retail sales including: region, price, housing type, sqfeet, and even if pets are allowed 

### Methods
* Imported data as a Pandas DataFrame because it works well with many python libraries used for Data Mining related projects.
* Cleaned up the data, removing outliers since there is plenty of data and we are not looking focusing on housing units with 100 bedrooms nor 10 million dollar units.
* Grouped data by region.
* Split grouped data  into train data and test data to avoid overfitting.
* Created a SKLearn’s DecisionTreeRegressor model as our Regression Tree for each region to run predictions.
* Used Means Square Error to see how much our predictions deviated from the original target
* Used Cross Validation to evaluate the results of the model for any selected region.

### Results
* We found that the region was the #1 determining factor for what the price of a housing unit would be.
* Square Feet was the second highest determining factor with the number of bedrooms, bathrooms, whether pets or smoking were allowed, wheelchair access, EV charging etc. mattered less.
* Right tailed distribution for price

### Evaluation
* Focused in on Athens
* Using Cross-Validation for our regression tree on the Athens region, we discovered that our model was performing relatively well. 
* For each run of cross validation we got on the lower end, 40%-70% and hit better values of 80-90%.

### Problems We Encountered
* Some major outliers made the data impossible to interpret.
* Since we had enough data, we decided to just remove these outliers which made the data more readable.
* Sometimes when running our model, we would receive negative cross validation scores especially for SF bay area.
  * This could be caused by over fitting data or data that has aggressive outliers. Sometimes the data is a bad fit for the model.
  * The SF bay area data was more sporadic compared to other regions like Athens and Atlanta that we tested.
* Fake listings
  * House with 100 bedrooms


### Next Steps
* Fix bad fit that occurs for some subsections of data
* Maybe the data is not clean enough?!
  * Implement automated outlier detection
  * Perform more preprocessing
* Implement the same problem using a NN and compare results
* Train and test on a more recent dataset

