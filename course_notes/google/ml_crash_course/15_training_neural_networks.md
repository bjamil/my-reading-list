# Training Neural Networks

Failure Cases: 
* Vanishing Gradients
	* What: Problem with larger networks + backpropagation. When you multiply many many many small numbers, the earlier numbers become too small. They train too slowly or not at all as a result.
	* Solution (s):
		* Keep network as small as possible
		* RelU
* Exploding Gradients
	* What: When the weights are too large, gradients can get too large to converge for the earlier nodes OR veer towards NaNs. 
	* Solution (s)
		* Normalization within the same range (usually 0-1)
		* Lower learning rate
* Dead ReLU 
	* What: once ReLU weighted sum falls below zero, it gets stuck there. Gets in the way of backpropagation + learning. 
	* Solution (s):
		* lower learning rate

Other: 
* Dropout regularization
	* Probability that any random node activation in the network can be dropped out
	* Strong method of network regularization. Prevents networks from getting too complex. 

## Additional Topics to Explore
* Dropout Regularization
* Backpropagation

## Resources
* Course Links:
	* Best Practices: https://developers.google.com/machine-learning/crash-course/training-neural-networks/best-practices