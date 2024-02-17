# Regularization: Simplicity

## Playground Exercise
* Adding feature crosses/usinga a complex model when they're not necessary may lead to the model overfitting to the training dataset. Essentially, capturing relationships in the training set that are actually noise rather than meaningful relationships. 

## Video Lecture
* Regularization is a strategy for reducing overfitting
* It penalizes having complex models
* Complexity can have several definitions. One popular one is the sum of squares of the model weights (L2 norm).
* So the objective function now `= min(loss) + theta * (sum(squared(weights)))`
* Regularization not as necessary when we have a large train/val/test dataset and the two datasets are fairly similary (IID)
* Early stopping is another strategy for minimizing overfitting

## L2 Regularization
* Regularization = penalizing model complexity to prevent overfitting to the training dataset
* Empirical Risk Minimization = minimize(Loss(Model|Data))
* Structural Risk Minimization = minimize(Loss(Model|Data) + Complexity(Model)) 
* L2 Regularization = sum(squares(feature_weights))
	* We want to minimize any one feature's high contribution to the overall results 

## Lambda
* Lambda = Regularization rate
	* Minimization function = `minimize(Loss(Model|Data) + lambda * complexity(Model)`
* High lambda = more regulariztaion = simple model = underfitting
* Low lambda = low regularization = complex model = overfitting
* L2 Regularization impacts the model by: 
	* encourages weights veering towards 0
	* encourages bell shaped/Guassian distribution of weights with a mean around 0. 
* Tweaking learning rate and lambda together can have unexpected results

## Additional Topics to Explore
* Bayesean priors
* Generalization Curve
* Early stopping


## References
* Course links
	* Video Lecture https://developers.google.com/machine-learning/crash-course/regularization-for-simplicity/video-lecture
	* L2 Regularization https://developers.google.com/machine-learning/crash-course/regularization-for-simplicity/l2-regularization
	* Lambda https://developers.google.com/machine-learning/crash-course/regularization-for-simplicity/lambda