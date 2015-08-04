---
title: Occam's Razor
layout: default
comments: true
---

# Occam's Razor

## Truth is found where less assumptions are made

One of the cornerstones of Machine Learning is Occam's Razor. Essentially it's a principle by which two competing hypotheses about the world may be compared according to their simplicity. An appropriate definition may be lifted off from Wikipedia:

>The principle states that among competing hypotheses that predict equally well, the one with the fewest assumptions should be selected. Other, more complicated solutions may ultimately prove to provide better predictions, but—in the absence of differences in predictive ability—the fewer assumptions that are made, the better.

The principle is indeed sensible but I always had a feeling that there must be some basic argument showing why it is indeed better to assume simpler hypothesis when possible. Therefore with what follows I'll make a simple probabilistic argument that will hopefully show you why Occam's Razor is indeed a good principle.

## Truth is found in likelihood

Suppose I gave you a list of numbers \\(D = \\{ 16,32,4 \\} \\) and asked to what hypothesis class do these numbers belong to. In the absence of more information, many valid hypotheses could be formed.
You could say:

* D belongs to the set containing even numbers
* D belongs to the set containing powers of two
* D belongs to the set of powers of two under 50
* D belongs to the set of even number under 100

While there is seemingly no clear answer, we can do some back of the envelope mathematics to see which of these hypotheses is the most likely. The hypothesis that's the most likely would be a good candidate for the correct one.

Let's call the space containing all possible hypotheses \\(H \\), we will call \\(D\\) our version space. Now suppose we are trying to find how likely it is that the points in \\(D\\) belong to some hypothesis \\(h \in H\\). Well we can formalize this as the probability of \\(D\\) given the hypothesis \\(h\\). 

\\(p(D | h) = \frac{1}{|h|^N} \\)

The above formula is simply making a counting argument where we assume we are drawing \\(N \\) points from \\(h\\) with replacement. The probability of drawing any one point from \\(h \\) is just the inverse of the number of elements in \\(h\\). 

Let's see how we can use the above formula to compare what's more likely that \\(D \\) belong to either one of:
* \\(h_1 = \\{ \\) the set of powers of two under 50 \\(\\}\\)
* \\(h_2 = \\{\\) the set of even numbers under a 100 \\(\\} \\)

We just need to compute the size of \\(h_i\\) and evaluate \\(p(D|h_i)\\) for all \\(i\\) in our case \\(i = \\{1,2 \\}\\) 

* \\(|h_1| = 5 \\) since \\(h_1 = \\{2,4,8,16,32 \\}\\) so that \\(p(D|h) = \frac{1}{|h_1|^3} = \frac{1}{5}^3 = 0.008 \\)
* \\(|h_2| = 50\\) so that \\(p(D | h_2) = \frac{1}{50}^3 = 0.000008 \\)

In short \\(h_1\\) is \\(0.008/0.000008 = 1000  \\) times more likely than \\(h_2\\) and that's just after observing 3 examples!

The difference is even more apparent if our dataset is larger so feel free to evaluate \\(p(D|h)\\) when \\(N = 100\\).


## Epilogue

Hopefully I've given you a taste as to why a likely hypothesis is probably the correct one. Astute readers might have noticed that \\(h_1\\) highly overfits the data since it's just a hypothesis that fits exactly the points in \\(D\\). Suppose we observe a new point 52 then \\(h_1\\) would no longer fit the data but \\(h_2\\) still would. There are many tricks employed in Machine Learning to avoid this scenario and hopefully I'll cover those in another blog post. 
