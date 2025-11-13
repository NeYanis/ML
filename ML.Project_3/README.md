# Model quality estimation

Summary: This project discusses different validation techniques. We will discuss how to correctly measure model quality and avoid leaks. We also consider several ways to optimize model hyperparameters and various methods of feature selection.


## Chapter V. Task

We will continue our training with a problem from Kaggle.com. 
In this chapter, we will implement all the validation schemes, some hyperparameter tuning methods, and feature selection methods described above. Measure quality metrics on training and test samples. Will detect overfitted models and regularize them. And dive deeper with native model estimation and comparison.
1. Answer the questions from the introduction
   1. What is leave-one-out? Provide limitations and strengths.
   2. How do Grid Search, Randomized Grid Search, and Bayesian optimization work?
   3. Explain classification of feature selection methods. Explain how Pearson and Chi2 work. Explain how Lasso works. Explain what permutation significance is. Become familiar with SHAP.

2. Introduction — do all the preprocessing from the previous lesson
   1. Read all the data.
   2. Preprocess the "Interest Level" feature.
   3. Create features:  'Elevator', 'HardwoodFloors', 'CatsAllowed', 'DogsAllowed', 'Doorman', 'Dishwasher', 'NoFee', 'LaundryinBuilding', 'FitnessCenter', 'Pre-War', 'LaundryinUnit', 'RoofDeck', 'OutdoorSpace', 'DiningRoom', 'HighSpeedInternet', 'Balcony', 'SwimmingPool', 'LaundryInBuilding', 'NewConstruction', 'Terrace'.

3. Implement the next methods:
   1. Split data into 2 parts randomly with parameter test_size (ratio from 0 to 1), return training and test samples.
   2. Randomly split data into 3 parts with parameters validation_size and test_size, return train, validation and test samples.
   3. Split data into 2 parts with parameter date_split, return train and test samples split by date_split param.
   4. Split data into 3 parts with parameters validation_date and test_date, return train, validation and test samples split by input params.
   5. Make split procedure determenistic. What does it mean?

4. Implement the next cross-validation methods:
   1. K-Fold, where k is the input parameter, returns a list of train and test indices. 
   2. Grouped K-Fold, where k and group_field are input parameters, returns list of train and test indices. 
   3. Stratified K-fold, where k and stratify_field are input parameters, returns list of train and test indices.
   4. Time series split, where k and date_field are input parameters, returns list of train and test indices.
 
5. Cross-validation comparison
   1. Apply all the validation methods implemented above to our dataset. To apply Stratified algorithm you should preprocess target.
   2. Apply the appropriate methods from sklearn.
   3. Compare the resulting feature distributions for the training part of the dataset between sklearn and your implementation.
   4. Compare all validation schemes. Choose the best one. Explain your choice.

6. Feature Selection
   1. Fit a Lasso regression model with normalized features. Use your method for splitting samples into 3 parts by field created with 60/20/20 ratio — train/validation/test.
   2. Sort features by weight coefficients from model, fit model to top 10 features and compare quality.
   3. Implement method for simple feature selection by nan-ratio in feature and correlation. Apply this method to feature set and take top 10 features, refit model and measure quality.
   4. Implement permutation importance method and take top 10 features, refit model and measure quality.
   5. Import Shap and also refit model on top 10 features.
   6. Compare the quality of these methods for different aspects — speed, metrics and stability.

7. Hyperparameter optimization
   1. Implement grid search and random search methods for alpha and l1_ratio for sklearn's ElasticNet model.
   2. Find the best combination of model hyperparameters.
   3. Fit the resulting model.
   4. Import optuna and configure the same experiment with ElasticNet.
   5. Estimate metrics and compare approaches.
   6. Run optuna on one of the cross-validation schemes.
