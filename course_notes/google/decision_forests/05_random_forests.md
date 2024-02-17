# Random Forests

* Ensemble model: a collection of models whose decision is aggregated
	* mimic central limit theorem when done right
	* requires more training + inference than a single model - because these are multiple models
	* Individual models must be independent for it to work best
		* but forcing independence can worsen model predictive quality. 
			* We need to strike the right balance b/w model independence & quality of sub models 

* Random Forest is an ensemble decision tree in which each tree is trained with specific random noise
	* most popular decision forest
* Creating independent decision tree strategies: 
	* Bagging: bootstrap aggregation
		* Each decision tree is trained on a different random subset of the full dataset
		* Even though the tree is trained on a subset, examples are repeated to make the specific tree's dataset's size be equal to the full forest's dataset size. This is because fewer or more examples tend to reduce perf or decision trees
	* Attribute Sampling:
		* In each tree, only n% of the features are examined as potential decision points. The rest are ignored. The highest scoring feature at each node is selected as the decision point. 
		* n can be tuned as a regularization hyperparam
* Regularization in decision trees is not needed -- even though individual decision trees can overfit and are poor predictors, since they're generally independent due to bagging + attribute sampling, their ensemble generalizes well. (central limit theorem)
	* In practice, we would still limit max depth/max observations per leaf node, which are tunable hyperparams
* Overfitting
	* We expect training accuracy of random forests to be very high (even 100%) and we expect testing accuracy to be lower.
	* Random forests **do overfit**, contrary to this article + terminology in original paper
	* However, **generalization error** does not get worse as more trees are added. At some point, it just plateaus.
		* The forest would still perform equally badly on the test set as more trees are added (overfitting)
* Out of Bag (OOB) Evaluation
	* Random forests don't need a validation dataset: You can treat the training dataset as a cross-validation dataset
		* i.e. Since each tree in the random forest is only trained on a subset of the data, you can validate how the forest performs by getting the predictions for each training example on all trees except for the trees that trained on it. 
* Interpretability: 
	* More difficult to interpret than individual decision trees due to the randomness. 
	* Can use strategies like CART, Permutation Variable Importance, and SHAP (SHapley Additive exPlanations) for interpretation
* Pros & Cons
	* Pros: 
		* don't need feature preprocessing
		* trees can be trained in parallel since trees are independent
		* default params work great out of the box/don't need much tuning
	* Cons:
		* doesn't do so great on non-tabular data
		* trees can get massive (>1M nodes) since we don't enforce pruning
		* each tree in forest has to relearn the dataset pattern

## Additional Resources
* https://www.stat.berkeley.edu/%7Ebreiman/randomforest2001.pdf
* https://datascience.stackexchange.com/a/48863
* Course links:
	* https://developers.google.com/machine-learning/decision-forests/random-forests