title: More on Extracting Google+ Photos
date: 2014-08-08 11:34:08
tags: [javascript, node, gplus]
---

This is a follow-up on my recent post called [Extract photos from Google Plus](/2014/08/07/extract-photos-from-google-plus/). A close friend of mine (and Angular Hacker), Ronneil at [c0debreaker.github.io/](http://c0debreaker.github.io/), suggested that we can also use an external module called ['request'](https://github.com/mikeal/request). This is much simpler to use to make http calls, than using the native module 'http'. See the code below:

```js
var request = require('request')
 
var url = 'http://picasaweb.google.com'
        + '/data/feed/api/user/102873175118305865375/'
        + 'albumid/5646665615382099025'
        + '?alt=json'
 
request.get(url, function(err, res, body) {
    var gplus = JSON.parse(body)
    var len = gplus.feed.entry.length
    ;(function iterator(i) {
      if (i >= len) return
      console.log('' + (i+1) + '. '
                + gplus.feed.entry[i].content.src
                + ' - ' + gplus.feed.entry[i].summary['$t'])
      iterator(i + 1)
    })(0)
})
```

See, it is much less code. The request module is doing all the work for you.

If you notice, I'm using iterator iife/recursion for looping. I will post another topic on that, as I need to do something else now. So, stay tuned! 
