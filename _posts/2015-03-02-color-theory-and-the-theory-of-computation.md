---
title: Color Theory and Theory of Computation
layout: default
comments: true
---

# Color Theory and The Theory of Computation

Over the past few months I've been trying to train my eye to appreciate better design. People tend to find better designed blogs to be more trustworthy. While content is king, looks matter too. So I know it will be worthwhile for me to learn more about design. Today I decided to explore the topic of color theory.

**Disclaimer: The below is an informal argument that does not constitute a real mathematical proof, it's value is in providing some intuition behind diagonalization.**

## The fundamental theorem of color engineering

My brief foray into design has led me to find this commonly held belief in the design community.

> "A device that is able to reproduce the entire visible color space is an unrealized goal within the engineering of color displays and printing processes".

The above is directly pulled from Wikipedia. Usually I would not attach much thought to such a statement but its formulation reminded me pretty strongly of a type of statement that I've encountered in a theory of computation class I TA'd for back in UCSD.

For this blog post I will prove a stronger statement:

> There cannot exist a device that can reproduce the entire visible color space.

## The Godel, Escher and Bach argument

I will prove the above statement by reducing it to another statement which was proven to be true in the wonderful [Godel, Escher and Bach](http://www.amazon.com/G%C3%B6del-Escher-Bach-Eternal-Golden/dp/0465026567/ref=sr_1_1?ie=UTF8&qid=1425267550&sr=8-1&keywords=godel+escher+and+bach)

> There cannot exist a gramophone that can play any disk

Hofstatder lays out a thought experiment where he discusses whether a gramophone that can play any disk could exist in principle. Hofstatder's argument is an intriguing one. He makes a claim that given such a perfect gramophone he would inspect its inner workings and construct a disk such that when that disk is played, its creases which would typically produce vibrations in the air to create sound, would instead produce vibrations that oscillate at the disk's resonant frequency, causing the disk to break. Therefore, we've shown that for any gramophone there exits a disk that it cannot play. Or in other words, there exists no gramophone that can play any disk.


## The fundamental theorem of color

A printer operates in much the similar way: a printer recieves a digital encoding of all colors and positions they should occupy on a sheet of paper. Given the encoding, my idealized theoretical printer vibrates its needle to move to different locations on the page to bring about the miracle of color.


Similarly to how Hofstatder exploited the property of resonant frequency to make a disk break, we know that there is a one to one mapping between the digital encoding that a printer receives and the displayed colors on an image. This means that given a handcrafted encoding we should in principle be able to manipulate the color needle of a printer in whatever way we wish. Therefore, there must exist at least one encoding that can force the printer to malfunction by making the needle vibrate uncontrollably. In other words, for any printer ever invented or to be invented in the distant future, there must exist a encoding of colors which the printer will not be able to print.

## Epilogue

With this we can finally conclude that:

> There cannot exist a device that can reproduce the entire visible color space.

In fact we have illustrated something much more powerful:

> There cannot exist any device that can reproduce the entirety of any space.

And here I leave you with one of the deepest truths uncovered in Mathematics, Gödel's incompleteness theorem. I'll prove Gödel's incompleteness theorem in a formal but easy argument in my next blog post. What we will cover is specifically the process by which we inspect a printer or gramophone to find the respective encodings of color and sound that would cause them to malfunction.
