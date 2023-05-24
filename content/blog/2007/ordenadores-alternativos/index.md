---
title: 'Ordenadores alternativos'
description: 'Más allá de los ordenadores con Windows'
date: Mon, 20 Aug 2007 06:15:46 +0000
draft: false
tags: ['Tecnología']
categories: ['Artículos']
---

Generalmente, cuando se habla de un **PC**, se piensa en un equipo de sobremesa o portátil, generalmente con **Windows** instalado. Esto se debe a la popularidad de esta plataforma, ya que **PC** es el acrónimo de "Ordenador Personal" -"Personal Computer" en inglés-, y es un término bastante genérico. En este sentido, poco importa el Sistema Operativo que tengamos instalado y el hardware que tenga, sea compatible o no con el estándar establecido por **IBM** hace más de 25 años.

Antes de que **IBM** acaparase el mercado con sus ordenadores, la gente tenía una variedad increíble de ordenadores para llevar a sus hogares. Desde los modestos **Spectrum** y **Amstrad CPC**, hasta bestias multimedia como el **Amiga** o el **Atari ST**, por no olvidar a los **Macs** de **Apple**, que incluso hoy tienen éxito y son muy apreciados en ciertos entornos, como el mundo editorial.

Mucha gente, ya sea por nostalgia de esos días, o por la rebeldía de no dejarse llevar por las tendencias actuales, se resiste a comprar el modelo de **PC** que se puede encontrar en las tiendas de informática convencionales y en las grandes superficies. Gracias a Internet se forman comunidades de usuarios de ordenadores _vintage_ --los fans de **Amiga** son legión, por ejemplo--, y también han surgido empresas que han apostado por ordenadores diferentes. Ya sea por su semejanza con sistemas antiguos o por el uso de arquitecturas fuera de lo normal, estas computadoras consiguen destacar, y aportan un toque original dentro del cada vez más aburrido panorama de los "ordenadores compatibles".

## Sprinter

