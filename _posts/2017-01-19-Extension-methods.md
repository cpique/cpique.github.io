---
layout: post
title: Extension methods in C# 
tags: c#, extension-methods, programming
---

According to MSDN, Extension methods enable you to “add” methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. Extension methods are a special kind of static method, but they are called as if they were instance methods on the extended type. There is no apparent difference between calling an extension method and the methods that are actually defined in a type.

### Where do we find extension methods and how do we create them?

The most common extension methods are the LINQ standard query operators that add query functionality to the existing System.Collections.IEnumerable and System.Collections.Generic.IEnumerable types.
This means that if you import the using statement related to Linq (System.Linq), you will have right away new methods to invoke from types like arrays or List.

So, the framework provides extension methods, but you can also create your own. To create one, it's as easy as create a static method whitin a static class receiving at least one parameter with the 'this' keyword in front of it. More on this below in the Examples section.

### Facts about extension methods

- They are defined as static methods.
- They are called as if they were an instance method.
- Their first parameter specifies which type the method operates on, and the parameter is preceded by the this modifier.
- Extension methods need that you explicitly import the corresponding namespace with a using directive.
- They need to be defined inside a non-nested, non-generic static class.

### Examples

You'll have to code along to see the example working. If you don't want to, you can scroll
down to see the code corresponding to the extension method.
We're going to create an extension method that will tell us if a value entered by the user
it's a number or not. Also, we're going to use a built-in extension method in the System.Linq namespace.

Open Visual Studio and create a new Console Application (.NET Framework). VS will create a Program.cs file with a little bit of code to get started. We will need the Main() method later. Now, create a new class called CustomExtensionMethods and marked it as static.
Then, paste the following code inside the class just created:
{% highlight csharp %}
public static bool IsNumeric(this string theValue)
{
   long retNum;
   return long.TryParse(theValue, System.Globalization.NumberStyles.Integer, System.Globalization.NumberFormatInfo.InvariantInfo, out retNum);
}
{% endhighlight %}

Our extension method is ready to use. Let's get back to Program.cs to use it. 
Copy and paste the following code inside the Main() method:
{% highlight csharp %}
string[] values = new string[] { "1", "A", "0a", "5", "five", "01/01/2017" };

Console.WriteLine($"{values.Count()} elements found");
Console.WriteLine();

foreach (var value in values)
{
    var result = value.IsNumeric() ? "numeric" : "NOT numeric";
    Console.WriteLine($"The value {value} is " + result);
}

Console.ReadLine();
{% endhighlight %}

We didn't just use our extension method, we are also using a extension method provided by LINQ to count how many elements the array has. (The namespace System.Linq should be there by default. If not, add it or otherwise solution won't build).

Pay attention on how the custom extension method is called from the string variable, as if it was a built-in method provided by the String class like toString().
You can now run the Console and see if our custom method works properly.
A very simple example that nevertheless lets us see the basics of an extension method.

Tags: 
<ul>
  {% for tags in page.tags %}
    <li>{{ tags }}</li>
  {% endfor %}
</ul>
