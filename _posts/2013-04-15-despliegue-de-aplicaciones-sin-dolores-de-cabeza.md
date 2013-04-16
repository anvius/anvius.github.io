---
layout: post
title: Despliegue de aplicaciones sin dolores de cabeza
description: Cómo desplegar una aplicación desde su estado de desarrollo a su estado de producción y no morir en el intento.
image: s3ruby.jpg
author: Antonio Villamarin
tag: Programacion
---

Cuando uno busca información sobre métodos para trabajar más eficientemente en el desarrollo de software encuentra montones de sistemas muy útiles y bien pensados. Lamentablemente todos estos sistemas suelen estar orientados a grandes equipos de programación y nunca a pequeños o muy pequeños equipos, incluso de uno solo.

Existen muchas pequeñas empresas, muchísimas más que empresas con equipos grandes de desarrollo, pero desgraciadamente son las grandes olvidadas a la hora de sistemas específicos para ellas.

Por ejemplo kanban, es un sistema de trabajo basado en tarjetas creado inicialmente por Toyota y que resulta bastante útil, pero en equipos de 2 o 3 personas no resulta ser muy eficiente.

Es cierto que para equipos tan pequeños organizarse en equipos es mucho más sencillo, pero nunca está de más que puedan tener ciertas herramientas, cierta organización para llevar a cabo su tarea más eficientemente.

Muchos se sentirán identificados con cómo se hacen algunos desarrollos, incluso de aplicaciones grandes, que gestionan grandes bases de datos, subiendo los ficheros del programa por ftp al servidor de producción directamente, haciendo cambios a mano en ese mismo servidor, no teniendo versiones de lo que se ha desplegado, ver que no funciona y volver a la copia de seguridad que se tenía anterior, etc... Esto tiene una sencilla solución siguiendo una pautas que son posiblemente más sencillas de seguir que todo ese proceso de subir los ficheros a partir de Filezilla.

En mi caso, acostumbrado a trabajar en entornos pequeños sigo una pautas (hay que decir que en ocasiones me las salto :)) bastante sencillas en el desarrollo de aplicaciones. Prácticamente todos los desarrollos que he hecho han sido para terceros, y cuenta mucho que el cliente vea que todo funciona correctamente.

## Proceso de desarrollo.

Lo primero que hago para empezar un desarrollo es la preparación, es decir, tener todo listo para programar. Qué voy a necesitar para desarrollar una determina web por ejemplo. Normalmente necesitaré un editor o un IDE, normalmente SublimeText2, y si es muy grande el proyecto en ocasiones uso NetBeans. También necesito tener instalado git para el control de versiones, un sitio donde crear un repositorio central para compartir, normalmente Github y algunas herramientas accesorias, como por ejemplo Stylus para crear el CSS si se necesita, un procesador de Markdown a HTML en algunos casos, quizá algún programa de scrapping porque debo tomar algunos datos de una determinada web o liquid para generar plantillas (esto son solamente ejemplos).

Una vez todo preparado y transmitido para todo el equipo creo una carpeta para el desarrollo al que le pongo el nombre de la aplicación dentro de mi carpeta *código* en *Home*, y creo un *git init* para inicializar el control de versiones.

Después creo las ramas que necesito para desarrollar. Todos los miembros del equipo empleamos dos ramas principales, *master* y *dev*. *Master* es la rama principal, es decir, la que será de producción, así que en principio no se toca hasta estar seguros de que funciona. *Dev* es aquella donde vamos a tener el programa en desarrollo, pero aquí no programamos nada, vamos creando ramas de esta rama para ir creando el programa, y una vez testado la juntamos con la rama de desarrollo.

Cuando se ha probado todo entonces lo juntamos todo en la rama *master*, manteniendo abierta la rama *dev* y etiquetamos ese *commit* de la rama master como la versión.

Otro aspecto a tener en cuenta es el uso de dependencias de nuestro programa. Si vamos a emplear una o varias librerías hechas por nosotros o bien hechas por terceros para nuestro proyecto, empleamos composer, que nos permite satisfacer todas las necesidades de las dependencias, por ejemplo si empleamos un framework como **CodeIgniter** o **Symfony**, o si usamos algún componente como plantillas **Mustache** por ejemplo. Composer está pensado principalmente para trabajar con PHP, ya que es comunidades como python, ruby o node ya tienen su propio composer. Por lo tanto composer pasa a formar parte del proyecto, aunque luego no lo enviemos a producción.

Todos los fichero que no se desplieguen lo metemos en un fichero para no tenerlos en cuenta y que luego pueda leerlos nuestro script a la hora de enviarlos. También creamos un fichero *.gitignore* que permite quitarnos nuestros ficheros del repositorio.

Por supuesto también usamos un sistema de notas, mejor dicho issues, en github, para estar al día de 3 cosas: ¿Qué hicimos cada uno ayer?, ¿Qué problemas han surgido? y ¿Qué voy a hacer hoy? Con esto cubrimos tada la información que necesitamos si el trabajo está bien repartido. Es más, aunque solamente sea uno el programador, está bien seguir esta pauta para uno mismo porque siempre tiene una idea más clara del *momento* en el que está del proyecto.

## Pruebas.

