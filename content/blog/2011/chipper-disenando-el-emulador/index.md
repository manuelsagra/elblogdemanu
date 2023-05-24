---
title: 'Chipper: Diseñando el emulador'
description: 'El meollo del asunto'
date: Mon, 10 Jan 2011 12:33:26 +0000
draft: false
tags: ['Desarrollo']
categories: ['Artículos']
---

{{< fg src="chi.webp" alt="Chipper" >}}

Hace unos tres años, decidí emprender una serie de proyectos de desarrollo, aunque realmente sólo me tomé en serio uno de ellos: un [emulador de Chip-8](/proyectos/chipper/). El programa estaba prácticamente terminado, y sólo me quedaba por implementar el sonido, pero por pereza lo fui dejando... hasta ahora. El problema es que cuando quise retomarlo, me di cuenta que había perdido el código fuente, así que decidí aprovechar la ocasión para reescribirlo en otro lenguaje.

En [el artículo que escribí al respecto hace un par de años](/chipper-eleccion-del-lenguaje/), desestimaba los lenguajes interpretados por falta de rendimiento, pero después de los avances que ha habido en temas de navegadores web, y tras haber rediseñado el tema del blog en HTML5, decidí probar suerte con JavaScript...

El resultado me ha sorprendido gratamente, ya que en unos días he podido implementar de nuevo todo el proyecto, y con un navegador decente que soporte HTML5 --especialmente en [Google Chrome](http://www.google.com/chrome?hl=es)-- corriendo en un ordenador reciente, el emulador llega los 60 frames por segundo sin problema :smile:

El código fuente del proyecto [lo podéis encontrar en github](https://github.com/manuelsagra/chipper), y la gracia del asunto está en [un fichero JavaScript de 20KB](https://github.com/manuelsagra/chipper/blob/master/chipper.js).

Si echáis un vistazo, veréis que hay un objeto definido para gestionar la memoria (Memory), otro para la pantalla (Screen), otro pequeño para el sonido (Sound), otro para los eventos del teclado (Keyboard), otro para emular las instrucciones (CPU), y finalmente otro que tiene la lógica del emulador (Chipper). Creo que el código es relativamente sencillo de seguir, y aunque hay algunas optimizaciones en algunos puntos críticos --sobre todo a la hora de hacer multiplicaciones--, no es demasiado ofuscado.

En cualquier caso, lo importante está el núcleo principal: el método Chipper.frame. Tras inicializar el emulador y cargar un fichero en memoria, se intenta ejecutar un frame de emulación cada 16ms. Aquí se actualizan los registros que dependen del tiempo, se gestiona el teclado, se ejecutan unas cuantas instrucciones, y se actualiza la pantalla. Este bucle es la piedra angular de un emulador --y de un juego--, y es la clave para entender el programa.