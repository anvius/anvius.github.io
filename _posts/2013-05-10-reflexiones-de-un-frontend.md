---
layout: post
title: Reflexiones de un frontend
description: Reflexiones de un frontend
author: Antonio Villamarin
tag: Programacion
---

Bueno, primero he de decir que en cuanto al desarrollo no soy un frontend más bien un backend.

Hace 15 años, cuando salí de la facultad de Matemáticas, los servicios de páginas web eran muy pocos y con sistemas de desarrollo pequeños, apenas empezaba a existir Amazon, se buscaba en el portal más completo que había: Yahoo, y Google daba sus primeros pasos. También eran pequeños los programas de escritorio (el borland Pascal ocupaba algo así como 50kb). Pero a pesar de esto, los cambios se sucedían a una velocidad de vértigo ya entonces. Por supuesto las universidades lamentablemente no absorbían nada de esto hasta años más tarde cuando ya era bastante menos útil, como la adopción de Java o algo más interesante todavía, C/C++.

En 1998 empecé con una página web. Aquello se hacía en un "plisplas" y no podías aspirar a hacer nada muy dinámico a parte de incluir algunas cositas en PHP 2, o PHP 3 un poco más tarde. Casi todo era feo. Con todo y con eso ha habido algunas buenas páginas desde entonces que mejoraban con cada innovación.

Después de la historieta del abuelo cebolleta :) voy a hablar por fin del frontend.

Hoy en día la programación del frontend es prácticamente imposible que sea programada por una sola persona cumpliendo los plazos que se manejan en la empresa. Hay tantas cosas nuevas y diferentes cada día para añadir funcionalidades que no hay tiempo de apegarse a una tecnología determinada y se necesitan especialistas multidisciplinares en CSS, JavaScript, CoffeeScript, LESS o Stylus, JQuery o Sencha, iOS y Android, Backbone o Lungo, etc...

Simplemente el planteamiento del diseño ya tiene que pasar por ser responsive, adaptarse bien a los móviles de diferentes resoluciones o emplear diferentes tecnologías para cada una de ellas.

Existen algunas buenas prácticas que en general no se están cumpliendo precisamente por toda esta maraña de tecnologías a las que los frontend (y sobre todo los backend) no conseguimos adaptarnos todo lo rápido que se necesita.

En la inmensa mayoría de los casos de sitios web o aplicaciones web, no se tienen en cuenta los aspectos prioritarios en sí, sino que se premia la rapidez con la que se hace y la facilidad de hacerlo buscando refugio en solo un par o tres de esas tecnologías.

Algunos tips que yo daría sobre el frontend serían enfocados a la optimización sin dejar atrás en demasía la rapidez.

1. El sitio web debería ocupar lo menos posible. A más tamaño, más consumo inútil de recursos, más tiempo de espera para el usuario, más tiempo de espera para los buscadores a la hora de indexar nuestra web, etc...

2. Si en nuestro sitio controlamos tan solo 5 o 6 eventos, ¿para qué añadir 70Kb de JQuery? JavaScript es lo suficientemente potente para esto con muchísima menos carga. Recuerda que existe la función "querySelectorAll" para hacer prácticamente los mismo que "$" de JQuery. Esta función también hace prácticamente los mismo:

        function $(a,b){
            a = a.match(/^(\W)?(.*)/); 
            return(b||document)['getElement'+(a[1]?a[1]=='#'?'ById':'sByClassName':'sByTagName')](a[2])
        }

        // Se llama así, como en jQuery
        $('#cabecera');

3. Hay que conocer bien HTML5, CSS3 y JavaScript. Ya está. Luego podemos ayudarnos de precompiladores como Stylus para facilitarnos la tarea. No hay que seguir lo que la mayoría hace sino que hay que usar el preprocesador que a nosotros nos venga bien. Personalmente recomiendo Stylus. También CoffeeScript para JavaScript, aunque este es más complicado de aprender.

4. El Ajax de una aplicación no necesita de grandes librerías, solo 3 o 4 líneas en JavaScript puro.

