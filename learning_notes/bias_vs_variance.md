# Bias vs Variance

This captures the tradeoff that ML practitioners have to make during model selection in terms of model complexity. 
High bias means the model is underfit and thus does not capture the relationship between the data and labels well. 
High variance means that the model is overfit and thus captures relationships in the training dataset and labels that may just be noise. Such models have low loss but don't generalize well on unseen examples. In an ideal situation, we would want to lower the model's bias and variance at the same time. 

The model's performance on the train and validation (or validation) datasets can be an indication on where the model lies in terms of bias and variance. Higher loss in the train set means higher bias. Higher difference between the train and validation set's loss means higher variance. 

Higher Bias/Lower Variance models tend to be simpler in complexity while lower bias/high variance ones tend to be more complex.


## Spark Notes from Video(s): 
* High Bias = Underfit = model too simple
* High Variance = Overfit = model too complex
* Look at training vs dev set errors as an indicator of overfitting vs underfitting
	* Train set error low, dev set error high -> Overfitting to training set -> high variance
	* Train set error high, dev set error similarly high -> Underfitting to training set BUT generalizing well -> high bias 
	* Train set error high, dev set error much higher -> Underfitting to training set, but also overfitting to it -> high bias, high variance
* Train set error indicates bias
* Dev set error indicates variance

## Resources
* Andrew Ng's Bias/Variance (C2W1L02) - https://www.youtube.com/watch?v=SjQyLhQIXSM