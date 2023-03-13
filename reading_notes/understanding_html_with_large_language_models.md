# Reading Notes
--- 

Key Takeaways
----

* **Encoder-Decoder models (T5- ) performed best, even when smaller than their encoder-only and decoder-only counterparts;**
  * Possible explanation: bidirectional attention may be able to process HTML relationships better
* **Pretraining on HTML is not necessary when fine tuning on HTML understanding tasks**
* **Context Window is a bottleneck for HTML understanding** - 
  * even with models that accept >1k tokens, LLMs don't perform too well. 
  * increasing snippet size led to performance degradation
  * may need to develop new methods to reduce the state representation of web content for use in LLM context windows. 
* **The largest model is not necessarily the best one to use, depending on use-cases**
  * While fine tuned PaLM-65B performed the best (88.7% on test set), fine tuned T5-large (800M params) gave a better ROI (87.0% on test set) given that it's a significantly smaller model


Canonical Tasks: 
---
* Autonomous Web Navigation
* Semantic Classification
* Description Generation

Datasets:
---
* [MiniWoB](http://proceedings.mlr.press/v70/shi17a/shi17a.pdf)
* [Generative MiniWoB](https://arxiv.org/abs/2201.08896)
* [Common Crawl](https://commoncrawl.org/)

|Task| Dataset|
|---|---|
|Autonomous Web Navigation | MiniWoB benchmark - 12k examples from 62 website applications from email fwding to social media interactions|
|Semantic Classification | gMiniWob (?) - 28k labeled examples, 66 diff categories, format: (HTML, element, category). Source: real world shopping websites . Paper: https://arxiv.org/abs/2201.08896 |
| Description Generation | Custom new dataset derived from Common Crawl. 85k samples|


Preprocessing
---
* Raw HTML text is fed into the models. enables reuse of existing seq2seq architectures. 
* **Snippet extraction** is performed on pages that are too long; Essentially they pick a target element in the DOM and crawl up its ancestors until some criteria is reached (depth/seq length?)

Model Training
---
* Encoder-Decoder & Decoder only models for all three categories 
* Encorder only models (i.e. BERT) for semantic classification - add a classification layer after the final encoder layer

Results - Metrics
---

* Autonomous web navigation - *Success Rate* 
* Semantic Classificaiton - *Accuracy* measures exact match between prediction & ground truth
* Description Generation 
  * *Accuracy* measures exact match between prediction & ground truth
  * 'soft' evaluation metrics like BLEU and Rouge-1 to measure similarity b/w prediction & ground truth


Results -- Autonomous Web Navigation
---
<TODO: fill-me-in>


Results -- Semantic Classification Task
---
Methods:
* 3 size variants of T5 encoder-deocder architecture (base, large, 3B) 
* fine tuned on 22k real human labeled web sites
* compare with ...
  * fine tuned encoder only arch - BERT
  * 3 fine tuned decoder only arch (LaMDA-1B, PaLM-8B, PaLM-62B)
  * encoder-decoder trained on human labeled websites from scratch
  * decoder only models trained on human labeled websites from scratch

Results
* All LLMs perform well - 78-88% on test set for pretrained; 73-76% on tests set for training same architectures from scratch
* As seen above, pretrained perform better than non-pretrained
* **While fine tuned PaLM-65B performed the best (88.7% on test set), fine tuned T5-large (800M params) gave a better ROI (87.0% on test set) given that it's a significantly smaller model**
* model did better on unambiguous categories than ambiguous ones
* using larger snippets decreated performance
* Using just 1000 pretraining examples allowed pretrained T5-3B to perform better than non-pretrained/trained from scratch T5-3B on a much larger training corpus


Results -- Description Generation Task
---
Methods: 
* Split the dataset across top level domain to see how well the model generalizes to unseen domains
* Fine tuned encoder-decoder T5* architectures
* Fine tuned decoder only models - LaMDA*
* Compare with a *Closest Description* heuristic baseline as well 

Results:
* All models performed well - ~90% accuracy on exact match & ~94 on BLEU/Rouge-1 - meaning models can locate the descriptions but can't always generate the exact output

Analysis across tasks
---
* Pretraining helps across the board
* **Encoder-Decoder models performed best, even when smaller than their encoder-only and decoder-only counterparts;**
  * Possible explanation: bidirectional attention may be able to process HTML relationships better
* Model size matters but gets decreasing returns. 
  * Model perf is O(log(log(n)) wrt model size for semantic classification

Discussion
---
* **Pretraining on HTML is not necessary when fine tuning on HTML understanding tasks**
  * BERT and T5 do not have HTML in their pretraining dataset
  * LaMDA and PaLM have HTML in their pretrainign dataset
* Bi-directional attention seems to be very helpful in understanding HTML. Pre-training T5 on HTML may yield better results.
* We need fewer and fewer labeled examples when fine tuning using LLMs (~30x-200x reduction)
* The largest model is not necessarily the best one to use, depending on use-cases
* **Context Window is a bottleneck for HTML understanding** - 
  * even with models that accept >1k tokens, LLMs don't perform too well. 
  * increasing snippet size led to performance degradation
  * may need to develop new methods to reduce the state representation of web content for use in LLM context windows. 


