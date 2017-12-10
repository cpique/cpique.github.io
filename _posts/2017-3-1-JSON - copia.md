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

#### Object
<p class="full-width"><img src="/public/image/2017-3-1-JSON_01.png" alt="Object example" /></p>

Begins with { and ends with }. Inside of these curly braces there are key/value pairs separated by a comma ','.
Each pair at the same time is divided by a colon ':'.

#### Array
Array: It's an ordered collection of values. It begins with a [ and ends with ] and its values are separated by a comma ','
Example of an array:
<p class="full-width"><img src="/public/image/2017-3-1-JSON_02.png" alt="Array example"/></p>

Note that the array above has different types of values (object, number, boolean ...)
The structures can be nested. This means that an object can have as one of its values another object or maybe an array, an array can have
another array inside of it, and so on.

### Examples 
[Here](https://goo.gl/Lw5tO2) you'll find real-life escenarios.

### Tools 
Formatters
[JSON Formatter and validator](https://goo.gl/ZbC1fN) Allows you to validate json text indicating you whether it is valid or not. If it is valid, it will petty print your text. If not, it will inform you about the errors in the input.
[Another JSON Formatter](https://goo.gl/8wffRD) Another formatter with validation. It has also different conversion options.




### Reference links
[JSON org](https://goo.gl/O2WH)
[W3schools](https://goo.gl/EJuVgM)
[Formatter and validator](https://goo.gl/ZbC1fN)
[Formatter](https://goo.gl/8wffRD)

Thanks for reading !




