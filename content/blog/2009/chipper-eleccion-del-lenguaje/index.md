---
title: 'Chipper: Elección del lenguaje'
description: 'A veces, el lenguaje de programación condiciona un proyecto'
date: Thu, 09 Apr 2009 10:19:38 +0000
draft: false
tags: ['Desarrollo']
categories: ['Artículos']
---

{{< fg src="dev.webp" alt="Developer" >}}

El lenguaje que utilicemos para desarrollar un emulador depende de varios factores. En primer lugar, obviamente están nuestras preferencias y conocimientos personales. Puede que nos guste la rapidez de desarrollo utilizando lenguajes interpretados, a lo mejor nos encanta que nuestros programas sean _multiplataforma_, o quizás somos unos enamorados de la programación orientada a objetos... o, porqué no, todo a la vez. Un emulador no deja de ser un programa más --algo especial, eso sí--, por lo que parte de esta elección tiene un componente subjetivo.

Por otro lado, hay que tener en cuenta la plataforma --o plataformas-- sobre la que queremos que funcione, y las limitaciones que ello conlleva. En algunas máquinas --como en una consola portátil--, no andamos sobrados de recursos, para otras no existen intérpretes o compiladores para ciertos lenguajes, y en otras quizás estamos atados a ciertos entornos de desarrollo.

En mi caso, quería hacer algo sencillo de entender, y que funcionase en la mayor cantidad de máquinas y sistemas operativos posible. Así que hice el siguiente repaso mental de los lenguajes que tenía disponibles...

## Lenguajes interpretados

{{< fg src="c1.webp" alt="Lenguajes interpretados" >}}

Ahora la potencia de las máquinas ha dejado de ser un problema, así que no es extraño ver programas relativamente complejos realizados con lenguajes interpretados. [Python](http://www.python.org/) o [Ruby](http://www.ruby-lang.org/es/) cada vez están más de moda --de hecho, un amigo ha hecho [un emulador de Chip-8 usando este lenguaje](http://stu.pido.us/blog/emulacion-del-chip-8-con-ruby-y-sdl-viii)--, e incluso se pueden ver [auténticas virguerías hechas con JavaScript](http://jsmsxdemo.googlepages.com/jsmsx.html).

Sin embargo, personalmente creo que les falta bastante para ganar a un programa compilado, a pesar de que suelen ser excelentes para el prototipado de un proyecto. Además, en un futuro es posible que lleve el emulador a alguna consola portátil, y utilizar un lenguaje interpretado es un pequeño _handicap_ a tener en cuenta.

## C

{{< fg src="c2.webp" alt="Lenguaje C" >}}

Si hay un lenguaje que ha marcado un antes y un después en la historia de la informática, es [C](http://es.wikipedia.org/wiki/Lenguaje_de_programaci%C3%B3n_C). Es la piedra angular de sistemas operativos como [GNU/Linux](http://es.wikipedia.org/wiki/Linux) o [FreeBSD](http://www.freebsd.org/es/), y de muchas aplicaciones que utilizamos a diario. Además, su sintaxis ha creado escuela, y muchos de los lenguajes de programación que existen hoy en día se basan en ella.

Sin duda, es una opción muy válida, sobre todo si tenemos en cuenta la velocidad de los programas realizados en C, y el hecho de que exista un compilador para casi cualquier máquina, incluyendo alternativas libres como el megaproyecto [GCC](http://gcc.gnu.org/).

## C++

{{< fg src="c3.webp" alt="Lenguaje C++" >}}

Por diseño, C es relativamente limitado, y además no está pensado para la programación orientada a objetos. Para suplir estas carencias, **Bjarne Stroustrup** creó [C++](http://es.wikipedia.org/wiki/C%2B%2B), una especie de lenguaje híbrido compatible con los programas escritos en C, que permitía estructuras de datos más avanzadas, una mejor gestión de la memoria, además de tener una biblioteca enorme de clases que nos simplifica el desarrollo de nuevas aplicaciones.

Aunque es una alternativa muy viable, el problema es que no estoy demasiado familiarizado con él, y aunque pretendo suplir esta carencia personal en un futuro cercano, quería hacer el proyecto sin complicarme demasiado la vida.

## Java

{{< fg src="c4.webp" alt="Lenguaje Java" >}}

Aunque es uno de los líderes en el desarrollo web, [Java](http://java.com/es/) todavía no es demasiado popular para realizar programas de escritorio. A pesar de que cada vez la velocidad de ejecución va dejando de ser un problema, y existe la ventaja de tener programas multiplataforma sin complicarnos la vida, tiene ciertas limitaciones que son difíciles de solventar, como el hecho de que no existe máquina virtual para algunos sistemas operativos, ni para muchas plataformas portátiles.

Además, es una tecnología que uso cada día en el trabajo, por lo que quería probar nuevos aires :wink:

## Conclusiones

Obviamente, me he dejado muchos lenguajes en el tintero, pero lo cierto es que en este pequeño repaso he cubierto la mayoría de los que se usan en el desarrollo de emuladores.

Por diversos motivos, al final he decidido hacerlo en C, y me he ayudado de la biblioteca [SDL](http://www.libsdl.org/) para facilitar el acceso al hardware de vídeo y a la lectura de eventos. De esta manera, el código se puede llevar fácilmente entre sistemas operativos, y entre distintas máquinas. El resultado espero publicarlo muy pronto... estad atentos :wink: