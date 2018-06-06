---
layout: post
title: Constructors in C#
tags: constructor chsarp programming this base
---

## Definition
A __constructor__ is a special method of a class that is called indirectly when creating an object using the `new` keyword. However, unlike a “normal” method, constructors never have a return value (not even `void`) and are always named identically to the class they are constructing.  
Given that objects have state, a programmer will typically want to assign relevant values to the object’s field data before use. Due do the fact that it is not uncommon for a class to have dozens of fields to contend with, it would be undesirable to author 20 initialization statements to set 20 points of data, for example.
Thanks to constructors, __C#__ allows the state of an object to be established at the time of creation. 

> According to the spec: "An instance constructor is a member that implements the actions required to initialize an instance of a class."

****

## The default constructor
Every __C#__ class is provided with a default constructor that you can redefine if need be. By definition, a default constructor never takes arguments. After allocating the new object into memory, the default constructor ensures that all field data of the class is set to an appropriate default value.
You can redefine the default constructor to suit your needs.   

Example:  
{% highlight csharp %}
public class Book
{
    //State
    public string _isbn;
    public int _year;

    // A custom default constructor.
    public Book()
    {
        _isbn = "123ABC";
        _year = 2018;
    }
}
...
//Invoking default constructor.
Book sciFiBook = new Book();
{% endhighlight %}


****

## Custom constructors 
Typically, classes define additional constructors beyond the default. Here's and update of the class _Book_ with now three constructors:
{% highlight csharp %}
public class Book
{
    public string _isbn;
    public int _year;

    // A custom default constructor.
    public Book()
    {
        _isbn = "123ABC";
        _year = 2018;
    }
    // Here, year will receive the default value of an int
    public Book(string isbn)
    {
        _isbn = isbn;
    }
    
    // Set the full state.
    public Book(string isbn, int year)
    {
        _isbn = isbn;
        _year = year;
    }
}
{% endhighlight %}

What makes one constructor different from another is the number of and/or type of constructor arguments. When you define a method of the same name that differs by the number or type of arguments, you have overloaded the method. Thus, we've overloaded the constructor of the class to provide more ways to create an object at the time of creation.  
Now you can create _Book_ objects using any of these constructors:  
{% highlight csharp %}
Book book1 = new Book();
Book book2 = new Book("AFG431");
Book book3 = new Book("ZZG431", 2015);
{% endhighlight %}


#### What happens with the default constructor when we define a custom constructor?
All classes are provided with a free default constructor. Thus, if you insert a new class without a constructor, you are still able to create an instance of that class type via the default constructor out of the box.  
In this next example, you could create an instance even though we haven't defined a constructor:
{% highlight csharp %}
public class LoggerUtility
{
    public void Log(string message)
    {
        Console.WriteLine(message);
    }
}

...
//This is valid
LoggerUtility log = new LoggerUtility();
{% endhighlight %}


However, as soon as you define a custom constructor with any number of parameters, the default constructor is silently removed from the class and is no longer available. Think of it this way: if you do not define a custom constructor, the __C#__ compiler grants you a default in order to allow the object user to allocate an instance of your type with field data set to the correct default values. However, when you define a unique constructor, the compiler assumes you have taken matters into your own hands. Therefore, if you want to allow the object user to create an instance of your type with the default constructor, as well as your custom constructor, you must explicitly redefine the default. To this end, understand that in a vast majority of cases, the implementation of the default constructor of a class is intentionally empty, as all you require is the ability to create an object with default values. 

> If you don't specify any constructors at all, a default constructor is provided by the compiler. This default constructor is a parameterless constructor with no body, which calls the parameterless constructor of the base class. If the base class has no accessible parameterless constructor (including a default one), you get a compile-time error if the derived class doesn't have any constructors - because the default constructor will implicitly try to call a parameterless constructor from the base type.

> A nice shortcut: The VS IDE provides the `ctor` code snippet. When you type `ctor` and press the _Tab_ key twice, the IDE will automatically define a custom default constructor. You can then add custom parameters and implementation logic.

****

## `*this*` keyword and constructors 
__C#__ supplies a `this` keyword that provides access to the current class instance.  
One use of the `this` keyword is to design a class using a technique termed **constructor chaining**. This design pattern is helpful when you have a class that defines multiple constructors. Given that constructors often validate the incoming arguments to enforce various business rules, it can be quite common to find redundant validation logic within a class’s constructor set. 

With the goal of avoid redundant code statements in constructors, you can define a method in the class that will validate the incoming argument(s). If you were to do so, each constructor could make a call to this method before making the field assignment(s). While this approach does allow you to isolate the code you need to update when the business rules change, you still have redundancy as each constructor needs to invoke the method.

A cleaner approach is to designate the constructor that takes the _greatest number of arguments_ as the “master constructor” and have its implementation perform the required validation logic. The remaining constructors can make use of the `this` keyword to forward the incoming arguments to the master constructor and provide any additional parameters as necessary. In this way, you need to worry only about maintaining a single constructor for the entire class, while the remaining constructors are basically empty. Here's an example