Hace unos diez años, una empresa rusa llamada [Peters Plus, Ltd.](http://www.eng.petersplus.ru/) anunció un nuevo ordenador que tenía una característica realmente peculiar: era capaz de funcionar como un **Spectrum**. El equipo tiene un procesador Z84C15 de 8 bits --una evolución del clásico Z80 de **Zilog**--, y una FPGA de **Altera** como núcleo del sistema, y es capaz de mostrar una resolución de 640x256 con 16 colores en una televisión o un monitor CGA.

La primera versión tenía 128 KB de ROM, 256 KB de RAM, una disquetera de 3.5", un chip de sonido de 8 bits, e incorporaba puertos para conectar teclado, ratón, discos duros y otras ampliaciones. En el año 2000 se ampliaron estas características base, y ahora [por 165 dólares podemos comprar un **Sprinter 2000**](http://www.eng.petersplus.ru/products/) con 4 MB de RAM, 256 KB de Video RAM, teclado, ratón y una caja AT, así como los correspondientes manuales.

{{< fg src="sprinter.webp" alt="Sprinter" >}}

Actualmente los equipos los fabrica la compañía [NedoPC](http://www.nedopc.org/nedopc/sprinter/index.shtml), que también ofrece un emulador para facilitar el desarrollo con [el SDK oficial](http://www.nedopc.org/nedopc/sprinter/sdk/index_e.shtml).

Aunque el diseño basado en FPGA podría haber sido más flexible, sólo incorporaron la posibilidad de convertir el **Sprinter** en un **Spectrum**. Sin embargo, esta concepto hizo que otros ingenieros se animaran a construir otras máquinas con una arquitectura similar.

## C-One: (Commodore One)

Una de ellas es este ordenador, obra de la diseñadora de hardware [Jeri Ellsworth](http://en.wikipedia.org/wiki/Jeri_Ellsworth). El [C-One](http://c64upgra.de/c-one/), como su nombre indica, empezó siendo en 2002 una versión extendida del clásico **Commodore 64** --el sistema más vendido de la historia--, aunque gracias a su núcleo programable, también se puede convertir en un **Amstrad CPC**, o un humilde **Vic 20**.

Para lograr esta versatilidad, se puede cambiar el procesador principal con una tarjeta --por defecto se usa un 65C816 a 20 MHz--, y se puede reconfigurar la FPGA para emular por hardware las funciones de otros chips, o para diseñar un ordenador totalmente nuevo. De serie, soporta hasta 1 GB de memoria principal, 128 MB de memoria multimedia, resoluciones de hasta 1280x1024, varios canales de audio de 8 y 16 bits, discos duros IDE, tarjetas Compact Flash, etc.

{{< fg src="cone.webp" alt="C-One" >}}

A cambio de estas prestaciones, el precio es bastante más caro que en el caso del **Sprinter**, ya que por 269 Euros sólo adquirimos la placa base, y nosotros tendremos que poner la caja ATX --con su correspondiente fuente de alimentación--, el ratón, el teclado, el monitor, y el resto de periféricos.

Una máquina interesante, con el incentivo de poder tener un ordenador de 8 bits totalmente nuevo.

## One Chip MSX

También conocido como [1chipMSX](http://en.wikipedia.org/wiki/1chipMSX), este ordenador producido en 2006 por [D4 Enterprise](http://www.d4e.co.jp/) y distribuido fuera de Japón por [Bazix](http://www.bazix.nl/), guarda algunas similitudes con el **C-One**. Sin embargo, a diferencia de este último, implementa toda la lógica en una sola FPGA Cyclone de **Altera**, de ahí su nombre.

La memoria disponible es de 32MB, y permite cargar software mediante tarjetas SD y MMC, así como por cartuchos originales de **MSX** gracias a los dos puertos que incorpora. Se puede conectar directamente a una televisión o a un monitor VGA, y también tiene conector para teclado, dos puertos de joystick, y otros dos USB. Todo ello contenido dentro de una curiosa caja azul transparente.

{{< fg src="1cmsx.webp" alt="1 Chip MSX" >}}

El sistema configurado por defecto es un MSX2 con 1MB de RAM, 128kB de VRAM y unas ROMS preparadas para cargar software desde la tarjeta flash. Si se tienen conocimientos avanzados de **VHDL**, se puede ampliar esta configuración, e incluso convertir este peculiar **MSX** en un **Atari ST** o un **Apple II**, por poner un par de ejemplos.

Hace unos meses se podía adquirir por un precio cercano a los 200 Euros, pero una vez que se agotó la primera tirada a los pocos días, se retiró de la venta. Todavía no se sabe cuando se va a hacer una segunda remesa --que seguramente tendrá un rediseño para ajustarse a [la Directiva RoHS](http://es.wikipedia.org/wiki/Rohs)--, así que la propia **Bazix** recomienda [apuntarse a la lista de correo](http://www.bazix.nl/onechipmsx_registration.html) en caso de estar interesado en comprar uno de estos sistemas.

## CPC-TREX

Dada la versatilidad del [Cyclone](http://www.altera.com/products/devices/cyclone/cyc-index.jsp) de **Altera**, algunos usuarios han usado placas de desarrollo basadas en esta FPGA para construir sus ordenadores. En concreto, este **CPC-TREX** está basado en [la placa TREX C1](http://www.terasic.com.tw/cgi-bin/page/archive.pl?Language=English&CategoryNo=39&No=14) de **Terasic**, que incorpora de serie puertos USB, conector PS/2 compartido para ratón y teclado, salida VGA, y un lector de tarjetas Compact Flash, todo por 149 dólares.

La arquitectura es muy similar a la del **Commodore One**, y por ello los creadores del **SymbOS** adaptaron el núcleo de **Amstrad CPC** programado por **Tobliflex**, teniendo como resultado [este peculiar ordenador](http://www.symbos.de/trex.htm). Puede configurarse como un **CPC** a 4 ó a 24 MHz, con 576 KB de RAM --se espera llegar hasta los 8MB--, 256 KB de ROM altamente compatible, capaz de ejecutar un sistema operativo multitarea.

{{< fg src="trex.webp" alt="CPC T-Rex" >}}

[Miguel Ángel Montejo](/25-anos-de-spectrum-entrevistas-miguel-angel-montejo/), más conocido en Internet como [Radastan](http://www.bytemaniacos.com/), ha puesto en su web [una completa guía para poder disfrutar de un **CPC-TREX**](http://www.bytemaniacos.com/html/cpctrex.htm), por si nos animamos a tener el ordenador que todo usuario de un **Amstrad** de 8 bits hubiese soñado hace unos años.

## EFIKA

[Genesi](http://www.genesippc.com/) es una compañía especializada en arquitectura **PowerPC**, formada por ex-empleados de **Phase 5**, una empresa que se dedicaba a fabricar aceleradoras para los modelos **1200** y **4000** de **Amiga**. Hace unos años comercializaron los ordenadores [Pegasos](http://en.wikipedia.org/wiki/Pegasos) basados en procesadores G3 y G4, y capaces de ejecutar varios "_sabores_" de **UNIX**, **MacOS** --gracias a [Mac-on-Linux](http://mac-on-linux.sourceforge.net/), pero el usuario violaba la licencia de **Apple**--, **QNX** y [MorphOS](http://en.wikipedia.org/wiki/MorphOS), un clon de **AmigaOS** realizado por la propia **Genesi**.

Estos ordenadores fueron discontinuados hace un tiempo debido a Directiva **RoHS**, por lo que la empresa se centró en crear una plataforma que cumpliese dicha normativa, y que ofreciese algo diferente a los usuarios. De esta manera nació el [EFIKA](http://www.genesippc.com/efika.php), un ordenador aparentemente desfasado que apuesta por el ahorro de energía --gasta una media de 10W en las configuraciones títpicas--, y el silencio, debido a que no necesita ventiladores. No en vano, el término Efika significa "eficiente" en [Esperanto](http://es.wikipedia.org/wiki/Esperanto).

Las limitaciones del [EFIKA](http://en.wikipedia.org/wiki/EFIKA) vienen por la baja velocidad de la CPU --un **Freescale** MPC5200B que corre a 400 MHz con sonido y tarjeta Ethernet incorporados--, un sólo puerto PCI --que se puede convertir a AGP 1.0--, los puertos USB 1.1, y la apuesta por IDE frente al más eficiente SATA. Sin embargo, muchas de estas decisiones se derivan del objetivo por conseguir un ordenador que disipe poco calor, y es previsible que las especificaciones cambien cuando la tecnología avance lo suficiente para incorporar componentes más avanzados y eficientes.

{{< fg src="efika.webp" alt="EFIKA" >}}

Los 128 MB de memoria RAM se muestran algos escasos para ejecutar eficientemente [OpenSolaris](http://www.opensolaris.org/os/project/ppc-dev/) o **Linux** --ya hay disponibles varias distribuciones--, aunque el EFIKA está pensado sobre todo para correr sistemas operativos más ligeros como [QNX](http://zone.ni.com/devzone/cda/tut/p/id/6208) o [MorphOS](http://bbrv.blogspot.com/2007/07/efika-morphos.html), que estará próximamente disponible en su esperada versión 2.0.

La comunidad se ha volcado con [multitud de proyectos](http://www.powerdeveloper.org/program/efika/accepted) que van desde dispositivos multimedia hasta estaciones científicas, e incluso se ha escrito [un completo libro en varios idiomas](http://book.efika.org/) para mostrar las posibilidades de este ordenador.

Se puede adquirir en varias configuraciones que van desde [una placa](https://www.pegasosppc.com/store.php?category=19) que cuesta sólo 99 Dólares, hasta [un equipo con disco duro de 40GB](https://www.pegasosppc.com/store.php?category=24) por unos 280 Euros.

Personalmente tengo muchas esperanzas puestas en el **EFIKA**, y creo que puede tratarse de un equipo que puede reemplazar fácilmente muchos ordenadores de varias familias que sólo se utilizan para navegar por Internet, ver el correo y escribir algunos documentos. Eso por no hablar de los ahorros en muchas empresas con un **PC** barato, fácil de mantener, virtualmente inmune a virus y repleto de posibilidades. En este sentido, conviene echar un vistazo al [blog de Bill Buck y Raquel Velasco](http://bbrv.blogspot.com/) --los _General Managers_ de **Genesi**--, en el que se comentan algunas iniciativas interesantes.

## Otros proyectos

Me gustaría destacar otros proyectos que no tienen las dimensiones de los ordenadores anteriores, pero que pueden ser el comienzo de algo más grande.

### Torlus

**Greg** es un ingeniero francés que bajo el nick de [Torlus](http://www.torlus.com/) ha publicado varios desarrollos software, así como sistemas clásicos --generalmente bastante oscuros-- recreados en FPGAs. Algunas de sus "víctimas" han sido el [Thomson MO5](http://www.torlus.com/index.php?2007/03/19/200-thomson-mo5-in-a-fpga), el [Micronique Hector HRX](http://www.torlus.com/index.php?2007/01/31/198-hector-hrx-in-a-fpga), o la más conocida [Intellivision](http://http://www.torlus.com/index.php?2006/11/01/194-intvfpga-reloaded-).

{{< fg src="mo5.webp" alt="Thomson MO5" >}}

También son interesantes otros proyectos, como [su portátil](http://www.torlus.com/index.php?q=mex), su [emulador de disquetera](http://www.torlus.com/index.php?2006/09/16/191-floppy-drive-emulator) --para usar imágenes ST y ADF en los ordenadores reales--, o [el chip SID conectado al ordenador por USB](http://www.torlus.com/index.php?2006/11/12/195-another-day-another-dead-project-usbsid).

### Minimig

[Minimg](http://home.hetnet.nl/~weeren001/) es un pequeño juego de palabras que significa "Mini Amiga", debido a que el holandés **Dennis van Weeren** ha conseguido implementar la lógica de un **Amiga 500** en una pequeña placa de 12x12cm. El 25 de Julio de este año liberó el diseño bajo [GPLv3](http://en.wikipedia.org/wiki/GPL#Version_3), y cualquiera con conocimientos electrónicos avanzados puede construirse su propio prototipo.

{{< fg src="minimig.webp" alt="Minimig" >}}

Todo comenzó como [un "pequeño" reto personal a principios de 2005](http://en.wikipedia.org/wiki/Minimig), y él sólo ha sacado adelante más rápido un trabajo que un equipo de tres personas todavía está ultimando en forma del **Clone-A** --un clon comercial del **Amiga**--, aunque también es cierto que [Individual Computers](http://www.jschoenfeld.de/indexe.htm) esta tratando de recrear también el chipset AGA.

En el foro de [Amiga.org](http://www.amiga.org/), el propio **Dennis** ha creado [un hilo](http://www.amiga.org/modules/newbb/viewtopic.php?topic_id=39358&forum=8) para ver la gente que estaría interesada en una placa montada --supuestamente por 60 Euros--, o un kit --teóricamente la mitad de precio--, y la respuesta ha sido abrumadora. ¿Veremos pronto un nuevo modelo de **Amiga 500**?

Más información:

*   [CPC-NG](http://cpcng.gryzor.info/prototype.html), un proyecto fallido para resucitar el **Amstrad CPC**.
*   [NatAmi](http://www.natami.net/), otro intento de recrear un **Amiga**.
*   [Experiencias con el C-One](http://www.bytecellar.com/archives/000036.php)
*   [Zonbu](http://www.zonbu.com/), un **PC** con **Linux** con un curioso modelo de suscripción.