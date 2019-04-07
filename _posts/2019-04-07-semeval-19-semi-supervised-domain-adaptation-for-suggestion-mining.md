---
title: SemEval 2019 - Semi-Supervised Domain Adaptation for Suggestion mining
categories: publications
tags: [NLP, Semi-Supervised Learning]
toc: true
toc_label: Contents
toc_icon: "yin-yang"
---

SemEval Workshop regularly has been conducting tasks in NLP to evaluate the progress in the field.

I and my colleague Ananda Seelan participated in this year SemEval's Suggestion mining task (Task 9).
Here is our [submission](https://arxiv.org/abs/1902.10623) to be published in NAACL 2019 proceedings, and the code is on [github](https://github.com/sai-prasanna/suggestion-mining-semeval19).

This blog is a summary of the key techniques and ideas which influenced this work.


## Suggestion Mining Task

The suggestion mining task in brief is a text classification task to find whether a sentence contains a suggestion.

Example,

-   **Suggestion**     - It would be nice if they had vegan options.
-   **Non Suggestion** - This restaurant has good vegan options.

About 8k sentences scrapped from technical forumns were provided as training data. 
The task was divided into two subtasks.

-   Subtask A - Evaluation on same domain   - technical forums posts.
-   Subtask B - Evaluation on out of domain - hotel reviews.

The catch for subtask B is human labelled data in hotel reviews domain is not allowed for training.
Our model was placed third place in the leaderboard for Subtask B.



## Key Techniques

We used simple convolutional neural networks for text classification. And we applied transfer learning and semi-supervised learning for the tasks.



### Transfer Learning

The current trend in machine learning for NLP is to using pre-trained language models. We used google's recently published BERT model as our representation layer.
Take a look at <http://jalammar.github.io/illustrated-bert/> for a good description of how pre-trained models work for NLP.



### Semi-Supervised Learning
In ACL 2018 conference Melbourne, I attended two talks which impacted the work in this paper. One was Sebastien Ruder's talk on Strong baselines for semi-supervised
learning in NLP. The conclusion of [Sebastian Ruder, Barbara Plank (2018)](https://aclweb.org/anthology/P18-1096) was that classic machine learning techniques for semi-supervised learning such as Tri-Training prove as strong baseline in NLP with neural nets.
Sebastien has a very accessible and thorough [blog post](http://ruder.io/semi-supervised/) explaining the techniques. They have also made their code available on [github](https://github.com/bplank/semi-supervised-baselines). 

<iframe src="https://player.vimeo.com/video/285802189" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

We applied a variant of tri-training. We use three models of the same architecture trained initially on data [bootstrap sampled](https://en.wikipedia.org/wiki/Bootstrapping_(statistics)) from the tech reviews data. The three models
are used to iteratively label unlabelled data from hotel reviews domain. Agreement of labels between two models is used as way to select sentences to be added to next iteration
of training. Pseudo-code and detailed explanations can be found in the paper. Or you might as well look to the code, as its way simpler than a dry description of it might suggest.



## Statistical Significance

The other work [published](https://aclweb.org/anthology/P18-1128) and presented in ACL 2018 that influenced this paper is Rotem Dror's "The Hitchhiker's Guide to Statistical Significance in NLP".

<iframe src="https://player.vimeo.com/video/285803636" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

We report confidence intervals for five random seeds for all our experiments. And we also do pair-wise significance testing via McNemar's test to evaluate 
whether pair-wise model performance on the test set vary significantly. 



### Metrics

![img](https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/bf7927798419277eea7063f40d4329f8b8fa31ad/3-Table1-1.png)



### McNemar's Test

![img](https://ai2-s2-public.s3.amazonaws.com/figures/2017-08-08/bf7927798419277eea7063f40d4329f8b8fa31ad/5-Table3-1.png)


