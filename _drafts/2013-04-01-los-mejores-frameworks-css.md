---
layout: post
title: Los mejores frameworks css
description: Los mejores frameworks css para elaborar tus paginas web
image: bootstrap.jpg
author: Antonio Villamarin
tag: Programacion
---

Siempre los frameworks, más o menos encapsulados, han facilitado la vida al programador. Los hay para todos los lenguajes y en todas las formas. Más sencillos y más completos. Más enrevesados y más básicos. Más o menos útiles. De hecho en mismo PHP es en sí un framework de HTML para facilitar su interacción con el servidor.

Sin embargo los frameworks de CSS son algo un poco más reciente (no demasiado). Empezaron a tener un hueco en el mercado hacia el año 2005 y muchos diseñadores, y especialmente programadores con pocas habilidades de diseño, se subieron a adoptarlo.

Es curioso, porque CSS no es un lenguaje de programación al uso, así como HTML, son sencillos lenguajes de marcado. Pero con el tiempo se van complicando los desarrollos que se hacen con ellos y por extensión complicado cada vez más las etiquetas, los cierres, esos punto y coma, etc...

Han aparecido "ayudantes" de formas diferentes. Por ejemplo en la comunidad Ruby existe HAML, que es una forma simplificada de hacer HTML. Para CSS hay más (al menos que yo conozca), como por ejemplo Stylus (El que yo recomiendo), LESS, Compass, SASS, y algunos más.

En este artículo me voy a centrar en otra forma de facilitar el trabajo en CSS, y es la de emplear código ya escrito y empaquetado listo para usar.

Los frameworks de CSS son grupos de clases predefinidas en uno o varios archivos css que hacen tareas comunes a la hora de diseñar una plantilla para un sitio web.

Existen muchos tipos de frameworks, desde los resets, que envían a cero todos los bordes, márgenes, etc, para que en todos los navegadores el resultado se vea igual; lo normalizadores como normalizer.css que iguala los valores entre los diferentes navegadores; hasta los super completos con definiciones de botones, tablas, menúes, etc...

Soy firme defensor de emplear el código ya hecho y no repetir el esfuerzo en hacer lo mismo una y otra vez, y siempre que se conozca bien el CSS (especialmente CSS3) recomiendo encarecidamente el uso de frameworks.

Aquí hay varias partes de las que quiero hablar.

La primera es sobre los resets y normalizadores. Los resets hacen un trabajo repetitivo pues redefine todo en todos los navegadores para darle valores posteriormente de nuevo. Por eso creo que es mucho más eficiente utilizar un normalizador, que no redefine todo, solo aquello que diferencia a los navegadores.

Por otra parte los frameworks más desarrollados que definen elementos gráficos como los botones, existen de varias formas, desde los asépticos hasta los completos. Todos ellos incluyen la adaptación a diferentes resoluciones de pantalla, incluyendo los móviles, así como un grid para la maqutación.

Por asépticos me refiero a aquellos que definen varias etiquetas css o añaden clases que no hacen cambios radicales, sino que ayudan a una maquetación desde el principio con las cosas básica ya hechas. En este grupo puedo destacar Skeleton o el que yo mismo estoy desarrollando Grid.CSS.

*[Grid.css][1]*:

*[Skeleton][2]*: Es un framework sencillo que redefine algunos elementos básicos del HTML como los formularios, pero sin hacerle cambios en su forma o colores (sólo algunos muy leves). No tiene demasiadas cosas, pero las suficientes como para empezar una buena maquetación. Dispone de un Grid para la colocación de los DIVS, algo imprescindible a día de hoy en cualquier framework.

*[1kbgrid][3]*: Se trata de un grid sencillo sin cambios en los elementos HTML.

*[Responsive grid system][4]*: Un grid también sencillo.

Este tipo de framework es perfecto para los buenos diseñadores. Ahorra las partes básicas del css y luego el diseñador hace el diseño de verdad, los colores, la colocación de los elementos, formularios, etc...

Hay otros muchos más completos, como es el caso del Bootstrap de twitter, probablemente el más famoso de todos, que incluye una ingente cantidad de componentes. Un grid, por supuesto. Botones de diferentes colores, menúes de navegación, pestañas, intro, mensajes de error o información, y un largo etcétera.

*[Bootstrap][5]*:

*[Foundation][6]*:

*[Base][7]*:

Este tipo de componentes son muy útiles para los que no solemos saber diseñar porque prácticamente no hay que hacer nada, viene todo hecho. pero sí veo una gran pega, y es que si nos fijamos en muchos de los nuevos desarrollos, estamos twiterizando internet, con montones de páginas con el mismo diseño.

En un punto intermedio se encuentran algunos como:

*[amazium][8]*:

*[blueprint][10]*:

*[inuit][11]*:

A mí me parece que hay que diferenciar entra varias capas dentro de las plantillas.

Primero está la parte del núcleo, es decir, el comportamiento de las etiquetas de HTML. Aquí entiendo que deberían ir el normalizador, y algunas clases que ayuden a hacer cosas que ya hace el HTML más sencillo, del tipo .center para centrar un párrafo.

Segundo estaría la capa de layout, es decir la parte que da forma a la maquetación de la página. Esto son los grids. Los grids los hay de formas diferentes, aunque prácticamente ha quedado como un estándar el formato de divs dividido en 12, 16 o 24 celdas dentro de cada fila. Sin embargo existen otras formas de hacerlos, por ejemplo usando divs de tamaños predefinidos que tengan la propiedad display: inline-block;.

Como tercera capa diría que están los estándares que usaremos como fuentes, tamaños y colores generales de la plantilla. Algo que pueda ser sustituido fácilmente por el diseñador.

Como cuarta y última capa deberían estar las formas los elementos de uso habitual que el diseñador empleará a modo de plugins, como botones, tablas, mensajes, pestañas, etc... Esta capa es la que el diseñador deberá dar forma y emplear de manera inteligente para hacer su diseño exclusivo.

Por supuesto debería haber una quinta capa del usuario que es la que definiría los ids de la pagina concreta y darle color y forma al layout. También incluiría las definiciones de las mediaqueries para adaptarlo a móviles.

Con esta estructura el diseñador tendría que tocar, seleccionar o adaptar la tercera y cuarta capa y crear la quinta, pero también podría solamente hacer la quinta, eso ya dependería de lo exclusivo que quiera el diseñador hacer el desarrollo.