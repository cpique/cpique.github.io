---
layout: post
title: Introducción a las cookies (Parte 2)
tags: csharp cookie cookies programming
---

## Cómo crear una cookie
When creating a cookie, you must specify at least name and value. Each cookie must have a unique name so that it can be identified later when reading it from the browser. Because cookies are stored by name, naming two cookies the same will cause one to be overwritten. 
If you do not set the cookie's expiration, the cookie is created but it is not stored on the user's hard disk. Instead, the cookie is maintained as part of the user's session information. When the user closes the browser, the cookie is discarded. A non-persistent cookie like this is useful for information that needs to be stored for only a short time or that for security reasons should not be written to disk on the client computer. For example, non-persistent cookies are useful if the user is working on a public computer, where you do not want to write the cookie to disk.

### `C#`
Cookies are sent to the browser via the HttpResponse object that exposes a collection called Cookies. You can add cookies to the Cookies collection in a number of ways. The following example shows two methods to write cookies:

{% highlight csharp %}
Response.Cookies["userName"].Value = "patrick";
Response.Cookies["userName"].Expires = DateTime.Now.AddDays(1);
{% endhighlight %}

Another method to write cookies:  
{% highlight csharp %}
HttpCookie aCookie = new HttpCookie("lastVisit");
aCookie.Value = DateTime.Now.ToString();
aCookie.Expires = DateTime.Now.AddDays(1);
Response.Cookies.Add(aCookie);
{% endhighlight %}

Both examples accomplish the same task, writing a cookie to the browser. In both methods, the expiration value must be of type DateTime. All cookie values are stored as strings, meaning that you will need to do a cast if you have another type to store.

### JavaScript


### Cookies with more than one value
You can also store multiple name-value pairs in a single cookie. The name-value pairs are referred to as subkeys. You might use subkeys for several reasons. First, it is convenient to put related or similar information into a single cookie. In addition, because all the information is in a single cookie, cookie attributes such as expiration apply to all the information. (Conversely, if you want to assign different expiration dates to different types of information, you should store the information in separate cookies.). By using a single cookie with subkeys, you use fewer of those 20 cookies that your site is allotted.

Creating a cookie with two subkeys:
{% highlight csharp %}
HttpCookie aCookie = new HttpCookie("userInfo");
aCookie.Values["userName"] = "patrick";
aCookie.Values["lastVisit"] = DateTime.Now.ToString();
aCookie.Expires = DateTime.Now.AddDays(1);
Response.Cookies.Add(aCookie);
{% endhighlight %}


****

## Cómo leer cookies

When a browser makes a request to the server, it sends the cookies for that server along with the request. In your ASP.NET applications, you can read the cookies using the HttpRequest object. The structure of the HttpRequest object is essentially the same as that of the HttpResponse object, so you can read cookies out of the HttpRequest object much the same way you wrote cookies into the HttpResponse object. Here are two examples of how to read cookies:

{% highlight csharp %}
if(Request.Cookies["userName"] != null)
{
    HttpCookie aCookie = Request.Cookies["userName"];
    //Use cookie or its value (aCookie.Value) ...
}
{% endhighlight %}

Before trying to get the value of a cookie, you should make sure that the cookie exists; if the cookie does not exist, you will get a NullReferenceException exception. Notice also that the HtmlEncode method was called to encode the contents of a cookie before displaying or using it.

****

## Cómo modificar y eliminar una cookie
You cannot directly modify a cookie. Instead, changing a cookie consists of creating a new cookie with new values and then sending the cookie to the browser to overwrite the old version on the client. The following code example shows how you can change the value of a cookie that stores a count of the user's visits to the site:
{% highlight csharp %}
int counter;
if (Request.Cookies["counter"] == null)
    counter = 0;
else
{
    counter = int.Parse(Request.Cookies["counter"].Value);
}
counter++;

Response.Cookies["counter"].Value = counter.ToString();
Response.Cookies["counter"].Expires = DateTime.Now.AddDays(1);
{% endhighlight %}

### Eliminando una cookie
Deleting a cookie is a variation on modifying it. You cannot directly remove a cookie because the cookie is on the user's side. However, you can have the browser delete the cookie for you. The technique is to create a new cookie with the same name as the cookie to be deleted, but to set the cookie's expiration to a date earlier than today (the past). When the browser checks the cookie's expiration, the browser will discard the now-outdated cookie.  
The following code example shows one way to delete all the cookies available to the application:
{% highlight csharp %}
HttpCookie aCookie;
string cookieName;
int limit = Request.Cookies.Count;
for (int i=0; i<limit; i++)
{
    cookieName = Request.Cookies[i].Name;
    aCookie = new HttpCookie(cookieName);
    aCookie.Expires = DateTime.Now.AddDays(-1);
    Response.Cookies.Add(aCookie);
}
{% endhighlight %}


****

## Cookies en el navegador
Users can clear the cookies on their computer at any time. Even if you store cookies with long expiration times, a user might decide to delete all cookies, wiping out any settings you might have stored in cookies.


### Cómo ver las cookies actuales

### Configurar navegador

****

### Reference links
[MSDN](https://msdn.microsoft.com/en-us/library/ms178194.aspx#CodeExamples){:target="_blank"}  
[Developer Mozilla](https://developer.mozilla.org/es/docs/Web/HTTP/Cookies){:target="_blank"}   
