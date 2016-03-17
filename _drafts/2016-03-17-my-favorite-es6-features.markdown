---
layout: post
title:  "My Favorite ES6 Features"
categories: javascript es6 updates
---
I tried out React.js two years ago and I loved it. Unfortunately, I've been preoccupied cleaning stuff up in my day job's code base which prevented me from playing around with tools other than Angular.js 1 and Django for a couple of months. Now that workload is starting to clear out, I decided to play with React.js again and my first thought was "WTF happened to the syntax?"

After a couple hours of research, this new syntax seems to be brought about by ECMAScript 2015 (or ES6.) Turns out, the numerous changes actually brought in several welcome additions to the core feature set of Javascript - several of these I'm actually quite fond of!

### Variables: let, const, and how they compare with var
ES6 brings in a new way of declaring variables with **let** and **const**. The main difference between the two is that const declares a read-only reference to the value. Compared to **var**, the difference of these two statements are the rules on how a variable is scoped.

**ES5**
{% highlight javascript %}
var x = 1;
function sample() {
	console.log(x); // 1
}
{% endhighlight %}

**ES6**
{% highlight javascript %}
let x = 1;
function sample() {
	console.log(x); // undefined
}
{% endhighlight %}

As you can see, the value inside a variable declared by **var** is preserved or carried over inside the function's "child" block(s) while **let** only exists inside the specific block it has been defined in.

* Take note that it is still possible to create a locally scoped variable with ES5 but you would have to use an IIFE.

### String interpolation, finally!
Instead of concatenating variables and strings, you can now use template literals!

{% highlight javascript %}
function sum(numA, numB) {
	console.log('The sum of ${numA} and ${numB} is ${numA+numB}.');
}

sum(2, 1); // The sum of 2 and 1 is 3.
{% endhighlight %}

Along with that, Multi-line strings are no longer annoying thanks to template literals.

{% highlight javascript %}
// You can now do this
var x = '
	<div>
		<p>Some Text</p>
	</div>';

// Instead of this
var x =
	'<div>\n' +
	'	<p>Some Text</p>\n' + 
	'</div>';
{% endhighlight %}

### Arrow functions: No more confusing reference to this
I'm sure a lot of JS developers have had to capture the 'this' keyword to point to the needed reference to an object.

{% highlight javascript %}
function SampleModule() {
	var self = this;

	setTimeout(function() {
		self.timeoutHandler();
	});
}

SampleModule.prototype.timeoutHandler = function() {
	console.log('Timed out!');
}
{% endhighlight %}

Well you no longer need to do that thanks to arrow functions!

{% highlight javascript %}
class SampleModule {
  constructor() {
    setTimeout(() => {
      this.timeoutHandler();
    })
  }
  timeoutHandler() {
    console.log('Timed out!');
  }
}
{% endhighlight %}

### Looping with for-of
ES5 brought in a new way of iterating over arrays through forEach. Although I like how simple it is to use, I found myself reverting back to the tried and tested 'for (var i = 0; i < sampleArray.length; i++) {}' because of how we can break out of it anytime. I'm happy to say that for-of is the absolute solution to take care of this issue.

{% highlight javascript %}
for (let item of sampleArray) {} // Look how nice it looks, AND we can break anytime out of this.
{% endhighlight %}

### Default params
You no longer have to catch and check each parameter if it was undefined before using it. You can now supplement default values this way:

{% highlight javascript %}
function sample(a = 1) {
	console.log(a);
}

sample() // 1 instead of undefined
{% endhighlight %}

### Classes
You no longer have to use the prototype property to declare methods
{% highlight javascript %}
class Pet {
	constructor(name) {
		this.name = name;
	}
	walk() {
		console.log('${this.name} walks toward you');
	}
	eat(food) {
		console.log('${this.name} eats ${food}');
	}
}
{% endhighlight %}

### derived classes/inheritance
It is also now less messy to inhert from other classes (or constructor functions)
{% highlight javascript %}
class Dog extends Pet {
	constructor(name, breed) {
		super(name) // calling constructor function of Pet
		this.breed = breed;
	}
	bark() {
		console.log('${this.name} barks at you');
	}
}
{% endhighlight %}

### single & multiple named exports
{% highlight javascript %}
// helpers.js
export function sum(x, y) {
	return x + y;
}

// app.js
import { sum } from 'helpers';

sum(1,2) // 3

// or
import * as helpers from 'helpers';

helpers.sum(1,2) // 3
{% endhighlight %}


Anyway, that's it! Those are my favorite ES6 features so far based on MY experience.
