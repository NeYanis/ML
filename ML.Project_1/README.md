# Machine learning introduction

Summary: This project is an introduction to machine learning and especially to primary data analysis with some practical basics.

## Chapter V. Task

We will practice using a problem from Kaggle.com. You will predict the price of an apartment rental listing based on the listing content such as text description, photos, number of bedrooms, price, etc. The data comes from renthop.com, an apartment listing website. 

Follow the instructions, answer the questions and get your final score!

1. Introduction. Write your answers in the *Intro* section of your notebook. 
   1. To get started, please write 5 examples of the application of ML methods in life. What is the benefit of using machine learning methods in each of your examples? 
   2. Use the classification of tasks in the introduction to decide which class you can assign to the tasks from the table above and to the 5 examples you provided. 
   3. Think about what the difference is between multiclass and multilabel.
   4. Is an example case with house prices from the theory a classification of a regression problem? Is it possible to reduce the regression problem to classification?
2. Introduction to Data Analysis
   1. Import the libraries **pandas**, **numpy**, **sklearn**, **lightgbm**, **scipy**, **statsmodels**, **matplotlib**, **seaborn**. Use **pip install** if necessary.
   2. Load data from [kaggle](https://www.kaggle.com/competitions/two-sigma-connect-rental-listing-inquiries/data) using **pandas**. You only need the table data, which is in **train.json**.
   3. What is the size (the number of rows and columns) of your data? 
   4. Print the list of columns. Which column is a target? 
   5. Make a quick analysis of the data: use the methods **info()**, **describe()**, **corr()**. Explain the results of the outputs. Are there any empty columns? 
   6. We'll work with only 3 features: 'bathrooms', 'bedrooms', 'interest_level' and with the target column 'price'. Create a dataframe with only these columns.
3. Statistical Data Analysis
   1. To get started with statistical data analysis, we recommend that you refresh your basic knowledge of statistics, such as Mean / Median / Mode / Variance / Standard Deviation. Also you are welcome to be free with distributions (Discrete uniform Distribution, Bernoulli Distribution, Binomial Distribution, Poisson Distribution, Normal Distribution, Exponential Distribution). Please make sure that you know the definitions of outliers, percentiles, confidential intervals. The article will be presented later. 
   2. Have a quick look at [this article](https://towardsdatascience.com/how-to-compare-two-or-more-distributions-9b06ee4d30bf). Please pay attention to such aspects as distributions and histograms, boxplots, outliers, kernel density function.
   3. Target analysis
      1. Plot a histogram to understand the distribution of the target. Is it all clear? 
      2. The next step is boxplot(). What can you say about the target? Are there any outliers? 
      3. Drop the rows that are outside the 1 and 99 percentiles from the target column. 
      4. Plot another histogram for price. Explain the result.
   4. Characteristics Analysis
      1. What is the type of column 'interest_level'? 
      2. Print the values in this column. How many entries does each value contain? 
      3. Encode these values. For example, you can replace each value with 0, 1, or 2.
      4. Plot histograms for the features 'bathrooms', 'bedrooms'. Are there any outliers?
   5. Complex analysis
      1. Plot a correlation matrix to understand the correlation between features and target. Plot a heat map for the correlation matrix. Is there a correlation? 
      2. Plot a scatterplot to visualize the correlation between the features and the target. You should return 3 plots where the X-axis is the target and the Y-axis is a feature.
4. Creating Features
   1. This step is very broad. You can create as many features as you want. For example, you can add 3 new features that are squared: 'bathrooms_squared', 'bedrooms_squared', ''interest_level_squared'. Plot a correlation matrix with the new features. Are the new features more correlated with the target than the basic features? 
   2. To train the model here, we will not use your new features. Remember this example and use it in Lecture 2. To train the model, we will only consider the features 'bathrooms' and 'bedrooms'.
   3. Read this [Sklearn info about PolynomialFeatures](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.PolynomialFeatures.html).
   4. To use PolynomialFeatures, we first need to split the data into training and test samples. We have already done this for you, please read the training and test data. 
   5. Initialize PolynomialFeatures() with a degree of 10. 
   6. Apply PolynomialFeatures() to fit and transform your training and test data.
5. Now you need to train 3 models: linear regression, decision tree and naive model. We will use them as black boxes without deep understanding. 
   1. Results table 
      1. Create two empty Pandas DataFrames with columns 'model', 'train', 'test'. Let's call the first one result_MAE and the second one result_RMSE. We will fill these tables with the results of the models.
   2. Linear Regression 
      1. Initialize linear regression from **sklearn** with no parameters. 
      2. Fit your model and make predictions on training and test features. Save it as new columns in data.
      3. Compute MAE (Mean Absolute Error) on training and test targets.
      4. Calculate RMSE (Root Mean Square Error) on training and test objectives.
      5. Insert your metrics into tables *result_MAE* and *result_RMSE* with model name 'linear_regression'.
   3. Decision Tree
      1. Initialize decision tree regressor from sklearn with fixed random_state=21.
      2. Fit it to train features and train target and make prediction on train and test features. Save it as a new column in data. 
      3. Compute MAE (Mean Absolute Error) on train and test targets.
      4. Compute RMSE (Root Mean Square Error) on train and test targets.
      5. Insert your metrics into tables *result_MAE* and *result_RMSE* with model name 'decision_tree'.
   4. Naive Models
      1. Calculate the mean and median of 'price' on the training and test data and create a column with these values. 
      2. Calculate the MAE on the training and test targets between your target and the calculated mean and median. 
      3. Calculate the RMSE on the training and test targets between your target and the calculated mean and median. 
      4. Insert your metrics into tables result_MAE and result_RMSE with model names 'naive_mean' and 'naive_median'.
   5. Compare the results 
      1. Print your final result_MAE and result_RMSE tables. 
      2. Which is the best model?
   6. Additional
      1. You can practice with all the data in your starting dataset. Use and generate all the features you want.

