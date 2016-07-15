---
title: Probability without measure theory
layout: default
comments: true
---

# What does it mean to say \\(P(event) = something \\)

This blog post is an attempt to explain the following [tutorial](https://www.dropbox.com/s/zwio6k94ix40q1s/ItsOnlyAGame.pdf) to a more general audience. I gave that tutorial to explain some of my favorite ideas in the Shafer and Vovk book [Probability and Finance, It's only a Game!](http://www.amazon.com/Probability-Finance-Its-Only-Game/dp/0471402265/ref=sr_1_1?ie=UTF8&qid=1424136245&sr=8-1&keywords=probability+and+finance)

## Horse Gambling Games

Way before Probability Theory was its own field let alone a field with rigorous foundations, two fairly celebrated mathematicians Pascal and Fermat wanted to win a ton of money betting on horses. Before doing so they of course had to first check whether horse gambling was a fair game. This meant they had to first define what it means for a game to be fair. The definition they came up with involves two parties which we'll call A and B involved in a zero sum game.

* If A pays x$
* And B pays x$
* The winner gets paid 2x$

This definition seems fairly intuitive because we can actually attribute a meaning to the title \\(P(event) = something \\) by claiming that:



>P(event) = how much money you're willing to spend on a game where you could win 1$.


## Mathematization of Probability Theory

The above definition is indeed intuitive but it hardly seems inline with what we'd imagine a mathematical definition of probability would look like.


Kolmogorov rigorously formalized probability theory using just 6 axioms; what was previously a subfield of mathematical physics became its own deep topic. I might need a whole other blog post on Kolmogorov's 6 axioms but I'll mention one small but interesting thing here. The sixth axiom uses what is called the axiom of choice. The axiom of choice is . For our purposes though it would be interesting to explore the possibility of a different foundation to probability theory in games instead of measure theory.

## Sequential Learning

Von Mises was the first to propose that probability theory could find its foundation in games.

* Given an observed bit string 001110
* What is the probability that the next bit observed is a 1 so that sequence becomes 0011101?

The question is meaningful becomes if the length of the string is sufficiently large then we expect that looking at a subset of the strings will give us a statistical estimate of the frequency of each bit.

Fortunately we also have a method of quantifying how random a length \\(n \\) bitstring is: Kolmogorov Complexity!

## A brief fugue into Kolmogorov Complexity

Suppose you're given two strings:

* \\(A = 01 01 01 01 01 01 01 \\) 
* \\(B = 00 10 01 00 10 11 11 \\)

My question is which string looks more random? Well one way to approach this is to see if a string has many repetitions and we notice indeed that \\(A \\) is simply 01 repeated 7 times so it's essentially the same message appended to itself 7 times. \\(B \\) on the other hand seems to lack such a clear looking pattern so we can claim that \\(B \\) is more random than \\(A \\). 

This is exactly the notion that Kolmogorov complexity captures! Unfortunately, it is also impossible to determine the Kolmogorov complexity of a random string! Whaaaat? Kolmogorov complexity belongs to a class of problems called undecidable which means that it can be reduced to the halting problem.

 If there's enough interest in the comments I can write a whole other blog post about Kolmogorov complexity and the halting problem but to give you an intuition of what the halting problem is all about: just think about how you'd know in a finite amount of time if something is going to run forever. Turns out computer science has answers to lots of philosophical questions.

## The weak law of large numbers

The weak law of large numbers is generally covered in undergraduate statistics class using measure theoretic tools even though measure theory is outside the scope of many undergraduate programs. But it's worth going over the "classical" proof to appreciate the game theoretic proof.

We will make the typical assumption that we are observing \\(n \\) random variables \\(X\_1 \dots X\_n \\) are i.i.d variables with mean \\(\mu \\) and variance \\(\sigma^2 \\). 

The i.i.d assumption part stands for independent and identically ditributed, this assumption is an important one because without it learning seems quite impossible. In the most degenerate case if every random variable depends on every other one and each one has its own distribution it is impossible to generalize any knowledge about the points. 

Let us define \\(A\_n = \frac{X_1 + \dots + X_n}{n} \\) to be the average value of the random variables. Then the expected value of \\(A\_n \\) is \\(E[A\_n] = \frac{n \mu}{n} = \mu \\). Similarly \\(Var[A\_n] = \frac{n \sigma^2}{n^2} = \frac{\sigma^2}{n}   \\).

The proof of the weak law of large numbers is then concluded using Chebyshev's inequality which is simply a formalization of the intuition that rare things happen rarely.

\\(P(\|A\_n - \mu \| \geq \epsilon) \leq Var[A\_n]/ \sigma^2 = \frac{\sigma^2}{n \epsilon^2}  \\)


## Bounded Fair Coin Game

Now we will instead show how to prove the weak law of large numbers using games instead. We will setup a game between two parties that we will call the skeptic and nature.

* \\(K\_i \\) will be the skeptic capital at time \\(i \\)
* \\(M\_n \\) is the amount of tickets that the skeptic purchases
* \\(x\_n \\) is the value of a ticket determined by nature

Now we can finally introduce the game:

* \\(K\_0 = 1 \\)
* For \\(n = 1,2 \dots \\):
	* Skeptic announces \\(M\_n \in R \\)
	* Reality announces \\(x\_n \in \{0,1 \} \\)
	* \\(K\_n = K\_{n - 1} + M\_{n}x\_{n} \\)

What we will prove is that there exists a winning strategy for the skeptic. But first we will use a favorite trick employed by philosophers and first define what we mean by winning. The relationship with the weak law of large numbers will come out soon.

We claim that the skeptic wins \\(K\_n > 0 \\) for all \\(n \\) we call this condition the no-bankruptcy condition. And if one two things happen either:

* \\(\lim_{n \rightarrow \infty} \sum\_{i = 1}^{n}x\_i = 0 \\) Or

* \\(\lim_{ \rightarrow \infty} K_n = \infty\\)

Everytime an author proposes new definitions, I find it helpful to understand what the equations mean in plain english. 

The condition after the "or" states that the skeptic wins if he becomes infinitely rich and I'm sure we can all agree that the constitutes a reasonable definition of winning. 

The first needs some more clarification it states that if the outcome of the game is truly random then the skeptic wins, what is meant here is that if nature plays a completely arbitrary strategy then no winning strategy exists. Which is another way of saying that any given skeptic can't possibly play better than any other skeptic in retrospect. 

Note how I use the term arbitrarily instead of the term randomly, this distinction seems pendantic but is quite important. Since randomly means according to some distribution while arbitrarily means there is absolutely no limitation to how a random variable may act. 

## Proving the bounded fair coin game

Now for the proof: If the skeptic bets an infinitely small amount \\(\epsilon \\) on heads then nature will be forced to not play heads often or else the skeptic will become infinitely rich. Therefore nature will start playing tails, when that happens the skeptic starts playing tails. Essentially this almost silly example provides a proof of concept for machine learning: If nature's strategy is not completely arbitrary then nature's strategy has an underlying strategy that can be learnt from data! 

> TLDR: If nature's strategy is not completely uniform, meaning if nature does not play heads as often as tails then the skeptic can learn nature's strategy and become infinitely rich by playing an infinite number of rounds.

And that's the proof of the weak law of large numbers! We can think of nature as an entity trying to minimize rare events: that's why there aren't that many infinitely rich folks out there! (Actually the real proof is slightly more complicated and is covered in my original [tutorial](https://www.dropbox.com/s/zwio6k94ix40q1s/ItsOnlyAGame.pdf)

Not only is this a completely valid proof of the weak law of large numbers it also does not make the i.i.d assumption so it also implies the measure theoretic result!

\\(A \wedge B \rightarrow A \\)

## Epilogue

The efficient market hypothesis is an economic concept that states that it is impossible to consistently achieve better returns than the market. Did we also prove this statement as a corollary?
