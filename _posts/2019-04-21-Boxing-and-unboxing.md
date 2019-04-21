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


---


### Definition

**Boxing** is the mechanism of converting a value type to a reference type.
When the CLR boxes a value type, it wraps the value inside a `System.Object` and stores it on the managed heap. 
**Boxing** can be formally defined as the process of explicitly assigning a value type to a `System.Object` variable.

**Unboxing**, the opposite process, extracts the value type from the object. 
It converts the value held in the object reference back into a corresponding value type on the stack.

If you try to unbox a null you will get a _NullReferenceException_. 
Trying to unbox a reference to an incompatible value type causes an _InvalidCastException_.


---


### Example

An example extracted from MSDN that shows boxing and unboxing in a few lines:

```
int i = 55;      // a value type
object o = i;     // boxing
int j = (int)o;   // unboxing
```

<img src="{{ site.img_path }}/boxandunbox/01.png" alt="Object example" width="25%">

---


### Comparative table

<table style="font-family: arial, sans-serif;border-collapse: collapse;width: 100%;">
  <tr>
    <th style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        Boxing
    </th>
    <th style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        Unboxing
    </th>
  </tr>
  <tr style="background-color: #dddddd;">
    <td style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        From value type to reference type
    </td>
    <td style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        From reference type to value type
    </td>
  </tr>
  <tr>
    <td style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        After boxing, value is stored on the heap
    </td>
    <td style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        After unboxing, value is on the stack
    </td>
  </tr>
  <tr style="background-color: #dddddd;">
    <td style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        Implicit
    </td>
    <td style="border: 1px solid #dddddd;text-align: left;padding: 8px;">
        Explicit
    </td>
  </tr>
</table>


---

### Performance

You should avoid when possible classes or structs with methods and properties that can cause implicit boxing when used with value types. 
You can determine them by looking at their signatures: if a method takes an argument of type 'object' or an interface then the value type instance will be boxed.


---


### Summary

Boxing is the implicit conversion of a value type to a reference type.
Unboxing is the explicit conversion of a reference type back to a value type.


---

### Reference links

https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/boxing-and-unboxing
