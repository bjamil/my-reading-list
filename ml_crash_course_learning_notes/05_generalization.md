# Generalization 

## Notes

* Don't overfit models. Overfit models don't perform well on unseen examples.
* Split data into train/test to avoid overfitting. Don't let test set bleed into train set.
* Ockham's razor: Simpler models generalize better. 
	* There's a body of theoretical work in statistical learning theory and computational learning theory based off of this. It defines generalization bounds based on the model's complexity and performance on training data. This unit won't go into that. 
* Generalizability of a supervised ML model relies on 3 assumptions: 
	* Examples are independently and identically (iid) sampled at random from a given distribution
	* The distribution is constant; it does not change over time.
	* The same distribution is used to sample very example. 
	* If any of these assumptions are broken, generalizability assumptions don't hold. 
* In the real world the assumptions may be broken. Pay closer attention to your monitoring metrics when you know this is the case.

## Additional Reading/Topics
* Ockham's razor
* generalization bounds

## References
* Course link: https://developers.google.com/machine-learning/crash-course/generalization/peril-of-overfitting
