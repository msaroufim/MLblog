---
title: Quantum Computers Can Simulate Classical Computers
layout: default
---

# Simulating a Classical Computer Using a Quantum Computer

## An easier way to think of quantum computers 

I was very fortunate my last quarter as a graduate student at UCSD to have helped organize a quantum computing seminar. I was strongly influenced by Aaronson's excellent book [Quantum Computing Since Democritus](http://www.amazon.com/Quantum-Computing-since-Democritus-Aaronson/dp/0521199565) where Aaronson's makes a strong point that Quantum Computing is easy if you abstract away the physics.

That may sound controversial but it really isn't, do algorithmists think of the electromagnetic waves storing bits on disk when they write pseudocode. Theorists are generally unaware of how computers work and more applied computer scientists are similarly unaware of how electronics work. Abstraction is powerful and allows one to focus on problems that exist at different conceptual levels. Why should quantum computing be any different? The approach that makes the most sense is to take it as a given that physicists will provide us with a basic set of quantum logic gates whether they are spinning or freezing or backflipping elementary particles in various gases is irrelevant to us. We can make more progress if we work with quantum logic gates as opposed to quantum physics.

## What is a Quantum Computer?

I'll assume that my reader has no knowledge of quantum computing and attempt to draw an analogy with a more well known device: the classical computer.

### Boolean logic fugue
At the most abstract level, a computer is a function \\(f \\) of \\(n \\) bits that returns either 0 or 1.

\\(f(b_1, \dots , b_n) = \{0,1 \} \\)

Any binary function on \\(n \\) bits can be computed using combinations of the well known "AND", "OR" and "NOT" gates or just a "NAND". The fantastic book The Elements of Computing Systems by Nisan and Schocken shows how it is possible to start with a "NAND" gate and move on to assemblers, compilers, virtual machines and finally tetris.


I leave it as an exercise to the reader to see how a "NAND" gate can be implemented using the basic "AND", "OR" and "NOT" gates. The hardware implementation of "AND", "OR" gates are easy if one remembers the distinction between in-series and in-parallel circuits.

<!-- 2- I will sketch a proof by induction which shows why you can write any binary function $$f$$ on \\(n \\) bits as a circuit consisting solely of "NAND" gates.

* Base Case (two bit function: \\(n =2 \\)): A single gate circuit recieves two inputs whose combination takes a total of 4 values. For each of the four rows the output can be one of two values. So the total number of possible truth table configurations for a two bit function is $$2^4$$. It's a tedious but easy exercise to find a NAND circuit corresponding to each one of those configurations.
* Inductive Step: Assume you can construct a circuit consisting solely of "NAND" gates for any function $$f$$ on $$n$$ bits. Any $$n+1$$ bit function   -->


If you've ever wondered why binary is the base of choice for computers the above is a strong argument for that choice, the other being that it is simple to represent one of two states 0 or 1 using a ground or 5V.

### Back to Quantum Computers

A quantum computer is then a function \\(f \\) of \\(n \\) quantum bits that when measured (think of this as returning for now) returns either 0 or 1.  



## Quantum Computers are at least as powerful as Classical Computers

This is a neat result that I proved in the introductory lecture of the seminar, of course this result is not novel in any way: I'm not sure if it was even formally stated in a paper or just taken as a known trivial result but regardless it's a good exercise to prove your first result about quantum computers. 

### Proving that quantum computers are at least as powerful as classical computers using truth tables

Let's take a look at the truth table of a NAND gate where the first two columns represent the two inputs and the last colum presents the output.


<!-- <img src="http://www.zseries.in/electronics%20lab/ics/pictures/truth%20table%20of%20ic7400.png" alt="Drawing" style="width: 100px; height="50px" "/> -->



|IN1|IN2|OUT        |
|:---:|:---:|:-----------:|
|0  |0  |1          |
|0  |1  |1          |
|1  |0  |1          |
|1  |1  |0          |


Now let's take a look at the truth table for a basic quantum gate the Toffoli gate. A Toffoli gate takes in three inputs and produces three outputs.


