title: Extract photos from Google+
date: 2014-08-07 23:38:42
tags: [javascript, node, gplus]
---

Here is how you can extract photos from Google+ photo albums. All you need to know is the userId and albumId of a Google+ user. The data being used here are my own photos, my street photography album. You have to have node.js installed to run the code below:

```js
#!/usr/bin/env node
 
var http = require('http')
 
// Google Plus Photos API
// Sample data from Felipe Apostol's Street Photography album
// userId is 102873175118305865375
// albumId is 5646665615382099025
 
var options = {
  host: 'picasaweb.google.com',
  path: '/data/feed/api/user/102873175118305865375/'
        + 'albumid/5646665615382099025?alt=json'
}
 
var req = http.request(options, function(res) {
 
  var body = ''
  res.setEncoding('utf8')

  res.on('readable', function() {
    var chunk = this.read() || ''
    body += chunk
  })
 
  res.on('end', function() {
    var gplus = JSON.parse(body)
    var len = gplus.feed.entry.length
    ;(function iterator(i) {
      if (i >= len) return
      ;// we are interested with feed.entry property
      ;// log photo url + caption
      console.log('' + (i+1) + '. '
                + gplus.feed.entry[i].content.src
                + ' - ' + gplus.feed.entry[i].summary['$t'])
      iterator(i + 1)
    })(0)
  })
 
  req.on('error', function(e) {
      console.log('error' + e.message)
  })
 
})
 
req.end()
```

The code will log out the photo url and description. You can try logging out the whole body and inspect to see all the information.

Here are some of the photos in the album:
![The Eye](http://lh6.ggpht.com/-qEohzb-j6o0/ToBNSlnTd-I/AAAAAAAADx8/YS00Zkk3QrA/P1100450.jpg)
![Louvre](http://lh6.ggpht.com/-CIaO4eMsdEw/Tnxu5BetWHI/AAAAAAAADrU/AqWGN-u4jxA/P1050525.jpg)
![Stairs](http://lh5.ggpht.com/-L1-WZpG41Ww/TmCtq1ThxSI/AAAAAAAADHQ/I4fgcJ6-FMY/nik_aug_11.jpg)

