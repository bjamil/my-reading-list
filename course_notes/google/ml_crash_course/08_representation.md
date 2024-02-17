# Representation

## Video Lecture
* Feature Engineerng is important. A lot of time is spent on this. 
* Categorical features can be one-hot encoded
* Features may need to be tweaked to remove or flatten outliers
* Binning is a good strategy for continuous variables that make more sense as categorical ones (e.g. latitude/longitude)
* Always know your data!
	* Plot your data. Describe your data
	* Use metrics for real world monitoring wherever possible
* Use high quality features 

## Feature Engineering

* Feature Engineering is the process of converting raw data into a representation the model can understand. Generally numerical in nature. 
* Numerical values can easily be copied over as is
* Categorical values (e.g. street names, or numerical values that should be categorical like zip codes) can be **one-hot encoded**.
* One Hot Encoding: Create binary vector for each possible value the category can take that we know of and. Set 1 for the value that is present in the input (e.g. Quail Pass Rd.) and 0 for everything else. This almost acts as a mask. 
	* If multiple values can be set to 1, then it's called as **multi-hot encoding**
	* This is a sparse vector that can get massive as your category values increase. There are efficient ways to represent & store this such that only the True value is stored. 
	* You can add an Out of Vocab (OOV) element in this sparse vector as well for any value you see in teh real world that you didn't see in your training set and hence don't have an entry in your encoded vector for. 

## Qualities of Good Features

* Use high quality features whenever possible 
* **Good features appear at least 5 times in the data set.** This allows the model to learn relationships between the feature and label. For example, height might appear multiple times in a dataset of students but uuid or student id may appear only once, making height a better predictor. 
* **Assign meaningful names to features.** One shouldn't have to dig into code or find the the engineer who created it to understand what a feature is representing. 
* **Don't use magic numbers.** It's very tempting to add in -1, -inf or some other value to a variable in error or invalid scenarios. For example when the mileage of a car is unknown, we may just put in -1 instead of a value. This messes with the expected range of the feature. Instead, one should always maintain the natural range of a variable and employ strategies to obviate magic numbers, such as: 
	* Add a new boolean feature that says whether the value is present or not
	* For continuous variables, fill missing values with the average value of that feature
	* For categorical variables, fill missing value with the most frequent value of that feature
	* (mine) for time series, fill missing values the previous value seen 
* **Account for Upstream Instability** Pick features whose meanings wouldn't change over time. For example, the language feature probably won't change in meaning over time (although you may still have to account for changes in its representation like switching from eng -> en). Alternatively, if you're using a feature derived from an upstream model such as feature_cluster_id, that computer generated value may change over time as the model is rerun and retrained and may not be a reliable predictor over time. 

## Cleaning Data 
* A lot of an MLE's/DS's time is spent on cleaning up real world data
* **Scaling Feature Vectors** Scale features so they lie in a reasonable range. This doesn't mean all need to be in the same range. However, the ranges shouldn't be too diff from each other (e.g. 1000-4000 for feature A and 0-1 for feature B). 
	* Scaling helps with the following concerns: 
		* A feature doesn't contribute too much to the label just by nature of its possible range
		* Avoids the NaN trap - where one weight becomes NaN because it is too large, leading to others eventually NaN'ing out too. 
		* Helps gradient descent converge more quickly. 
	* Strategies for Scaling
		* Linear map [min, max] to a small scale such as [-1, 1]
		* Compute the `Z` score of a number s.t. `Z score = (vlaue - mean)/stddev` . Most values will fall between -3, +3 (b/c of stdev. Some will fall outside of this range)
* **Handling Extreme Outliers** We want to minimize the influence of outliers. Some strategies are: 
	* logarithmic scaling. Could work but may still leave a long tail
	* Clipping values. Cap the max/min values to an arbitrary number that makes sense. We'll now have a normal dist + a small hill for outliers in the graph
	* **Binning** Certain numeric variables may not have a linear relationship with the label but still provide meaningful information on the label (e.g. zip code, lat/long). In such cases, it may make more sense to bin these values at some granularity and treat each bin as a categorical value encoded using one-hot encoding*
		* Quantile binning is a binning strategy that removes the need to worry about outliers. 
	* **Scrubbing** It is important to detect and remove bad examples in the dataset. This is hard. but important. *
		* Also use devices such as histograms and summary statistics to ensure the dataset in aggregate form meets expectations. 
* **Know Your Data** Know what to expect and ensure actual data meets expectations, or have an explanation for why it doesn't. Ensure the training data is similar to data you'd see in production in terms of distribution, units, fields available, etc. 

## Additional Topics to Explore
* Binning by Quantile
* NaN Trap 


## References
* Course Links:
	* Feature Engineering: https://developers.google.com/machine-learning/crash-course/representation/feature-engineering
	* Qualities of Good Features: https://developers.google.com/machine-learning/crash-course/representation/qualities-of-good-features
	* Cleaning Data: https://developers.google.com/machine-learning/crash-course/representation/cleaning-data
