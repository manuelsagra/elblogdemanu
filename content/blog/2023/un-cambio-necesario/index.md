---
title: "Un cambio necesario"
description: "De Wordpress a Hugo y tiro porque me toca"
categories: ['Varios']
tags: ['Blog', 'Desarrollo', 'Internet']
date: 2023-05-28T10:54:43+02:00
draft: false
---

Este 2023 se han cumplido 17 años [desde que empecé este blog](/hello-world/) en **Wordpress**. Durante todo este tiempo, he pasado por varios servicios de hosting, hasta que hace seis años contraté un Cloud VPS en **Gigas**. He estado bastante contento con el servicio, pero la verdad es que siempre he pensado que me venía un poco grande. Pagar casi 230€ anuales me parecía algo excesivo para mis necesidades, y la gota que colmó el vaso fue una carta que recibí a principios de año en la que explicaban que subían el precio un 5%. Realmente no es un gran aumento frente a otros que hemos tenido en los últimos años con otro tipo de servicios, pero fue algo que me animó a explorar alternativas.

En primer lugar, pensé pasar a un servidor más económico, pero luego decidí que era el momento de intentar un cambio más radical. Aunque a estas alturas me siento bastante cómodo con **Wordpress**, es un software que no está falto de desventajas: puede suponer un problema en sitios con mucho tráfico, el sistema de comentarios es un coladero de _SPAM_ pese al plugin de Akismet, y al ser el software más popular en la web, es un foco de ataques continuos de todo tipo, obligándote a estar preocupado protegiendo el servidor y a actualizar constantemente a las últimas versiones. Desde hace tiempo quería dar el salto a una plataforma de generación de páginas estáticas, y era la ocasión perfecta para intentarlo.

{{< fg src="old.webp" alt="Diseño antiguo" title="No estaba mal, pero esta página necesitaba transferir más de 500KB de recursos (comprimidos) para renderizarse" >}}

Estuve explorando varias alternativas, y finalmente me decanté por [Hugo](https://gohugo.io/). Tiene una pequeña curva de aprendizaje inicial --como cualquier software--, pero cuando le pillas el truco permite construir una web de forma rápida y flexible. Exporté todo el contenido del blog a [Markdown](https://es.wikipedia.org/wiki/Markdown) utilizando una versión modificada de [blog2md](https://github.com/palaniraja/blog2md), y estuve repasando manualmente todas las entradas para simplificar la estructura de [categorías](/categories/) y [etiquetas](/tags/), optimizar la mayoría de imágenes --las convertí a [WebP](https://es.wikipedia.org/wiki/WebP) y las organicé en [page bundles](https://gohugo.io/content-management/page-bundles/)--, y también eliminé muchos vídeos que ya no existían. 

Me animé también a desarrollar [un pequeño shortcode](https://github.com/manuelsagra/elblogdemanu/blob/master/layouts/shortcodes/yt.html) para añadir los vídeos de **YouTube** sin un iframe, alojando la miniatura del mismo y poniéndolo como un simple enlace. También hice algo similar para los tweets, y descargué todas las imágenes de **Flickr** para no depender de ningún servicio de terceros. Como resultado de todo esto, no tengo que poner ningún tipo de aviso de cookies, ya que no se emplean en ninguna página. 

En el camino, una de las bajas ha sido el sistema de comentarios. Durante los últimos años, los comentarios útiles que he recibido casi los puedo contar con los dedos de la mano, y he tenido que eliminar manualmente mucha publicidad y también algunos mensajes ofensivos. A pesar de que hace tiempo sí que recibía aportaciones de calidad, he pensado que lo mejor era cerrarlos, y que si alguien quiere decirme algo que [me contacte por redes sociales](https://twitter.com/manuelsagra) o [me envíe un correo electrónico](mailto:manuelsagra@gmail.com).

{{< fg src="new.webp" alt="Diseño nuevo" title="Sí, es un diseño mucho más básico, pero no necesita ninguna imagen y en total son 10KB de datos" >}}

Lo mejor del cambio ha sido la forma de servir todo el contenido. Gracias a [Cloudflare Pages](https://pages.cloudflare.com/) podéis estar leyendo esto a coste cero para mí --salvo por el dominio, pero es un pequeño gasto que ya tenía antes--, las páginas se cargan mucho más rápido y publicar un cambio se hace fácilmente gracias a un simple push a [mi repo de Github](https://github.com/manuelsagra/elblogdemanu/). Si a esto le unimos un tema sencillo y minimalista que quería acometer desde hace tiempo --con [un protagonismo más destacado de las imágenes](/retropixel-malaga-2023/) en los artículos--, la verdad es que estoy bastante contento con el resultado, y espero que también sea más agradable de leer para vosotros.