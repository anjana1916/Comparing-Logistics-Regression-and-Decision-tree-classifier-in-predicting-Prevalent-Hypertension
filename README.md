
# **Comparing Logistic Regression and Decision tree classifier in Predicting Prevalent Hypertension**
### Introduction
Hypertension is associated with high blood pressure. Generally, as an adult, you are considered to 
have high blood pressure if your systolic pressure reading is greater than or equal to 140 mm Hg or if 
your diastolic pressure is greater than or equal to 90 mm Hg. Early onset of hypertension can 
cause many cardiovascular diseases and organ degradation. There are many factors which can lead to 
an early onset of hypertension – like smoking, unhealthy eating habits..etc. In this report, our main 
aim is to predict hypertension in patients based on their medical records, demographic and
behavioural aspects using Logistic regression and Decision tree classifier and compare the results.
### Problem Formulation
I have chosen the dataset from Kaggle website. The dataset consists of 4000 data points. Each data 
point is a patient – his medical records + behaviours. There are 8 features, all are numeric(integers 
and float numbers): 
#### Demographic:
• Age: Age of the patient
#### Behavioural:
• Cigs Per Day: the number of cigarettes that the person smoked on average in one day. 
#### Medical records:
• Tot Chol: total cholesterol level   
• Sys BP: systolic blood pressure   
• Dia BP: diastolic blood pressure   
• BMI: Body Mass Index   
• Heart Rate: heart rate   
• Glucose: glucose level  
#### The label :  
prevalent hypertension or not (0 or 1). It is a nominal variable(binary)    

Behavioural aspects like the number of cigarettes smoked significantly contributes to our objective or 
label, as smoking is one main cause of hypertension. Majority of the patients are from age group 35-
55 that is about 67%, and 31% above 55, whereas only 2% below 35. Factors like unhealthy eating habits will be reflected on the medical records mainly – cholesterol, 
BMI and glucose level. Our objective is to create a model using the above mentioned features to 
predict the possibility of hypertension.  

### Methods
Initially, exploratory data analysis was carried out. There were quite a few missing values in 4 
features (458 missing totally), which were substituted with the average of that feature. For selecting 
the important features, I made use of the correlation chart with the help of seaborn package. Systolic 
bloodpressure and diastolic blood pressure are highly correlated to each other. None of the features 
were correlated to the label, Prevalent stroke. Therefore I chose the features based on domain 
knowledge[4], mostly focusing on medical records and unhealthy habits( that is considering Blood 
pressure, BMI, Cigs Per Day and glucose level).  

![dow](https://user-images.githubusercontent.com/103304121/162563561-ecccbff7-b536-4a54-a184-2d83fb565153.png)  

#### Logistic Regression:  
Since our label is binary (0or 1), it is ideal to use logistic regression instead of linear regression so as 
to get a probabilistic value. Here we are interested in knowing the probability of having hypertension
or not, which is a value between 0 and 1. If we use Linear regression the model will be trained to get 
absolute values which might fall outside the rage 0 and 1. So I fit the model using Sklearn package.
Here we use Logistic loss instead of Mean squared error, to measure the performance of the model. 
The reason being, Y is a non-linear function(sigmoid function) and if we put this in MSE equation it 
will give us a non-convex graph. Hence gradient descent approach to find global minima in this graph 
will create complictaions. Therefore we stick with log loss.

Before fitting the model we split the dataset into training and testing sets, 80% and 20% respectively
initially. And then split the training data to training and validation sets, 70% and 30% respectively.
For training we need more data hence the split is more for train set. And for easy computation we go
for a single split. Training and validation sets will be used to create the model and the testing set is
used to evaluate the model. Any dataset which had had influenced the creation of the model cannot
give a fair evaluation of the performance of that model.  

#### Decision tree :
The reason behind choosing this model is that decision trees can be visualized as a chart and is easy to
interpret. In addition, it allows representing highly non-linear functions and can separate data points
according to their labels more accurately.
We use Gini entropy as the loss function, as it allows to measure the variance across the different 
classes. Here again we use the same split as the previous model for the same reason. In addition to 
that I have used GridSearchCV to tune the hyperparameters. So that it gives a combination of 
hyperparameters for which the model performs the best.  
![dt](https://user-images.githubusercontent.com/103304121/162564293-a62c0350-7181-4d42-aede-538046ac201f.png)


### Results and Conclusion
Both models perform quite well when we take a look at the accuracies and errors. The training 
accuracies differ by 0.001 but the validation accuracies are the same.  
![deci](https://user-images.githubusercontent.com/103304121/162564214-227b2bcb-3d1b-462a-9ce6-032da5c99f44.png)
![logist](https://user-images.githubusercontent.com/103304121/162564215-667918e1-2e27-462e-bbb1-e24fa87dd678.png)  

The training and validation accuracies for logistic regression are 0.9949 and 0.9911 respectively and logistic loss for the same are 0.174 and 0.305 respectively. 
The training and validation accuracies for Decision tree classifier are 1.0 and 0.9911 respectively.  
Based on the result, it seems that the Decision tree classifier is a little overfit, this happened since we used GridSearchCV. Overfitting is one of the major disadvantages of GridSearch as it tunes the hyperparameters based on the training data. Logistic regression seems to perform quite well. But one thing I noticed while going through the data is that it has a highly uneven class distribution(see histogram last plot). This results in false positive paradox. I would consider collecting data with an even class distribution and then apply both the models and interpret the results.  
The test set construction is explained above and is 20% of the dataset. The test error for Logistic regression is 0.005 and for Decision Tree classifier is 0.0166. Even though the test error for logistic regression is much lower than the decision tree classifier, I would choose the later as they are capable of representing highly non-linear functions and can perfectly separate data points according to their labels. For logistic regression the only possible decision boundary is a straight line as it consists of linear functions.  
This report can be extended by using a good dataset with even class distribution. For the most part Decision tree classifier seems like a good model in terms of interpretability, calculation and results. GridSearchCV is quite useful for tuning the hyperparameters and it is better to apply it on a validation set.



