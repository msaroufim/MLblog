---
title: Alternative Numbering Schemes
layout: default
comments: true
---

## Alternative Numbering Schemes
---
---
Today's post will be a short one, I recently bought a copy of [The Little Schemer](http://www.amazon.com/Little-Schemer-Daniel-P-Friedman/dp/0262560992/ref=sr_1_1?ie=UTF8&qid=1426735911&sr=8-1&keywords=the+little+schemer) and have had a really fun experience with it. The Little Schemer introduces many deep mathematical ideas in a concise Socratic treatment. I enjoyed many sections of the book but chose to comment briefly on just one.

### Representations (What are numbers?)
---

Depending on who you ask you might get a different answer. In the first corner, we have Intuitionists who claim that mathematical constructions including numbers are abstract entities. An Intuitionist would for instance claim that there is no such thing as a true infinity and that things merely appear infinite to us if they are large enough.

In the second corner, we have Platonists who espouse the falsehood of assuming that perception and the object of perception are the same. A chair is not the same thing as the mental image of a chair and it often proves useful to dissociate our own perceptions of truth from Mathematics. It might have been obvious to the human race at some point that the sun spins around the earth since that is what people observed by looking at the sky. 

>Q: So what's a number?

>A: Umm 0,1,2,3,4...

That's not a bad attempt: we have symbols that correspond to different quantities. The 3 dots tell us that there are many more symbols and that starting at 0 we can generate all quantities by repeatedly adding 1.

Let's try something else

>Q: What's a number?

>A: (), (()), ((),()),((),(),())

>Q: wat?

So what's going on here is we've simply picked different symbols for our numbering scheme: instead of using the integers we instead use a list where the number of empty lists corresponds to our quantities. So (()) corresponds to 1 and ((),()) corresponds to two. 

###Implementing an alternative numbering scheme in Scheme
---
To show that I am not in fact rambling over trivialities, I will show you how to implement addition using our parenthesis based numbering scheme. But first we'll build up the helper functions we'll need to perform addition.

>Q: How would you test for zero?

>A: Test if the list is null

{% highlight scheme %}
(define sero?
    (lambda (n)
    (null? n)))
{% endhighlight %}


>Q: How would you add 1 to a number

>A: Prepend () to it

{% highlight scheme %}

(define edd1
    (lambda (n)
    (cons (quote ()) n)))
{% endhighlight %}

>Q: How would you subtract one?

>A: Remove one ()

{% highlight scheme %}

(define zub1
    (lambda (n)
        (cdr n)))
{% endhighlight %}

>Q: How would you add two numbers n and m?

>A: Add 1 to n, m times

{% highlight scheme %}

(define +
    (lambda (n m)
        (cond
            ((sero? m) n)
            (else (edd1 (+ n (zub1 m)))))))
{% endhighlight %}

###Epilogue
---
This is a simple yet neat application showing why we shouldn't attach much importance to our numbering scheme. This idea is familiar to most computer scientists since they are used to working in different numerical bases.
