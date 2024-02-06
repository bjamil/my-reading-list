# Training and Test Sets 

## Notes
* We want to split our model into train and test sets
* Test sets are held out and we should **never** train on them
	* If you're getting close to 99-100% accuracy on your test sets, make sure your test set hasn't accidentally blended into your train set. 
* Test set must
	* be large enough to be statistically significant
		* For large datasets this is easy. For smaller, we may want to do some k-fold cross validation or other creative approaches
	* be representative of the whole dataset
		* You probably want to randomize before creating the train test split to allow for this

## References
* course link: https://developers.google.com/machine-learning/crash-course/training-and-test-sets/splitting-data
