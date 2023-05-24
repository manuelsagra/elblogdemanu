---
title: 'Entrevista a Igor Modino sobre el proyecto Armiga'
description: 'Un prometedor aparato que emula el Amiga'
date: Wed, 07 May 2014 08:12:31 +0000
draft: false
tags: ['Amiga', 'Internet', 'Juegos', 'Tecnología']
categories: ['Entrevistas']
---

{{< fg src="a1.webp" alt="Armiga" >}}

Desde que se anunció a principios de este año, siempre he sentido curiosidad por el [Armiga](http://www.armigaproject.com/). A diferencia de otros proyectos como el [Minimig](/dentro-de-poco-podras-comprar-un-minimig/), no han apostado por recrear el mítico ordenador de [Jay Miner](/jay-miner-el-padre-del-amiga/) y su equipo a bajo nivel, sino con una emulación basada en una placa **ARM**. Y como detalle diferenciador, incorpora una controladora propia y una unidad de disco que permite leer directamente juegos desprotegidos de **Amiga**.

Tras [ver el dispositivo en la pasada RetroMadrid](/retromadrid-2014-ii-cacharreo-retrodesarrollo-indies-podcasts-y-asociaciones/), y charlar un rato con los creadores, me animé a hacerles una entrevista para conocer más detalles del mismo, ahora que [todavía es posible apoyar la campaña de crowdfunding](https://www.indiegogo.com/projects/armiga-project). He intentado evitar [las preguntas que ya hicieron hace un tiempo en RetroManiac](http://retromaniacmagazine.blogspot.com.es/2014/04/entrevistamos-al-equipo-que-desarrolla.html), y el resultado ha sido el siguiente:

**En vuestra opinión, ¿qué le hace tan especial al Amiga como para "resucitarlo" con este proyecto?**

> El **Amiga 500** fue un ordenador adelantado a su tiempo y mantuvo una considerable ventaja sobre los PCs durante varios años, siendo referencia en cuanto a gráficos y sonido. Hoy en día, los usuarios que lo tuvimos guardamos un magnífico recuerdo de los momentos pasados jugando con él y no es extraño que muchos lo guardemos, junto a una caja llena de juegos, que es lo que nos ha hecho pensar en "_resucitarlo_".

{{< yt WWPOYFEDl3I >}}

**¿Por qué decidisteis optar por la vía de la emulación con una placa basada en ARM, y no sintetizar los componentes en una FPGA al estilo Minimig / MiST?**

> Ésta es una discusión bastante extendida. En su momento valoramos todas las opciones, incluso diseñar la controladora para usarla con [Minimig](http://www.minimig.net/). Los grandes problemas de **Minimig** son el tamaño y el precio, así que pronto barajamos otras alternativas. [ARM](/arm-el-lider-en-microprocesadores-tiene-acento-britanico/) era un firme candidato desde el principio, ya que son pequeños, asequibles, potentes y eficientes, aunque también barajamos **MIPS**, **x86** e incluso introducir un [M68K](/la-herencia-del-motorola-68000/). En cualquier caso, **Minimig** y cualquier otra implementación FPGA no deja de ser una emulación de muy bajo nivel, realizada con puertas lógicas. Desde nuestro punto de vista, una CPU **ARM** moderna ofrece potencia suficiente como para emular el **Amiga** de forma precisa y así se puede comprobar en el **Armiga**.

**Dado que la controladora de discos en su estado actual prácticamente sólo carga juegos "piratas", ¿no habría tenido más sentido haber diseñado el Armiga más pequeño y que funcionase exclusivamente con tarjetas SD?**

> Lamentablemente, los discos crackeados se extendieron mucho en la época del **Amiga** y es muy habitual que los usuarios tengan muchos de estos discos. Aparte, muchos juegos originales funcionan con **Armiga**, siempre que no contengan pistas de densidad variable. Por ejemplo, muchos juegos intentaban evitar la piratería con preguntas relativas al manual y no con modificación de la densidad de las pistas, por lo que deberían funcionar.
> 
> Por otra parte, [ADF](http://en.wikipedia.org/wiki/Amiga_Disk_File) es el estándar "de facto" en el mundo de la emulación del **Amiga** y es un formato incompatible con las variaciones en la densidad de pista, ya que únicamente representa datos y no mantiene referencias temporales. En este sentido, uno de nuestros objetivos es dar soporte a formatos que mantengan referencias temporales, con lo cual soportan variaciones en la densidad de pistas. En problema aquí es que no hay un "estándar" y hay varias implementaciones que compiten entre sí. Nosotros hemos desarrollado la nuestra propia, mucho más compacta que las alternativas que hemos encontrado.
> 
> Sobre hacer un **Armiga** sin disquetera, creemos que perdería su gracia, ya que no aportaría nada sobre **Pandora** o incluso un **PC** tradicional, más allá de nuestro software.

{{< fg src="a2.webp" alt="Armiga" >}}

**¿No es un poco extraño que se permita usar directamente discos pero no periféricos de la época, como por ejemplo un joystick Quickshot?**

> Es algo que valoramos, pero incluir puertos de joystick de **Amiga**, aunque no es complejo técnicamente, sí encarece el producto final y, si bien ciertos usuarios estarían interesados, creemos que no la mayoría. Hay alternativas, como re-ediciones de joysticks clásicos con conexión USB y adaptadores DB9-USB, que podrían ser usados con el **Armiga**. En cualquier caso, hoy en día es muy sencillo y económico encontrar joysticks y pads USB.

**¿Qué tal ha sido vuestra experiencia en RetroMadrid? ¿Habéis recibido ánimos, consejos y críticas para mejorar el proyecto?**

> Ha sido magnífica. Ciertamente todo el que probó los prototipos quedó muy satisfecho y en la mayoría de los casos sorprendidos porque el producto ha superado sus expectativas.
> 
> Para nosotros era una prueba de fuego, tanto por la previsible exigencia de los visitantes, como por la exigencia técnica de estar más de 12 horas funcionando sin parar, en un entorno no controlado. El balance no ha podido ser mejor, ya que no hemos tenido ningún problema técnico y, como comentaba, los visitantes han quedado muy satisfechos con lo mostrado.

{{< yt nwMZdMloqfE >}}

**¿Fue complicado conseguir una licencia de Kickstart para el Armiga? ¿Hay algún requerimiento especial para conseguirla?**

> En principio, cualquier persona puede conseguir una licencia personal a través de [Amiga Forever](http://www.amigaforever.com/), que son los licenciatarios en exclusiva para emulación. Conseguir licencia para el **Armiga** ha requerido una negociación con **Amiga Forever**, pero llegamos a un acuerdo de forma relativamente rápida, ya que siempre se mostraron interesados en el proyecto.

**Hace unos años, para emular un Amiga hacía falta un equipo bastante potente, y hoy se puede hacer con uno que cabe en la palma de una mano. ¿Creéis que dentro de unos años los eficientes procesadores ARM serán lo suficientemente potentes como para hacerse un hueco en el escritorio? ¿O directamente los ordenadores de escritorio dejarán paso a dispositivos móviles?**

> No hace falta hablar del futuro para encontrar esos entornos. Hoy en día, un procesador **ARM** de gama media-alta es igual o más potente que un **x86** de gama baja. Queda mucho camino por recorrer para llegar a niveles de **Core i5** y plantearse desbancar a chips como los **Core i7** sería una locura a medio plazo, además de que no creo que sea el objetivo. No obstante, cada vez se popularizan más pequeños "PCs" de escritorio basados en **ARM**, sobre los que corre **Linux** o **Android**, e incluso sistemas todo-en-uno basados en **Android** se encuentran fácilmente en grandes almacenes.
> 
> El uso de un dispositivo híbrido móvil-sobremesa está ya al alcance los usuarios, por ejemplo, con los [Padfone](http://en.wikipedia.org/wiki/Asus_PadFone) de **Asus**. El gran problema aquí es el concepto de un sistema operativo para ambos entornos.

**Con el progreso actual de la campaña, parece complicado llegar al 100% de la financiación en el plazo previsto. ¿Habéis previsto cuál es el futuro del Armiga? ¿Sería posible comprar sólo el software?**

> Muchos nos preguntan por el monto de la campaña y "_aconsejan_" que hubiera sido mejor ir a por un importe menor. La justificación es que $140.000 es el "[break even](http://es.wikipedia.org/wiki/Punto_muerto_(econom%C3%ADa))" del proyecto al actual precio de venta ($139). Para poder vender a ese precio, tenemos que hacer una partida de al menos 1000 unidades, para obtener precios competitivos por parte de proveedores y poder repercutir los costes directos con poco impacto en el precio.
> 
> Estaba claro que sería complicado, pero no podíamos correr el riesgo de apostar por una cantidad menor y no llegar a cubrir costes, en caso de llegar a producción, ya que estaríamos perdiendo dinero con cada unidad vendida.
> 
> Una vez terminada la campaña decidiremos, con los datos obtenidos de la misma, cómo enfocar el futuro del **Armiga**. Existen varias posibilidades en este momento pero podéis contar con que el proyecto continuará.
> 
> Sobre vender el software, si te refieres al emulador, no es nuestro objetivo y no creemos que haya mercado. En cuanto al sistema de lectura de discos, sí tenemos pensado vender la controladora, junto con su software, como ya ofrecemos en **Indiegogo**.

{{< fg src="a3.webp" alt="Armiga" >}}

**¿Qué ventajas y desventajas veis a la financiación por crowdfunding?**

> La mayor ventaja es que te permite conocer el mercado antes de salir al mismo... aunque sólo conocerás una parte.
> 
> La gran desventaja es que la gente aún es escéptica sobre estas plataformas. En **RetroMadrid** pudimos comprobar que mucha gente no conoce el concepto y, de los que lo conocen, muchos no tienen claro su funcionamiento y que, en este caso concreto, nunca perderán su dinero, ya que si el proyecto no se financia completamente, el dinero será devuelto a los usuarios. De hecho, nosotros no recibimos dinero hasta que finalice la campaña y únicamente en caso de ser totalmente financiados. Por tanto, es una inversión segura: si tiene éxito, consigues tu **Armiga**, si no, te devuelven el dinero.

**Muchas gracias por vuestro tiempo, y mucha suerte con el proyecto. ¿Que diríais a los indecisos para que se animen a apoyar la campaña?**

> En línea como lo comentado anteriormente, ésta es la forma más segura de conseguir un **Armiga** y, desde luego, la única de hacerlo a este precio.
> 
> Muchas gracias a vosotros.