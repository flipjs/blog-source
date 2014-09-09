title: AngularJS - Isolate scope properties in controller context via controllerAs
date: 2014-09-09 04:00:00
tags: angular
---

As discussed in [isolate scope properties in controller context via controllerAs](https://github.com/angular/angular.js/pull/7645). Topic was started sometime in May, this feature is now live in 1.3.0!

Since controllerAs is gaining a lot of momentum as of late, being mentioned a lot of times from many popular blogs, I've started to move away from using $scope in controller, whenever possible. If I need to incorporate some kind of watchers, I use ngChange directive and Object.defineProperty(). Check out [MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty) for details and examples. Object.defineProperty is really cool, especially the accessor property descriptor!

Anyways, back to **bindToController**, here is the description from official [AngularJS](https://docs.angularjs.org/api/ng/service/$compile) site:
> "When an isolate scope is used for a component (see above), and controllerAs is used, bindToController will allow a component to have its properties bound to the controller, rather than to scope. When the controller is instantiated, the initial values of the isolate scope bindings are already available."

There you go. When you set controllerAs and bindtoController, your isolate scope is now bound to controller, no need to to reference from $scope. You can then reference your isolate scope, say in your template or linking function, via the instantiated controllerAs. See the code below:

{% gist 3ddd5295a5843cf988bb %}

In my MusicPlayerCtrl.prototype, I can reference the isolate scope properties, as they are now bound to the controller. I can also reference them inside the linking function through the controller parameter.

Here is the view/index.html:

{% gist 93419df0b65f0b3ab968 %}

Notice the symbol :: in {{expression}}, that is another neat feature in 1.3.0, it's called one-time binding. You don't need 2-way binding for all of your data in the view. Now we have this new feature, we can start using it to reduce overhead performance of our application.

Here's the output/view of this demo.

![png image file](/images/bindtoctrl@2x.png)

If writing directives or isolate scope is new to you, check out [egghead.io](https://egghead.io/) videos. I find them easier to understand when I was learning Angular. I guess, John Lindquist is really good at explaining things and makes complex things simple to $digest. :)

You can view the full source code at [https://github.com/flipjs/bindtocontroller](https://github.com/flipjs/bindtocontroller). Let me know your thoughts in the comments section. Thanks for reading!
