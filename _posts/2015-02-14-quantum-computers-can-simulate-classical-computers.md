---
title: Quantum Computers Can Simulate Classical Computers
layout: default
---

### Is Quantum Computing Hard to Understand?

I was very fortunate my last quarter as a graduate student at UCSD to have helped organize a quantum computing seminar. I was strongly influenced by Aaronson's excellent book Quantum Computing Since Democritus where Aaronson's makes a strong point that Quantum Computing is easy if you abstract away the physics.

That may sound controversial but it really isn't, do algorithmists think of the electromagnetic waves storing bits on disk when they write pseudocode. Theorists are generally unaware of how computers work and more applied computer scientists are similarly unaware of how electronics work. Abstraction is powerful and allows one to focus on problems that exist at different conceptual levels. Why should quantum computing be any different? The approach that makes the most sense is to take it as a given that physicists will provide us with a basic set of quantum logic gates whether they are spinning or freezing or backflipping elementary particles in various gases is irrelevant to us. We can make more progress if we work with quantum logic gates as opposed to quantum physics.

### What is a Quantum Computer?

I'll assume that my reader has no knowledge of quantum computing and attempt to draw an analogy with a more well known device: the classical computer.

#### Boolean logic fugue
At the most abstract level, a computer is a function \\(f \\) of \\(n \\) bits that returns either 0 or 1.

\\(f(b_1, \dots , b_n) = \{0,1 \} \\)

Any binary function on \\(n \\) bits can be computed using combinations of the well known "AND", "OR" and "NOT" gates or just a "NAND". The fantastic book The Elements of Computing Systems by Nisan and Schocken shows how it is possible to start with a "NAND" gate and move on to assemblers, compilers, virtual machines and finally tetris.

Nisan and Schocken's argument is much more compelling than the one I will present since they actually build a computer using their claim. 

I will proceed instead proceed in two steps

1- I point the reader to the following reference so they can see how a "NAND" gate can be implemented using the basic "AND", "OR" and "NOT" gates. The hardware implementation of "AND", "OR" gates is easy if one remembers the distinction between in-series and in-parallel circuits.

2- I will prove by induction why you can write any binary function on \\(n \\) bits as a circuit consisting solely of "NAND" gates.

* Base Case (Single gate circuits: \\(n =1 \\)): 
* Inductive Step: Assume you can construct a circuit consisting solely of "NAND" gates for any function $$f$$ on $$n$$ bits. 




If you've ever wondered why binary is the base of choice for computers the above is a strong argument for that choice, the other being that it is simple to represent one of two states 0 or 1 using a ground or 5V.

#### Back to Quantum Computers

A quantum computer is then a function \\(f \\) of \\(n \\) quantum bits that when measured (think of this as returning for now) returns either 0 or 1.  



### Quantum Computers are at least as powerful as Classical Computers

This is a neat result that I proved in the introductory lecture of the seminar, of course this result is not novel in any way: I'm not sure if it was even formally stated in a paper or just taken as a known trivial result but regardless it's a good exercise to prove your first result about quantum computers. 

### Are computers more powerful if they are allowed to make coin flips?

The short answer is nobody knows for sure but it is hypothesized that it indeed is. This seems counter-intuitive, nobody would expect that two-face could make superior decisions by flipping a coin so why would the same not be true for computers. 


#### Polynomial identity testing: Case study for randomized algorithms

Suppose you were given two large polynomials \\(P_1 \\) and \\(P_2 \\) with many variables each. A natural question is: is \\(P_1 \equiv P_2\\)? There is no known deterministic algorithm for it but there is an incredibly simple randomized one!

* While you are not sure if $$P_1 \equiv P_2 $$
* Pick a point uniformily at random \\(x \in \\) Domain
* Evaluate \\(P_1(x) - P_2(x) \\)
	* If \\(P_1(x) - P_2(x) \\) == 0
		* continue
	* Else
		* Return: $$P_1 ! \equiv P_2$$

Why does this work? Well the more times we iterate over the loop the more confident we are that the two polynomials are equivalent! For two polynomial with \\(n \\) variables we can show that

#### Simulating a coin flip using a quantum computer

We will use, the basic quantum Hadamard Gate. \\(H = \frac{1}{\sqrt{2}} \\) $$\begin{bmatrix}1 & 1 \\ 1 & -1 \end{bmatrix} $$. We then apply \\(H \|0> \\)

### Epilogue
Good news is that quantum computers could probably run your favorite videogame. This is however not the most interesting property of quantum computers, if there is any interest then I can probably have some followup posts on Grover's search algorithm and Shor's factoring algorithm. If you can't wait then I'd highly recommend Chapter in 10 
see how to add links and references in the end. The two big open questions are perhaps: can quantum computers actually be built? If they can, can they solve more problems than classical computers? Nobody knows, but as Aaronson would say: all possibilities are equally intriguing since either we learn some pretty fundamental limitations of phyics or we get swanky new quantum computers.

http://cseweb.ucsd.edu/~dasgupta/book/index.html>Chapter 10
