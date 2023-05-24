---
title: 'Chipper: Documentación sobre Chip-8'
description: 'Conociendo esta curiosa máquina virtual'
date: Mon, 03 Mar 2008 04:19:52 +0000
draft: false
tags: ['Desarrollo', 'Tecnología']
categories: ['Artículos']
---

{{< fg src="cosmac.webp" alt="Cosmac VIP" >}}

El primer paso a la hora de hacer un emulador, es documentarse bien sobre la plataforma --o plataformas-- que queremos implementar en nuestro programa. En el caso de **Chip-8** la cosa se complica un poco, ya que a pesar de ser una máquina con multitud de emuladores, realmente quedan muchas lagunas acerca del funcionamiento real de la misma.

En cualquier caso, lo importante es que su comportamiento básico es muy sencillo de emular, y puede llegar a entenderse aunque no tengamos demasiada idea sobre arquitectura de ordenadores.

## ¿Qué es esto de Chip-8?

Para entender porqué se creo el **Chip-8**, tenemos que echar la vista atrás para ver como estaba la informática a mediados de los 70. En esa época, tener un ordenador personal en casa no era algo habitual, y todavía quedaban unos años para la salida del **Spectrum**. Una práctica común, era que los aficionados a la electrónica se construyesen un ordenador en forma de kit, y que interactuasen con él mediante microinterruptores o teclados hexadecimales. Aunque el **Apple I**, el **Commodore PET**, o el **TRS-80** estaban empezando a comercializarse, no todo el mundo podía permitirse uno.

