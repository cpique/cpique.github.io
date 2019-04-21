---
layout: post
title: "Boxing and unboxing in C#"
tags: [csharp,boxing,unboxing,performance]
date:   2019-04-19
desc: "What do boxing and unboxing mean?"
keywords: "c#,boxing,programming,unboxing,visual studio"
categories: [Net]
icon: fa-dot-circle-o
---

Before starting, you should know that in C# you can work with 3 different types: *value*, *reference* and *pointer* types.
'Boxing' and 'unboxing' are processes that work with value and reference types.
'Value types' (int, char, float, double, bool and so on) are stored in the stack, whereas 'reference types' are stored in the managed heap.

<br>

### Definition

'Boxing' is the mechanism of converting a value type to a reference type.
When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap. 
Boxing can be formally defined as the process of explicitly assigning a value type to a System.Object variable.

'Unboxing', the opposite process, extracts the value type from the object. 
It converts the value held in the object reference back into a corresponding value type on the stack.

<br>

---

### Example

An example extracted from MSDN that shows boxing and unboxing in a few lines:

```
int i = 123;      // a value type
object o = i;     // boxing
int j = (int)o;   // unboxing
```

<br>

### Comparative table

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

<br>
<br>

---

### Performance

You should avoid when possible classes or structs with methods and properties that can cause implicit boxing when used with value types. 
You can determine them by looking at their signatures: if a method takes an argument of type 'object' or an interface then the value type instance will be boxed.

<br>

### Reference links

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/boxing-and-unboxing
