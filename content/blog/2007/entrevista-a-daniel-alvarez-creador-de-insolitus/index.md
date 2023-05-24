---
title: 'Entrevista a Daniel Álvarez, creador de in.solit.us'
description: 'Servicios disruptores en la red'
date: Thu, 04 Jan 2007 08:41:26 +0000
draft: false
tags: ['Internet']
categories: ['Entrevistas']
---

{{< fg src="insolitus.webp" alt="ins.olit.us" >}}

Desde hace unos meses está disponible [in.solit.us](http://in.solit.us/), una aplicación web 2.0 que nos permite subir archivos sin ningún límite y compartirlos con el resto del mundo, o bien dejar que sólo un grupo de personas a nuestra elección tengan acceso a ellos. Todo esto desde una interfaz sencilla, de un modo completamente gratuito, y sin moletos banners ni esperas como en otros servicios similares.

Lo he utilizado para subir algunos archivos del blog, y cuando vi que el autor era español, me animé a hacerle una entrevista, a la cual accedió amablemente:

**Cuéntanos, ¿quién es Daniel Álvarez?**

> [Daniel Álvarez](http://www.gra2.com/) es un Computer Scientist (o Ingeniero Informático, como prefieras), de 23 años, nacido en Barcelona.

**¿Por qué te decidiste a hacer una aplicación como in.solit.us? ¿Crees que Megaupload o Rapidshare no tienen un planteamiento adecuado?**

> **in.solit.us** empezó como una aplicación para demostrar lo que se podía hacer en [Ruby on Rails](http://www.rubyonrails.org/) y en cuanto tiempo. Una vez acabada, decidí hacer pública una versión inicial, para uso exclusivo de algunos conocidos y mío. De todos modos, siempre estuvieron abiertos los registros a cualquiera. Un tiempo después, decidí escribir un post sobre **in.solit.us** en mi blog, y a partir de ahí, se fue haciendo conocido, principalmente por blogs en Español.
> 
> No quiero en absoluto restar importancia a servicios como **Megaupload** o **Rapidshare**, aunque creo que son planteamientos completamente diferentes. Además, estoy seguro que su modelo de negocio es mucho mejor que el de **in.solit.us**. Ellos proporcionan un servicio de upload y download de archivos, con mucha publicidad contextual, con usuarios "pro" y con esperas para los downloads.
> 
> La idea de **in.solit.us**, como alguien ya ha comentado, es la de "_social file sharing_", donde, además del mero hecho de subida/descarga de archivos, también existe un contacto entre los usuarios (tag clouds, grupos, comentarios, mensajes, etc.), y no se "esconden" los archivos, como en el caso de **Rapidshare** o **Megaupload**.

**¿De dónde viene tu afición por Ruby on Rails? ¿Por qué apostaste por este lenguaje para hacer in.solit.us?**

> Cómo imagino que mucha gente, quedé impresionado hace algo más de un año por [los screencasts](http://www.rubyonrails.org/screencasts) de [David Hansson](http://www.loudthinking.com/about.html) en la web oficial de **Ruby on Rails**. En unos 10 minutos, desarrolló las partes básicas de un blog. Unos meses más tarde, empecé a aprender **Ruby on Rails**, y de ahí surgió **in.solit.us**.
> 
> Aunque **Ruby on Rails** puede parecer algo complejo de aprender al principio, es impresionante como llega un punto en el que pasas de odiarlo a no poder vivir sin él. **Java** ([Struts](http://es.wikipedia.org/wiki/Struts)) hubiera sido mi segunda opción (nunca me ha gustado **PHP**).

**No se puede negar que la aplicación funciona realmente bien y es bastante útil. Además, recientemente has añadido funcionalidades como WebDAV, que aumentan aún más el valor que tiene de por sí. ¿Qué podemos esperar de in.solit.us a corto y medio plazo?**

> Muchas de las nuevas funcionalidades, como [WebDAV](http://es.wikipedia.org/wiki/WebDAV), han sido sugeridas por usuarios, así como partes de la interfaz. Los usuarios suelen ser los que mejor saben como mejorar la usabilidad o la funcionalidad. Por ello, agradezco enormemente sugerencias, que me llegan, tanto a través del [formulario Contact us](http://in.solit.us/contact), como de comentarios en [el blog de in.solit.us](http://in.solit.us/blog/).
> 
> Actualmente, una de las nuevas funcionalidades previstas es crear un sistema de blogs para usuarios, en el que puedan, transparentemente, incluir los archivos subidos en los posts (imágenes, vídeos, música, etc.)

**Aunque me imagino que lo harías para que llegase a más gente, ¿cómo es que in.solit.us sólo está disponible en inglés?**

> Decidí desarrollar inicialmente la aplicación en inglés, precisamente por lo que has comentado, aunque en un futuro me gustaría traducirla a español, francés y alemán, y si alguien se ofreciese para traducirla alguna otra lengua, también.
> 
> Veo en tu blog que eres un aficionado de Japón, esa sería una de las candidatas :wink: . A mí también me gusta Japón, aunque quizá no lo conozca tanto como tú. Tengo un buen amigo de Tokyo de mi época en el [CERN](http://es.wikipedia.org/wiki/CERN).
> 
> El problema es que las traducciones requieren bastante tiempo, no sólo la traducción en sí, sino modificar la aplicación para que soporte múltiples lenguas, además de traducir cada cambio que se realice posteriormente. Por ello, no lo descarto a largo plazo, aunque sí debo decir que no está entre los objetivos principales.

**¿Qué parte de la aplicación te ha dado, por alguna u otra razón, más quebraderos de cabeza?**

> Sin lugar a dudas, la implementación de **WebDAV**. He usado parte del [código de Stuart Eccles](http://www.liverail.net/articles/2006/06/25/webdav-ruby-on-rails-plugin), con [licencia MIT](http://es.wikipedia.org/wiki/Licencia_MIT), modificado para **in.solit.us**. El problema es que su implementación suponía que los directorios son directorios físicos y los archivos son archivos en esos directorios, y en el caso de in.solit.us, no es del todo cierto, ya que, ni existen directorios (son virtuales), ni los archivos están donde debe mostrarse que están ni con el nombre que deben mostrarse. Así que prácticamente, de la implementación inicial de **Stuart**, sólo queda su comentario de copyright.
> 
> Aún queda pendiente arreglar algunos problemas que algunos usuarios tienen al usar **WebDAV**, como el de los archivos con espacios, que no se suben correctamente debido al estándar de DAV, y bugs con algunos clientes. Espero poder subir la nueva versión con estos cambios en breve.

**Es sorprendente que no haya una limitación de espacio, al menos de momento. ¿Pagas tú mismo el ancho de banda consumido?**

> Por el momento sí, con ayuda de los anuncios [Adsense](http://es.wikipedia.org/wiki/Adsense), colocados en la parte inferior de las páginas de download. Mucha gente ni se fija que están, así que imagino que no molestan demasiado.

**La cantidad de ficheros subidos debe ser increíble. ¿Alguna vez los echas un vistazo por curiosidad? ¿Hay alguno que haya llamado especialmente la atención?**

> Actualmente, hay alrededor de 6000 archivos subidos. Alguna vez echo un vistazo en la página inicial, a los últimos archivos subidos, o a los de los usuarios que más archivos han subido. Especial mención al usuario que más archivos ha subido hasta ahora, [originalconcept](http://in.solit.us/users/public/originalconcept) --más de 450 en el momento de escribir esto--, que ha sido uno de los que más nuevas funcionalidades me ha sugerido, y fue de los primeros en probar **WebDAV** y comentarme sus problemas.
> 
> Uno de los archivos que más me llama la atención, sigue en el top 5 de los archivos más descargados, y se trata de [un vídeo borroso](http://in.solit.us/archives/download/787) (creo que incluso en verde nocturno), de una pareja, supuestamente famosos, que no conozco (unos tales **Fabiana Masena** y **Jorge Petrone**). Siempre me ha producido curiosidad el por qué de la gente que descarga este tipo de vídeos en el que no se ve absolutamente nada, y que podría perfectamente ser cualquiera.

**Basta con echar un vistazo a los archivos más populares para darse cuenta que la gente sube contenidos de dudosa legalidad. Como pusiste en el blog, Dreamhost ya puso problemas por esta razón y tuviste que tomar medidas al respecto. ¿Han intentado cerrarte la página por otros medios?**

> A propósito de [Dreamhost](http://www.dreamhost.com/), como [ya comenté en el blog,](http://in.solit.us/blog/post/downtime-and-back-up/) es mucho más probable que pusieran problemas, no por los archivos subidos, sino por la gran cantidad de ancho de banda y espacio en disco que les estaba consumiendo. Como mucha gente sabrá, el negocio de **Dreamhost** se basa en vender más recursos de los que realmente tiene, confiando en que la mayoría de la gente sólo usará 100MiB de los 10GiB de espacio en disco que contrata, y 1GB de 1TB que se le ofrece.
> 
> Algunas veces, recibo correos en los que se me solicita que se borre un determinado archivo porque tiene copyright. El último, una empresa rusa, me contactó pidiendo que eliminara un archivo, y así se hizo.
> 
> Como se comenta en los [Terms of Service de in.solit.us](http://in.solit.us/about/terms), no vamos a mirar archivo por archivo para eliminar los que incumplan copyright, pero si el propietario de dichos archivos nos pide que se eliminen, lo haremos con la mayor prontitud posible.

**Desde que salió a la luz hace unos meses, ¿cómo medirías el éxito de in.solit.us?**

> Creo, que sin invertir ni un solo Euro (ni [CHF](http://es.wikipedia.org/wiki/Francos_suizos)) en publicidad, gracias a los comentarios en diversos blogs, se ha hecho relativamente conocida a **in.solit.us**, así que no puedo más que estar contento por el momento por los resultados. Por supuesto, siempre puede mejorarse.

**Youtube ha tenido un éxito arrollador y finalmente la acabó comprando un gigante como Google, al igual que ha pasado con muchas aplicaciones "Web 2.0". ¿Te han hecho ya alguna oferta? ¿Crees que se perdería parte de la filosofía inicial de la aplicación si alguna empresa grande la comprara?**

> Me halaga que compares a **in.solit.us** con **YouTube**, aunque por el momento, está a años luz. De momento, nadie me ha hecho ninguna oferta, aunque como ya comenté en uno de los primeros posts sobre **in.solit.us**, nunca lo convertiría en un lugar tipo **Rapidshare**, con más publicidad que contenido y esperas para los downloads. Si llegara dicho punto, en el que fuera imposible financiarlo de otra manera, y nadie estuviera interesado en invertir en **in.solit.us**, cerraría el proyecto.
> 
> Creo que no tiene por qué perderse la filosofía inicial de in.solit.us en el caso que una empresa grande la comprara. Todo depende de la empresa compradora, claro está. El ejemplo podemos verlo en **YouTube**, **Flickr** o **Bloglines**.

**Te agradezco enormemente el tiempo que has dedicado a contestar estas preguntas, y te deseo la mejor de las suertes con la aplicación.**

> Lo mismo digo, suerte con tus proyectos.