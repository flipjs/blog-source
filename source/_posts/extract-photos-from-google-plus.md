title: Extract photos from Google+
date: 2014-08-07 23:38:42
tags: [javascript, node, gplus]
---

Here is how you can extract photos from Google+ photo albums. All you need to know is the userId and albumId of a Google+ user. The data being used here are my own photos, my street photography album. You have to have node.js installed to run the code below:

{% gist ff0b605b4f67891e8c34 %}

The code will log out the photo url and description. You can try logging out the whole body and inspect to see all the information.

Here are some of the photos in the album:
![The Eye](http://lh6.ggpht.com/-qEohzb-j6o0/ToBNSlnTd-I/AAAAAAAADx8/YS00Zkk3QrA/P1100450.jpg)
![Louvre](http://lh6.ggpht.com/-CIaO4eMsdEw/Tnxu5BetWHI/AAAAAAAADrU/AqWGN-u4jxA/P1050525.jpg)
![Stairs](http://lh5.ggpht.com/-L1-WZpG41Ww/TmCtq1ThxSI/AAAAAAAADHQ/I4fgcJ6-FMY/nik_aug_11.jpg)

