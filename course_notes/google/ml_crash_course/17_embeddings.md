# Embeddings

**Embeddings** transform sparse vectors from higher dimension space into lower dimensions. 
* Useful in things like collaborative filtering/recommendation systems/many other applications
* Example: mapping all possible movies and books into a lower dimensional space to learn their characteristics
	* Alternative: one hot encoding for each and every movie/book, which can get massive and unwieldy
* Useful embedding sizes may be on the order of ~100s of dimensions to be able to capture rich semantic relations. 
* Can be trained standalone or as part of a larger model 
* Similar items are closer together in the embedding space than non-similar items

Issues with one-hot encoding for large input space / **motivation for embeddings**:
* network size:
	* large amount of training data required; more weight count -> more training data
	* more computation required; more GPUs, more time. 
* minimal/no meaningful relations between input vectors 
	* one vector being closer to another means nothing meaningful. 

Obtaining Embeddings: 
* Many options; any mathematical technique to map imp structures from high dim space to lower dim
* Examples
	* Principal Component Analysis (PCA) - collapses highly correlated dims into one
	* Word2Vec - Algorithm for training word embeddings via a Neural Network
		* follows distributional hypothesis (similar words share similar contexts)
		* trains a small neural network with one hidden layer that maps sparse input vectors into embeddings
			* weights of the trained network are used to translate new input vectors into embeddings. 
			* outputs can be used in other classification settings 
	* As a hidden layer in a larger model
		* more expensive than training a standalone embedding (like word2vec) - will take longer to train
		* more tailored to your use case
		* edge weights correspond to the coordinates of each embedding
		* can be used alongside other features 

Training Embeddings
* Triplet loss
	* at each training step, minimize distance between example and a positive example (something close to it), AND maximize distance between example and a negative example (something far from it)
* word2vec
	* sliding window to create contexts
	* no need to spend a lot of time on training data; model can infer relations well
	* Can create negative examples by either swapping target word in context with random noise OR by choosing random context for target word
	

## Terms: 
* **Collaborative filtering** Predicting what a user would like based on what other users liked
* **Categorical Data** Input features that represent one or more discrete items from a finite set of choices
* **Sparse vectors** Vectors with very few non-zero values. Unwieldy. Harder to train well. One hot encoding would create these
* **Distributional Hypothesis** Semantically similar words have similar contexts - theory behind word2vec

## Additional Topics to Explore
* Distributional Hypothesis
* word2vec
* Latent semantic analysis (LSA) -  used for topic modeling. 
* Latent Dirichlet allocation (LDA) -  used for topic modeling. 

## Resources

* Course Links: 
	* https://developers.google.com/machine-learning/crash-course/embeddings/motivation-from-collaborative-filtering
	* https://developers.google.com/machine-learning/crash-course/embeddings/categorical-input-data
	* https://developers.google.com/machine-learning/crash-course/embeddings/translating-to-a-lower-dimensional-space
	* https://developers.google.com/machine-learning/crash-course/embeddings/obtaining-embeddings
* Other links
	* Very well written from StackOverflow: https://stackoverflow.blog/2023/11/09/an-intuitive-introduction-to-text-embeddings/
