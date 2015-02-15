---
layout: default
title: About
---

If you're here and interested to learn more about my work in industry or academia, I'd recommend you follow the links to the left on the navigation bar.
 

#### What I've been up to with Web Development

Over the past few weeks, I've been trying to flex some web development muscles. I've been frantically going over both frontend and backend books. 
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


* JS Patterns: This book made me understand why people hate on JS so much. I probably need to go over the code reuse chapter again.
* Functional JS: The book looks good so far but I'm still unsure what underscore.js brings that can't be implemented using the helper functions that JS the good parts highlights. I'll have to read more to find out
* Node.js in Action is a good book, it's difficult to read without the online code companion. I used it to implement a simple RESTFUL command line todo list. I'm currently working on 