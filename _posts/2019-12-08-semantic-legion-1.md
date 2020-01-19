---
title: Semantic Legion \#001
categories: semantic-legion
tags: [Computer Science, Machine Learning, Philosophy, Semantic Legion]
---
I am guilty of spamming people in the degree one of my network with too many links in topics that fancy the Legion of varied interests that haunt me. Following the suggestion of Ananda Seelan, I am consolidating my link blasts into a considated blog post format, thus begins the "Semantic Legion". This exercise might help organize the "Legion" in my head and maybe lead to more focused blog posts.

> "My name is Legion, for we are many."

## Machine Learning

### [The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks](https://arxiv.org/abs/1803.03635)
The lottery ticket hypothesis suggests that big Deep Neural Nets train better than smaller nets because they get lucky. Essentially like someone who has purchased more number of lottery tickets.

1. Prune a large neural network by zeroing the bottom x% of weights by magnitude. This can be done one shot or iteratively while training.
2. Reset the obtained subnetwork weights to the exact weights you randomly intialized before training the large neural network.
3. The pruned subnetwork converges to similar test error rate as the full network or even better in the same number of epochs.
4. The authors notice that if you were try some other initialization for the subnetwork or even sample from similar distribution it doesn't work.
   Hence they hypothesise that the larger network essentially got lucky.

Though the subnetwork is smaller, computations will need sparse matrix multiplication optimizations to be faster.

### [Understanding the generalization of ‘lottery tickets’ in neural networks](https://ai.facebook.com/blog/understanding-the-generalization-of-lottery-tickets-in-neural-networks)

Facebook extends the study and checks it for various architectures, tasks and optimizer setting. The lottery ticket phenomena seems to occur in most places. The lottery ticket subnetworks generalize across datasets. This blog post is a summary of multiple papers by Facebook AI group in analyzing this phenomena.

### [New Theory Cracks Open the Black Box of Deep Learning](https://www.quantamagazine.org/new-theory-cracks-open-the-black-box-of-deep-learning-20170921/)

Information bottleneck theory a hypothesis about how neural nets learn is creating some buzz. One of the claims is that the output of earlier layers have more mutual information with the inputs while final layer outputs have more mutual information with the outputs than the inputs. The information about input gets compressed in each layer.

