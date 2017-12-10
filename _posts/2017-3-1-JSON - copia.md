---
layout: post
title: JSON
tags: c# json programming
---

The purpose of this tutorial is give the reader an introduction to JSON.
It provides definitions, what are the parts of a JSON, how to build one, useful tools and examples.


### JSON (JavaSricpt Object Notation)
First of all, it's not a programming language. It's rather just text, written with JavaScript object notation.
It's a data-interchange format. A syntax for storing and exchanging data. All JSON files are built on two structures:
* A collection of key-value pairs
* A list of values which it's generally called as an array.

### Key benefits
* Easy to read and write by humans
* Easy to create and process by computers
* "Self-describing"
* Language independent (Can be read and used as a data format by any programming language.)
* Can easily be sent to and from a server

### Syntax rules
* Data is in name/value pairs
* Data is separated by commas
* Curly braces hold objects
* Square brackets hold arrays

### Structures 
Valid data types to use in JSON:
String (It must be written in double quotes)
Number
Object
Boolean
Null
* Array

### Object
{% highlight javascript %}
var obj = 
{
    "name": "john",
    "age": 26
}
{% endhighlight %}
Begins with { and ends with }. Inside of these curly braces there are key/value pairs separated by a comma ','.
Each pair at the same time is divided by a colon ':'.
Example of an object:
 

or by using bracket notation
x = obj["name"];

### Array
Array: It's an ordered collection of values. It begins with a [ and ends with ] and its values are separated by a comma ','
Example of an array:
[{"name":"john"}, 26, 1, false, undefined, {"age":35}];
Note that the array above has different types of values (object, number, boolean ...)
The structures can be nested. This means that an object can have as one of its values another object or maybe an array, an array can have
another array inside of it, and so on.
=== Examples ===
- Link to real examples. Here you can see how big JSONs in real applicattions could be