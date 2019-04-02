---
title:  Function Currying, Composition in Redux Middleware
categories: functional-programming
tags: [Javascript, Redux, Functional Programming]
---
I am new to functional programming paradigm, though I do understand something about closures ,pure functions and have used some programming structures related to functional concepts like map, reduce, blocks in my iOS applications at work, I don’t have much experience with functional paradigm.

I started learning about react js, and eventually ended up learning about Redux. I would assume you to have basic knowledge about redux , if not read about it here. It is very well documented, and the whole api is small, If you are feeling adventurous read the redux source code, it is a few hundred lines.

Redux seems to be a more elegant implementation of Flux methodology without some components of flux like multiple stores communication via a dispatcher which is made redundant in redux pattern.

So as I was playing with redux by implementing a small application mentioned in this tutorial , I came across something called middlewares. These middleware intercept the actions to store and do some extra processing on it. I couldn’t wrap my head around how a middleware for handling Promises mentioned in that post worked.

{% highlight js %}
export default function promiseMiddleware() {
  return next => action => {
    const { promise, type, ...rest } = action;

    if (!promise) return next(action);

    const SUCCESS = type;
    const REQUEST = type + '_REQUEST';
    const FAILURE = type + '_FAILURE';
    next({ ...rest, type: REQUEST });
    return promise
      .then(res => {
        next({ ...rest, res, type: SUCCESS });

        return true;
      })
      .catch(error => {
        next({ ...rest, error, type: FAILURE });

        // Another benefit is being able to log all failures here
        console.log(error);
      return false;
      });
   };
}
{% endhighlight %}

It seemed to use functional magic which somehow allowed waiting for a promise to resolve and then dispatch the action or call next middleware.
S
o I was wondering how that worked and came across this excellent post titled ["Understanding Redux Middleware"](https://medium.com/@meagle/understanding-87566abcfb7a#.l7hsexyp7). I encourage you to check it out here if you haven’t already. This post is meant to clarify some things in it a bit further.
From that article I came to understand that middleware functions got composed in the following fashion

    Middleware1(Middleware2(…))

Then by chance I was reading through documentation of redux-logger middleware which said that for it to log state , actions properly from it has to be passed as parameter after any asynchronous middleware. So from what I read in redux source for applyMiddleware I gathered that logger middleware will be a parameter for Async middleware for it to log correctly,
Assume we do this , then

    applyMiddleware(PromiseMiddleware, LoggerMiddleware)

will compose them in this order

    PromiseMiddleware(LoggerMiddleware)

This seemed to make less sense as I wrongly thought that promise middleware will wait for LoggerMiddeware to process and then execute.


But after meditating on the redux source code ,creating curried functions and composing them , I got it.
The actual execution order of middleware when dispatch action occurs, starts from PromiseMiddleware, which resolves the promise and only then calls the LoggerMiddleware.

This is because LoggerMiddleware is a curried function , so it doesn't return any value and it is simply a function that is passed to Promisemiddleware. The Promisemiddleware takes up the action, resolves it, and inside "then" of promise calls the LoggerMiddleware using

    next({ ...rest, res, type: SUCCESS });

and hence passes the action to LoggerMiddleware Function. The PromiseMiddleware can refer to the next function inside it using the properly named param "next".
Now lets make some curried functions with asynchronous operations and uncurry them with parameters . Type these in js console
We are first creating a curried function that takes another function as input and also some params.

{% highlight js %}
var asyncFunction = nextFunction => params => window.setTimeout(
    function() {
      alert("In Async Callback");
      nextFunction(params);
 }, 1000);
{% endhighlight %}

This is similar to the promise middleware. asyncFunction takes in parameter a function called nextFunction. From the signature of nextFunction(params) used inside , we can get it that it simply takes a object.
Now let us create a function to pass into async

{% highlight js %}
var alertFunction = parameters => alert(parameter);
{% endhighlight %}


alertFunction simply alerts the parameter passed to it.
COMPOSING Alert and asyncFunction manually, and calling the result of composition

{% highlight js %}
var composedFunction = asyncFunction(alertFunction);
composedFuntion(1);
{% endhighlight %}


Output
    Alert:- In Async Callback
    Alert:- 1

VOILA! Our alertFunction executes inside the async callback
To clarify replacing the nextFunction with body of alertFunction

{% highlight js %}
function params => window.setTimeout(function() {
   alert("In Async Handler");
   // nextFunction(params) becomes
   alert(params);
 }, 1000)
{% endhighlight %}

I couldn't grok async code in middleware because I was making similar mistake as in thinking that as alertFunction is innermost function in composition and so its body would execute first.But in actuality it doesn’t evaluate to value and hence the order of execution starts from outermost function .

This seems trivial after seeing the above example but it wrecked my understanding of middleware code.
if G is a function and F is higher order function , ie F(someInputFunction) is also a function , then when you "uncurry" by calling F(G)(x) the evaluation begins from operations defined inside/ to perform F, and operations defined inside/to perform G may or may not be used by F.

So we can wrapping asynchronous operations in a chain of composed functions, define them in seemingly synchronous way. And I think this is how Promises are actually implemented, will have to read about that later.

Anyway this really excites me, how mind bending functional jui jutsu can accomplish a lot with less code. Will post more when I learn more..
Eager to hear your experience in learning functional programming inception.

Reposted from [medium.com](https://medium.com/@sai_prasanna/order-of-execution-in-function-currying-composition-in-context-of-asynchronous-operation-722575cb382c#.4y6l1uttu)
