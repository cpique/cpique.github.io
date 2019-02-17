---
layout: post
title: "Introducción a las cookies (Parte 1)"
tags: [cookies,cookie,programming]
date: 2018-06-02
desc: "Intro to cookies P1"
keywords: "cookies,cookie,http,software"
categories: [HTML]
icon: icon-html
---

En este artículo se intenta dar una introducción a las cookies, definirlas, explicar su funcionamiento, listar los tipos de cookies que existen, repasar un poco la historia y tocar el tema de la privacidad que se relaciona de cerca con las cookies. En otro artículo se incluirá una segunda parte, con ejemplos prácticos de cómo implementar, crear y manipular cookies.

****

## Definición
Una cookie es un archivo creado por un sitio web que contiene pequeñas cantidades de datos y que se envían entre un servidor y un navegador al consultar páginas en Internet.
Es decir, es básicamente texto que acompaña las peticiones y páginas que viajan entre server y browser.
Las cookies proveen una forma de almacenar información específica del usuario en aplicaciones web.
Las cookies se asocian con un sitio web, no con una página específica, de tal manera que el navegador y el servidor intercambien información sin importar qué página el usuario peticiona del sitio web. A medida que el usuario visita diferentes sitios, cada sitio puede enviar una cookie al browser del usuario también; el browser almacena todas las cookies por separado.
Las cookies son conocidas también como galletas informáticas, especialmente en documentación en español.

Su propósito principal es identificar al usuario almacenando su historial de actividad en un sitio web específico, de manera que se le pueda ofrecer el contenido más apropiado según sus hábitos. Esto quiere decir que cada vez que se visita una página web por primera vez, se guarda una cookie en el navegador con un poco de información. Luego, cuando se visita nuevamente la misma página, el servidor pide la misma cookie para arreglar la configuración del sitio y hacer la visita del usuario tan personalizada como sea posible.


Principales funciones:
* Llevar el control de los usuarios y su actividad
* Identificar usuarios en un sitio web
* Conseguir información sobre los hábitos de navegación del usuario
* Intentos de spyware por parte de agencias de publicidad y otras compañías
* Personalizar sitios web según preferencias del usuario

Las cookies son usadas por muchos propósitos, todos relacionados con ayudar a un sitio web a recordar y reconocer usuarios.

<img src="{{ site.img_path }}/cookies/01.jpg" alt="HTTP Cookie" width="50%">

Otra forma de ver a las cookies es como una manera de realizar gestion del estado y mantener continuidad en una aplicacion web. Esto se debe a que, excepto por el breve tiempo en el que realmente intercambian información, tanto el browser como el server están desconectados. Cada petición que un usuario hace al servidor web es tratada de forma independiente de cualquier otra petición. 

Las cookies pueden ser borradas, aceptadas o bloqueadas según se desee, configurando el navegador web.

****

## Funcionamiento

Las cookies son trozos de datos arbitrarios definidos por el servidor web y enviados al navegador. El navegador los devuelve al servidor sin modificar en las transacciones HTTP, que de otra manera serían independientes de ese estado (El protocolo HTTP es un protocolo sin estado).  
Sin las cookies, cada petición de una página web o un componente de una página web sería un evento aislado, sin ninguna relación con el resto de peticiones de otras páginas del mismo sitio. Pero devolviendo una cookie al servidor web, el navegador proporciona al servidor un medio para relacionar la solicitud de la página actual con solicitudes de páginas anteriores. Además de ser definidas por un servidor web, las cookies también pueden ser definidas por un script en un lenguaje como JavaScript, si éste está soportado y habilitado en el navegador web.
Las especificaciones de cookies8 sugieren que los navegadores deben soportar un número mínimo de cookies o una cantidad mínima de memoria para almacenarlas. En concreto, se espera que un navegador sea capaz de almacenar al menos 300 cookies de 4 kilobytes cada una y al menos 20 cookies por servidor o dominio. Algunos browsers también ponen un límite al número de cookies totales que aceptarán de todos los sitios combinados (usualmente 300).

<img src="{{ site.img_path }}/cookies/02.png" alt="How cookies travel" width="50%">

