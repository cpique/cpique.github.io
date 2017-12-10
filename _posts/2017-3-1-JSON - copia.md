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
* String (It must be written in double quotes)
* Number
* Object
* Boolean
* Null
* Array

### Object

Begins with { and ends with }. Inside of these curly braces there are key/value pairs separated by a comma ','.
Each pair at the same time is divided by a colon ':'.

### Array
Array: It's an ordered collection of values. It begins with a [ and ends with ] and its values are separated by a comma ','
Example of an array:

Note that the array above has different types of values (object, number, boolean ...)
The structures can be nested. This means that an object can have as one of its values another object or maybe an array, an array can have
another array inside of it, and so on.
=== Examples ===
- Link to real examples. Here you can see how big JSONs in real applicattions could be

### Tools�
Formatters
https://goo.gl/ZbC1fN --> Allows you to validate json text indicating you whether it is valid or not. If it is valid, it will petty print your text. If not, it will inform you about the errors in the input.
https://goo.gl/8wffRD ---> Another formatter with validation. It has also different conversion options.
JavaScript
JSON.stringify() & JSON.parse()

JSON.parse() : parses a JSON string, constructing the JavaScript value or object described by the string
A common use of JSON is to exchange data to/from a web server. When receiving data from a web server, the data is always a string.
Because of that, it's a common practice parsing the data with JSON.parse(), and the data becomes a JavaScript object.
var obj = JSON.parse('{ "name":"John", "age":30, "city":"New York"}');

JSON.stringify() : converts a JavaScript value to a JSON string
When sending data to a web server, the data has to be a string.
Convert a JavaScript object into a string with JSON.stringify().
var obj = { "name":"John", "age":30, "city":"New York"};
var myJSON = JSON.stringify(obj);�
The line of code above produces a string ready to be sent to a server