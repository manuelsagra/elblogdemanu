---
title: 'EucaliptouS, un juego en formato "Elige tu propia aventura" para Amstrad CPC'
description: 'Mi primer juego para este ordenador'
date: Sat, 23 Dec 2017 09:31:19 +0000
draft: false
tags: ['Amstrad CPC', 'Desarrollo', 'Juegos', 'Retro']
categories: ['Varios']
---

{{< fg src="e1.webp" alt="EucaliptouS" class="crt" >}}

Hace tiempo que quería programar algo para uno de mis ordenadores favoritos de los ochenta --y parte de los noventa--, y desde que [Fran Gallego](https://twitter.com/FranGallegoBR) publicó la [CPCtelera](http://lronaldo.github.io/cpctelera/) cada vez tenía menos excusas para ponerme manos a la obra. Hace unas semanas, [Radastan](https://twitter.com/Bytemaniacos) organizó [una nueva edición de su concurso de creación de aventuras](http://www.bytemaniacos.com/?page_id=3473) y la verdad es que en un principio no tenía muy claro si iba a participar. Sin embargo, unos días después **Pedro Fernández** publicó [un tweet](https://twitter.com/zona_fi/status/940328797651562497) que fue la chispa que necesitaba.

Ese día estuve dando algunas vueltas en la cabeza al juego y empecé a apuntar algunas ideas. Finalmente decidí hacer una historia de humor plagada de tópicos de la escena retro (el bocata de Nocilla, el pesado de turno obsesionado con su ordenador, OPQA vs. la otra opción esa rara,...), con un tema estrella: [la reciente campaña de crowdfunding de Nogalious](/la-sospechosa-campana-de-crowdfunding-de-nogalious/).

Al día siguiente empecé a trastear con la **CPCtelera**, y lo primero que pensé fue en hacer una fuente personalizada para facilitar la lectura del juego. Además, la fuente que tiene por defecto el **Amstrad CPC** creo que está muy vista a estas alturas. Después de preguntar a **Fran Gallego** --al pobre le di bastante turra durante unos días--, la opción más sencilla para hacer esto era crear una imagen con todos los caracteres, y luego usar una macro en el fichero `image_conversion.mk` para generar el código necesario para poder usar los sprites en el programa.

Estuve mirando algunos diseños, y llegué a la clásica [web de NFG con fuentes de juegos arcade](https://nfggames.com/games/fontmaker/). Una de las que más me gustó fue la de "_Armored Warriors_", y me basé en ella para hacer los caracteres que necesitaba.

{{< fg src="e2.webp" alt="EucaliptouS" class="crt" >}}

Como el juego iba a usar tildes, la eñe, la letra u con diéresis y otros caracteres propios del castellano, me aseguré de que las cadenas de texto estaban codificadas en ISO-8859-1 en el código fuente, para simplificar la función que pintase el texto en pantalla. De esta manera, todos las letras tendrían un valor inferior a 255, ya que si usaba UTF-8, algunas se codificarían con dos bytes.

Una vez que tuve claro esto, programé la función para pintar texto en pantalla con estos caracteres personalizados. Lo único que tenía que hacer era ir pintando palabras hasta que la siguiente no cupiese en la propia línea --o llegar a un retorno de carro--, y en ese momento pasar a la siguiente línea. Así hasta llegar a un byte con valor cero que marca el final de la cadena.

Pintando las letras de esta manera, podía controlar el interlineado. Decidí añadir un par de píxeles a la altura estándar de ocho para que las líneas no estuviesen demasiado pegadas entre sí. Esto me limitaba la cantidad de texto en pantalla, pero creo que así el resultado es más legible:

{{< fg src="e3.webp" alt="EucaliptouS" class="crt" >}}

Gracias a esta rutina, pintar cada una de las pantallas del juego era fácil. Sólo tenía que borrar todo, dibujar la barra de título, la barra de estado y luego los textos correspondientes. La lógica del juego también la hice sencilla. Preparé el sistema para aceptar cuatro opciones --aunque al final sólo hay pantallas con un máximo de tres--, y al pintar cada pantalla hice un bucle que espera una tecla del uno al cuatro --o la tecla "Esc" para volver al título--, y pasaba a la siguiente mirando las opciones en el array correspondiente a esa pantalla en concreto.

Si el número es un cero, te dirige a la pantalla de título y un 255 indica que esa opción no existe. De esta manera, el sistema permite un juego de hasta 254 pantallas distintas --que seguro que no cabrían en memoria sin un sistema de compresión--, aunque en esta ocasión solo llegué a usar veintidós.

Para crear el array de punteros a las cadenas de textos que necesitaba, hice un pequeño programa en Java que coge un fichero de texto con un formato muy sencillo y genera un fichero .c y otro .h con los datos que utiliza el "motor" del juego. Las distintas pantallas se separan con una línea compuesta por guiones, y al final están todas las frases de estado... que los más curiosos ya habrán visto que forman una especie de "metadiálogo" con el jugador si vuelve al edificio varias veces. Como ejemplo, este es el texto que genera los textos de la pantalla que hemos visto antes:

```
\[1:EL DÍA DEL UNBOXING\]
Acabas de recibir un paquete que llevabas esperando durante varios días. Lo abres con ilusión y por fin contemplas el juego del que todo el mundo habla: "EUCALIPTOUS". 

Sacas la cinta de la caja, la introduces en tu CPC y te dispones a cargar el juego.


\[\] Esperas pacientemente a que cargue. >2
\[\] Vas a la cocina a preparar un bocata de Nocilla. >3
```

La primera línea define el número de pantalla y el título. Luego está el texto principal y finalmente las opciones las marco con corchetes. El número que hay al final de cada una de ellas indica qué pantalla se muestra a continuación. De esta manera, pude dedicar tiempo a crear las distintas pantallas despreocupándome de cómo codificarlas.

Con el juego casi terminado, ya sólo faltaba dar un poco de lustre. Creé un logotipo usando la fuente [Inmortal](https://www.dafont.com/es/immortal.font), y una pantalla de carga basándome en [la foto del Amstrad CPC de la Wikipedia](https://es.wikipedia.org/wiki/Amstrad_CPC#/media/File:Amstrad_CPC464.jpg). Para esto último, seguí los consejos de [esta página de la CPCWiki](http://www.cpcwiki.eu/index.php/Creating_images_for_the_Amstrad), edité la imagen con [Gimp](https://www.gimp.org/) y luego la convertí en binario con la utilidad [png2crtc](https://github.com/cpcsdk/gfx2crtc).

Con la ayuda de **Fran Gallego** --_again_--, pude integrar todo esto fácilmente en el proyecto:

{{< yt mxvc73CE1dA >}}

Obviamente hay mucho margen de mejora --de hecho, los juegos de otros participantes me parecen más completos--, y espero que el año que viene si se repite el concurso pueda presentar algo más decente. Al menos, espero que viendo [el código del proyecto](https://github.com/manuelsagra/eucaliptous) se anime a participar más gente, viendo que con las herramientas de hoy en día es relativamente sencillo crear juegos para ordenadores a priori tan "limitados" como pueda ser un **Amstrad CPC**.