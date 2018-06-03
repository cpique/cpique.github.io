---
layout: post
title: Introducción a las cookies 1ra parte
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

****

## Funcionamiento

Las cookies son trozos de datos arbitrarios definidos por el servidor web y enviados al navegador. El navegador los devuelve al servidor sin modificar en las transacciones HTTP, que de otra manera serían independientes de ese estado. (El protocolo HTTP es un protocolo sin estado)
Sin las cookies, cada petición de una página web o un componente de una página web sería un evento aislado, sin ninguna relación con el resto de peticiones de otras páginas del mismo sitio. Pero devolviendo una cookie al servidor web, el navegador proporciona al servidor un medio para relacionar la solicitud de la página actual con solicitudes de páginas anteriores. Además de ser definidas por un servidor web, las cookies también pueden ser definidas por un script en un lenguaje como JavaScript, si éste está soportado y habilitado en el navegador web.
Las especificaciones de cookies8 sugieren que los navegadores deben soportar un número mínimo de cookies o una cantidad mínima de memoria para almacenarlas. En concreto, se espera que un navegador sea capaz de almacenar al menos 300 cookies de 4 kilobytes cada una y al menos 20 cookies por servidor o dominio. Algunos browsers también ponen un límite al número de cookies totales que aceptarán de todos los sitios combinados (usualmente 300).

<p class="full-width"><img src="/public/image/2018-6-2-Cookies-intro-first-part_01.jpeg" alt="How cookies travel" /></p>

El servidor que establece la cookie puede especificar una fecha de borrado, en cuyo caso la cookie será borrada en esa fecha. Si no se define una fecha de borrado, la cookie es borrada cuando el usuario cierra su navegador. Por lo tanto, definir una fecha de borrado es una manera de hacer que la cookie sobreviva entre sesiones. Por esta razón, las cookies con fecha de borrado se llaman persistentes.

****

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

****

## Privacidad y cookies de terceros
Cookies have a domain associated to them. If this domain is the same as the domain of the page you are on, the cookies is said to be a first-party cookie. If the domain is different, it is said to be a third-party cookie. While first-party cookies are sent only to the server setting them, a web page may contain images or other components stored on servers in other domains (like ad banners). Cookies that are sent through these third-party components are called third-party cookies and are mainly used for advertising and tracking across the web. 

Las compañías publicitarias utilizan cookies de terceros para realizar un seguimiento de los usuarios a través de múltiples sitios. En concreto, una compañía publicitaria puede seguir a un usuario a través de todas las páginas donde ha colocado imágenes publicitarias o web bugs. El conocimiento de las páginas visitadas por un usuario permite a estas compañías dirigir su publicidad según las supuestas preferencias del usuario.

La posibilidad de crear un perfil de los usuarios se ha considerado como una potencial amenaza a la privacidad, incluso cuando el seguimiento se limita a un solo dominio, pero especialmente cuando es a través de múltiples dominios mediante el uso de cookies de terceros. Por esa razón, algunos países tienen legislación sobre cookies.

Facts:
El gobierno de los Estados Unidos definió estrictas reglas para la creación de cookies en el año 2000

Se descubrió que la Oficina de Control de Drogas Nacional de la Casa Blanca utilizaba cookies para seguir a los usuarios que tras visitar su campaña anti-drogas, visitaban sitios relacionados con la fabricación o el uso de drogas. 

En 2002, el activista por la privacidad Daniel Brandt averiguó que la CIA había estado definiendo cookies persistentes en ordenadores durante diez años. 

El 25 de diciembre de 2005, Brandt descubrió que la Agencia de Seguridad Nacional había estado creando dos cookies persistentes en los ordenadores de sus visitantes

Cualquiera puede actualmente configurar su navegador para que se deshabiliten las cookies de terceros, pero lo que se pide segun las reglases que sea al contrario, y que el usuario que quiera aceptar este tipo de cookies tenga que realizar una acción consciente para su activación.

****

## TL;DR
Una cookie HTTP, cookie web o cookie de navegador es una pequeña pieza de datos que un servidor envía a el navegador web del usuario. El navegador guarda estos datos y los envía de regreso junto con la nueva petición al mismo servidor. Las cookies se usan generalmente para decirle al servidor que dos peticiones tiene su origen en el mismo navegador web lo que permite, por ejemplo, mantener la sesión de un usuario abierta. Las cookies permiten recordar la información de estado en vista a que el protocolo HTTP es un protocolo sin estado.

Se utilizan entre otras cosas, para:
-Primero, para reconocer al usuario, es decir, si alguien introduce su nombre y contraseña en una página web, la próxima vez que este acceda al sitio será reconocido automáticamente sin tener la necesidad de volver a identificarse.
-Otro uso de las cookies es para conocer el comportamiento de los usuarios, es decir, para personalizar la navegación y ofrecer publicidad relevante según la conducta del consumidor.


La primer cookie se creo en 1994 para mantener un carrito de compras disminuyendo los recursos utilizados del servidor.
Hay muchos mitos asociados a las cookies, pero debe saberse que son solo datos y no codigo, y por lo tanto no pueden ser virus o spywares.
Existen diferentes tipos de cookies segun su duracion, finalidad, y quien las gestione, entre otras clasificaciones.

Las cookies pueden ser borradas, aceptadas o bloqueadas según se desee, configurando el navegador web.

****

## Reference links
[Blog ThinkBig](https://blogthinkbig.com/que-son-las-cookies){:target="_blank"}   
[MDN web docs](https://developer.mozilla.org/es/docs/Web/HTTP/Cookies){:target="_blank"}   
[MSDN](https://msdn.microsoft.com/en-us/library/ms178194.aspx){:target="_blank"}   
[Wikipedia](https://es.wikipedia.org/wiki/Cookie_(inform%C3%A1tica)){:target="_blank"}  
[Política de cookies](http://politicadecookies.com/cookies.php){:target="_blank"}  
[40 de fiebre](https://www.40defiebre.com/que-es/cookies/){:target="_blank"}  
[The guardian article](https://www.theguardian.com/technology/2012/apr/23/cookies-and-web-tracking-intro){:target="_blank"}  