|IN1  |IN2  |IN3  |OUT1  |OUT2  |OUT3  |
|:---:|:---:|:---:|:----:|:----:|:----:|
|0    |0    |0    |0     |0     |0     | 
|0	  |0    |1    |0     |0     |1     |
|0	  |1    |0    |0     |1     |0     |
|0	  |1    |1    |0     |1     |1     |
|1	  |0    |0    |1     |0     |0     |
|1	  |0    |1    |1     |0     |1     |
|1	  |1    |0    |1     |1     |1     |
|1	  |1    |1    |1     |1     |0     |



Now inspect the third output in the rows for which the third input is 1. Do those rows look familiar? They should! Because they correspond exactly to the NAND gate! So we can fix the third input bit of a Toffoli gate to 1 to simulate a NAND gate. Therefore we can simulate any NAND circuit or any boolean circuit using Toffoli gates.

## Are computers more powerful if they are allowed to make coin flips?

The short answer is nobody knows for sure but it is hypothesized that it indeed is. This seems counter-intuitive, nobody would expect that two-face could make superior decisions by flipping a coin so why would the same not be true for computers. 


### Polynomial identity testing: Case study for randomized algorithms

Suppose you were given two large polynomials \\(P_1 \\) and \\(P_2 \\) with many variables each. A natural question is: is \\(P_1 \equiv P_2\\)? There is no known deterministic algorithm for it but there is an incredibly simple randomized one!

* While you are not sure if $$P_1 \equiv P_2 $$
* Pick a point uniformily at random \\(x \in \\) Domain
* Evaluate \\(P_1(x) - P_2(x) \\)
	* If \\(P_1(x) - P_2(x) \\) == 0
		* continue
	* Else
		* Return: \\(P_1 ! \equiv P_2 \\)

Why does this work? Well, if for any \\(x\\), \\(P_1(x) != P_2(x)\\) then they are not equivalent. In addition, the more times we iterate over the loop the more confident we are that the two polynomials are equivalent!

## Simulating a coin flip using a quantum computer

First we're going to have to define what a quantum bit is. We represent an arbitrary quantum bit \\(a\\) as \\( \| a > = \alpha \| 0 > + \beta \| 1 > \\)

The above definition is read as a quantum bit \\(a\\) is in state 0 with probability \\(\alpha^2\\) and in state 1 with probability \\(\beta^2\\). When people talk about how a quantum bit can be both 1 and 0 at the same time they are refering to the above expression yet they are incorrectly interpreting it. There is nothing weird, magical or massively paralell about a distribution over two variables. Next we note that any gate whether its quantum or not can be represented algebraically. 

e.g: \\(A \wedge B = A . B \\)

We will use, the basic quantum Hadamard Gate. \\(H = \frac{1}{\sqrt{2}} \\) \\(\begin{bmatrix}1 & 1\\) \\(1 & -1 \end{bmatrix}\\). We then apply \\(H \|0> = \frac{1}{\sqrt{2}}\|0> + \frac{1}{\sqrt{2}}\|1> \\) which when measured gives us either 0 or 1 with probability 1/2 and we're done. 

This doesn't seem like a lot but it is quite significant! Think of how you'd simulate a uniform distribution over \\(n \\) variables using a uniform distribution over 2 variables. Also related, I hear simulating a fair coin using an unbiased coin is a popular interview question. Another natural question to think about is then how would you simulate a biased coin using an unbiased one?

## Epilogue

Good news is that quantum computers could probably run your favorite videogame. This is however not the most interesting property of quantum computers, if there is any interest then I can probably have some followup posts on Grover's search algorithm and Shor's factoring algorithm. Although those are arguably the most well known quantum algorithms there are many results that are incredibly funky and I'd recommend you check out the [ topics](http://www.cse.ucsd.edu/theory_reading_group/) we had in theory reading group at UCSD.  

 The two big open questions are perhaps: can quantum computers actually be built? If they can, can they solve more problems than classical computers? The complexity theory community seems to think so. As Aaronson would say: all possibilities are equally intriguing since either we learn some pretty fundamental limitations of phyics or we get swanky new quantum computers.

<!-- http://cseweb.ucsd.edu/~dasgupta/book/index.html>Chapter 10 -->
