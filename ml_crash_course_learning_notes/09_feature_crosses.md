# Feature Crosses

## Encoding Non-Linearity
* We can encode non-linear relationships in data using feature crosses (cross comes from cross product) and feed them as input as new **synthetic features** into our model
	* E.g [AxB] , [AxBxCxD] , [AxA]

## Crossing One-Hot Vectors
* Crossing one-hot encoded vectors is equivalent of a logical conjunction of the two binary vectors (e.g. `country=USA AND language=spanish`)
* It creates a cross product. So A x B, s.t. size(A) = 5, and size(B) = 4 will result in AB of size(AB) = 20. This new vector, AB, will also be one-hot encoded - i.e. will only haves many zeroes and one 1. 
* These help the model learn relationships between two different features

## Questions/followups
* Why can' the model learn these relationships by nature of the linear equation/weights itself?
** Ans: B/c these features alone do not have a linear relationship with the label. Their multiplier (weights) are not constant across examples. Their product *does* have a linear relationship with the label and the model can't learn cross products in a single layer linear regression model. 


## References
* Course Links:
	* Encoding Non-Linearity: https://developers.google.com/machine-learning/crash-course/feature-crosses/encoding-nonlinearity
	* Crossing one-hot vectors: https://developers.google.com/machine-learning/crash-course/feature-crosses/crossing-one-hot-vectors