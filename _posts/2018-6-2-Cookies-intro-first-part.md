---
layout: post
title: Introducción a las cookies: 1ra parte
tags: cookies cookie programming post
---

En este artículo se intenta dar una introducción al tema de las cookies, definirlas y explicar su funcionamiento, listar los tipos de cookies que existen, repasar un poco la historia y tocar el tema de la privacidad que se relaciona de cerca con las cookies. En otro artículo se incluirá una 2da parte, con ejemplos prácticos de cómo implementar, crear y manipular cookies.


## Definición
Una cookie es un archivo creado por un sitio web que contiene pequeñas cantidades de datos y que se envían entre un servidor y un navegador al consultar páginas en Internet.
Es decir, es básicamente texto que acompaña las peticiones y páginas que viajan entre server y browser.
Las cookies proveen una forma de almacenar información específica del usuario en aplicaciones web.
Las cookies se asocian cono un sitio web, no con una página específica, de tal manera que el navegador y el servidor intercambien información sin importar qué página el usuario peticiona del sitio web. A medida que el usuario visita diferentes sitios, cada sitio puede enviar una cookie al browser del usuario también; el browser almacena todas las cookies por separado.
Las cookies son conocidas también como galletas informáticas, especialmente en documentación en español. Permiten a los sitios web consultar la actividad previa del usuario.

Su propósito principal es identificar al usuario almacenando su historial de actividad en un sitio web específico, de manera que se le pueda ofrecer el contenido más apropiado según sus hábitos. Esto quiere decir que cada vez que se visita una página web por primera vez, se guarda una cookie en el navegador con un poco de información. Luego, cuando se visita nuevamente la misma página, el servidor pide la misma cookie para arreglar la configuración del sitio y hacer la visita del usuario tan personalizada como sea posible.


Principales funciones:
* Llevar el control de los usuarios y su actividad
* Identificar usuarios en un sitio web
* Conseguir información sobre los hábitos de navegación del usuario
* Intentos de spyware por parte de agencias de publicidad y otras compañías
* Personalizar sitios web según preferencias del usuario

Cookies are used for many purposes, all relating to helping the Web site remember users. 
Las cookies son usadas por muchos propósitos, todos relacionados con ayudar a un sitio web a recordar y reconocer usuarios.

Las cookies ayudan a sitios web a almacenar información acerca de los visitantes. Más generalmente, las cookies son una manera de realizar gestion del estado y mantener continuidad en una aplicacion web. Esto se debe a que, excepto por el breve tiempo en el que realmente intercambian información, tanto el browser como el server están desconectados. Cada petición que un usuario hace al servidor web es tratada de forma independiente de cualquier otra petición. 
Por este motivo, es útil para los servidores web usar cookies, para reconocer a los usuarios que peticionan las páginas.


Las cookies pueden ser borradas, aceptadas o bloqueadas según se desee, configurando el navegador web.


## Funcionamiento

Las cookies son trozos de datos arbitrarios definidos por el servidor web y enviados al navegador. El navegador los devuelve al servidor sin modificar en las transacciones HTTP, que de otra manera serían independientes de ese estado. (El protocolo HTTP es un protocolo sin estado)
Sin las cookies, cada petición de una página web o un componente de una página web sería un evento aislado, sin ninguna relación con el resto de peticiones de otras páginas del mismo sitio. Pero devolviendo una cookie al servidor web, el navegador proporciona al servidor un medio para relacionar la solicitud de la página actual con solicitudes de páginas anteriores. Además de ser definidas por un servidor web, las cookies también pueden ser definidas por un script en un lenguaje como JavaScript, si éste está soportado y habilitado en el navegador web.
Las especificaciones de cookies8 sugieren que los navegadores deben soportar un número mínimo de cookies o una cantidad mínima de memoria para almacenarlas. En concreto, se espera que un navegador sea capaz de almacenar al menos 300 cookies de 4 kilobytes cada una y al menos 20 cookies por servidor o dominio. Algunos browsers también ponen un límite al número de cookies totales que aceptarán de todos los sitios combinados (usualmente 300).

