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
The label : prevalent hypertension or not (0 or 1). It is a nominal variable(binary)  
Behavioural aspects like the number of cigarettes smoked significantly contributes to our objective or 
label, as smoking is one main cause of hypertension. Majority of the patients are from age group 35-
55 that is about 67%, and 31% above 55, whereas only 2% below 35