Una de las empresas que comercializaba ordenadores en forma de kit era **RCA**, una empresa que en 1976 creó el microprocesador RISC **RCA 1802**. Como dato curioso, esta es la CPU que más distancia ha viajado, ya que ha sido usado en las sondas [Voyager](http://es.wikipedia.org/wiki/Voyager), [Viking](http://es.wikipedia.org/wiki/Viking), y [Galileo](http://es.wikipedia.org/wiki/Sonda_Galileo), así como en varios satélites terrestres.

En 1977, RCA lanzó el kit [COSMAC VIP](http://en.wikipedia.org/wiki/COSMAC_VIP), un ordenador basado en el 1802 que podía adquirirse por 275 dólares. Las prestaciones no eran precisamente impresionantes, pero no tardaron en aparecer numerosos clones, como el [Telmac 1800](http://en.wikipedia.org/wiki/Telmac_1800) o el **ETI 660**. Una de las razones, es que **Joseph Weisbecker** creó una máquina virtual llamada **Chip-8** que permitía crear juegos de una manera rápida, sencilla y utilizando pocas instrucciones.

## ¿Qué permite hacer?

Para comprender las limitaciones del **Chip-8**, hay que tener en cuenta las características del hardware sobre el que se ejecutaba. El micro era de 8 bits y corría a 1.76Mhz, la memoria básica era de 2KB --ampliable hasta 32KB--, el teclado era hexadecimal, y el chip de vídeo --un CDP1861--, permitía resoluciones desde 64x16 hasta 64x128 píxeles, aunque dado que la memoria era un bien escaso se empleaba normalmente una resolución de 64x32 píxeles, que además tenía la ventaja de que los píxeles en pantalla eran más o menos cuadrados. Todo esto con una profundidad de color de 1 bit, es decir, cada cuadrado podía ser blanco o negro.

El lenguaje **Chip-8** es capaz de acceder hasta a 4KB de memoria. Sin embargo, las posiciones que van de 000h a 1FFh no deben usarse, ya que es donde residía el intérprete en las máquinas originales. Por eso la mayoría de los programas empiezan en 200h, aunque los que estaban destinados al ordenador **ETI 660** empiezan en 600h, debido a que en ese sistema el intérprete era algo más grande de lo normal.

Existen dieciséis registros de 8 bits propósito general (V0 a VF), aunque el último está normalmente reservado para algunos flags. Además, existe un registro de 16 bits de direccionamiento llamado I, que se utiliza por algunas instrucciones que acceden a la memoria. Si tenemos en cuenta la limitación de los 4KB, realmente sólo son útiles los primeros 12 bits. También existen otros dos registros especiales de 8 bits, que se utilizan por los dos timers que tiene el **Chip-8**. Si tienen un valor distinto de 0, se decrementan una unidad a 60Hz. Uno de ellos es para hacer retardos --DT, Delay timer--, y otro produce un sonido hasta llega a 0, y se denomina ST o Sound timer.

La entrada se hacía a través de un teclado hexadecimal, con la siguiente disposición:

{{< fg src="cv.webp" alt="Cosmac VIP" >}}

Algo extraña si la comparamos con cualquier teclado actual, y más cercana a la de un teléfono.

En cuanto a la pantalla, hay que tener en cuenta que el sistema de coordenadas comienza en la esquina superior izquierda, y todas las coordenadas son positivas, hasta (63,31) en la esquina inferior derecha. Para dibujar objetos en pantalla, se utilizan sprites y se dibujan mediante XOR, es decir, cambian el estado de lo que haya dibujado previamente en la pantalla. Los sprites siempre tienen 8 píxeles de ancho --en formato bigendian--, y pueden tener hasta 15 píxeles de altura, utilizando 15 bytes de memoria. Tambíen hay que saber que cuando se pinta un sprite, y se sale de la pantalla, el resto aparece por el lado opuesto.

Por otra parte, hay 16 sprites especiales --de 5 bytes de tamaño--, que representan los caracteres hexadecimales de 0 a F. Éstos deben estar en el área de memoria del intérprete --de 000h a 1FFh--, y sirven para dibujar rápidamente estos caracteres. En cualquier caso, la dirección exacta es desconocida, aunque esto no afecta demasiado a la emulación.

El **Chip-8** tiene 35 instrucciones, y la ventaja --de cara a hacer un emulador y un depurador, sobre todo-- es que todas son de 16 bits de longitud, y empiezan en una dirección par por convenio. Con este reducido set, que permite dibujar en pantalla, leer del teclado, hacer operaciones aritméticas, comprobaciones, saltos y poco más, se puede programar un juego en poco espacio. ¿Un "_Tetris_" en menos de 500 bytes? Es posible :wink:

## Un paso más: Super Chip-8

Cuando **HP** sacó su linea de calculadoras gráficas **HP-48** --famosas entre los universitarios de la época--, el **Chip-8** se puso otra vez de moda. Debido a que no era fácil programar para estas máquinas, **Andreas Gustafsson** hizo un intérprete de Chip-8 llamado **Chip-48**, que luego fue evolucionando con el tiempo. De hecho, se añadieron funcionalidades nuevas en lo que se terminó conociendo como **SCHIP** (_Super Chip_), una ampliación del lenguaje creada por **Erik Bryntse** en 1991.

Esta extensión del lenguaje hace que se aprovechen mejor las capacidades de las calculadoras **HP-48**, por lo que se implentaron las siguientes mejoras:

*   Modo de pantalla extendido de 128x64 píxeles, con sprites de hasta 16x16.
*   Se puede hacer scroll de la pantalla, tanto horizontal como verticalmente.
*   Hay 10 caracteres especiales de 10 bytes cada uno en el modo extendido, aunque sólo se representan los números.

Para manejar todo esto, se han añadieron nueve instrucciones nuevas, y se modificó la que dibujaba los sprites en pantalla.

## ¿Y ahora?

En el próximo artículo mostraré con detalle el conjunto de instrucciones de **Chip-8** y **SChip**, mostrando las peculiaridades de cada una de ellas. Después, veremos los lenguajes en los que se puede hacer un emulador, para posteriormente hablar acerca de cómo se hace un programa de este tipo.

Más información:

*   [Página de la Wikipedia](http://en.wikipedia.org/wiki/CHIP-8)
*   [COSMAC ELF](http://www.cosmacelf.com/)
*   [Emulador SVision-8 y documentación](http://devernay.free.fr/hacks/chip8/)
*   [Hilo en Emutalk sobre la emulación de Chip-8](http://www.emutalk.net/showthread.php?t=19894)
*   [Listado con gran cantidad de emuladores sobre Chip-8](http://www.geocities.co.jp/Playtown-Yoyo/6130/chip8.htm)