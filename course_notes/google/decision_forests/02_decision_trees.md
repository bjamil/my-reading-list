# Decision Trees

* Decision Forests are comprised of Decision Trees
* Non-leaf nodes can be called conditions, splits, or tests
* Axis-Aligned conditions vs. Oblique Conditions:
	* Axis Aligned conditions operate on just one feature/condition (e.g. num_eyes >? 2)
	* Oblique Conditions operate on multiple features (e.g. num_eyes >? num_legs) - costlier to train but can have more discriminative powers
* Generally decision trees are binary. Prevents overfitting and non-binary trees can be modeled using a sequence of binary decisions. 

