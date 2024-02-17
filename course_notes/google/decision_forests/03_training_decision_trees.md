# Training Decision Trees

* Usually a greedy algorithm is employed to recursively grow the tree until no conditions are left
	* There are alternative non-recursive algorithms too (also greedy)
	* NP-hard problem so heuristics are used instead
* Splitter: Is the routine responsible for finding the optimal condition to pick. Usually bottleneck for training b/c of large space of options to pick from. 
	* loss function is task depdendent. 
	* multiple splitter algorithms exist 

## Binary Classification 
* Shannon Entropy - measure of disorder
	* minimum when labels in examples are pure (i.e. 100% one label) 
	* maximum when labels are balanced (i.e. half and half)
* Information Gain - Difference in entropy of a node and the weighted sum of entropies of its children
	* we want to maximize Information Gain / minimize weighted sum of child entropies
* Generally the value of the features doesn't matter as much as how well they separate the data. This is why we don't need to normalize the features so much. 

## Regularization 
* Decision trees are prone to under/overfitting
* The following regularization strategies can be applied to limit overfitting
	* Setting minimum number of examples per leaf node
	* Setting maximum tree depth
	* Performing pruning -- i.e. taking a random intermediary node and converting it to a leaf node (i.e. pruning off all of its children)
* These regularization params are hyperparams. Can use a validation dataset or cross validation to quickly tune them efficiently. 

## Variable Importance
* Variable importance aka feature importance, measures how valuable a feature is to the model
	* There may be multiple definitions of valuable (i.e. how often it's observed, depth of first occurrence, permutation variable importance, etc.), each potentially giving conflicting values. It's wise to view a number of importance metrics before accepting a feature's importance & acting on it (e.g. for feature removal)
	

## Additional Topics to Explore
* Shannon Entropy
* Information Gain