El servidor que establece la cookie puede especificar una fecha de borrado, en cuyo caso la cookie será borrada en esa fecha. Si no se define una fecha de borrado, la cookie es borrada cuando el usuario cierra su navegador. Por lo tanto, definir una fecha de borrado es una manera de hacer que la cookie sobreviva entre sesiones. Por esta razón, las cookies con fecha de borrado se llaman persistentes.

****

## Historia y Mitos

La primera cookie se creó en 1994 cuando un empleado de Netscape Communications decidió crear una aplicación de e-commerce con un carrito de compras que se mantuviese siempre lleno con los artículos del usuario sin requerir muchos recursos del servidor. El desarrollador decidió que la mejor opción era usar un archivo que se guardara en el equipo del receptor, en lugar de usar el servidor del sitio web.

Las cookies ya existían desde hace algún tiempo, solo que nunca se habían usado en los navegadores.

> La primera cookie fue creada por el programador <i class="em em-us"></i> [Lou Montulli](https://es.wikipedia.org/wiki/Lou_Montulli){:target="_blank"} en 1994, por entonces desarrollador de [Netscape Communications](https://es.wikipedia.org/wiki/Netscape_Communications_Corporation){:target="_blank"}.

  
Mitos <i class="em em--1"></i>
* Las cookies son similares a gusanos y virus en que pueden borrar datos de los discos duros de los usuarios. <i class="em em-expressionless"></i> 
* Las cookies son un tipo de spyware porque pueden leer información personal almacenada en el ordenador de los usuarios. 
* Las cookies generan ventanas emergentes. 
* Las cookies se utilizan para generar contenido basura. 
* Las cookies solo se utilizan con fines publicitarios. 


Las cookies son solo datos, no código.

****

## Tipos de cookies

+ Según su finalidad
  - Técnicas: Controlan el tráfico, identifican sesiones, almacenan contenidos...
  - De personalización: Idioma, tipo de navegador, configuración regional.
  - De análisis: Siguen el comportamiento de los usuarios para medir actividad del sitio.
  - Publicitarias: Permiten la gestión de espacios publicitarios que el editor incluyó en la web.
  - De publicidad comportamental: Crean un perfil específico del usuario.


+ Según su duración
  - _Session cookies o temporales_: Una vez que el usuario cierra el navegador desaparecen. Tienen un tiempo corto de vida.
  - _Persistent cookies o permanentes_: Continúan una vez cerrado el navegador, pudiendo llegar a establecerse durante un tiempo ilimitado. Se usan para rastrear al usuario guardando información sobre su comportamiento en un sitio web durante un período de tiempo determinado; las cookies persistentes pueden ser borradas limpiando los datos del navegador pero algunas tienen una fecha de expiración.

+ Según quién las gestione
  - _1st party (1ª parte)_: Establecidas por el mismo dominio que aparece en tu navegador.
  - _3rd party (3ª parte)_: Gestionadas por un tercero, normalmente son las compañías publicitarias las que administran este tipo de cookies. Su objetivo es controlar el comportamiento del usuario en varios sitios web.

+ Otras:
  - _Secure cookies_: Almacenan información cifrada para evitar que los datos almacenados en ellas sean vulnerables a ataques maliciosos de terceros. Se usan sólo en conexiones HTTPS.
  - _Zoombie cookies_: Se recrean a sí mismas luego de que son borradas. Esto quiere decir que el navegador realmente no tiene ningún poder sobre ellas porque continuarán regenerándose. Las cookies zombies se guardan en el dispositivo y no en el navegador, usualmente con la finalidad de que se pueda acceder a ellas sin importar qué navegador se esté usando. Esta misma característica puede convertirlas en una amenaza para la privacidad y seguridad del usuario, y en muchas ocasiones son usadas con fines ilegítimos y malintencionados.
  - _HttpOnly cookies_: Para prevenir ataques XSS, HttpOnly cookies son inaccesibles desde la API Document.cookie de JavaScript; sólo son enviadas al servidor. Por ejemplo, las cookies que persisten sesiones del lado del servidor no necesitan estar disponibles a código Javascript, y por lo tanto el flag _HttpOnly_ debe setearse en _true_.

****

## Privacidad y cookies de terceros
Las cookies tienen un dominio asociado a ellas. Si este dominio es el mismo que el dominio de la página sobre la que te encuentras, las cookies se dicen que son cookies de primera parte o first-party cookies. Si el dominio es diferente, se dice que es una cookie de terceros o una third-party cookie. Mientras que las primeras son sólo enviadas por el servidor que las setea, una página web puede contener imágenes o componentes almacenados en servidores de otros dominios. Las cookies que son enviadas a través de estos componentes de terceros se conocen como cookies de terceros y son principalmente usadas para publicidad y rastreo a través de la web.  
Las compañías publicitarias utilizan cookies de terceros para realizar un seguimiento de los usuarios a través de múltiples sitios. En concreto, una compañía publicitaria puede seguir a un usuario a través de todas las páginas donde ha colocado imágenes publicitarias o web bugs. El conocimiento de las páginas visitadas por un usuario permite a estas compañías dirigir su publicidad según las supuestas preferencias del usuario.

Algunos datos históricos:
> 1996: Aparecen las primeras preocupaciones respecto a las cookies. Las preocupaciones se centraron en el hecho de que las cookies almacenaban información en las computadoras de los usuarios sin su conocimiento o consentimiento.

> Se descubrió que la Oficina de Control de Drogas Nacional de la Casa Blanca utilizaba cookies para seguir a los usuarios que tras visitar su campaña anti-drogas, visitaban sitios relacionados con la fabricación o el uso de drogas. 

> 2000: El gobierno de los Estados Unidos definió estrictas reglas para la creación de cookies.

> 2002: Daniel Brandt averiguó que la CIA había estado definiendo cookies persistentes en ordenadores durante diez años. 

> 2005: Nuevamente Brandt descubrió que la Agencia de Seguridad Nacional había estado creando dos cookies persistentes en los ordenadores de sus visitantes

Cualquiera puede actualmente configurar su navegador para que se deshabiliten las cookies de terceros, pero lo que se pide según las reglas es que sea al contrario, y que el usuario que quiera aceptar este tipo de cookies tenga que realizar una acción consciente para su activación.

****

## TL;DR
Una cookie HTTP, cookie web o cookie de navegador es una pequeña pieza de datos que un servidor envía a el navegador web del usuario. El navegador guarda estos datos y los envía de regreso junto con la nueva petición al mismo servidor. Las cookies se usan generalmente para decirle al servidor que dos peticiones tiene su origen en el mismo navegador web lo que permite, por ejemplo, mantener la sesión de un usuario abierta. Las cookies permiten recordar la información de estado en vista a que el protocolo HTTP es un protocolo sin estado.

Se utilizan entre otras cosas, para reconocer al usuario; es decir, si alguien introduce su nombre y contraseña en una página web, la próxima vez que este acceda al sitio será reconocido automáticamente sin tener la necesidad de volver a identificarse. Otro uso de las cookies es para conocer el comportamiento de los usuarios, es decir, para personalizar la navegación y ofrecer publicidad relevante según la conducta del consumidor.

La primera cookie se creó en 1994 para mantener un carrito de compras disminuyendo los recursos utilizados del servidor.
Hay muchos mitos asociados a las cookies, pero debe saberse que son sólo datos y no código, y por lo tanto no pueden ser virus o spywares.
Existen diferentes tipos de cookies segun su duración, finalidad y quién las gestione, entre otras clasificaciones.

Las cookies pueden ser borradas, aceptadas o bloqueadas según se desee, configurando el navegador web.

[Mirá la segunda parte del post](https://cpique.github.io/2018/06/04/Cookies-intro-second-part/){:target="_blank"}

****

## Reference links
[Blog ThinkBig](https://blogthinkbig.com/que-son-las-cookies){:target="_blank"}   
[MDN web docs](https://developer.mozilla.org/es/docs/Web/HTTP/Cookies){:target="_blank"}   
[MSDN](https://msdn.microsoft.com/en-us/library/ms178194.aspx){:target="_blank"}   
[Wikipedia](https://es.wikipedia.org/wiki/Cookie_(inform%C3%A1tica)){:target="_blank"}  
[Política de cookies](http://politicadecookies.com/cookies.php){:target="_blank"}  
[40 de fiebre](https://www.40defiebre.com/que-es/cookies/){:target="_blank"}  
[The guardian article](https://www.theguardian.com/technology/2012/apr/23/cookies-and-web-tracking-intro){:target="_blank"}  
[DigitalTrends](https://www.digitaltrends.com/computing/history-of-cookies-and-effect-on-privacy/){:target="_blank"}
