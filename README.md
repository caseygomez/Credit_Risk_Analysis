# Credit Risk Analysis

## Overview:
This project utilizes skills in data preparation, statistical reasoning, and supervised machine learning. Utilizing different techniques to train and evaluate models with unbalanced classes, the final result is a recommendation on which model performs best to predict credit risk. All analysis is written in Python.

---
### Resources:
* Source Code: [Credit Risk Ensemble](credit_risk_ensemble.ipynb), [Credit Risk Resampling](credit_risk_resampling.ipynb)
* Source Data: [2019 Q1 Loan Stats](LoanStats_2019Q1.csv)
* Technology: [Scikit-Learn](https://scikit-learn.org/stable/), [Imbalanced-Learn](https://imbalanced-learn.org/stable/index.html)

---
### Deliverables:
- [x] Deliverable 1: Use Resampling Models to Predict Credit Risk
- [x] Deliverable 2: Use the SMOTEENN Algorithm to Predict Credit Risk
- [x] Deliverable 3: Use Ensemble Classifiers to Predict Credit Risk
- [x] Deliverable 4: Write Credit Risk Analysis

---
### RandomOverSampler:

![RandomOverSampler](resources/ROS.png)

* Accuracy: .6428

* Precision: 
    * High Risk: .01 
    * Low Risk: 1 

* Recall:
     * High Risk: .61
     * Low Risk: .68

* F1:
    * High Risk: .02
    * Low Risk: .81 

* Benefits: 
    * Instances from the minority class are randomly selected and added to the minority training class until both classifications are equal.
---
### SMOTE:

![SMOTE](resources/SMOTE.png)

* Accuracy: .6201

* Precision: 
    * High Risk: .01
    * Low Risk: 1 

* Recall:
    * High Risk: .60
    * Low Risk: .64

* F1:
    * High Risk: .02
    * Low Risk: .78  

* Benefits:
    * For an instance from the minority class, a number of its closest neighbors is chosen. Based on the values of these neighbors, new values are created.
---
### ClusterCentroids:

![ClusterCentroids](resources/CC.png)

* Accuracy: .6201

* Precision: 
    * High Risk: .01
    * Low Risk: 1 

* Recall:
    * High Risk: .59
    * Low Risk: .44

* F1:
    * High Risk: .01
    * Low Risk: .61   

* Benefits: 
    * The algorithm identifies clusters of the majority class, then generates centroids, that are representative of the clusters. 
    * The majority class is then undersampled down to the size of the minority class.

---
### SMOTEENN Algorithm:

![SMOTEENN](resources/SMOTEENN.png)

* Accuracy: .5108

* Precision: 
    * High Risk: .01
    * Low Risk: 1 

* Recall:
    * High Risk: .70
    * Low Risk: .57

* F1:
    * High Risk: .02
    * Low Risk: .73   

* Benefits:
    * Oversample the minority class with SMOTE
    * Clean the resulting dara with an undersampling strategy. If the two nearest neighbors of a data point belong to two different classes, the data point is dropped. 
---
### BalancedRandomForestClassifier:

![BalancedRandomForestClassifier](resources/BRFC.png)
   
* Accuracy: .7878

* Precision: 
    * High Risk: .04 
    * Low Risk: 1 

* Recall:
    * High Risk: .67
    * Low Risk: .91

* F1:
    * High Risk: .07
    * Low Risk: .95  

* Benefits:
    * Are robust against overfitting as all of those weak learners are trained on different pieces of the data.
    * Can be used to rank the importance of input variables in a natural way.
    * Can handle thousands of input variables without variable deletion.
    * Are robust to outliers and nonlinear data.
    * Run efficiently on large datasets.
---
### EasyEnsembleClassifier:
![EasyEnsembleClassifier](resources/EEC.png)
   
* Accuracy: .9254

* Precision: 
    * High Risk: .07
    * Low Risk: 1 

* Recall:
    * High Risk: .91
    * Low Risk: .94

* F1:
    * High Risk: .14
    * Low Risk: .97  

* Benefits:
    * The classifier is an ensemble of AdaBoost learners trained on different balanced bootstrap samples. 
    * After evaluating the errors of the first model, another model is trained. This time, however, the model gives extra weight to the errors from the previous model. The purpose of this weighting is to minimize similar errors in subsequent models.
---
### Credit Risk Analysis:
After thorough analysis it is clear that all six models have inherent risk, however the EasyEnsembleClassifer (EEC) model yields the best results. Many of the rates were highest using the EEC model. The overall accuracy rate of 92.54% as well as the 7% precision rate for "High Risk" loan candidates were both the highest. Additionally the recall rates for both risk groups were high and the F1 rate for the "High Risk" loan candidates was highest at 14%. 

It is important to remember that sampling techniques cannot overcome the deficiencies of the original dataset. The majority of the applications were classified as "Low Risk". With so few data points for the "High Risk" classification the algorithms could skew results. For this project the Q1 2019 data was used, it would be interesting to compare Q1 data from previous years or to look at all of 2019. 