---
layout: post
title: Modelo Vista Controlador adaptado a la web
description: Paradigmas de programacion Modelo Vista Controlador adaptado a la web
image: 
author: Antonio Villamarin
tag: Programacion
---

La estructura de programación de moda es MVC o Modelo-Vista-Controlador. Esta forma de separar en capas diferenciadas es muy útil en la mayoría de los proyectos, bien de escritorio/móvil, bien web.

Si no conoces este paradigma, en resumen se trata de separar la programación de tu proyecto en tres partes.

1. **Modelo**: Aquí se programan todo aquello relacionado con las bases de datos, es decir, las entradas y salidas de datos y se devuelven como se necesiten desde el programa principal. Siendo imaginativos sería como acceder a los datos de algo a través de un API y el API sería el modelo.
2. **Vista**: Aquí se programa la parte visual del software, o lo que es lo mismo, la parte que usa el usuario. En el caso de un sitio web la parte de HTML, CSS y JavaScript normalmente.
3. **Controlador**: Es la lógica del programa. Aquella que le pide al modelo los datos y los muestra en la vista. Vamos, lo que viene a ser el núcleo.

Este modelo facilita algunas partes de la programación para hacerlas más, mucho más, ágiles, como que al tener separado el código en diferentes capas, cuando se hacen modificaciones sobre la plantilla (por ejemplo) solo hay que tocar esta parte que tiene un tipo de código más homogéneo y el resto no hace falta tocarlo para que funcione bien.

Además, este modelo ha facilitado la aparición de muchas, muchísimas utilidades orientadas a cada una de las capas, como pueden ser los motores de plantillas, o que se convierta en un estándar en los frameworks como CodeIgniter, RubyonRails o Django.

En cuanto a cómo se pasan los datos de una a otra capa debemos pensar en la forma más sencilla posible. La comunicación entre estas capas debe ser rápida y limpia, para que aquel programador que se encargue de la vista no tenga que tocar código en los controladores y viceversa. La forma más fácil de hacer es predefinir unas cuantas variables que pasarán del controlador a la vista, y la vista se encargue de emplearlas allí donde las necesite. Igualmente en la comunicación entre modelo y controlador.

En mi caso, cuando me enfrento a una programación que se divide en dos partes bien diferenciadas, como pueden ser cliente y servidor (caso de los sitios web), lo estructuro de un modo un poco diferente, aunque teniendo presente el modelo MVC. El porqué cambio algo el modelo es sencillo, creo que la parte de cliente y la parte de servidor deben estar completamente separadas, por muchas razones, pero principalmente porque cada cosa va programada con un lenguaje diferente. No me gusta mezclar lenguajes de programación o lenguajes de marcado entre sí, y al igual que no se debe añadir CSS dentro del HTML, tampoco php, python, etc... entre sí.

Por una parte creo la parte de cliente:

1. **Cliente (Vista)**: Esta será la parte que verá el usuario de la aplicación. No tiene que ver con administración y parte de usuario, sino únicamente con la vista.
	1. *Diseño*: Aquí estaría el HTML y el CSS (que a su vez están separados).
		1. *Layout*: Plantilla principal. HTML Base para todas las páginas y CSS global.
		2. *Componentes*: Aquí irían los diseños de los componentes específicos.
		3. *Contenido*: Aquí va la parte de contenido estático, como textos, imágenes, etc...
	2. *Acciones*: Aquí irían las partes ejecutables, normalmente JavaScript.
2. **Socket/Ajax (Intermedio)**: Comunicación Cliente Servidor.
	1. *Cliente*: Aquí iría la comunicación con el servidor. Normalmente también JavaScript, pero usando Ajax.
	2. *Servidor*: Aquí está la comunicación con el cliente (el Ajax).
3. **Servidor (Modelo y Controlador)**: Aquí irá todo lo que depende del servidor.
	1. *Modelo*: Aquí va todo lo relacionado con la base de datos.
	2. *Controlador*: Esta es la lógica del programa.
4. **Global**:
	1. *Nucleo*: Esta es la base de funciones y utilidades que pueden ser empleadas en las otras áreas.
	2. *Herramientas*: Librerías y herramientas de apoyo. Normalmente clases concretas y scripts para realizar acciones concretas en el servidor como el cron.

Además en cada una de estas hay que hacer una diferenciación entre lo programado por nosotros y de las librerías que hemos añadido de otros (vendor).

Esta forma de diferenciar las capas me permite que cualquier cambio por más grande que sea, se circunscriba únicamente a un área.

Hay que tener en cuenta, que esta separación la hago así, un poco más complicada probablemente por los lenguajes de programación que suelo usar, pero que algunas pueden variar si éstos cambian. Como referencia decir que se trata de HTML5, JavaScript+jQuery y CSS3 en las vistas. Los modelos los gestión con PHP y la librería Idiorm (altamente recomendado por su simplicidad y ligereza) o RedBean en el caso de MySQL o SQLite. PHP (aunque últimamente más Python) y Bash en la parte del controlador.