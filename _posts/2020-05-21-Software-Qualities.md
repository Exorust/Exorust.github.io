---
layout: post
title: "Fundamental Software Qualities"
description: "What qualities are essential to building a great software?"
category: articles
comments: true
tags: [Software, Engineering]
---

After my first couple of projects, I realized inadvertently, I was making certain tradeoffs. Certain patterns started to emerge. So, when I read the book, [Seriously Good Software](https://www.amazon.com/Seriously-Good-Software-works-survives/dp/1617296295) I knew I had to write about it.

As with all engineered things, there are fundamental qualitiess that comprise a good software product. Things that define the product.

And at times, while building a project the developer is pulled in many directions most of which require some kind of trade off. Take building an airplane. There are multiple tradeoffs involved, should it be faster or more fuel efficient? Should it carry more passengers or more cargo?

This is my list of software qualities

### 1. Functional Correctness
 
####  *Does the program do what it says?*

For a water bottle to have functional correctness, it needs to store water without leaking and allow the user to drink water. Functional correctness is easiest to ensure with a precise functional spec. As long as you define your input & output clearly, you can ensure functional correctness. Much too often details will be discovered during the coding process, instead of before while writing the spec. 

If you think about it functional correctness can be seen as a user facing quality, or an external quality.

### 2. Robustness

####  *What happens to the program when something not expected happens?*

Much too often robustness and correctness are lumped together. But robustness is our way of 'fighting' Murphy's law, how we ensure safeguards to prevent the breakdown of our software. Maybe you expected dates in dd/mm/yy format but the user gave you mm/dd/yy. It needs to fight both malicious intents (hacking) and unintentional mistakes.

Robust software usually should follow Postel's principle, used in the making of TCP: "Be conservative in what you do, be liberal in what you accept from others." In simpler words, make sure you accept a wide variety of inputs, but ensure that your outputs are rigidly specified.

### 3. Usability

####  *Can the user easily use your program?*

This is a key quality to a good product, software or otherwise. From Apple to Ikea to many others the pursuit of usability is most essential. Software usability is embedded with UI (User Interface) and UX (User Experience), with both having their own set of ideas and principles. Keeping usability in mind ensures its quality.

### 4. Efficiency

####  *How fast is it? How little memory does it use?*

A key part of algorithms lies in time and space complexity. Many large-scale programs like databases or distributed systems require specific thought on how efficient it needs to be. Adding efficiency requirements while making design specifications will ensure that one does not become blase about efficiency tradeoffs.

Efficiency is not truly user-facing, the user does notice the execution time, but can he see the bandwidth comsumption? Efficiency needs to have a priority in cases of:
- Performance-critical Applications: Operating systems or device drivers need to ensure performance.
- Large-scale Applications: Netflix, Amazon, and such websites need to ensure each small component does not introduce lag in other components.
- Applications that have exceptionally poor efficiency: In cases of existing applications that are sluggish, newer features should be added with efficiency as a key priority.

### 5. Readability

####  *Can the next dev actually understand what's going on?*

More often than not, readability is not given a second thought. Yet as always, the lifespan of your software will be longer than the time it took you to write it. Which means at some time you will go back to this software and try to fix something or add something in which case you or the new dev needs to know what exactly was done here and why.

A simple enough fix would be to maintain documentation and follow a standard coding guideline for the language being used.

### 6. Reusability

####  *Do I need to write the same thing again? Or is it abstracted already?*

Functions and Objects were given to us so that we can abstract certain things for later use. While designing, ensuring similar aspects can be abstracted will allow the next dev down the line to easily pick up from where you left off! 

Its that simple! [And also that hard.] Ensuring a good and reusable design is not obvious but must be kept in mind while designing and coding.

### 7. Testability

####  *Can we write a test, or is it a jumble of tightly coupled things?*

Testable code usually is one that was designed to be reusable, and contained API's abstracting the internal functionality. We've probably never come across something that cannot be tested, but you can always make it more testable. We've all seen unit tests that doesn't really test anything, and so the quest to make our code testable isn't really a joke.

Remember a single test done by the dev prevents bugs later caught by the tester, or if we're really unlucky bugs caught by the user himself. 

### 8. Maintanability

####  *Someday, very far away, someone will be maintaining the code you wrote. Will he curse at the original dev?*

Well the truth remains that code lasts longer than we expect. Tell every dev who wrote Windows NT that the same kernel would be used 25 years later and they would have scoffed, yet the reality is that the same kernel powers every Windows OS since then. Windows 10 reboots to update because the kernel was designed that way (Not saying that its a bad design, it is what it is). 
