---
layout: post
title: Introducción a las cookies (Parte 2)
tags: csharp cookie cookies programming
---

Ya vimos en la [parte 1 del post](https://cpique.github.io/2018/06/02/Cookies-intro-first-part/){:target="_blank"} qué son las cookies, los tipos que existen, para qué se crearon y un poco de historia. Ahora veremos cómo crearlas a través de algunos ejemplos.

## Cómo crear una cookie
Cuando se crea una __cookie__, se debe especificar al menos _nombre_ y _valor_ Cada cookie debe tener un nombre único para que pueda identificarse más tarde cuando se lea desde el browser.   Debido a que las cookies son almacenadas por nombre, nombrar dos cookies igual causaría que una sea sobreescrita.
Si no se setea la expiración de la cookie, esta es creada pero no es almacenada en el disco rígido del usuario. En cambio, la cookie es mantenida como parte de la información de sesión del usuario. Cuando el usuario cierra el browser, la cookie es descartada. Una __cookie no persistente__ como esta es útil para información que necesita ser almacenada por sólo un período corto de tiempo o que por razones de seguridad no debería ser escrita en el disco de la computadora del cliente. Por ejemplo, las cookies no persistentes son útiles si el usuario está trabajando desde una computadora pública, donde no querrías escribir la cookie en el disco.

### C sharp
Las cookies son enviadas al browser mediante el objeto `HttpResponse` que expone una colección llamada `Cookies`. Se pueden agregar cookies a la colección de múltiples maneras. A continuación se muestran dos métodos de escribir cookies:

{% highlight csharp %}
Response.Cookies["userName"].Value = "patrick";
Response.Cookies["userName"].Expires = DateTime.Now.AddDays(1);
{% endhighlight %}

Otra forma:  
{% highlight csharp %}
HttpCookie aCookie = new HttpCookie("lastVisit");
aCookie.Value = DateTime.Now.ToString();
aCookie.Expires = DateTime.Now.AddDays(1);
Response.Cookies.Add(aCookie);
{% endhighlight %}

Ambos ejemplos logran la misma tarea, escribir una cookie en el navegador. En ambos métodos, el valor de expiración debe ser del tipo `DateTime`. Todos los valores de cookies son almacenados como _strings_, con lo que se necesitará hacer un casteo si se tiene otro tipo de dato a la hora de almacenar el valor en la cookie.

### JavaScript
__JavaScript__ puede crear, leer y eliminar cookies con la propiedad `document.cookie`.  
Ejemplo:  
{% highlight javascript %}
document.cookie = "username=John Doe";
{% endhighlight %}

También se puede agregar una fecha de expiración (en UTC). Por defecto, la cookie es eliminada cuando el browser se cierra:  

{% highlight javascript %}
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2013 12:00:00 UTC";
{% endhighlight %}


### Cookies con más de un valor
También se pueden almacenar múltiples pares _nombre-valor_ en una única cookie. Estos pares son llamados __subkeys__. Puedes usar subkeys por muchas razones. Primero, es conveniente poner toda la info similar o relacionada en una misma cookie. Además, debido a que la información esta en una única cookie, los atributos tales como la expiración aplican a toda la información (De la misma manera, si necesitas asignar diferentes fechas de expiración a diferentes tipos de información, deberías almacenar la info en cookies separadas). Usando una única cookie con subkeys, también usas menos de las 20 cookies que se le permiten al sitio

Creando una cookie con dos subkeys  
{% highlight csharp %}
HttpCookie aCookie = new HttpCookie("userInfo");
aCookie.Values["userName"] = "patrick";
aCookie.Values["lastVisit"] = DateTime.Now.ToString();
aCookie.Expires = DateTime.Now.AddDays(1);
Response.Cookies.Add(aCookie);
{% endhighlight %}


****

## Cómo leer cookies

Cuando un browser hace una petición al servidor, envía las cookies para ese servidor junto con el request. En las aplicaciones ASP.NET, puedes leer las cookies usando el objeto `HttpRequest`. La estructura de un objeto `HttpRequest` es escencialmente la misma que la del objeto `HttpResponse`, con lo cual puedes leer cookies de este objeto de una manera similar a las cuales las escribiste con el objeto `HttpResponse`. 2 ejemplos de cómo leer cookies:  

{% highlight csharp %}
if(Request.Cookies["userName"] != null)
{
    HttpCookie aCookie = Request.Cookies["userName"];
    //Use cookie or its value (aCookie.Value) ...
}
{% endhighlight %}

Antes de tratar de obtener el valor de una cookie, nos debemos asegurar que la cookie existe; si la cookie no existe y tratamos de recuperar el valor, obtendremos una excepción del tipo `NullReferenceException`. De notar es además que se usó el método `HtmlEncode` para encodear los contenidos de la cookie antes de mostrarlo o usarlo.  

### JavaScript
Con JavaScript, las cookies pueden leerse de la siguiente manera:  

{% highlight javascript %}
var x = document.cookie;
{% endhighlight %}

> `document.cookie` retornará todas las cookies en un string. Por ejemplo: `"cookie1=value; cookie2=value; cookie3=value"`;

****

## Cómo modificar y eliminar una cookie
No se puede directamente modificar una cookie. En cambio, modificar una cookie consiste en crear una nueva cookie con nuevos valores y enviar la cookie al navegador para sobreescribir la versión vieja en el cliente. Básicamente sería crear una nueva cookie con mismo _name_ pero nuevo _value_.  El siguiente ejemplo muestra cómo puedes cambiar el valor de una cookie que almacena el contador de las visitas de un usuario al sitio:  
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
Eliminar una cookie es una variación de modificarla. No podemos eliminar una cookie debido a que está del lado del usuario. Sin embargo, puedes hacer que el navegador elimine la cookie por ti. La técnica es crear una nueva cookie con el mismo nombre que la cookie a ser eliminada, pero setear la expiración de la cookie a una fecha anterior a hoy (el pasado). Cuando el navegador chequea la expiración de la cookie, el navegador la descartará.  
El siguiente ejemplo muestra una manera de eliminar todas las cookies disponibles en la aplicación:  
{% highlight csharp %}
HttpCookie aCookie;
string cookieName;
int limit = Request.Cookies.Count;
for (int i=0; i < limit; i++)
{
    cookieName = Request.Cookies[i].Name;
    aCookie = new HttpCookie(cookieName);
    aCookie.Expires = DateTime.Now.AddDays(-1);
    Response.Cookies.Add(aCookie);
}
{% endhighlight %}

#### JavaScript
Eliminar una cookie en Javascript es muy simple. No se necesita especificar un valor cuando eliminas la cookie, simplemente setear el parámetro __expires__ a una fecha pasada:  
{% highlight javascript %}
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
{% highlight javascript %}

****

## Cookies en el navegador
Los usuarios pueden limpiar las cookies en su computadora en cualquier momento. Incluso si almacenas cookies con tiempo de expiración muy grandes, un usuario podría decidir eliminar todas las cookies, limpiando totalmente cualquier configuración que se haya almacenado en las cookies.

### Deshabilitar cookies (no recomendado)
[Deshabilitar cookies en Chrome](https://support.google.com/accounts/answer/61416?co=GENIE.Platform%3DDesktop&hl=es){:target="_blank"}    
[Borrar cookies en Chrome](https://support.google.com/accounts/answer/32050?hl=es&co=GENIE.Platform=Desktop){:target="_blank"}    

[Borrar cookies en Firefox](https://support.mozilla.org/es/kb/Borrar%20cookies){:target="_blank"}
[Deshabilitar cookies en Firefox](https://support.mozilla.org/es/kb/habilitar-y-deshabilitar-cookies-sitios-web-rastrear-preferencias){:target="_blank"}


### Observar cookies
Puedes ver desde la consola del navegador las cookies activas en la página:  
Cookies en el navegador (Chrome):
<p class="full-width"><img src="/public/image/2018-6-4-Cookies-intro-second-part_01.PNG" alt="Cookies browser" /></p>

Las cookies que viajaron en el request y el response: 
<p class="full-width"><img src="/public/image/2018-6-4-Cookies-intro-second-part_02.PNG" alt="Cookies in request and response" /></p>

****

### Reference links
[MSDN](https://msdn.microsoft.com/en-us/library/ms178194.aspx#CodeExamples){:target="_blank"}  
[Developer Mozilla](https://developer.mozilla.org/es/docs/Web/HTTP/Cookies){:target="_blank"}  
[W3Schools](https://www.w3schools.com/Js/js_cookies.asp){:target="_blank"}