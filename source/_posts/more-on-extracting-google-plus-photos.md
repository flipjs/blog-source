title: More on Extracting Google+ Photos
date: 2014-08-08 11:34:08
tags: [javascript, node, gplus]
---

This is a follow-up on my recent post called [Extract photos from Google Plus](/2014/08/07/extract-photos-from-google-plus/). A close friend of mine (and Angular Guru), **Ronneil** at [c0debreaker.github.io](http://c0debreaker.github.io/), suggested that we can also use an external module called [**request**](https://github.com/mikeal/request).

{% codeblock lang:sh %}
npm install request
{% endcodeblock %}

This is much simpler to use to make http calls, than using the core module [**http**](http://nodejs.org/api/http.html). See the code below:

{% gist 6c24d36f0287e8e0ef7f %}

See, it is much less code. The request module is doing all the work for you.

If you notice, I'm using iterator iife/recursion for looping. I will post another topic on that, as I need to do something else now. So, stay tuned! 
