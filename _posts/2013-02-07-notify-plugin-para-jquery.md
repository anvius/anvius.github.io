---
layout: post
title: "Notify: plugin para JQuery"
description: Plugin para jQuery que permite mostrar un mensaje de notificación fijado a la ventana de la página.
image: notify-jquery.png
---

JQuery Notify es un plugin que permite crear un mensaje de alerta, información u oferta desplegable en la parte superior de la pantalla cuando el usuario está viendo tu web. Es un componente de [Grid CSS][1].

Este plugin no necesita añadir CSS especial ya que viene incluido en el propio archivo js. En cualquier caso, si quisieras modificar el aspecto del mensaje existen dos opciones.

La primera de ellas se trata de añadir en la misma llamada al plugin el color de fondo y el del texto. La segunda es que puedes añadir una configuración CSS sobre la clase *.notify-message*.

Ahora vamos a ver cómo implementarlo.

Primero debemos añadir el mensaje que queremos que aparezca en el notify.

	<div id="anyIDtag">Mensaje de notificación</div>

Ahora añadimos los ficheros js, que deberían ir al final del html, justo antes de "<body>".


	<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
	<script src="notify.jquery.min.js"></script>
	<script>
		$(document).ready(function(){
			$('#anyIDtag').notify();
		});
	</script>

Con esto ya tendríamos funcionando el plugin al cargar la página.

Vamos ahora con las opciones.

El plugin incorpora cuatro posibles opciones a la hora de su carga, que son: color, background, close, active.

**color**: Se usa para especificar el color del texto que aparecerá en el mensaje. Se especifica como **color: "#FFF"**

**background**: Se trata del color de fondo del mensaje. El color en formato hexadecimal.

**close**: Por defecto es **false** y se usa para indicar si queremos que aparezca un *aspa* para su cierre definitivo o un *flecha* para su ocultación temporal.

**active**: Se emplea para indicar si el mensaje debe aparecer activo o por el contrario debe aparece la flecha para desplegar el mensaje. por defecto es activo.

Ejemplo:


	<script>
		$(document).ready(function(){
			$('#anyIDtag').notify({ // Optional parameters. Default values.
				active: true, // Muestra el mensaje.
				close: true, // Muestra el aspa para cerrar.
				color: "#444", // Color de la fuente gris al 80%.
				background: "#FF9" // Color de fondo amarillo suave.
			});
		});
	</script>

Como decía al principio, puedes cambiar el formato del mensaje definiendo en CSS la clase *.notify-message* como por ejemplo:

	.notify-message { font-size: 16px; }

Hay que tener en cuenta que el plugin, coge por defecto la configuración de fuente que esté definida en la página, tamaño, negrita, etc...

Más información: [Web][2] - [Descarga][3] - [Código fuente en GitHub][4]

[1]: //www.gridcss.com
[2]: //notify.gridcss.com
[3]: //github.com/zeura/notify.jquery/tarball/master
[4]: //github.com/zeura/notify.jquery












