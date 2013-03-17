---
layout: post
title: Generadores de sitios estáticos. La última moda vintage.
description: Generadores de sitios estáticos. La ultima nueva moda de generar sitios web a partir de únicamente HTML.
image: generadores-estaticos.jpg
author: Antonio Villamarin
tags:
- programacion
- jekyll
- generadores estaticos de contenido
category: Programacion
---

Una moda relativamente reciente ha sido la de recuperar las "buenas" costumbres de montar un sitio web solamente con lo que necesita, es decir, con HTML, CSS y si quieres algo de JavaScript.

En realidad se trata de algo muy sencillo pero a la vez muy potente. Una de las grandes ventajas de generar sitios web estáticos es que al generar el HTML no necesitamos muchos recursos de hosting, podemos alojar nuestra web prácticamente en cualquier sitio. Esto era un problema hace algún tiempo, puesto que editar el HTML directamente es muy tedioso, principalmente por su sintaxis, además de ser un problema si queríamos mudarlo de plataforma.

La desventaja principal que tiene es que si necesitamos base de datos o interactuar con el servidor de alguna manera, necesitaremos algún lenguaje script para manipularlo y no nos servirá esta solución. Pero realmente, la mayoría de las páginas que encontramos por internet no necesitan interactuar con el servidor y en los casos en que sí existes servicios externos que lo hacen por nosotros.

El gran ejemplo es el blog. Un porcentaje bastante alto de los sitios de internet son blogs. Para un blog, en general, no necesitamos ni base de datos, ni interactuar con el servidor para nada. Lo más interactivo que debería hacer un blog es usar comentarios para lo que nos podemos servir de la ayuda de [Disqus][1] o [Facebook][2] entre otras opciones.

Aquí es donde entran en juego los generadores de sitios estáticos.

Como definición podríamos decir que un generador de sitios estáticos es una aplicación que nos permite generar un sitio web completo donde el resultado son ficheros HTML, CSS o JavaScript. Todo se ejecuta del lado del cliente, por lo que nuestro hosting (cualquier) puede hacer funcionar nuestra web.

Existen varios generadores (muchos en realidad) y varios tipos de generador. Los más comunes son los que podemos ejecutar en nuestro equipo de sobremesa con PHP, Python o Ruby.

Casi todos están orientados a generar blogs, pero con un poco de pericia pueden generarse sitios webs sin blog.

Suelen seguir un formato común todos, y es que al programa se le dice donde tenemos las fuentes y donde queremos el resultado de "compilarlo" y nos va generando los ficheros.

Otra gran ventaja de usar estos generadores estáticos es que nos facilitan la creación de páginas bajo un lenguaje de marcado ligero, mucho más entendible para un humano, como [Markdown][3] o [Textile][4].

El proceso es el siguiente:

1. Instalamos el programa en nuestro equipo.
2. Creamos nuestra plantilla.
3. Empezamos a crear el contenido en ficheros .md.
4. Ejecutamos el programa.
5. Ya podemos subir el resultado a nuestro hosting.

[Github][5] tiene integrado un servicio basado en [jekyll][6] con el que puedes crear tu blog fácilmente. Jekyll es uno de los más conocidos y usados debido al impulso de Github le ha dado y a la flexibilidad que ofrece. Está basado en Ruby, pero para los que le tengan miedo a la programación, no hay nada que programar, solo escribir nuestras páginas. Las plantillas pueden ser muy potentes y están basadas en el motor Jinja, propio de Ruby.

Basada en Python [Pelican][7] está tomando fuerza. Tanta, que su creador ha abierto un servicio llamado [Calepin][8] con el que crear nuestro blog y almacenarlo en [Dropbox][9].

En PHP no está demasiado extendido este sistema, pero existen algunos, el más cómodo a mi modo de ver es [SecondCrack][10] que se basa en el mismo principio.

*Imagen de [SEOPlanter][11]*

[1]: http://www.disqus.com
[2]: http://www.facebook.com
[3]: http://daringfireball.net/projects/markdown/
[4]: http://textile.sitemonks.com/
[5]: http://github.com
[6]: http://github.com/mojombo/jekyll
[7]: http://www.getpelican.com
[8]: http://calepin.co
[9]: http://db.tt/dtakgw07
[10]: http://github.com/marcoarment/secondcrack
[11]: http://www.flickr.com/photos/seoplanter/