---
layout: post
title: Un estándar para PHP
description: PHP necesita un estándar para poder seguir creciendo
image: elefantephp.jpg
author: Antonio Villamarin
tag: Programación
---

La historia de PHP es bastante interesante.

En 1994,  Rasmus Lerdorf, el creador de PHP, quería añadir a su currículum un contador de visitas y conocer quién lo visitaba. Para ello se puso a desarrollar PHP en Perl (un lenguaje creado 7 años antes) bajo la arquitectura de CGI y algunos ficheros compilados en C. El 8 de Junio de 1995 publicó el resultado bajo el nombre de PHP (Personal Home Page), al que le había añadido un analizador sintáctico al que llamó *Form Interpreter* de ahí que al final su nombre fuera PHP/FI. PHP fue incorporando algunos elementos nuevos, entre ellos la capacidad de poder integrarse en un documento HTML siendo invisible PHP para el navegador, algo que otros lenguajes un poco anteriores no podían hacer (y singuen sin poder hacerlo), como Perl, Ruby o Python.

En 1997, los programadores Zeev Suraski y Andi Gutmans reescribieron por su cuenta el analizador sintáctico *Form Interpreter* y 1998 publicaron lo que se pasaría a llamar PHP3, reescribiendo el motor denominado *zend engine* y cambiando el nombre por uno recursivo como es el de *PHP: Hypertext Preprocessor*. Con esta publicación crearon la empresa *Zend Technologies*.

En el año 2000 esta empresa publicó PHP4 bajo el motor *zend engine 1.0* en el que incorporó la programación orientada a objetos de forma algo somera, por ejemplo sin herencia. Bajo PHP4 la expansión de que tuvo fue increíble. Era fácil de aprender lo básico, se podía ejecutar en cualquier hosting y enseguida tenías  funcionando lo que necesitabas con unas pocas líneas de código.

En 2004 Zend Technologies sacó PHP5 que empezó a tomar mucha más fuerza a partir del año 2006 hasta hoy.

Aunque existe en beta PHP6, no hay todavía una versión estable y su aparición ha sido retrasada en varias ocasiones.

Y ¿a qué me lleva todo ésto?

Pues bien, el hecho de que PHP se haya desarrollado de esta forma bastante inusual, haciendo añadidos desde un motor muy básico y sencillo, ha hecho de PHP un lenguaje muy poderoso, pero sin ningún tipo de reglas o convenciones, algo que se vió hace ya bastantes años con la llegada de grandes programas en este lenguaje, y sobre todo cuando llegó a la empresa para desarrollar plataformas. por poner un ejemplo, la notación de las funciones es diferente según qué función estemos usando aunque se trate de dos funciones relativas a los *strings* por ejemplo. En unos casos emplean la notación C, separando palabras con guiones bajos y en otras no. En algunos casos las funciones comienzan por *str_* y en otras terminan por *string*, etc... Esto no favorece nada la comprensión del código y obliga a los programadores a consultar las funciones constantemente y por supuesto retrasa el trabajo.

El código de PHP no está bien organizado debido a que no hay convención entre los programadores, o directrices claras de los creadores, sobre donde es mejor poner una llave, líneas en blanco o cómo y cuánto debería tabular.

Estos inconvenientes y la disminución de los precios de servidores han hecho, creo yo, que en los últimos tiempos PHP haya perdido parte de su encanto en favor de otros lenguajes como Python. Python sigue sin ser tan fácil a la hora de instalar un servidor (cada día más) pero a cambio facilitan mucho más la creación de software potente entre varios programadores por convenciones ya establecidas.

Desde hace un tiempo, y con el auge de los frameworks en PHP, ha surgido un grupo denominado [PHP-FIG][1] cuya intención es dotar a todos estos frameworks de una convención común para facilitar la lectura de código entre diferentes programadores. Este grupo lo forman programadores que pertenecen a proyectos con frameworks como Symfony o PHPBB que son los que tienen derecho a voto. Cualquiera puede solicitar el ingreso en este grupo. A día de hoy cuenta con 26 miembros con derecho a voto. Eso sí, cualquiera puede proponer un estándar que será aplicado a los frameworks inscritos en el grupo.

Hasta ahora tienen 4 estándares aprobados, denominados PSR, del 0 al 3. Uno de los más importantes es el PSR-0 que nos dice cómo denominar los ficheros de las clases para que puedan ser cargados con un *autoload*, los *namespaces*, etc y por ejemplo ser incorporados a *composer*.

Evidentemente, no nos tiene que gustar todo. Personalmente no me gustan algunas decisiones que han tomado respecto al estilo de programación, como por ejemplo, que la llave de apertura de una estructura, si se trata de una clase va en la línea siguiente y si se trata de un if va en la misma línea. En mi caso habría preferido que siempre fuera en la misma línea.

Pero seguir un estándar tienen una gran ventaja, y es que los programadores que vayan a leer nuestro código lo entenderán con mayor facilidad. También ayuda a sumergirnos en cualquier framework que siga este estándar o a publicar código libre que pueda ser adaptado.

En estos momentos me encuentro traduciendo todas estas convenciones en mi [github][2] en las ramas **spanish** y **correcciones** junto con otra persona que está colaborando, esperando que lo incorporen oficialmente (Si quieres colaborar no dudes, colabora :)). No todo el mundo domina el inglés, tampoco yo, y eso facilita mucho las cosas para mantener estas normas cuando el código provenga de la comunidad hispana.

En conclusión diría que gracias a *[Symfony 2][3]* (en la comunidad hipanohablante está **[Symfony][4]** de [Javier Eguiluz][5]) y ahora también *[Laravel][6]* (aunque este no está en el FIG) se está creando un estándar de facto que le va a dar a PHP lo que le faltaba principalmente, que era convención.

Otras cosas que se le han achacado a PHP, principalmente en el pasado, es que era lento por ser interpretado o que su código byte no estaba optimizado. Esto son problemas que pueden existir, pero que a día de hoy están más que solventados. No es más lento que Python o Ruby, y es tan escalable como éstos. PHP tiene una comunidad monstruosa detrás y esto junto al hecho de tener un estándar creo que le va a dar una larga vida como lenguaje dominante en internet del lado del servidor.

<small>Imagen de http //www.flickr.com/photos/kea42/4372405053</small>

[1]: //www.php-fig.org/
[1]: https://github.com/villamarin/fig-standards
[3]: //symfony.com
[4]: //symfony.es
[5]: //javiereguiluz.com
[6]: //laravel.com