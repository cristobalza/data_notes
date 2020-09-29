#Model Evaluation and Selection

## Introduction: What is accuracy? How to estimate or calculate it?

So far, we have heard from different techniques such as  **cross-validation**,  **holdout**, or **bootstrap** from Statistics that are use to train our model and see how well it does for the various purposes that we want.

However, sometimes it is hard to choose what Classifier, model, algorithm to use. What are the exact thigs we should be looking at when evaluation and selecting a model in Machine Learning.

## Performance of a Model

We know the deal of using the training set to create some model that eventually will measure the **accuracy** of some model when predicting on a test set. Besides, accuracy we can also test for other things such as:
- **Recall**  
- **Precision**
- **F scores**


![measurements](imgs/model_selection/measurements.png)

*Source : Data Mining Concepts and Techniques, 3rd Edition by Kamber*

From above image, it is important to define some terms:

Consider an example where you live in a small town and you have to protect the town's citizens and animals from dragons. Predicting a "dragon will come" it is the Positive or target data we are looking for **(P)**. In the other hand, consider that a "no dragon is coming to town" is the negative data **(N)**.

**True Positive (TP)**: 
- Reality: "dragons came to the town"
- Predict: "dragons will come"
- Outcome: you are hero and save millions of human and animals lives from the flames of dragons

**False Positive (FP)**:
- Reality: "dragons did not come tonight"
- Predict: "dragons will come so let's evacuate the town"
- Outcome: citizens and animals are pissed off at you because you made them ecavuate in the middle of the night. Predict P when it turned out to be N.

**False Negative (FN)**:
- Realtity: "dragons came to town"
- Predict: "dragons will not come to town tonight"
- Outcome: millions of people died and animals were burned to ashes because predicting for N when it turned out to be P.

**True Negatives (TN)**:
- Reality: "dragons did not come to town tonight"
- Predict: "dragons will not come tonight"
- Outcome: People and animals are fine and nothing happened.

In real life, people don't use dragons burning or not towns as measurements for their classifiers.**Confusion Matrices** to read better this measurements and in the field of predictive analysis. The matrix or table of 2 by 2 it used to calculated more metrics in terms of proportions

Using a Confusion Matrix, accuracy is calculated by:

$$ \text { Accuracy } = \frac{TP + TN}{P + N}$$

In order to see the overall performance of a Confusion Matrix in a binary setting like the above example, we tend to look at Sensitivity (recognition rate) and Specificity 

- Sensitivity - model's ability to predict TP of each tuple.
- Specificity - model's ability to predict TN of each tuple.

Such that,

$$ \text { Sensitivity } = \frac{TP}{FN + TP} $$

$$ \text { Specificity } = \frac{TN}{FP + TN}$$



![specs](imgs/model_selection/data100_img.png)

*Source : Wikipedia*


### Recall and Precision vs Sensitivity and Specificity
 
 A this point we have defined Sensitivity and Specificity, how about recall and precision? Are they similar or not? Let's see now.

**Precision** it is the measurement of exactness. 

> *How many really are positive?*

>*What proportion of positive identifications was actually correct?*

 $$\text { Precision }=\frac{T P}{T P+F P}$$

 **Recall** it is the measurement of completeness. 

 > *How many are predicted as positive?*

 > *What proportion of actual positives was identified correctly?*

 $$\text { Recall }=\frac{T P}{T P+F N}$$

 Now, 

If we define a positive example as “dragons are coming to town” we can see that Recall and Sensitivity are the same, but Precision and Specificity are different. Precision is also called recognition rate or true positive rate. From now on we will refer to sensitivity as recall.

Those definitions are pretty simple, however, I found myself confused when trying to understand what does the combination of them mean about my algorithms. How do we know which combination of them to use? What scenarios or conditions? 

**If it helps, you may refer to specificity as the recall of the same problem when the positive label is defined as negative, and the negative as positive.**

 All the measures (precision, recall, and specificity) give us important information about how well is our classification model. **It is important to look at all of them**. For example, without looking at specificity you could create a model with great precision and recall that simply predicts everything as true, and has no real value.

 







