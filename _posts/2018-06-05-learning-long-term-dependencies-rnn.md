---
layout: post
title:  PaperWatch 002 - Learning Longer-term Dependencies in RNNs with Auxiliary Losses (ACL 2018)
date:   2018-06-05 08:00:00
categories: machine-learning
tags: [PaperWatch, Deep learning, RNN]
---

[Paper](https://arxiv.org/pdf/1803.00144.pdf) by Trieu H. Trinh, Andrew M. Dai,  Minh-Thang Luong,  Quoc V. Le
 
**TLDR;** RNNs can learn very long sequences when auxilary loss for predicting input sequence (forward and backward) from different timesteps is added.
 
### Problem being addressed

Recurrent neural nets in theory can learn arbitarily long sequences, but in practise suffer from problems like vanishing gradients etc.
Techniques to reduce vanishing gradients problem like LSTM alone don't work for very long sequences.

RNN has a better tradeoff when it comes to memory requirements compared to CNN based networks or vanilla [Transformer](https://arxiv.org/abs/1706.03762) nets.
When processing very large sequences this becomes important.

But the technique proposed by the authors is architecture independent, and can be potentially used for any sequence processing architectures.

### Proposed Method

Take the hidden state of main RNN used for a given task at sampled timesteps, use another RNN at sampled intervals, and try to predict the input sequence to certain time steps.
Truncated BPTT(Back propagation through time) to few timesteps would give a new loss.

### Evaluation and results

Evaluation is done on  MNIST, CIFAR-10, Stanford dog dataset is given as sequence of pixels to an RNN with
classification being the target. Since the pixels are flattened to sequential input, spatial location information is now across whole range of the
sequence, requiring long dependecies to be formed to get good results.

The authors also test it on character based classification on dbpedia.

This techinque achieves very significant results on long sequences compared to existing LSTMs, Transformers etc.

### Opinions 

This paper makes a significant experiment to improve a crucial behaviour of RNNs on long sequences. 
The ablation study is well done.
This auxillary loss reminded me of the [World models](https://worldmodels.github.io/) paper where the task of predicting future states improves current tasks output.





