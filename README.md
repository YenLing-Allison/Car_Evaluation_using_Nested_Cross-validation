# Car_Evaluation_using_Nested_Cross-validation
Build five different models to predict car evaluation using nested cross-validation with categorical and ordinal target variable

# Business Question
1. Among the basic classification techniques that you are familiar with (i.e., decision tree, k-NN, logistic regression, NB, SVM) use all that would be applicable to this dataset to predict the evaluation of the cars based on their characteristics. Explore how well these techniques perform for several different parameter values. Present a brief overview of your predictive modeling process, explorations, and discuss your results. Present your final model (i.e., the best predictive model that you were able to come up with), and discuss its performance in a comprehensive manner (overall accuracy; per-class performance, i.e., whether this model predicts all classes equally well, or if there some classes for which it does much better than others; etc.).
2. In this classification problem your input variables are ordinal. Should you treat them as numeric or categorical? What are pros and cons? You can try building your models both ways; which demonstrate better predictive performance?

# Data Resource
Dataset: [https://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data ](https://archive.ics.uci.edu/dataset/19/car+evaluation)   
This dataset has 1728 records, each record representing a car evaluation. Each car evaluation is described with 7 attributes. 6 of the attributes represent car characteristics, such as buying price, price of the maintenance, number of doors, capacity in terms of persons to carry, the size of luggage boot, and estimated safety of the car. The seventh variable represents the evaluation of the car (unacceptable, acceptable, good, very good).

# Analysis Process
1. Input
   * Processed model hyperparameters  
   * Scaling method
2. Inner loop   
   * Tune hyperparameters  
   * Searching optimal hyperparameters  
3. Outer loop  
   * Retrain on training set
   * Predict on testing set
4. Build models again using optimal model  
   * Train-test split and build the model
   * Make prediction
5. Summarize performance  
   * Confusion matrix, predictive accuracy, precision, recall, f-measure
   * ROC and Lift curve
![analysis_process_nested_cv](https://github.com/YenLing-Allison/Car_Evaluation_using_Nested_Cross-validation/assets/144725779/44dbbe65-702a-4abd-9163-83ffb0636042)


# Result
1. Models of One hot encoding vs. Ordinal dataset
* Overall models with ordernal dataset perform better than one hot encoding dataset.  

2. Models comparision of ordinal dataset  
* In the five models with ordinal data, I found that **mean scores of mostly models are up to 90%, and support vector machine performs the best.** Thus I use SVM to rebuild the model and tune hyperparameters again.

3. Model comparison  
| Model | Mean accuracy of categorical data | Mean accuracy of ordinal data |
| --- | --- | --- |
| Decision Tree | 0.94 | 0.98 |
| Logistic Regression | 0.90 | 0.82 |
| KNN | 0.85 | 0.94 | 
| Naive Bayes | 0.85 | 0.94 | 
| SVM | 0.99 | 0.98 |

4. Final SVM model  
| Description | Result | 
| --- | --- |
| Model | SVM |
| Best parameters | {'C': 9.5, 'gamma': 1, 'kernel': 'rbf'} |
| Accuracy | 0.99 |
| Kappa | 0.97 |
| MCC | 0.97 |
