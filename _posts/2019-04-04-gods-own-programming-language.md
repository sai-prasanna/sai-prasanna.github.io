---
title: God's own Programming Language
categories: programming
tags: [LISP, Programming Languages]
toc: true
toc_label: Contents
toc_icon: "yin-yang"
---

Found this interesting [blog post](https://twobithistory.org/2018/10/14/lisp.html) explores why many programmers hold a high regard for an ancient programming language which you might not have heard about or use daily.

```
For God wrote in Lisp code
When he filled the leaves with green.
The fractal flowers and recursive roots:
The most lovely hack I’ve seen.
And when I ponder snowflakes,
never finding two the same,
I know God likes a language
with its own four-letter name.
```
{: style="text-align: center;"}

*Poem from [twobithistory.org](https://twobithistory.org/2018/10/14/lisp.html)*
{: style="color:gray; font-size: 80%; text-align: center;"}

![XKCD LISP - We think God created the world in LISP, but he merely hacked it in Perl.](https://imgs.xkcd.com/comics/lisp.jpg)
*[XKCD Comics](https://xkcd.com/224/)*
{: style="color:gray; font-size: 80%; text-align: center;"}

Also a good read are the [posts on LISP](http://www.paulgraham.com/lisp.html) by Paul Graham of YCombinator/HackerNews fame. 

## How to attain Nirvana with the God's own language?

To attain programming nirvana - Start reading the SICP Book.

SICP (Structure and Interpretation of Computer Programs) is a introduction to computer science book. It can change how you view even simple constructs we use for code (like loops, if, etc). A book that will teach timeless concepts in programming which you would never come across easily. I started reading it ages ago, haven't completed it , the first few chapters themselves were sufficiently mind blowing.

**[Original book](https://web.mit.edu/alexmv/6.037/sicp.pdf)** 

**[A modern interactive version](https://xuanji.appspot.com/isicp/1-1-elements.html)** Now you can run the examples of SICP book God's own language in the browser with godforsaken javascript. And laugh morosely on the irony of running LISP in a half baked language (javascript) which was inspired from it. 

**[A Distilled version with illustrations](http://www.sicpdistilled.com/)** - Smaller, condensed version.


> To use an analogy, if SICP were about automobiles, it would be for the person who wants to know how cars work, how they are built, and how one might design fuel-efficient, safe, reliable vehicles for the 21st century. The people who hate SICP are the ones who just want to know how to drive their car on the highway, just like everyone else. **- Peter Norvig on SICP**


### (How to Write a (Lisp) Interpreter (in Python))

Follow this [guide](http://www.norvig.com/lispy.html) to implement your own LISP Interpreter in an hundred lines of python.
You might think, "Is he crazy to ask a language beginner to implement the interpreter before learning it?"
Answer is while I am partly crazy LISP is not, it has the simplest structure of all programming languages. It's just lists duh! (LiSt Processing).

## LISP for AI
You can practise LISP for Artificial Intelligence algorithms with Peter Norvig's book on ["Paradigms of Artificial Intelligence Programming"](https://github.com/norvig/paip-lisp).


## Say you don't want Nirvana, but something more pragmatic

You can learn Clojure to use God's Language to do some real world wizardry. Clojure is a form of LISP which is modern, functional and runs on JVM. [Brave Clojure](https://braveclojure.com) is one of the best sources out there for Clojure. For front end development/nodejs there is clojure-script which compiles down to javascript.

> Learning Clojure is the best way you can improve as a programmer because it introduces you to powerful concepts implemented in a simple, cohesive, and practical language. You learn Clojure here. Therefore, Brave Clojure is your very best friend when it comes to programming.” And lo, the syllogism was born!

![XKCD comic - LISP is passed down generation after generation as elegant weapons for a more Civilized age.](https://imgs.xkcd.com/comics/lisp_cycles.png)
*[XKCD Comics](https://xkcd.com/297/)*
{: style="color:gray; font-size: 80%; text-align: center;"}

## A Note and a Zen Koan

Use any language that solves your problem and learn about others which have different paradigms conceptually like LISP, etc when you find the time. It a enjoyable exercise if you are curious about digging deeply into what makes computers tick.

As [Master Foo says](http://catb.org/jargon/html/koans.html) says,

> Master Foo once said to a visiting programmer: “There is more Unix-nature in one line of shell script than 
> there is in ten thousand lines of C.”
>
> The programmer, who was very proud of his mastery of C, said: “How can this be? C is the language in
> which the very kernel of Unix is implemented!”
>
> Master Foo replied: “That is so. Nevertheless, there is more Unix-nature in one line of shell script 
> than there is in ten thousand lines of C.”
>
> The programmer grew distressed. “But through the C language we experience the enlightenment of the Patriarch Ritchie! 
> We become as one with the operating system and the machine, reaping matchless performance!”
>
> Master Foo replied: “All that you say is true. But there is still more Unix-nature in one line of shell script
> than there is in ten thousand lines of C.”
>
> The programmer scoffed at Master Foo and rose to depart. But Master Foo nodded to his student Nubi, 
> who wrote a line of shell script on a nearby whiteboard, and said: “Master programmer, consider this pipeline. 
> Implemented in pure C, would it not span ten thousand lines?”
>
> The programmer muttered through his beard, contemplating what Nubi had written. Finally he agreed that it was so.
>
> “And how many hours would you require to implement and debug that C program?” asked Nubi.
>
> “Many,” admitted the visiting programmer. “But only a fool would spend the time to do that when so many more worthy tasks await him.”
>
> “And who better understands the Unix-nature?” Master Foo asked. “Is it he who writes the ten thousand 
> lines, or he who, perceiving the emptiness of the task, gains merit by not coding?”
>
> Upon hearing this, the programmer was enlightened.

For more funny hacker koans, visit [here](http://thecodelesscode.com/contents) and [here](http://catb.org/esr/writings/unix-koans/introduction.html).

I am currently learning emacs-lisp for I have become a convert/evangelizer of the [Church](https://stallman.org/saint.html) of [Emacs](https://www.gnu.org/s/emacs/) on a Starship called [Spacemacs](http://spacemacs.org/). But that's a post/sermon (;P) for another time.
