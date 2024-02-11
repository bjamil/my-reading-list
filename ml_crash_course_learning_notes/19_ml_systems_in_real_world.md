# ML Systems in the real World
* Cancer Prediction Case Study:
	* Label leakage -- hospital names as features to the model helped models 'cheat' in predicting cancer or not in train/test set but led to poor generalization on new examples
* Literature Case Study: 
	* Need to understand what data & features represent to randomize well - otherwise can have model memorization
* Guidelines from real world examples
	* keep first model simple - a simple linear model is more than enough in the first pass. See how much complexity you actually need
	* Ensure data processing pipeline correctness - using the simple model, ensure the data pipeline doesn't have any bugs as those are harder to catch later on. 
	* Use simple, observable metrics for training and eval - to make sure model is behaving as expected
	* Own & monitor input features
	* Treat model config as code - reproducibility & auditing & version control are essential in understanding what went wrong, when, where, why
	* Document all experimental results, esp failures - Needed for understanding & learning what worked, what didn't, and why

# Additional Topics to Explore/Readings
* [Meaning and Mining: the Impact of Implicit Assumptions in Data Mining for the Humanities](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.103.21)
* [Leakage in data mining: formulation, detection, and avoidance](https://dl.acm.org/doi/10.1145/2020408.2020496)
* [Rules of ML: Best Practices for MLE](https://developers.google.com/machine-learning/guides/rules-of-ml)

# Resources
* Course Links:
	* https://developers.google.com/machine-learning/crash-course/cancer-prediction	
	* https://developers.google.com/machine-learning/crash-course/18th-century-literature
	* https://developers.google.com/machine-learning/crash-course/real-world-guidelines




