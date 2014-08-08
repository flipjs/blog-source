title: Sublime Text Build System for JavaScript
date: 2014-08-02 00:00:00
tags: [javascript, sublime]
---

Today, my daughter kicked me out of my desk because she wants to use my macbook pro. She is contented with just using the iPad, but today, she wants to play an online game with her sister and friends. She has her own computer, but it is broken for quite some time now. As for me, it's time to use my old, trusty macbook again.

But alas, I didn't have Sublime Text installed on my old macbook! I was a Textmate user before, so that was the text editor installed on it. Nothing to worry, just download Sublime Text (ST2 was used here), and install some packages.

I downloaded NodeJS package too, and use it as build system for JavaScript. Please note that, prior to this, I already have Node.js installed. It can be downloaded from [nodejs.org](http://nodejs.org/). 

Problem is, it displays nothing when I build from this package. I remember I had the same issues before, but for the life of me, I can't remember how I solved it. Well, Google is your friend. :) I decided to just create a new build system, and leave the NodeJS package alone. From the Sublime Text menu, select Tools --> Build System --> New Build System:

![png image file](/images/st-new-build-system.png)

Then, copy and paste this code:
```
{
  "cmd": ["node", "$file"],
  "selector": "source.js"
}
```

And then, save it as, say "Node.sublime-build". There is a problem though, when I execute Sublime Text from the dock or finder, it can't find node. It could be the environment variable $PATH does not exist in finder shell or the path to node is not defined. Well, not to worry, it is an easy fix. Just prepend 'node' with '/usr/local/bin' (or whereever it was installed) in sublime-build file:

```
{
  "cmd": ["/usr/local/bin/node", "$file"],
  "selector": "source.js"
}
````

And, that's it!

As for my daughter, I should fix her computer soon. Otherwise, she will always bug me, whenever she wants to play that game again. Ok, Evernote, add it on my todo list!
