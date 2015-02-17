---
layout: default
title: About
---
## Serious Work Stuff

If you're here and interested to learn more about my work in industry or academia, I'd recommend you follow the links to the left on the navigation bar.

## Standup Comedy

I took a wonderful class at the University of Washington with Peter Greyy (Yes two y's) on standup comedy, we met for 3 sessions then had to perform in front of a live audience at the comedy underground in Seattle. You can chekout the video in navigation bar, it's a 3min video whose material took me about 20h worth of work. I would love to do more but I've been pretty swamped with learning web development.

## What I've been up to with Web Development

Since the beginning of February, I've been trying to flex some web development muscles. I hadn't done any web development before but I've getting more excited about sharing some of my work so I've been frantically going over both frontend and backend books to do so. 

* JS and Jquery: It's refreshing to see a good CS book written by people with a good design background. The book really is beautiful and the graphics help make a lot of things really clear. For example, I understood why Jquery was necessary by looking at graphical drawings of the DOM that show how .nextsibling works across different browsers.

* JS the good parts: A classic! and for a good reason too, I found myself going huh to wow. By the end of this good I couldn't understand why people complained so much about JS. Some favorites included:

{% highlight javascript %}
   var memoizer = function (memo, fundamental) {
        var shell = function (n) {
            var result = memo[n];
            if (typeof result !== 'number') {
                result = fundamental(shell, n);
                memo[n] = result;
            }
            return result;
        };
        return shell;
    };

{% endhighlight %}


* JS Patterns: This book made me understand why people hate on JS so much. I probably need to go over the code reuse chapter again. The objective is for me to understand how to come up with the below snippet from the perspective of someone who has never seen it.

{% highlight javascript %}
function inherit(C, P) {
var F = function () {};
 F.prototype = P.prototype;
 C.prototype = new F();
 C.uber = P.prototype;
 C.prototype.constructor = C;
}

{% endhighlight %}
* Functional JS: The book looks good so far but I'm still unsure what underscore.js brings that can't be implemented using the helper functions that JS the good parts highlights. I'll have to read more to find out
* Node.js in Action is a good book, it's difficult to read without the online code companion. I used it to implement a simple RESTFUL command line todo list. I'm currently working on a bunch of more interesting node projects now. 
* If Hemingway wrote JS: This is a creative programming book that shows code examples written in the style of authors ranging from 2pac, Kerouac to Roy. I expected this book to be more fun, I can't say that I got much out of it. I'm remined of Richard Hamming's remark which goes: If you wanna be succesful then study successes.
* Front-End Frameworks: I'm still scratching the surface here. I started looking into the ember and ember data docs and really appreciated how well implemented the observer pattern (discussed in JS patterns) was used to create awesome functionality like:

{% highlight javascript  %}
fullName: function() {
    return this.get('firstName') + ' ' + this.get('lastName');
  }.property('firstName', 'lastName')
});
{% endhighlight %}

Ember Data also feels like a node brainchild where a data store (data cached into the browser) does not need to be aware of how an adapter actually gets data whether its a server DB call or external API call. This article goes over some of the stuff I liked in more detail http://www.smashingmagazine.com/2013/11/07/an-in-depth-introduction-to-ember-js/

The naming convention also affords a lot of advantages since it makes it easy to go through online code examples. I haven't necessarily settled for Ember, I'm also looking into Angular which at a first glance seemed pretty complicated but I'm not one to judge the quality of a framework after going through a tutorial. DAE HASKAL FOR WEBSCALE?