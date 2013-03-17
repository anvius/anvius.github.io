---
layout: post
title: "Manual práctico de ZenCoding"
description: "Manual práctico de ZenCodding. Escribe código HTML como un ninja con ZenCoding y tu IDE favorito"
image: zencoding.jpg
tags:
- programacion
- html
- zencoding
- emmet
- sublime text 2
---

ZenCoding es un plugin existente para muchos editores e IDE's que se ha extendido mucho en los últimos tiempos debido a su facilidad para aumentar la rapidez a la hora de escribir HTML, lo que a la mayoría de los desarrolladores nos parece una de las partes más tediosas de tratar (al menos a mí).

ZenCoding empezó siendo un plugin JavaScript, pero su aceptación por parte de la comunidad ha sido tan rápida que ya está portado a la inmensa mayoría de los editores.

En mi caso, el editor que uso para programar es sublime Text 2, que desde aquí se lo recomiendo a todo el mundo.

Vamos a empezar.

Lo primero que debemos hacer es instalar el plugin para nuestro editor. Lo hay para NetBeans, Eclipse, NopePad++, Geany, Gedit, TextMate, y un largo etc. Desde su [web][1] en Google Code se pueden descargar la mayoría.

Una vez instalado, en la mayoría de los editores habrá que reiniciar y después a escribir HTML fácilmente. Hay que recordar que para que normalmente funcione, según el editor, habrá que estar en un fichero HTML y probablemente guardado como tal para que ZenCoding detecte que es así. En algunos editores, sus plugins ya han cambiado al plugin Emmet, de la misma empresa.

Con todo listo vamos a ver algunos comandos. Anotar que para que cambie el código de la sitaxis de ZenCoding a HTML hay que pulsar Tab al final de la sentencia y lo transformará.

Se puede iniciar un documento HTML completo, por ejemplo en HTML5 con solo un comando:

	html:5

Esto daría como resultado el siguiente código:

	<!doctype html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
	</head>
	<body>
		
	</body>
	</html>

Hay alternativas para hacerlo HTML 4 Strict, por ejemplo, o cualquier de otros.

	html:4s

Resultado

	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
	<html lang="en">
	<head>
		<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
		<title>Document</title>
	</head>
	</html>

Además, por ejemplo sublime text, nos sitúa directamente en la posición para escribir dentro del código. Esto a veces puede ocasionar problemas, en el sentido de que ZenCoding espera que escribamos html y no más ZenCoding. Para seguir escribiendo ZenCoding habrá que mover el cursor a cualquier sitio y volverá al sistema ZenCoding.

Podemos añadir elementos dentro de otros elementos con el símbolo de mayor que ">", por ejemplo:

	div>ul>li

Resultado:

	<div>
		<ul>
			<li></li>
		</ul>
	</div>

También multiplicadores:

	div>ul>li*5

Resultado:

	<div>
		<ul>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
		</ul>
	</div>

Podemos sumar dos grupos de elementos si están al mismo nivel, agruparlos con los paréntesis y añadir texto literal, por ejemplo:

	html>(head>title{Titulo de mi web})+body>header+article+footer

Resultado:

	<html>
	<head>
		<title>Titulo de mi web</title>
	</head>
	<body>
		<header></header>
		<article></article>
		<footer></footer>
	</body>
	</html>

