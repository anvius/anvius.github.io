---
layout: post
title: Como crear un virtual host local
description: Como crear un virtual host local en lighttpd, apache y nginx.
image: virtualhost.jpg
tags:
- hosting
- servidor virtual
- lighttpd
- local
- apache
- nginx
---

Antes de empezar, habría que aclarar para los más novatos, qué es un virtual host y para qué puedo querer uno local.

### ¿Qué es un virtual host? ###

Un virtual host es como se denomina a un "servidor" virtual dentro de un servidor real. Por ejemplo, si nosotros tenemos un servidor para alojar nuestras páginas web, primero tenemos configurado el servidor para que responda a las peticiones que se le hacen desde el exterior y después dentro de este servidor debemos crear un "servidor virtual" que responda a un determinado dominio o grupo de dominios. Este servidor virtual (que no es un servidor como tal) lo que hace es crear un entorno sobre ese dominio, donde puede definirse la carpeta donde estará, quién puede acceder a él, etc...

### ¿Porqué querría definir un virtual host local? ###

Cuando se programan servicios web y debemos hacer pruebas de la programación, es cómodo no tener que subir la programación que hemos hecho a un servidor o a un hosting para  probarlo, sino probarlo en nuestro equipo directamente. Para eso creamos un virtual host local con un dominio "inventado" y así podemos probarlo con comodidad, para que cuando esté listo podamos subirlo a nuestro servidor en producción.

### Crear virtual host local ###

Para definir un virtual host en un servidor de producción, normalmente tendríamos que hacer dos cosas; primero redirigir las peticiones del dominio al servidor web de la máquina con, por ejemplo, bind9, definiendo sus dns. Segundo Crear el virtual host en nuestro servidor de páginas web añadiendo el dominio, puerto, etc...

En el caso de ser local, no es necesario tocar el bind, porque nuestra máquina, al primer sitio que va a revisar el nombre del dominio es a nuestro fichero hosts en caso contrario es cuando busca las dns del dominio en internet. Esto es así en linux, windows y mac, aunque en cada uno de ellos está situado en una parte del sistema. En linux y mac se encuentra en la carpeta /etc/hosts, mientras que en windows está en la ruta c:/windows/system32/drivers/hosts.

Este fichero tiene una estructura muy sencilla, indica la ip y después el host en cada linea, de la siguiente forma (recordar que esto solamente es el local).

{% highlight apache %}
127.0.0.1    localhost
{% endhighlight %}

localhost es nuestro virtual host local por defecto, solamente tendríamos que definir en nuestro servidor web en qué carpeta queremos que lea.

Pero normalmente no estamos desarrollando solamente una cosa, y nos puede venir bien definir nuestros propios dominios.

A modo de ejemplo voy a definir el dominio inventado **prueba.dev**.

{% highlight apache %}
127.0.0.1    localhost
127.0.0.1    prueba.dev
{% endhighlight %}

Guardamos y ya está.

Hay que decir que 127.0.0.1 es la ip local de nuestro equipo. Si lo tuviéramos en otro equipo podríamos definirlo con esa ip.

Ahora debemos cambiar el servidor de páginas web.

### LightTPD ###

Debemos ir al directorio de configuración de LightTPD en nuestro equipo (si pusimos 127.0.0.1). En linux y mac está en el directorio /etc/lighttpd (esta ruta puede cambiar según la versión). En windows donde hayamos instalado el LightTPD (Esto es igual en Apache y nGinX). Editamos el archivo virtualhosts.conf y añadimos un host virtual con el dominio inventado que hemos creado al final del fichero.

{% highlight lighttpd %}
$HTTP["host"] == "prueba.dev" {
    server.document-root = "/home/antonio/miweb/"
    server.name = "prueba.dev"
}
{% endhighlight %}

Hay muchas más opciones que pueden añadirse, como si queremos que se ejecute python o queremos que se haga visible nuestro directorio al entrar, pero con esto para ejecutarlo nos basta.

Después reiniciamos el servidor web. En linux y mac nos valdría con "sudo service lighttpd restart". En windows reiniciamos con el programa que hayamos instalado.

### Apache ###

El archivo que tenemos que editar se llama apache2.conf o httpd.conf, dependiendo de la versión.

{% highlight apache %}
<VirtualHost *:80>
    DocumentRoot /home/antonio/miweb
    ServerName prueba.dev
</VirtualHost>
{% endhighlight %}

Reiniciamos apache y listo.

### nGinX ###

En nGinX creamos un fichero para el virtual host en la carpeta "conf.d/" de la configuración (Recordamos que las configuraciones en LInux y Mac suelen estar en /etc y en este caso /etc/nginx/), llamado prueba.dev.conf y añadimos lo siguiente:

{% highlight nginx %}
server {
	listen       127.0.0.1:80;
	server_name  prueba.dev;
 	location / {
		root /home/antonio/miweb;
		index index.html index.htm index.php;
	}
}
{% endhighlight %}

Y por supuesto reiniciamos el nGinX.

### Uso ###

Ahora podemos abrir nuestro navegador favorito y poner la dirección prueba.dev y veremos el directorio al que lo hemos redirigido. En algunas ocasiones no funciona correctamente, porque el navegador se va a burcar la ruta a internet. Esto lo solventamos añadiéndole una barra al final, tal que prueba.dev/.

Y esto es todo, ahora a programar :)
