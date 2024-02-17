# Classification

## Classification Thresholding
* A **classification threshold** is the threshold used for converting probability outputs into binary outputs. 
* The threshold needs to be tuned per problem taking into account how much the business will be impacted by precision/recall 

## True vs. False; Positive vs. Negative
* True Positive (TP)
	* Reality: True
	* Label: True
	* We want this
* False Positive (FP)
	* Reality: False
	* Label: True
	* Model incorrectly predicts positive class
* True Negative (TN)
	* Reality: False
	* Label: False
	* We want this 
* False Negative (FN)
	* Reality: True
	* Label: False 
	* Model incorrectly predicts negative class

## Accuracy
* Accuracy = Fraction of predictions the model got right
	* (TP + TN) / (TP+FP+TN+FN)
* Accuracy isn't always a good measure of model goodness, esp. when there is a **class imbalance** in the dataset
	* class imbalance meaning there are very few examples of one class. 

## Precision and Recall
* **Precision** = Of the predicted positive labels, how many of them are correct
	* i.e. precision = TP/(TP+FP)
	* precision = 1.0 = No False Positives
* **Recall** = Of all the positive labels, how many did the model capture?
	* i.e. recall = TP/(TP+FN)
	* Recall = 1.0 = No False Negatives 
* Increasing precision can reduce recall and vice versa

## ROC Curve and AUC
* **ROC Curve**: Receiver Operating Characterisitc Curve
	* Used to see the performance of a classification model at all classification thresholds. 
	* Plots True Positive Rate vs False Positive Rate
	* Alternative to using many many confusion matrices
* **True Positive Rate (TPR)**
	* TPR = (TP)/(TP + FN)
	* aka Sensitivity aka Recall
* **False Positive Rate (FPR)**
	* FPR = (FP)/(FP + TN)
	* aka (1 - Specificity)
* **Area Under the Curve (AUC)** Measures the area under the ROC curve. 
	* Can be used to compare two different models: Models with higher AUC are better than models with lower AUCs
	* Ranges from 0-1
	* Model that's always wrong has AUC 0 and model that is always right has AUC 1. 
	* **Scale invariant** - doesn't care about actual prediction values
		* Con: Not always desirable
	* **Classification Threshold Invariant** - shows the model's quality across all thresholds. 
		* Con: We may want to optimize the threshold one way or another depending on the business need

## Prediction Bias
* Average of predictions should approximately equal average of observations
	* When this is not the case (the diff b/w them is not close to 0), then there is a **Prediction Bias** in the model
* No prediction bias doesn't mean we have a good model. But a high prediction bias does mean that we definitely have a bad model
* Causes for Prediction Bias
	* Too much regularization
	* Poor/incomplete features
	* Non-representative training dataset
	* noisy dataset
	* processing pipeline failures
* Do *not* use a calibration layer to fix prediction bias; it makes your model/pipeline brittle
* For logistic regression/binary classification, bucket a set of examples into bins and get their average prediction. Plot/compute the average of a set of these to get the prediction bias. 
	* This is because these outputs are always either 0/1 or very close to them so can't make a meaningful estimate of prediction bias on them alone. 

## Programming Exercise
* Calculate z-scores using the exact same values in both train and test sets. Meaning, in the test set, use the mean and stddev calculated from the train set. 







## Resources
* Course Links:
	* Thresholding: https://developers.google.com/machine-learning/crash-course/classification/thresholding
	* True vs False and Positive vs Negative: https://developers.google.com/machine-learning/crash-course/classification/true-false-positive-negative
	* Accuracy: https://developers.google.com/machine-learning/crash-course/classification/accuracy
	* Precision and Recall: https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall
	* AUC-ROC: https://developers.google.com/machine-learning/crash-course/classification/roc-and-auc
	* Prediction Bias: https://developers.google.com/machine-learning/crash-course/classification/prediction-bias

* Extra Sources:
	* ROC and AUC, Clearly Explained! by StatQuest (Bam!): https://www.youtube.com/watch?v=4jRBRDbJemM