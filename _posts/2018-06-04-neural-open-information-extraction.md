---
title:  PaperWatch 001 - Neural Open Information Extraction (ACL 2018)
date:   2018-06-04 08:00:00
categories: machine-learning
tags: [PaperWatch, Deep learning, NLP]
---

[Paper](https://arxiv.org/abs/1805.04270) by Lei Cui, Furu Wei, Ming Zhou
 
**TLDR;** Models Open information extraction as  Sequence to Sequence problem using neural nets.
 
### What is Open information extraction?

Open Information Extraction aims to extract one or more (Entity 1, Relationship, Entity 2) tuples from sentences.  
 
**Example**

```
"Deep learning is a subfield of machine learning." 
                   |
                   v
(Deep learning, is a subfield of , machine learning) 
```

Existing methods use handcrafted rules written on **syntatic parsers** which have poor perfomance and suffer from **cascading of errors**.  
This paper applies neural networks to get better accuracy and alleviate errors. 
 
### How is the problem modeled?
 
Sequence 2 Sequence task, where you take a source sentence as input and output the information tuple as sequence separated by special tokens (open arg1, arg2, arg3 and close arg1, arg2 arg3).  Currently the model is trained for single tuple extraction. 

"Deep learning is a subfield of machine learning." -> "<arg1> Deep learning </arg1>  <arg2> is a subfield of </arg2> <arg3> machine learning </arg3>" 
 
The paper uses a LSTM based **Sequence to Sequence** model with **attention**. 
The source and target vocabulary is same. If unknown word target is found, the model forms the target probability vector by placing attention on of source sequence as probability of the corresponding source words occurring.

### What are the benchmarks?
 
Evaluating on a large benchmark dataset, this model gets **0.473 AUC** (Area under curve) for Precision-Recall on **top 5 predictions** of this model (I think generated from beam search) has better performance , significantly higher than existing systems.  Among existing systems **OpenIE** has the best score of  **0.373 AUC** .  
 
One observation of authors is only 11 % of the predictions of Neural model matches with Open IE (rule based) model, but the performance is higher. This could be due to neural model generalizing on some of the patterns hard to capture by rules.
