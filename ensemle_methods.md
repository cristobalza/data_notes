# Ensemble Methods

## Introduction

Some ensemble methods:

- Bagging
- Boosting
- Random Forests

Ensemble methods has to goals: increase the accuracy of some model and to solve issues when the data is imbalanced.

## How does it work?

AN ensemble means that it combijes a series of $k$ learned models or base classifiers with the aim of creatin an improved compposite classification model.

It returns a class prediction based on the tuples of the base classifiers.

## Characterisitcs

### More Accuracy

Ensembles yield better results when there is significant diversity among the models. In other words, when there is **little to no correlations among the base classifiers**.

The base classifier may make mistakes, but the ensemble will misclassy a target variable only if over half of the base classifiers are in error.

Recall that each classifier is allocated in a CPU. Thus, an ensemble model is parallelizable.

## Bagging

Suppose you are patient and would like to have the diagnosis of 

## Boosting

Suppose you are a patient and have certain symptoms. You consult several doctors. Then you assign weights to the value or worht of each doctor's diagnosis, based on acc uracies from other doctors' diagnosises. The final diagnosis is a combination of the weighted diagnoses.

- *Step 1*: All observations in the dataset are initially given equal weights.
- *Step 2*: A machine learning model is trained on this dataset.
- *Step 3*: The model from step 2 is added to the ensemble with an error associated with it that is the sum of the weights for the misclassifed observations.
- *Step 4*: Misclassified observations are given greater weights.
- *Step 5*: Steps 2–4 are repeated for a number of epochs.


The idea here is to make misclassified observation stand out as being more important in subsequent learning iterations. It should be noted at this point that boosting is an immensely powerful ensembling technique but, due to its nature of focusing on difficult observations, it is prone to over-fitting.
