---
title: Using Non Microsoft Tools at the New Microsoft
layout: default
---

### Binging it

I'm not sure where this stereotype came from but apparently many people outside of Microsoft believe that Bing employees are deathly afraid of uttering the words: "I googled it". If ever someone would ever dare commit such a gaffe then the ghost of Steve Ballmer would take away your employee badge and ban you from ever entering Washington State again! In fact, nothing could be further from the truth, our engineering culture means that we don't spend all day bickering about the correct nomenclature of verbs pertaining to "search on the internet" and instead spend it on building tools that our clients care about. I'll give an example that some friends have found a bit surprising that illustrates that point.

### A case study

A few months ago, Bing Ads launched what is now known as Universal Event Tracking. It's essentially an offering with features similar to Google Analytics + Google Remarketing. The TLDR of it is: you put some tracking script on your webpage that lets you analyze the behavior of your webpage's users. 

#### The problem

We had a bunch of escalations from support where advertisers were complaining that the tag wasn't doing what they expected it to do. There were definitely two themes to the questions.

* Where do I put my tag?
* After I put place the tag on my page, how do I know if it is working correctly? 

#### The solution

The solution to the first problem was just to create a reference web page that shows a webpage correctly instrumented with the UET tag. I had already a few days before learnt how to serve a static html page using node so that's what I used. I queried for "node webapp hosting " and clicked on heroku. Set up my config files and had my super simple reference page up and ready within a few minutes. (Un)?Surprisingly nobody cared that I didn't write a dot net app and hosted it on Azure, in fact it would have been ridiculous for anybody to bring this up. Every engineer uses the tools that he's comfortable with, if those tools help him bring value to customers quicker then that's the technology stack he should go with.


The solution to the second problem was to create some sort of extension that could read through a customer's webpage and tell whether the UET tag was correctly instrumented. I never had much experience writing browser extensions but again I just looked up online my alternatives. The top ranking results were Firefox and Chrome, I skimmed through the documentation and found the Chrome docs to be easier to start with so I went with that. So now a tool that a lot of folks in support are using is this simple chrome extension.

The chrome extension is very simple, the core logic is 4 lines of javascript that tells whether a certain global object has a particular attribute and then uses that to send the user an alert as to whether their tag is correctly configured.

### Epilogue

There is no question that this kind of culture has been made possible by Satya, I hear that the above might have been difficult to achieve about a year ago. However, the culture has shifted from a product obsessed one to a customer obsessed one and I don't anybody is going to look back at this decision with any regret

