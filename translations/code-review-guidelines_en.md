Title: Code Review Guidelines
Category: Programming
Tags: code review,clean code,guidelines,reprinting
Authors: Philipp Hauer

> Origin Url: [Philipp Hauer's Blog][from]

Code reviews are a powerful mean to improve the code quality, establish best practices and to spread knowledge. However, code reviews can come to nothing or harm the interpersonal relations when they are done wrong. Hence, it’s important to pay attention to the human aspects of code reviews. Code reviews require a certain mindset and phrasing techniques in order to be successful. This post provides both the author and the reviewer with a compass for navigating through a constructive, effective and respectful code review.
<div style="text-align:center">![featured-image-large](./featured-image-large.png)</div>

# Code Reviews Guidelines For the Author 
For you, as the author (or “developer”, “submitter”), it’s important to have an **open and humble mindset** about the feedback you will receive.

## Be Humble 


<div style="text-align:center">![Alt text](./author-mistakes.jpg  "To err is human. Everybody makes mistakes")<p>To err is human. Everybody makes mistakes</p></div>

We are humans after all. And humans make mistakes. That’s normal. So as long as software will be written by humans, it will contain mistakes.

This doesn’t mean that you should code carelessly or stop writing tests. But this mindset will take away the fear of mistakes and create an atmosphere where making mistakes is accepted and admitting them is desired. This, in turn, is important for criticism during a code review to be accepted. Otherwise, you may end up in endless justifications and rejections because mistakes may be seen as something forbidden and have to be kept hidden. This prevents the required openness for feedback.
<div style="text-align:center">![Alt text](./cb60i-q8u5c.jpg "Making mistakes is accepted and admitting them is desired.")<p>Making mistakes is accepted and admitting them is desired.</p></div>


The key takeaway here is: **Be humble**. Mind that everybody’s code can be improved. You are not perfect. So you have to accept that you will make mistakes. It doesn’t matter how good you are, you can still learn and improve. Don’t consider yourself as infallible and don’t infer your professionalism and reliability as a software developer from infallibility and flawlessness. In fact, admitting mistakes shows that you are really professional, honest and after all a human being.

## You Are Not Your Code 
<span id="uanycode"></span>
> “Criticism is almost never personal in a professional software engineering environment — it’s usually just part of the process of making a better product”. Fitzpatrick, Collins-Sussman: [Debugging Teams][1], page 16

Repeat after me: You are not your code. Criticism on your code is not a criticism on you as a human. Don’t connect your self-worth with the code you write. You are still a valuable team member even if there are some flaws in your code.

In the end, programming is just a skill. It improves with training - and this improvement never stops.


## New Perspectives On Your Code 

Every developer has a different background, assumptions, knowledge, and experiences; and so does the reviewer of your code. It’s totally natural that they see your code differently than you do. Moreover, they are not so familiar with the domain or concrete functionality that kept you busy the last days. That’s great because this reveals code that was absolutely clear for you, but not for the reviewer.
```
// Reviewer: "When does this happen?" 
if (article.state == State.INACTIVE) { 
}
// Implicit knowledge here!
```
vs.
```
// Reviewer: "Ah, the state means out-of-stock"
boolean articleIsOutOfStock = article.state == State.INACTIVE;
if (articleIsOutOfStock) { 
}
// make knowledge explicit by using expressive names
```
So code reviews **reveal the implicit knowledge** that is not expressed in the code yet, because it appears natural for you. We are avoiding a tunnel vision.

But the best point here is: You don’t have to be angry with yourself as you often simply can’t see those issues. You only have one perspective. So just be thankful and embrace the opportunity to get a different perspective on your code. It’s so valuable.

## Exchange of Best Practices and Experiences

You and the reviewer are not only talking about your code - you are exchanging best practices and experiences. Code reviews are a great medium to establish and internalize good coding styles and best practices. And the exchange works in both directions. So consider code reviews as a valuable source of knowledge and an opportunity to learn.

# Code Reviews Guidelines For the Reviewer
For you, as the reviewer, it’s important to pay attention to the way you are **formulating your feedback**. The phrasing is extremely crucial for your feedback to be accepted.

## Use I-Messages 

> Right: “It’s hard for me to grasp what’s going on in this code.”
> 
> Wrong: “You are writing cryptic code.”

Always formulate your feedback from **your point of view** by expressing your **personal** thoughts, feelings, and impressions. Why? Because it’s hard for the author to argue against your personal feelings since they are subjective.

In contrast, You-Messages sound like an insinuation and an absolute statement. It’s an attack on the author. They will definitely lead to justifications, rejections and a defense stance. The author will not be thinking about how they can change, but rather how they can argue with you to show you that you are wrong. So the author will be less open for your feedback.

Using I-Messages is the most important feedback rule in general and is clearly not limited to code reviews.

## Criticize the Author’s Behavior, Not Their Attributes
> Right: “I believe that you should pay more attention to writing tests.”
> 
> Wrong: “You are sloppy when it comes to writing tests.”

Another general feedback tip is to criticize only the behavior of the author, not their attributes. Why? Attributes stick to a human and are really hard to change. That’s why that feedback often feels like an attack on the human being itself and will probably lead to resistance. The author will start to argue with you instead of thinking about how to improve the situation. Behavior, however, can be changed more easily. Criticism on the behavior is less likely to be perceived as a personal attack. The author will be more open for your feedback.

##Talk About the Code, Not the Coder 
> Right: “This code is requesting the service multiple times, which is inefficient.”
> 
> Wrong: “You’re requesting the service multiple times, which is inefficient.”

Take out the person in your feedback. Only talk about the code. Criticism on the code is much harder to take personally because you are simply talking about the code, an objective thing, and not the author. Again, this will improve the acceptance (as long as the author understands [that they is not their code][2]).

Moreover, this formulation prevents pointless discussions and finger pointing like: “No, it wasn’t me introducing this request logic. It was Dave who originally introduced this feature!”.

And finally, talking about the code supports the notion of [collective code ownership][3].

## Accept That There Are Different Solutions 

> Right: “I would always use fixed timestamps in tests for better reproducibility but in this simple test, using the current timestamp is also ok.”
> 
> Wrong: “I always use fixed timestamps in tests and you should too.”

You have to keep in mind that there are always different solutions to a problem. Most likely, you’ll have a favorite solution, but the author’s solution may also be valid. Don’t force your solution on the author if their solution is also fine.**Distinguish between common best practices and your personal taste**. Mind that your skepticism may just reflect your personal taste and not an objectively wrong code. **Make compromises and be pragmatic**.

This mindset should prevent you from being uncompromising, pedantic and from annoying the author, which in turn reduces their openness to further feedback and may harm your relationship.

## Don’t Jump in Front of Every Train 

Don’t be a pedant. Don’t criticize every single line of code. Again, this would annoy the author and reduce their openness to further feedback and harm your relationship. Instead, choose wisely the battles you are going to fight. Focus on the flaws and code smells that are most important to you.
I really like the metaphor used in [Debugging Teams][1] to emphasis this hint:
> “Every time a decision is made, it’s like a train coming through town — when you jump in front of the train to stop it you slow the train down and potentially annoy the engineer driving the train. A new train comes by every 15 minutes, and if you jump in front of every train, not only do you spend a lot of your time stopping trains, but eventually one of the engineers driving the train is going to get mad enough to run right over you. So, while it’s OK to jump in front of some trains, pick and choose the ones you want to stop to make sure you’re only stopping the trains that really matter.” Fitzpatrick, Collins-Sussman: Debugging Teams, page 72

## Praise 

Don’t forget that it’s totally fine to say: “Everything is good!”. No code changes is a valid outcome of a code review. Don’t feel forced to find something in the code.

And last but not least: Don’t forget to express your appreciation if you have reviewed good code. Praising doesn’t hurt you but will motivate the author and improve your relationship.

# TL;DR: The Code Review Cheatsheet 

## Rules For the Author 
For the author, it’s important to have an open and humble mindset about the feedback they will receive.

+ Be humble!
    - Mind that everybody’s code can be improved.
	- You are not perfect.
	- Accept that you will make mistakes.
	- No matter how you good you are, you can still learn and improve.
	- Don’t infer your professionalism and reliability as a software developer from infallibility and flawlessness.
+ You are not your code
	- Programming is just a skill. It improves with training – and this never stops.
	- Don’t connect your self-worth with the code you are writing.
+ Consider feedback as a valuable new perspective on your code
	- It reveals your implicit knowledge that is not expressed in the code yet, because it appears natural for you.
	- It avoids a tunnel vision.
+ Code reviews are a valuable source of best practices and experiences
+ Code reviews are a discussion, not a dictation. It’s fine to disagree, but you have to elaborate your reservations politely and be willing to make compromises.
+ Mind that finally, the reviewer wants the same as you: Creating high-quality software. You are on the same side.

## Rules For the Reviewer 
For the reviewer, it’s important to pay attention to the way they formulate the feedback. This is extremely crucial for your feedback to be accepted.

+ Use I-Messages:
	- Right: “It’s hard for me to grasp what’s going on in this code.”
	- Wrong: “You are writing cryptic code.”
+ Always criticize the behavior, not the attributes of the author.
	- Right: “I believe that you should pay more attention to writing tests.”
	- Wrong: “You are sloppy when it comes to writing tests.”
+ Talk about the code, not the coder.
	- Right: “This code is requesting the service multiple times, which is inefficient.”
	- Wrong: “You’re requesting the service multiple times, which is inefficient.”
+ Respect and trust the author
	- Nobody writes bad code on purpose.
	- The author wrote the code to the best of their knowledge and belief.
+ Mind the PIW-Rule of giving feedback
	- Perception - “For me, this method is too long.”
	- Impact - “This makes it hard for me to grasp the essential logic of this method.”
	- Wish - “I would extract the low-level-details into subroutines and give them expressive names.”
+ Accept that there are different solutions
	- Right: “I would do it in another way, but your solution is also fine.”
	- Wrong: “I always do it this way and you should too.”
	- Distinguish between common best practices and your personal taste.
	- Mind that your criticism may just reflect your personal taste and not an objectively wrong code.
	- Make compromises and be pragmatic.
+ Don’t jump in front of every train
	- Don’t be a pedant. Don’t criticize every single line in the code. This will annoy the author and reduce their openness to further feedback.
	- Focus on the flaws and code smells that are most important to you.
+ Ask questions instead of making statements.
	- Right: “What is the intention of this method?”
	- Wrong: “The intention of this method is unclear.”
+ Be humble! You are not perfect and you can also improve.
+ It’s fine to say: Everything is good!
+ Don’t forget to praise.
# Further Reading
I highly recommend the book [Debugging Teams][1] by Brian Fitzpatrick and Ben Collins-Sussman. Without exaggeration, this book inspired me.
[1]: https://www.amazon.com/gp/product/1491932058/ref=as_li_tl?imprToken=J0XagX3A.xDx6iMIXhtjjg&slotNum=0&ie=UTF8&camp=1789&creative=9325&creativeASIN=1491932058&linkCode=w61&tag=blogphilippha-20&linkId=11df23d70998637d042bc6a46a4e6d1f "Debugging Teams"
[2]: #uanycode
[3]: https://www.martinfowler.com/bliki/CodeOwnership.html "collective code ownership"
[from]:https://phauer.com/2018/code-review-guidelines/ "Code Review Guidelines"
