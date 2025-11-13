# Supervised Learning. Classification

Summary: this project is an introduction to classification problems and related ML algorithms.

## Chapter V. Task

1. Download data from Don’tGetKicked competition. <br/><br/>
2. Design the train/validation/test split. Use the "PurchDate" field for the split, test must be later than validation, same for validation and train: train.PurchDate < valid.PurchDate < test.PurchDate. Use the first 1/3 of dates for the train, the last 1/3 of dates for the test, and the middle 1/3 for the validation set. *Don’t use the test dataset until the end!* <br/><br/>
3. Use LabelEncoder or OneHotEncoder from sklearn to preprocess categorical variables. Be careful with data leakage (fit Encoder to training and apply to validation & test). Consider another coding approach if you encounter new categorical values in validation & test (not seen in training): https://contrib.scikit-learn.org/category_encoders/count.html <br/><br/>
4. Train LogisticRegression, GaussianNB, KNN from sklearn on the training dataset and check the quality of your algorithms on the validation dataset. The dependent variable (IsBadBuy) is binary. Don't forget to normalize your datasets before training your models.
<br/><br/>You must get at least **0.15 Gini score** (the best of all three). Which algorithm performs better? And why?
<br/><br/>
5. Implement Gini score calculation. You can use the 2\*ROC AUC - 1 approach, so you need to implement the ROC AUC calculation. Check if your metric is approximately equal to `abs(2*sklearn.metrics.roc_auc_score - 1)`.
<br/><br/>
6. Implement your own versions of LogisticRegression, KNN and NaiveBayes classifiers. For LogisticRegression compute gradients with respect to the loss and use stochastic gradient descent. Can you reproduce the results from step 4?
<br/><br/>Guidance for this task: Your model must be represented by class with methods *fit*, *predict* (*predict_proba* with 0.5 *threshold*), *predict_proba*. For LR moder, compute the loss gradient with respect to parameters **w** and parameter **b** in the fit function. Use a simple SGD approach to estimate optimal values of parameters.<br/><br/>
7. Try to create non-linear features, for example:
<br/><br/>
fractions: feature1/feature2
<br/>groupby features: `df[‘categorical_feature’].map(df.groupby(‘categorical_feature’)[‘continious_feature’].mean())`
<br/><br/>
Add new features to your pipeline, repeat step 4. Did you manage to increase your Gini score (you should!)?
<br/><br/>
8. Determine the best features for the problem using the coefficients of the logistic model. Try to eliminate useless features by hand and by L1 regularization. Which approach is better in terms of Gini score?
<br/><br/>
9. Select your best model (algorithm + feature set) and tweak its hyperparameters to increase the Gini score on the validation dataset. Which hyperparameters have the most impact?
<br/><br/>
10. Check the Gini scores on all three datasets for your best model: training Gini, valid Gini, test Gini. Do you see a drop in performance when comparing the valid quality to the test quality? Is your model overfitted or not? Explain.
<br/><br/>
11. Implement calculation of Recall, Precision, F1 score and AUC PR metrics.
<br/>Compare your algorithms on the test dataset using AUC PR metric.
<br/><br/>
12. Which hard label metric do you prefer for the task of detecting "lemon" cars?