5. Hay que olvidarse de navegadores que usa menos del 1% o 2% como Internet Explorer 6 o 7. Hacerlo compatible conlleva más gasto en desarrollo que posibles beneficios. A no ser que hablemos de una aplicación que venda mucho mucho y entonces nos compense, pero esto hay que evaluarlo.

6. Pasar test a las funciones de JavaScript y refactorizar siempre que sea posible. Para hacer test se pueden unar herramientas hechas para ello como [QUnit][1], o podemos simplemente hacernos nuestras pequeñas funciones para comprobar que hace lo que debe. Según el proyecto lo que nos se más fácil.

7. Por supuesto minificar todo lo que podamos, HTML, CSS y JavaScript. Y seguir las reglas básicas de carga con el JavaScript al final del renderizado.

8. A ser posible, en el diseño, no usar imágenes sino CSS. No necesitamos meter un gif para hacer un degradado, se puede hacer con CSS. Se pueden emplear fuentes con iconos tipo [awesome][2] que además se pueden escalar muy bien porque son vectoriales.

9. Usar una herramienta de plantillas para conectar el backend con el frontend. Hay que buscar la que más se adecue, no la que usamos siempre por comodidad. Siempre pensando en el rendimiento y el tamaño. Si hay que renderizar 4 cosas mejor usar [Mustache][3] que ocupa muy poco y es muy rápido que usar [Liquid][4] que es muy completo pero tarda mucho más.

10. Si necesitamos usar alguna librería de JavaScript buscar la que mejor haga lo que queremos y en menos espacio. Por ejemplo, en el caso de los móviles es mucho mejor emplear [QuoJS][5] (12kb) que [jQuery][6] (70Kb). También se va a ser offline, puesto que en algunos Android la caché solo permite ficheros de hasta 50Kb.

11. Empezar a no presentar el diseño a los cliente bajo un PSD. Esto debería haber muerto hace mucho tiempo. Los clientes pueden ser de muchos tipos, pero seguro que enseñándole un diseño base en HTML directamente estará más al corriente de lo que obtendrá que con un dibujo.

12. Optimiza el CSS. No uses [Bootstrap][7] porque todo el mundo lo usa. Dependiendo del proyecto le sobran muchísimas cosas. Quizá se adapte mejor [Skeleton][8], o [Amazium][9]. Incluso fabricarse un framwork uno mismo.

13. No ensucies cada lenguaje. El CSS con el CSS, el JavaScript con el JavaScript, y el HTML con el HTML. Intenta usar técnicas como [ooCSS][10] para el CSS.

14. Si es una aplicación rica en el cliente empezar a desarrollar sobre REST para pedir los datos usando el protocolo que lleva allí desde el 2000, el HTTP.

15. Si vas a usar un MVC en JavaScript plantéate cual de ellos es el más oportuno y sobre todo cual es el que menos "ensucia" el código. [Backbone][11] me parece que está bastante bien, pero en mi opinión ensucia mucho el HTML. [LungoJS][12] está bastante bien, así como [Angular][13]. Las plantillas en ficheros externos aunque el producción queden juntos, es decir, si vas a usar Mustache o Jade, crea las plantillas en ficheros separados.

Como conclusión diría que no hay que quedarse atrás nunca, hay que conocer todas las herramientas posibles y no anclarse en una determinada tecnología, estudiar todos los días, conocer nuevas librerías y técnicas, y separar bien el código para poder reutilizarlo como se debe. No hay que reinventar la rueda, pero tampoco hay que ponerle una rueda de camión a la bicicleta.

[1]: //qunitjs.com
[2]: //fortawesome.github.io/Font-Awesome
[3]: //mustache.github.io
[4]: //github.com/Shopify/liquid
[5]: //quojs.tapquo.com
[6]: //jquery.com
[7]: //twitter.github.io/bootstrap
[8]: //www.getskeleton.com
[9]: //www.amazium.co.uk
[10]: //oocss.org
[11]: //backbonejs.org
[12]: //lungo.tapquo.com
[13]: //angularjs.org