![Information Bottleneck process](https://d2r55xnwy6nx47.cloudfront.net/uploads/2017/09/DeepLearning_5001.jpg)
{: style="text-align: center;"}
*[Lucy Reading-Ikkanda/Quanta Magazine; adapted from arXiv:1703.00810 [cs.LG]](https://www.quantamagazine.org/new-theory-cracks-open-the-black-box-of-deep-learning-20170921/)*
{: style="color:gray; font-size: 80%; text-align: center;"}

### [Evolution of Representations in the Transformer](https://lena-voita.github.io/posts/emnlp19_evolution.html)

This is a great practical example of using information bottlenecks to analyze neural nets behaviour. This research (accompanied by inspirationally well written blog post) compares the evolution of representations in three different NLP encoder models. And in part explains some empirical findings such as why de-noising objective works better than casual language model objective or encoders from translation objective  for transfer learning.

### [Universal Adversarial Triggers for Attacking and Analyzing NLP (Wallace et al. EMNLP 19)](http://www.ericswallace.com/triggers)
This paper finds magic spells that make your NLP models malfunction. They find phrases that cause a specific model prediction when concatenated to 𝘢𝘯𝘺 input from a dataset. These phrases are reported to work across architectures for the same dataset.

    Triggers cause:

    1. GPT-2 to spew racism
    2. SQuAD models to answer "to kill american people" for 72% of questions asking "Why..."
    3. Classification models to drop from 90% accuracy to 1%

### [AllenNLP Interpret](https://allennlp.org/interpret)

This is a great set of features for interpretability added to AllenNLP library. 

>We present AllenNLP Interpret, a toolkit built on top of AllenNLP for interactive model interpretations. The toolkit makes it easy to apply gradient-based saliency maps and adversarial attacks to new models, as well as develop new interpretation methods. AllenNLP interpret contains three components: a suite of interpretation techniques applicable to most models, APIs for developing new interpretation methods (e.g., APIs to obtain input gradients), and reusable front-end components for visualizing the interpretation results. 

The amazing thing here is with implementing a simple interface in your model predictor allows you to apply a suite of interpretability techniques for our models.


### [AIDungeon2 is here](http://www.aidungeon.io/2019/12/aidungeon2-is-here.html)

This is a real fun application of langauge model generation.  [Nick Walton](https://twitter.com/nickwalton00) has adapted GPT2 to generate user guided "Choose your own" text RPG type games. Now you can try out anything you fancy by just issuing commands like "Cast a spell to Reverse entropy". A truly open world RPG with a AI dungeon master. The model weaves your actions to generalte plausible/surreal story continuations. [Hacker News](https://news.ycombinator.com/item?id=21717022) discussion about it. The nature of the model make them generate surreal dream like scenarios. There are glaring consistency issues in the generated story lines. This points to a symbolic gap that is yet to be filled.

![AIDungeon 2 generated story example.](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcSMELPoU7Br4TBHmaDn-eCYqQMFFrFUPlELxS1pYR1i3iPBOLTO)
{: style="text-align: center;"}
*[Source: aiweirdness.com](https://aiweirdness.com/post/189511103367/play-ai-dungeon-2-become-a-dragon-eat-the-moon)*
{: style="color:gray; font-size: 80%; text-align: center;"}


### [Controlling Text Generation with Plug and Play Language Models](https://eng.uber.com/pplm/)
On the topic of controlling language models, uber research has found a way to control the generation of models like GPT2 without fine-tuning. 

## Quantum Computing, Linear Algebra, Tools for Learning

### [Quantum Computing for the Very Curious](https://quantum.country/qcvc)

I wanted to try out Micheal Nielsen's (of neuralnetworksanddeeplearning.com fame) Quantum computing article. This long-form educational article attempts a unique teaching method by embedding flash cards (anki cards) and reminding readers via email to revisit the cards. I got around doing it at behest of the amzing Professor Balaji (a teacher of mine) who gave this as an exercise to test Linear Algebra understanding. Prior knowledge of the truly abstract nature of linear algebra (basis, linear transformations, linear combinations) really helped me to grok the essay.

The learning approach taken by this article (embedding flash cards + reminders) article shows how computing medium can be extended to augment our understanding. This scratches the surface of Alan Kay's vision of computers being tools that extend our mind.

### [Augmenting Long-term Memory](http://augmentingcognition.com/ltm.html)
If you're curious about spaced repition flash card approach to learn new math theorems, machine learning concepts etc Micheal has written extensively about it in the above link.

### [Anki Flash Cards with Spaced Repitition](https://apps.ankiweb.net/)
The free app Anki is example of good software aimed at expanding our capabilites rather than popular objective of draining attention. It has web, desktop and mobile versions for creating Anki (flash) cards with spaced repitition tracking. I am in the process of adopting it for my learning. Not yet successful in integrating it fully, will blog more about my experience in future.

### [Polar App](https://getpolarized.io/)
Related learning tool I found is Polar. 
> "A powerful document manager for web pages, textbooks, PDFs, and anything you want to read. Supports tagging, annotation, highlighting and keeps track of your reading progress."

It doesn't have a firefox extension yet. But it allows creating anki cards that can be synced to Anki app from web highlights. This helps in creating a learning expereince like the quantum computing blog for any document.

## Philosophy

### [Would aliens understand lambda calculus?](http://tomasp.net/blog/2018/alien-lambda-calculus/)
Platonism vs Aristotelianism is an age old debate in philosophy. Professor Balaji (a teacher of mine) had a strong notion that the current mathematics we have is strongly influenced by our spatio-visual sense. Stumbled upon the above post which makes similar claims. It claims that certain cognitive priors are necessary to converge upon ideas which some consider as universal. 

I don't know enough to lean on any side of the debate heavily. But my intution lies with universality/platonism of physics, mathematics and computatability. I think even if Alien's use some other metaphors to arrive at Lambda Calculus, the underlying notion of universal computability (if correct) will be the same.

### [New AI Strategy Mimics How Brains Learn to Smell](https://www.quantamagazine.org/new-ai-strategy-mimics-how-brains-learn-to-smell-20180918/)
I am now exploring search systems over neural net generated representation (vector spaces). This generally involves approximate methods such as Locality senstive Hashing. The method described in this post was interestingly derived from the sense of smell of fruit-flies. This lends some weight top the notion that our cognitive reliance on certain senses (vision) makes some ideas intutive, but exploring outside it can expand our horizons. (Purely my speculation to be taken with a grain of salt.)

## Programming Languages

### [Type State Pattern](http://cliffle.com/blog/rust-typestate/)
To eliminate errors make them impossible in runtime is a mantra I stand behind. Programming Patterns that are finally entering mainstream (after stewing in the academic functional world) such as Optional are moving errors to compile time. Among the patterns, type state caught my eye. Using rust's borrow checker and other langauge features allows one to build compile time state machines. They can be as simple as allowing the compiler to disallow methods such as read on file references that are closed. Or it can be taken one step beyond to write a full blown state machines that track the current state in compile time. ie Say you have an API that needs a handshake to be performed before sending, you can ensure in compile time that the "send" method can be called only after "handshake" is called. How awesome is that.


### [Why Monads matter?](https://cdsmith.wordpress.com/2012/04/18/why-do-monads-matter/)
This article explains what the usally hyped functional programming concept of monad solves for a imperative programmer. I have not dived deeply into any functional language yet. Seeing how even weakly adopted fucntional programming concepts such as Optionals (algebraic data types) and Optional Chaining (which is a monad) makes me question what is the cost with which the programming world is ignoring Functional paradigmn.
Are the functional languages difficult to learn, or is it exposure bias towards imperative languages? Or do we need the functional abstractions to be put in better terms for people to grok them? Only time will tell.
