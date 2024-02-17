# Validation Set

## Notes From the Reading
* Do not use the test dataset for hyper parameter tuning - you may overfit your model to the test set and lose confidence in its generalizability. Instead, create a validation set and use that instead. 
* So now we have 3 datasets:
	* Train - We train on this
	* Validation - We use this for hyper parameter tuning (learning rate, batch size, model architecture, etc.) 
	* Test set - This is held out until the very end. We use this to test our model's generalizability. How it performs on unseen examples. 
* This creates less exposure to the test set. 
* Tip from course: Test and val datasets get worn out as we use them. In other words, we may overfit our models to them as we iterate on them more and more. It is recommended by the course to periodically refresh them with new data (either appending or replacing the existing one).

## Notes from the Lab
* Generally a good idea to shuffle the dataset before splitting into train/test/val to ensure each split is representative of the whole dataset
	* This is a pretty neat way to shuffle: `shuffled_train_df = train_df.reindex(np.random.permutation(train_df.index))`
* Validation split size is important. If it's too small, it may not have enough examples to be representative of the full dataset
* When training, it's important to see how the loss appears across the splits (train, val, test). It should be roughly similar. If it's not, then the different splits may not have a similar distribution of the original dataset. 


## References
* course link: https://developers.google.com/machine-learning/crash-course/validation/another-partition