<p class="full-width"><img src="/public/image/2018-6-2-Cookies-intro-first-part_01.jpeg" alt="How cookies travel" /></p>

El servidor que establece la cookie puede especificar una fecha de borrado, en cuyo caso la cookie será borrada en esa fecha. Si no se define una fecha de borrado, la cookie es borrada cuando el usuario cierra su navegador. Por lo tanto, definir una fecha de borrado es una manera de hacer que la cookie sobreviva entre sesiones. Por esta razón, las cookies con fecha de borrado se llaman persistentes.




## Tipos de cookies

+ Según su finalidad
  - Técnicas: controlan el tráfico, identifican sesiones, almacenan contenidos...
  - De personalización: idioma, tipo de navegador, configuración regional.
  - De análisis: siguen el comportamiento de los usuarios para medir actividad del sitio.
  - Publicitarias: permiten la gestión de espacios publicitarios que el editor incluyó en web.
  - De publicidad comportamental: crean un perfil específico del usuario.


+ Según su duración
  - Session cookies o temporales: una vez que el usuario cierra el navegador desaparecen. Son las session cookies. Tiene un tiempo corto de vida.
  - Persistent cookies o permanentes: continúan una vez cerrado el navegador, pudiendo llegar a establecerse durante un tiempo ilimitado. se usan para rastrear al usuario guardando información sobre su comportamiento en un sitio web durante un período de tiempo determinado; las cookies persistentes pueden ser borradas limpiando los datos del navegador pero algunas tienen una fecha de expiración.


+ Según quién las gestione
  - 1st party (1ª parte): establecidas por el mismo dominio que aparece en tu navegador.
  - 3rd party (3ª parte): gestionadas por un tercero, normalmente son las compañías publicitarias las que administran este tipo de cookies. Su objetivo es controlar el comportamiento del usuario en varios sitios web.


+ Otras:
  - Secure cookies: almacenan información cifrada para evitar que los datos almacenados en ellas sean vulnerables a ataques maliciosos de terceros. Se usan sólo en conexiones HTTPS.
  - Zoombie cookies: se recrean a sí mismas luego de que son borradas. Esto quiere decir que el navegador realmente no tiene ningún poder sobre ellas porque continuarán regenerándose, de ahí el nombre tan creativo que tienen. Las cookies zombis se guardan en el dispositivo y no en el navegador, usualmente con la finalidad de que se pueda acceder a ellas sin importar qué navegador se esté usando. Esta misma característica puede convertirlas en una amenaza para la privacidad y seguridad del usuario, y en muchas ocasiones son usadas con fines ilegítimos y malintencionados.
  - HttpOnly cookies: To prevent (XSS) attacks, HttpOnly cookies are inaccessible to JavaScript's Document.cookie API; they are only sent to the server. For example, cookies that persist server-side sessions don't need to be available to JavaScript, and the HttpOnly flag should be set.






## Reference links
[Blog ThinkBig](https://blogthinkbig.com/que-son-las-cookies){:target="_blank"} 
[MDN web docs](https://developer.mozilla.org/es/docs/Web/HTTP/Cookies){:target="_blank"} 
[MSDN](https://msdn.microsoft.com/en-us/library/ms178194.aspx){:target="_blank"} 
[Wikipedia](https://es.wikipedia.org/wiki/Cookie_(inform%C3%A1tica)){:target="_blank"}
[Política de cookies](http://politicadecookies.com/cookies.php){:target="_blank"}
[40 de fiebre](https://www.40defiebre.com/que-es/cookies/){:target="_blank"}
[The guardian article](https://www.theguardian.com/technology/2012/apr/23/cookies-and-web-tracking-intro){:target="_blank"}