También podemos numerar múltiples entradas con el símbolo "$", añadir clases (.) e ids(#), y añadir atributos:

	div#identificador.clase>ul#mi_menu>li#item$*5>a[href="http://direccionweb"]

Resultado:

	<div id="identificador" class="clase">
		<ul id="mi_menu">
			<li id="item1"><a href="http://direccionweb"></a></li>
			<li id="item2"><a href="http://direccionweb"></a></li>
			<li id="item3"><a href="http://direccionweb"></a></li>
			<li id="item4"><a href="http://direccionweb"></a></li>
			<li id="item5"><a href="http://direccionweb"></a></li>
		</ul>
	</div>

Para los que, como yo, les parece tedioso rellenar contenido para ver cómo queda, tenemos el archiconocido Lorem Ipsum:

	lorem*5

Resultado:

	<div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dolorum quibusdam odit eveniet iste harum minima numquam distinctio cupiditate repellendus aliquam dolore aspernatur inventore adipisci mollitia accusantium facere porro ea fugit.</div>
	<div>Quaerat temporibus cum deserunt deleniti molestias assumenda aut quas eveniet labore consectetur libero blanditiis a maiores sit pariatur aliquam cumque id quod animi possimus. Reiciendis quos fugit vitae voluptate quis.</div>
	<div>Iusto sunt dignissimos blanditiis veniam harum asperiores reiciendis esse sint aperiam tempore dolorem possimus eius corrupti molestiae deserunt repudiandae quo voluptatum cupiditate assumenda distinctio quis labore atque illum in nisi!</div>
	<div>Veniam repellat atque eaque quisquam ab eos consequuntur perspiciatis dolorum nemo distinctio sed quis labore autem odit iusto repellendus minus libero quos rem quasi debitis cupiditate voluptate eveniet repudiandae sunt?</div>
	<div>Magni dolorum dolores ullam laudantium nobis natus quas nisi debitis sunt minima eveniet omnis repellat architecto numquam a beatae officia totam recusandae rerum ex sint! Ducimus ratione mollitia enim vitae?</div>

Hay unas cuantas opciones más, también para css que se pueden consultar en su [web][1]. Es una forma my interesante y fácil de escribir html rápidamente sin olvidarnos de cerrar etiquetas o escribir tantísimo.

Para finalizar voy a poner un ejemplo completo de esqueleto de sitio web tipo boilerplate:

	<!doctype html>
	html[lang="es"]>(head>meta[charset="UTF-8"]+title{Titulo}+script[src="js/modernizr.js"])+body>(header#header>hgroup>(h1{Titulo h1})+h2{Subtitulo})+(aside#menu>h2{Menu}+ul>li#menuitem)+(section#content>(header#header_articulo>h2{Articulo})+(article#articulo>p>lorem*3)+footer#footer_articulo>small>lorem)+footer#footer>p{&copy; 2013}

Resultado:

	<!doctype html>
	<html lang="es">
	<head>
		<meta charset="UTF-8">
		<title>Titulo</title>
		<script src="js/modernizr.js"></script>
	</head>
	<body>
		<header id="header">
			<hgroup>
				<h1>Titulo h1</h1>
				<h2>Subtitulo</h2>
			</hgroup>
		</header>
		<aside id="menu">
			<h2>Menu</h2>
			<ul>
				<li id="menuitem"></li>
			</ul>
		</aside>
		<section id="content">
			<header id="header_articulo">
				<h2>Articulo</h2>
			</header>
			<article id="articulo">
				<p>
					<span>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cupiditate sapiente dolor eum rem et ratione quisquam vitae reprehenderit fuga non dolorum enim placeat adipisci saepe ex impedit distinctio ipsum corporis.</span>
					<span>Saepe accusamus voluptatibus eum iure tempore iste magni quisquam explicabo eius vitae inventore enim deleniti quae tenetur tempora deserunt qui nesciunt vero facilis veritatis. Tempora ipsam fugit id tempore aperiam!</span>
					<span>Placeat quidem tenetur debitis libero aut quos ducimus similique eligendi incidunt modi harum ratione ea laboriosam deleniti delectus sapiente at ipsam adipisci architecto tempore. Saepe facilis atque ab inventore odit!</span>
				</p>
			</article>
			<footer id="footer_articulo"><small>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quam labore veritatis sint quis impedit tenetur in quaerat aspernatur praesentium similique obcaecati nostrum molestias officia. Quos ullam quidem mollitia esse dolorem!</small></footer>
		</section>
		<footer id="footer">
			<p>&copy; 2013</p>
		</footer>
	</body>
	</html>

[1]: http://code.google.com/p/zen-coding/
