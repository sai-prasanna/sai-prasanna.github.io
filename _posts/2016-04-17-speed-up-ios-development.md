---
layout: post
title:  Speed up iOS dev using XCode Injection Plugin
date:   2016-04-23 23:55:00
categories: ios
tags:  mobile ios-development
---

The most boring part of any development is waiting for your project to compile.
And if you have done iOS development, you know how much time is wasted for XCode to recompile
the project. And even if compile time is less, you have to follow a bunch of taps, long presses 
etc to get to the desired app state before even testing your changes.

If you have tried react native you would have gone green with envy for the developers using it,
because of auto refreshing (hot reloading) of code as it is saved in the editor. Now you can enjoy hot reloading and 
refreshing in ordinary swift/obj c code using [Injection for XCode](http://injectionforxcode.com/).

<iframe src="https://player.vimeo.com/video/50137444" width="640" height="366" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

As you change your code , you can inject the new class definition using this XCode plugin. 
It recompiles just changed file, and injects it into the live running app.
The great thing is it works for real device as well as  Simulator.

###Set up


  1. Install [Alcatraz](http://alcatraz.io/) package manager for XCode . Alcatraz allows you to install and remove XCode plugins hazzle free
  2. Open using Alcatraz with  package manager option in projects menu. 
  3. Search for injection plugin, and install it. Restart XCode after installations
  4. To make it work in real device you need to click on *Product -> Injection Plugin -> Patch Project* for Injection. It will add couple of lines to 
     your main.m of your project. If it is a swift project just create a empty main.m and do the above.

###Inject Code


  1. Run your project, make some changes to the code in a file, press ^ + = . 
  2. Your changed code in that file will get compiled and injected into the app live.
  3. Now you can simply have to somehow make your program create new object of the changed class to see the changes. For example, tap back button and then again go the view.
  4. There are few limitations on what can be injected, refer the Injection for XCode's [github project](https://github.com/johnno1962/injectionforxcode). And a small limitation currently is it wont work if you have more than 128 source files in your project due to a XCode limitation. Follow this and other issues in github issue tracker.
  5. You can also set it up to automatically inject changes by enabling File Watcher in *Product-> Injection Plugin -> Tunable App Parameters* 
  6. If you want it to make changes visible as you inject the changes in you have to modify your normal code. You have to  listen for callbacks after injection , and reload the view or do something else.Read the [instructions](https://github.com/johnno1962/injectionforxcode#callbacks-in-your-code).


This plugin will add a new folder to your project which you can add to .gitignore to avoid source control.

It is great that the developer has open sourced it. To know how it does its magic see [here](https://github.com/johnno1962/injectionforxcode#how-it-works)
The author has released it under "nagware" license, where he requests you to pay after using it for two weeks.

