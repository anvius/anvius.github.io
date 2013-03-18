---
layout: post
title: Algunos cambios en el blog.
description: Algunos cambios en el blog. Probando nuevas funcionalidades.
image: blog.jpg
tag: General
---

La verdad es que en general estoy bastante contento con el blog configurado bajo Jekyll, y con el servicio que da en este sentido Github para alojarlo.

Poner en marcha un blog básico es bastante fácil, así como sincronizarlo con Github para tenerlo activo en tiempo real. Mucho mejor y más rápido que Wordpress, por ejemplo. Pero no todo es tan sencillo.

He hecho una actualización de la plantilla, cambiando la cabecera, el pie, el menú de navegación, y algunos pequeños cambios sin mucha importancia. También he minificado (si es que esto puede decirse) el CSS para un mejor tiempo de respuesta. Todos estos cambios van del lado de la plantilla con lo que al fin y al cabo es como en cualquier otra página web, HTML, CSS y Javascript. Espero que estos cambios sean del agrado de todos.

Sin embargo he empezado a tener problemas con Jekyll a la hora de la paginación de las entradas. En realidad el problema es con Github, pues en local, en mi equipo me funciona correctamente, pero online no. Si alguien tiene alguna sugerencia lo agradecería.

No he conseguido que lea correctamente la variable paginator en Liquid así:

	for post in paginator.posts
		blablabla
	endfor

En cuanto a otros cambios que he realizado, he añadido entradas relacionadas a cada entrada, que siempre viene bien para los nuevos visitantes, al menos en mi caso, cuando llego a un blog que no conozco a través de algún artículo, los enlaces relacionados me mantienen más tiempo en el blog. Esto se hace con la extensión LSI que está integrada en Jekyll, bajo la variable **site.related_posts**.

También he creado una página de categorías mientras reordenaba el menú del blog y una pequeña navegación entre entradas al pié de la misma.

En el tema de las suscripciones, he eliminado definitivamente la suscripción por rss (digo el archivo rss.xml) y dejado únicamente el atom.xml. Aunque ahora está redireccionado a Feedburner, obviamente el fichero existe en el alojamiento para que éste lo lea. Debido al lamentable cierre de Google Reader, empiezo a pensar que Feedburner será una de las próximas opciones que esta empresa cerrará y estoy buscando alternativas.

Por último una crítica más a Google. Intentaba añadir el microformato vCard del autor, que permite que en varios buscadores aparezca una pequeña imagen a modo de avatar al lado de la búsqueda, y permite tener una mayor visibilidad. Desgraciadamente Google obliga a poner esta vCard con la dirección de Google+ y no con la del propio blog. Un obligación más que esta empresa impone para darle relevancia a su red social.

En la misma dirección parece que están yendo otras decisiones, como el cierre de Reader que antes mencioné. Es una obstinación que no llego a entender, ya que en vez de ofrecer y promocionar mejores servicios que su competencia (como los muy buenos HangOut) intentan forzar su uso.

Así que, aunque tengo cuenta en Google+, que no uso, he eliminado el enlace a esta red social que ya tenía.

Para terminar con lo que creo que será una buena noticia, estoy preparando algunos cursos y estoy viendo cómo configurarlo en Jekyll para que tengan su propia sección de cursos. Serán cursos de todo un poco, pero me gustaría que cada uno tuviera su espacio de relevancia. El primero que estoy preparando es sobre cómo usar Git que espero tenga buena acogida, ya que me lo habían pedido algunas personas.