Una vez terminado el desarrollo hacemos pruebas en la fase de pruebas, y los test unitarios. Ni mucho menos hacemos test para todo, solamente para las partes críticas (ya sé que debería ser para todo, pero a veces tengo la sensación que de que hago más test que programación efectiva). También es muy importante comprobar el uso de la base de datos, por supuesto sin usar la base de datos de producción. Puede ser una copia (que siempre es lo conveniente o si es demasiado amplia se puede generar una con datos aleatorios a partir de un script. Existen varios scripts que guardan datos semireales en una base de datos. En mi caso tengo un hecho para estas circunstancias. Hay que olvidarse de rellenar la base de datos con *prueba1*, *prueba2* y *prueba3*, porque hay muchos casos en los que necesitaremos comprobar una cantidad mayor de datos, por ejemplo para las búsquedas o la paginación.

Aquí también se hacen las pruebas de rendimiento. Hay que comprobar que el rendimiento es adecuado y anotar todo aquello que sea susceptible de mejora para después crear una rama de fixes para mejorar estas partes.

Una vez que todo se adecua a las especificaciones y se han hecho las correspondientes validaciones con los test. Si todo está Ok, hay que pasarlo a producción.

## Pre-producción.

En preproducción se puede probar en un entorno cerrado de prueba para el cliente, o si las pruebas son para nosotros esta parte se integraría en la anterior.

Para la pre-producción y comprobar que todo va bien, nosotros empleamos el mismo método para desplegar que en producción, pero en un entorno acotado, que suele ser o un vps para estas pruebas o bien una máquina virtual en nuestro equipo. Allí se despliega y se prueba. Si todo ha ido bien pasará a producción. Esto no solemos hacerlo en realidad, solamente en los casos en los que hay que enseñárselo a un cliente o que la cantidad de cambios hecha sea tan grande que haya aumentado exponencialmente la posibilidad de bug.

## Producción.

Por fin llegamos a la fase de producción y al despliegue de la aplicación al servidor final, allí donde la mantendremos en procesos más pequeños (pero esto es otra historia que contaré en el futuro, el proceso corto de mantenimiento y el de desarrollo continuo).

Para esta tarea hay varias herramientas que podemos emplear.

No es muy fiable y rápido emplear ftp para subirlo. Quizá una buena opción sería hacer un git pull desde el servidor de producción, pero por una parte la comunicación por git no es del todo segura y por otra no configura o hace tareas que deberíamos hacer, como por ejemplo poner en marcha la base de datos.

Para esto usamos capistrano, que permite configurar de una forma sencilla qué vamos a despleagar, dónde y cómo. Una vez configurado él se encarga de todo. Se conecta por ssh, comprueba cómo está todo, compila si es necesario, actualiza las dependencias, etc...sube todo y tachán!!! Todo listo.

Existen otras aplicaciones. *Capistrano* está hecho en ruby, así como su versión para Symfony2 *capifony*. También está *Magallanes* que está hecho en php. También podemos desarrollarlo nosotros mismos a base de scripts.

## Post-producción.

En postproducción hay cuatro partes importantes que hacer:

1. Copias de seguridad. Aquí la mejor opción, al menos para mí, es tener un cron que nos genere una copia de todo el contenido y lo versione cada X tiempo. Estas copias enviarlas a Dropbox, S3, Otro servidor, o donde sea, pero evidentemente no en el mismo sitio.

2. Ping. Otro aspecto importante a tener en cuenta es el mantenimiento online del producto. Esto hay que monitorizarlo. Se puede hacer con un pequeño script que haga ping al servidor y compruebe con otro script desplegado que todo está en correcto funcionamiento o se pueden usar herramientas (normalmente de pago) con New Relic.

3. Mantenimiento. Hay que tener los scripts suficientes para mantener la aplicación funcionando, así como ir comprobando sus funcionalidades para que si una falla se pueda pasar a fix lo más rápido posible.

4. Mejoras. Si tenemos un contrato de mantenimiento continuo con un cliente o bien es una aplicación nuestra, debemos estar mejorando y actualizando el producto constantemente. Esto nos los permite nuestra rama abierta en git de desarrollo, para que en cuanto tengamos una petición nueva podamos ponernos a ella.

## En resumen.

Dividimos el trabajo en cuatro fases y mantenemos dos controles de versiones.

1. Desarrollo: Control de versiones con Git.

	1. Versión principal.

	2. Versión de desarrollo.

		1. Ramas de corrección de errores.

		2. Ramas de nuevas funcionalidades.
2. Preproducción:

	1. Test unitarios para las partes más complejas (esto no es más que hacer algunas funciones para comprobar que hace lo que debe).

	2. Datos a la base de datos de prueba.

	3. *Entorno virtual [No necesaria en muchos casos]: Crear un entorno controlado para prueba en vivo y visto bueno del cliente.* 

3. Producción:

	1. Configurar capistrano o similar para desplegar.

	2. Despliegue automatizado.

4. *Postproducción  [Esto en realidad es una segunda parte separada del proceso principal].*

	1. Backups.

	2. Control de estado.

	3. Corrección de Bugs a la rama de desarrollo.

	4. Mejoras a la rama de desarrollo.

<small>Imagen de <a href="http://www.flickr.com/photos/jaygooby/391382834/sizes/m/">jaygooby</a></small>
