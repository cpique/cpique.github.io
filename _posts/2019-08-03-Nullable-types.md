---
layout: post
title: "Nullable types"
tags: [csharp,nullable,programming,nulls]
date:   2019-08-03
desc: "Handling null values in C#"
keywords: "c#,csharp,programming,null,visual studio"
categories: [Net]
icon: icon-html
---

As you may know by know, value types in C# (like int or bool) can not contain null values. But there may be times where a null value would make sense to represent the lack of data or an invalid value in terms of the business.
In these scenarios, nullable types come in handy. They are according to Microsoft instances of the System.Nullable<T> struct. Nullable types can represent all the values of an underlying type T, and an additional null value. 
So, if we have for example an int to represent the favorite number of an employee, but that value is optional because they could not have a favorite one, we can make use of `Nullable<int>` to handle null scenarios. This will avoid using -10000 for instance (I hope no one has that number as a favorite one), to represent cases where the info was not provided. Using null, we avoid using this numbers that will otherwise need to be consistent across the aplication and could be hardcoded in multiple projects. This works for any value type, so we can have a nullable DateTime as well (for instance, if we want to have the final date of former employees, we would need a null value for current ones)

We would have something like this:

```
public class Employee 
{
	public int ID { get; set; }

	public Nullable<DateTime> LastDay { get; set; }
	public Nullable<int> FavoriteNumber { get; set; }
}
```

You will probably see a green underline warning saying something like _Name can be simplified_.
That's because C# offers a shorthand for it: int?. Same for bool?, DateTime?, and so on.

If we use this approach, two readonly properties are available: `.HasValue` and `.Value`
`Nullable<T>.HasValue` tests for null and `Nullable<T>.Value` retrieves the actual value

```
if (employee.HasValue) 
{
	y = employee.Value;
}
```

If we access the `.Value` property when `.HasValue` returns false, we will get a `System.InvalidOperationException`.
We have a method `GetValueOrDefault()`, which retrieves as the name says the value stored or the default value of the underlying type. For int?, it will return the value that was assigned or 0 if no assign has been made.

> The syntax T? is shorthand for Nullable<T>. The two forms are interchangeable.
> Examples: bool?, int?, DateTime?

### Casting

From a value type to a nullable type, the casting is implicit.
From a nullable type to a value type, we need to be explicit. Although you have several ways, the `.GetValueOrDefault()` is a good option

```
	int? i = 52;
	int? j = null;
		
	int a = i.GetValueOrDefault(); //52
	int b = j.GetValueOrDefault(); //0
```

The null-coalescing operator is another option.

Last but not least, don't get confused with strings. Strings are reference types so they can hold the value null.
To check for null in strings, string.isNullOrEmpty() or string.isNullOrWhiteSpace() are widely used. The former checks if the string is either null or empty (""), while the latter checks the same with the additional of any strings that contain only whitespaces ("  ", " ",  "    ")

Examples:

```
string.isNullOrEmpty(""); //true
string.isNullOrEmpty(null); //true
string.isNullOrEmpty(" "); //false
string.isNullOrEmpty(" "); //true
string.isNullOrEmpty(null); //true
string.isNullOrEmpty(""); //true
```

### Further reading

If you want to know more, continue with this next post where I talk about the [Null Object Pattern](https://cpique.github.io/2019/08/03/Null-Object-Pattern/){:target="_blank"}

### References

[Pluralsight course](https://app.pluralsight.com/library/courses/csharp-nulls-working/table-of-contents){:target="_blank"}
[Microsoft Guide](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/nullable-types/){:target="_blank"}



