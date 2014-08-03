title: Using object literal as switch statement
date: 2014-07-18 00:00:00
tags: javascript
---

I came across an article from Todd Motto about [Replacing switch statements with Object literals](http://toddmotto.com/deprecating-the-switch-statement-for-object-literals/). It has enlightened me to force myself not to use switch statement again (unless it's absolutely necessary). Todd Motto showed a few examples, but what interested me is the fallthrough implementation. Here is an example:

```js
var classifyShape = function(shape) {

  var isTriangle = function() {}
  var isQuadrangle = function() {}
  var isPentagon = function() {}

  var shapes = {
    'isosceles': isTriangle,
    'rectangle': isQuadrangle,
    'square': isQuadrangle
  }

  return shapes[shape]()
}
```

What if I wanted a default clause? Simple, add another clause, say 'unknown: isUnknown'. But how would you call it if there is no case match? Good question! At first, I come up with this:

```js
return shapes[shapes.hasOwnProperty(shape) ? shape : 'unknown']()
```

But as Todd Motto pointed out, it involves extra function call, not to mention hasOwnProperty method has some issues. Then, I come up with this:

```js
return shapes[shapes[shape] ? shape : 'unknown']()
```

Just check the value, if its undefined, then call the default. Simpler. But why use ternary operator, when you can use short-circuit evaluation.

```js
return (shapes[shape] || shapes['unknown'])()
```

Much simpler!

Here is the [final code](https://gist.github.com/flipjs/b969fb7b659de5d04e95):

```js
var classifyShape = function(shape) {
  
  var isTriangle = function() {
    console.log('A triangle is a polygon with 3 sides.')
  }

  var isQuadrangle = function() {
    console.log('A quadrangle is a polygon with 4 sides.')
  }

  var isPentagon = function() {
    console.log('A pentagon is a polygon with 5 sides.')
  }

  var isUnknown = function() {
    console.log('Unknown shape.')
  }
  
  var shapes = {
    'isosceles': isTriangle,
    'rectangle': isQuadrangle,
    'square': isQuadrangle,
    'unknown': isUnknown
  }
  
  return (shapes[shape] || shapes['unknown'])()
  
}
  
classifyShape('square')
classifyShape('isosceles')
classifyShape('qwerty')
```
