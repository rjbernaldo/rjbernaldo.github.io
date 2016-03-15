---
layout: post
title:  "What's new with ES6"
categories: javascript es6 updates
---
I tried out React.js two years ago and I loved it. Unfortunately, I've been preoccupied cleaning stuff up in my day job's code base which prevented me from playing around with tools other than Angular.js 1 and Django for a couple of months. Now that workload is starting to clear out, I decided to play with React.js again and my first thought was "WTF happened to the syntax?"

After a couple hours of research, it was clear that the new syntax was brought about by ECMAScript 2015 (or ES6) and turns out, the numerous changes actually brought in several welcome additions to the core feature set of Javascript.

## Variable Declaration (Blocked Scope)

- LET (Before ES6)
{% highlight javascript %}
function doubleNum(x) {
	if (true) {
		let x = 0;
	}

	return x * 2;
}
{% endhighlight %}

- CONST

## Functions

Arrow

## Strings

Methods

Template Literal

## Arrays

## Math

## Spread Operator

## Destructuring

## Params

## Modules

## Classes

## Symbols

## Problem: Not Supported in Browsers
