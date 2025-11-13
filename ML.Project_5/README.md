# Supervised Learning. Decision Trees and ensembles

Summary: This project introduces decision trees (CART) and ensemble methods (Random Forest, GBDT).


## Chapter V. Task

1\. Download data from [Don’tGetKicked competition](https://www.kaggle.com/c/DontGetKicked).Design train/validation/test split.

Use the "PurchDate" field to split, test must be later in time than validation, same goes for validation and train: train.PurchDate < valid.PurchDate < test.PurchDate. 

Use the first 33% of the data for the training, the last 33% of the data for the test, and the middle 33% for the validation set. *Don't use the test dataset until the end!*

Use LabelEncoder or OneHotEncoder from sklearn to preprocess categorical variables. Be careful with data leakage (fit Encoder to training and apply to validation & test). Consider another coding approach if you encounter new categorical values in validation & test (not seen in training), for example: https://contrib.scikit-learn.org/category_encoders/count.html

2\. Create a Python class for Decision Tree Classifier and Decision Tree Regressor (MSE loss).

It should support *fit*, *predict_proba*, and *predict* methods. Also, the maximum depth (max_depth) must be a parameter of your class. Use the Gini impurity criterion as a criterion for choosing the split.

Here is the blueprint:

```python
model = DecisionTreeClassifier(max_depth=7)
model.fit(Xtrain, ytrain)
model.predict_proba(Xvalid)
```
* Create a separate class for Node. It should be able to hold data (sample features and targets), compute Gini impurity, and have pointers to children (left and right nodes). For the Regressor, use standard deviation instead of Gini impurity. 
* Implement a function that finds the best possible split in the current node. 
* Combine the previous steps into your working Decision Tree Classifier.
* Implement an Extra Randomized Tree by designing another function to find the best split.

3\. With your DecisionTree module, you must obtain a Gini score of at least 0.1 on the validation dataset.

4\. Use sklearn's DecisionTreeClassifier and check its performance on the validation dataset. Is it better than your module? If so, why?

5\. Implement the RandomForestClassifier and check its performance. You have to improve the result of a single tree and get at least 0.15 Gini score on the validation dataset. Be able to set a fixed random seed.

6\. Use your DecisionTree design class for GBDT classifier. This class must have *max_depth*, *number_of_trees* and *max_features* attributes. You must compute the gradient of the binary cross-entropy loss function and implement incremental learning: train the next tree using the results of the previous trees.

7\. Use LightGBM, Catboost, and XGBoost for fitting on a training set and prediction on a validation set. Review the documentation of the libraries and fine-tune the algorithms for the task.
Note key differences between each implementation. Analyze special features of each algorithm (how does "categorical feature" work in Catboost, what is DART mode in XGBoost)?
Which GBDT model gives the best result? Can you explain why?

8\. Take the best model and estimate its performance on the test dataset: check the Gini values on all three datasets for your best model: training Gini, valid Gini, test Gini. Do you see a drop in performance when comparing the valid quality to the test quality? Is your model overfitting or not? Explain.

9*. Implement the ExtraTreesClassifier and check its performance. You must improve the result of a single tree and obtain a Gini score of at least 0.12 on the validation dataset.

## Chapter VI. Bonus Part

Bonus part marked with * in [Chapter V. Task](#chapter-v-task).
