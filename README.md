# Prediction

Prediction of student behavior has been a prominant area of research in learning analytics and a major concern for higher education institutions and ed tech companies alike. It is the bedrock of [methodology within the world of cognitive tutors](https://solaresearch.org/hla-17/hla17-chapter5/) and these methods have been exported to other areas within the education technology landscape. The ability to predict what a student is likely to do in the future so that interventions can be tailored to them has seen major growth and investment, [though implementation is non-trivial and expensive](https://www.newamerica.org/education-policy/policy-papers/promise-and-peril-predictive-analytics-higher-education/). Although some institutions, such as [Purdue University](https://www.itap.purdue.edu/learning/tools/forecast.html), have seen success we are yet to see widespread adoption of these approaches as they tend to be highly institution specific and require very concrete outcomes to be useful. 

## Project Objective:

The purpose of this project was build models using CART, C4.5 and C5.0 classification algorithms to predict student course dropout and then compare these models based on validation metrics. 

## Dataset:

* drop-out.csv

A codebook can be found in this repository. 

## R Packages:

* dplyr
* tidyr
* ggplot2
* caret
* RWeka
* C50

## Procedure:

The dataset was separated into a training set and a test set. 75% of the dataset was randomly selected for a training set and the other 25% was selected for a test set. All of the variables were incorporated into the model to predict whether the student will complete the courses. Then the following models and their validation metrics were generated:

### CART Tree:

* ROC against the complexity parameter:
![CART Tree](https://github.com/lizarova777/Prediction_Project/blob/master/CartFit.png)

### C4.5-Type (J48) Tree:

* ROC against the complexity parameter:
![J48 Tree](https://github.com/lizarova777/Prediction_Project/blob/master/J48Fit.png)

### C5.0 Tree:

* ROC against the confidence threshold:
![C.50 Tree](https://github.com/lizarova777/Prediction_Project/blob/master/C50Fit.png)

Then the models were compared using the following code, which generated a model summary:

```
resamps <- resamples(list(cart = cartFit, jfoureight = j48Fit, cfiveo = c50Fit))
summary(resamps)

```

## Results:

Based on the model summary, C5.0 model has the highest average ROC, C4.5 model has the highest average sensitivity, and the CART model has the highest average specificity. Furthermore, the CART model has the lowest average ROC and sensiitvity. Nonetheless, the C5.0 model has a greater variation in regards to the sensitivity and specificity compared to the other models while the C4.5 model has the least variation in regards to the distribution of these metrics. Thus, the C4.5 model is the best in predicting whether the students will complete the course.