{% highlight csharp %}
public class Book
{
    public string _isbn;
    public int _year;

    // Constructor chaining.
    public Book() : this("", 0) { }
    public Book(string isbn) : this(isbn, 0) { }
    public Book(int year) : this("", year) { } 
    
    // 'Master constructor'
    public Book(string isbn, int year)
    {
        //Logic and extra stuff
        //...
        //
        
        _isbn = isbn;
        _year = year;
    }
}
{% endhighlight %}

> When chaining constructors, note how the `this` keyword is “dangling” off the constructor’s declaration (via a colon operator) outside the scope of the constructor itself.

****

> Using the `this` keyword to chain constructor calls is never mandatory. We could've used just 'Book' to make the chain. However, when you make use of this technique, you do tend to end up with a more maintainable and concise class definition. The real work is delegated to a single constructor (typically the constructor that has the most parameters).

****

> An alternative to this tecnique is to use optional parameters.

****

#### Constructor flow
Once a constructor passes arguments to the designated master constructor (and that constructor has processed the data), the constructor invoked originally by the caller will finish executing any remaining code statements.

As you can see, the flow of constructor logic is as follows:
* You create your object by invoking one of the constructors. 
* If you invoke the master constructor, only that one is going to be executed. If not, the following steps are executed.
* The constructor forwards the supplied data to the master constructor and provides any additional startup arguments not specified by the caller.
* The master constructor assigns the incoming data to the object’s field data.
* Control is returned to the constructor originally called and executes any remaining code statements.


#### Using optional parameters
With this example, we now provide a number of ways to construct objects using a single constructor definition:

{% highlight csharp %}
    public class Book
    {
        public string _isbn;
        public int _year;

        // Single constructor using optional args.
        public Book(string isbn = "", int year = 0)
        {
            //Logic and extra stuff
            //...
            //
            
            _isbn = isbn;
            _year = year;
        }
    }
{% endhighlight %}

With this one constructor, you are now able to create a new _Book_ object using zero, one, or two arguments.

****

## `*base*` keyword and constructors 
The `base` keyword is used to access members of the base class from within a derived class. 
A constructor can use the `base` keyword to call the constructor of a base class. Thus, we can specify which base-class constructor should be called when creating instances of the derived class.

{% highlight csharp %}
public class Manager : Employee
{
    public Manager(int annualSalary) : base(annualSalary)
    {
        //Add further code here.
    }
}
{% endhighlight %}

In this example, the constructor for the base class is called before the block for the constructor is executed. The `base` keyword can be used with or without parameters. 
In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.
If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using base.

Importante note: There are two forms of _constructor initializer_ - one which calls a base class constructor with the `base` keyword and one which calls another constructor from within the class, using the `this` keyword. There must always be a "chain" of constructors which runs constructors all the way up the class hierarchy. Every class in the hierarchy will have a constructor invoked, although some of those constructors may not explicitly appear in the code.
Every constructor of every class other than plain object does this, either explicitly or implicitly. 


****

## Static constructors

A static constructor is a special constructor that is an ideal place to initialize the values of static data when the value is not known at compile time (e.g., you need to read in the value from an external file, read in the value from a database, generate a random number, or whatnot). The CLR calls all static constructors before the first use (and never calls them again for that instance of the application).

A few points of interest regarding static constructors:
* A given class may define only a single static constructor. In other words, the static constructor cannot be overloaded.
* A static constructor does not take an access modifier
* They are parameterless.
* A static constructor executes exactly one time, regardless of how many objects of the type are created.
* The runtime invokes the static constructor when it creates an instance of the class or before accessing the first static member invoked by the caller.
* The static constructor executes before any instance-level constructors.

****

## TL;DR
A constructor (or more specifically an instance constructor) is a member that implements the actions required to initialize an instance of a class.
It's a special method of a class that is called indirectly when creating an object using the `new` keyword. Constructors never have a return value and are always named identically to the class they are constructing.

There are two forms of _constructor initializer_ - one which calls a base class constructor with the `base` keyword and one which calls another constructor from within the class, using the _this_ keyword. There must always be a "chain" of constructors which runs constructors all the way up the class hierarchy. Every class in the hierarchy will have a constructor invoked, although some of those constructors may not explicitly appear in the code. Thus, there must be at least one constructor invoked in each class in the hierarchy.

The __C#__ language spec refers to two types of constructors: instance constructors and static constructors. A static constructor it's useful to initialize static data at runtime. They're parameterless and don't have an access modifider.


****

## Reference links
[Pro C# 7](https://www.apress.com/la/book/9781484230176){:target="_blank"}     
[MSDN](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/using-constructors){:target="_blank"}  
[Jon Skeet article](http://jonskeet.uk/csharp/constructors.html){:target="_blank"}