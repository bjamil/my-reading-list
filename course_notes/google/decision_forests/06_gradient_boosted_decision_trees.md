# Gradient Boosted Decision Trees

* Examples: XGBoost, AdaBoost
* Very powerful 
* Ensemble of a **sequence** of weak learners (in this case, decision trees), with each tree in the sequence improving the accuracy of the previous one
	* Inference must happen sequentially through all trees (?)
	* Each learner is pretty small, one or few node tree 
	* The goal is to improve the prediction of the previous tree/sequence a little bit
		* The label for each sequential tree is the 'residual' of the sequence so far (?)
		* Uses gradient descent
* These trees **can** overfit as more trees are added in
* Regularization params
	* depth of tree
	* Shrinkage rate (learning rate?)
	* % attributes/features tested at each node
	* L1 & L2 regularization
* Cross validation / early stopping can be used
* Pros: 
	* Don't require preprocessing
	* Good defaults. Tuning makes them better
	* Small memory footprint + low latency (microseconds)
* Cons:
	* Slow training due to lack of parallelization/sequential training, unlike random forests
	* poor perf on unstructured data
	* each tree needs to relearn patterns from dataset independently 


## Things I still don't understand
* What's the input and output of each decision tree in the sequence? Do we reclassify the input at each step? Do we only use the final tree for inference? How do we get the inference output from the weak learners?


## Additional Resources
* Course Links: 
	* https://developers.google.com/machine-learning/decision-forests/intro-to-gbdt
* https://www.machinelearningplus.com/machine-learning/an-introduction-to-gradient-boosting-decision-trees/
* https://towardsdatascience.com/a-visual-guide-to-gradient-boosted-trees-8d9ed578b33&strip=0&vwsrc=1&referer=medium-parser
* https://www.youtube.com/watch?v=TyvYZ26alZs
* https://www.youtube.com/watch?v=yw-E__nDkKU
* https://www.youtube.com/watch?v=lOwsMpdjxog&t=0s
* https://bradleyboehmke.github.io/HOML/gbm.html#final-thoughts-7
