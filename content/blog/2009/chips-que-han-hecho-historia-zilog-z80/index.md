---
title: 'Chips que han hecho historia: Zilog Z80'
description: 'Una CPU que seguro que está en alguna de vuestras máquinas favoritas'
date: Mon, 11 May 2009 04:08:44 +0000
draft: false
tags: ['Juegos', 'Retro', 'Tecnología']
categories: ['Artículos']
---

A finales de 1974, y después de trabajar en el conocido 8080, **Federico Faggin** dejó **Intel** para crear junto a **Ralph Ungermann** una empresa dedicada al diseño de microprocesadores llamada **Zilog**. En el verano de 1976, ya tenían en el mercado su primer micro, que estaba basado en los principios del 8080, aunque añadía nuevas instrucciones, registros, modos de direccionamiento, refresco para memorias dinámicas, y otras mejoras; como por ejemplo la necesidad de una menor cantidad de componentes para tener un proyecto funcional... además de un precio bastante competitivo. Por estas razones, el Z80 se convirtió en una CPU bastante popular, y consiguió desbancar al 8080 de **Intel** sin problemas.

{{< fg src="z1.webp" alt="Z80" >}}

A partir de ese momento, se fue mejorando la frecuencia del reloj en las siguientes revisiones del chip --de los 2.5MHz iniciales se pasaron a los 4, 6 e incluso 8MHz--, y hoy en día se puede encontrar el [eZ80](http://www.zilog.com/index.php?option=com_content&task=view&id=58&businessLine=1&parent_id=77&Itemid=185), que sigue siendo compatible, y que ofrece velocidades de hasta 50MHz. En todos estos años, este chip ha sido clave en la revolución de la informática doméstica, y también se ha utilizado en numerosas recreativas, y en una cantidad ingente de dispositivos, que van desde calculadoras, hasta potentes secuenciadores MIDI. A continuación, voy a dar un repaso a algunas de estas creaciones, ya sea por su importancia histórica, o sencillamente por ser realmente curiosas...

## Ordenadores

La cantidad de ordenadores que tienen un Z80 en sus entrañas es enorme, así que me voy a dejar bastantes en el tintero, y sólo voy a comentar brevemente los que me parecen más relevantes. Si queréis una lista un poco más exhaustiva, podéis [echar un vistazo a la Wikipedia](http://en.wikipedia.org/wiki/List_of_home_computers_by_category#Zilog_Z80_and_clones).

### La familia Sinclair

Seguro que la mayoría de informáticos que ronden la treintena en España han tenido un ordenador de esta familia entre manos. De hecho, me consta que muchos nos hemos decantado por la informática y la tecnología profesionalmente después de haber tenido una de estas máquinas en casa. Y es que los **Spectrums** y sus abuelos -los **ZX80** y **ZX81**\- eran unos ordenadores realmente entrañables, y viéndolos a día de hoy, eran una auténtica maravilla de la ingeniería minimalista.

{{< fg src="z2.webp" alt="ZX Spectrum" >}}

Y es que con una circuitería que iba poco más allá de un Z80, algo de memoria, y un custom chip con funcionalidades muy limitadas, se ponían en pantalla unos gráficos bastante competentes --resolución de 256x192 píxeles con 15 tonalidades de color--, y se emitían sonidos a través de un altavoz interno. Esto cambió con la llegada del **ZX Spectrum 128**, que ya incorporaba un AY-3-8912, todo un clásico en las máquinas de la época.

Por otro lado, hay que tener en cuenta que los modelos que salieron a partir del **ZX Spectrum +2** ya no estaban diseñados por el equipo original, ya que en Abril de 1986 **Alan Sugar** compró los derechos de la marca a **Sir Clive Sinclair**.

### Amstrad CPC y PCW

La gran competencia del **Spectrum** --al menos en nuestro país-- fue el **Amstrad CPC**, introducido por primera vez en 1984, y a diferencia de otros ordenadores similares, se ofrecía directamente con monitor y con unidad de disco o cinta incorporada. Estas máquinas funcionaron bastante bien en bastantes academias de informática y en pequeñas empresas, y también en el mercado doméstico.

{{< yt r6CwGcJQpRo >}}

En 1990, **Amstrad** intentó hacerse con un trozo del pastel que le estaban quitando las consolas y los ordenadores de 16 bits con la gama **Plus**. El problema es que a pesar de que incorporaban hardware que mejoraba los gráficos --con sprites y una paleta de 4096 colores entre otras virguerías--, el corazón seguía siendo un "humilde" Z80, y el software tampoco era una maravilla.

Como dato curioso, sacaron una versión "capada" que sólo era capaz de reproducir juegos en cartucho, en forma de la consola **GX4000**. ¿Te suena? Lo dudo, porque fue un pequeño desastre comercial, con menos de 40 títulos comercializados.

{{< fg src="z3.webp" alt="GX4000" >}}

Para meterse de lleno en las oficinas, **Amstrad** lanzó la gama **PCW** (Personal Computer Word processor), que incluía un monitor monocromo, un mínimo de 256KB de memoria, y una impresora, para competir con las clásicas máquinas de escribir. Su arquitectura no estaba pensada para jugar, pero a pesar de ello salieron algunas joyitas como "_Head Over Heels_", "_Batman_", o "_Livingstone Supongo_".

{{< fg src="z4.webp" alt="Amstrad PCW" >}}

### MSX

La cantidad de ordenadores que se lanzaron bajo este nombre es bastante grande, ya que compañías tan grandes como **Sony**, **Sanyo**, **Panasonic** o **Canon** se subieron al carro del estándar creado en 1983.

{{< fg src="z5.webp" alt="MSX" >}}

Si queréis saber más sobre estos ordenadores, os dejo con un artículo que escribí para el [25º Aniversario del MSX](/msx-25-anos-de-un-estandar/), que creo es bastante completito :wink:

### SAM Coupé

El **SAM Coupé** es un gran sistema que quizás llegó demasiado tarde, concretamente a finales de 1989. Creado por la empresa británica **Miles Gordon Technology**, fue vendido como una especie de **Spectrum** avanzado --de hecho era compatible con los modelos de 48K--, pero realmente iba mucho más allá. Ofrecía un Z80B a 6 MHz, memoria que iba desde los 256KB hasta más de 4MB, cuatro modos gráficos con una resolución de hasta 512×192 píxeles, y sonido con seis canales y ocho octavas.

{{< fg src="z6.webp" alt="SAM Coupé" >}}

Se estima que sólo se vendieron unos 12000 ordenadores, y es una verdadera pena, ya que en el **Sam Coupé** se podían disfrutar de excelentes versiones de clásicos como "_Prince of Persia_" o "_Lemmings_".

### Enterprise

Los **Enterprise** --había un modelo de 64KB y otro de 128KB de memoria-- eran ordenadores que se diseñaron casi específicamente para jugar, algo que se intuye viendo sus características técnicas. Además de tener un Z80, podían poner gráficos a una resolución de hasta 672×256 píxeles con 256 colores, tenían sonido estéreo de 4 canales, un joystick incorporado, y una cantidad de conectores apabullante. Como detalle curioso, el cartucho de ROM se podía cambiar por uno que emulaba el BASIC del **Spectrum**.

{{< fg src="z7.webp" alt="Enterprise" >}}

Desgraciadamente, a la compañía no le salió nada bien el invento, y parece ser que se fabricaron menos de 100000 unidades de estos ordenadores. Una de las razones de este fracaso es la tardía comercialización --se anunció en 1983 pero no se puso a la venta hasta 1985--, y por otro lado, hay que tener en cuenta que tuvo que enfrentarse con máquinas mucho más consolidadas como el **Spectrum**, el **Amstrad CPC** o el **Commodore 64**.

### Jupiter Ace

Esta máquina, diseñada en 1982 por ex-ingenieros de **Sinclair**, hizo una apuesta fuerte en la época, ya que en vez de incorporar el omnipresente BASIC, tenía que programarse en FORTH, que también hacía las veces de Sistema Operativo.

{{< fg src="z8.webp" alt="Jupiter Ace" >}}

Por lo demás, se trataba de una máquina muy humilde, ya que sólo tenía 1KB de RAM, con otros 2KB para la memoria de vídeo. No tenía chip de sonido, y la arquitectura se reducía prácticamente al Z80 y pocos circuitos más. De hecho, está diseñado con chips discretos de toda la vida, y se puede hacer un [clon completamente funcional](http://home.micros.users.btopenworld.com/JupiterAce/JupiterAce.html) con unos pequeños conocimientos de electrónica... ¿alguien se anima?

### Mattel Aquarius

Este ordenador no está creado realmente por **Mattel**, ya que la compañía pidió a **Radofin** --el fabricante afincado en Hong Kong que les producía su **Intellivision**-- que les diseñara un sistema para entrar en el mercado de la informática personal. Poco después, esta compañía les hizo dos prototipos que se convirtieron en el **Aquarius** y el **Aquarius II**, que salieron al mercado en el verano de 1983.

{{< fg src="z9.webp" alt="Mattel Aquarius" >}}

Se trata de unas máquinas muy peculiares y poco potentes incluso para la época, tanto que los programadores de **Mattel** bromeaban diciendo que eran "sistemas de los setenta". A mí personalmente el **Aquarius** me pareció bastante curioso cuando tuve la ocasión de probarlo en [la penúltima edición de RetroMadrid](/retromadrid-2008-maquinas-viejas-y-producciones-nuevas/), aunque parecía más un juguete que un ordenador para hacer algo relativamente útil.

## Recreativas

La cantidad de recreativas gobernadas por un Z80 es desbordante, por lo que sólo voy a hacer un repaso por algunos de los arcades más populares que lo empleaban en sus circuitos, para que veáis la importancia que ha tenido este chip en el mundo de los videojuegos.

### Namco

Una de las primeras compañías en adoptar la tecnología de **Zilog** para sus juegos fue **Namco** --conocida como **Namcot** por aquellos días--, y algunos de los títulos que incluyen este microprocesador fueron "_Pac-Man_", "_Galaga_", "_Rally-X_", "_Dig Dug_", "_Xevious_" o "_Pole Position_"... ¿alguien puede pensar en títulos más míticos? :wink:

{{< fg src="z10.webp" alt="Z80 Arcade" >}}

### SEGA

Esta conocida compañía tampoco se quedó atrás, y el Z80 dio vida a juegos como "_Zaxxon_", "_Wonder Boy_", o "_Fantasy Zone II_", además de servir como chip auxiliar en arcades más avanzados como "_Out Run_", "_Space Harrier_", "_Shinobi_", "_Golden Axe_", o "_Afterburner_"... casi nada.

{{< fg src="z11.webp" alt="Z80 Arcade" >}}

### Capcom

Otra de las grandes en el mundo de los arcades también exprimió esta CPU con recreativas tan conocidas como "_1942_", "_Black Tiger_", "_Commando_", "_Trojan_" o "_Section Z_", que seguro que les suenan a los lectores más talluditos del blog.

{{< fg src="z12.webp" alt="Z80 Arcade" >}}

### Konami

Esta compañía japonesa empleó el Z80 en numerosas placas, para que disfrutáramos de joyas como "_Time Pilot_", "_Juno First_", "_Pooyan_", o "_Scramble_" --el precursor de la saga "_Gradius_"--, además de servir como coprocesador de sonido en títulos posteriores.

{{< fg src="z13.webp" alt="Z80 Arcade" >}}

### Otras recreativas

Otras compañías que usaron el Z80 fueron **Irem** --"_Kung Fu Master_", "_Vigilante_",...--, **Taito** --"_Arkanoid_", "_Bubble Bobble_", "_The New Zealand Story_",...--, o **SNK** --"_Athena_", "_Ikari Warriors_",...--, demostrando nuevamente la popularidad del diseño de **Faggin** en los salones recreativos.

{{< fg src="z14.webp" alt="Z80 Arcade" >}}

## Consolas

Volviendo al mercado doméstico, y centrándonos de nuevo en el sector más lúdico, sorprende ver la cantidad de sistemas que comparten este chip en sus entrañas, siendo algunos de ellos bastante populares en su época.

### Bally Astrocade

Quizás una de las consolas menos conocidas, creada por ingenieros de **Midway** en 1977. Era bastante avanzada para la época, pero la falta de marketing hizo que no tuviese nada que hacer frente a sistemas como [Atari 2600](/algunos-detalles-curiosos-sobre-la-atari-2600/), a pesar de que el sistema de **Bally** también integrara funcionalidades típicas de un ordenador.

{{< fg src="z15.webp" alt="Bally Astrocade" >}}

A pesar de todo, disfrutó de una buena cantidad de títulos, incluyendo conversiones de clásicos como "_Galaxian_", "_Wizard of Wor_", o por supuesto, "_Gunfight_".

### ColecoVision

Este sistema gozó de mucha más popularidad, y fue uno de los productos estrella del verano de 1982, cuando fue lanzado. Curiosamente, la arquitectura guarda muchas similitudes con la de los primeros **MSX** --y también con la de las primeras consolas de **SEGA**--, además de ser compatible con juegos de la **Atari 2600** mediante el uso de un adaptador, algo que trajo bastantes problemas legales a **Coleco**.

{{< fg src="z16.webp" alt="ColecoVision" >}}

La rivalidad con **Atari** era bastante alta, hasta el punto de que se acercaron a compañías como **Konami**, **SEGA** o incluso **Nintendo**, para que programar versiones de sus recreativas, siempre que no hubiesen aparecido en la consola rival. La calidad de estas versiones era en general bastante alta, gracias a la resolución de 256x192 píxeles con 16 colores y 32 sprites por hardware, haciendo que **ColecoVision** fuese bastante popular entre los amantes de los arcades.

### Sistemas de SEGA

**SEGA** usó el Z80 como CPU en sus primeros sistemas domésticos, desde la **SG-1000** hasta la **Game Gear**, pasando por la popular consola [Master Sytem](/master-system-1%C2%AA-parte/).

{{< fg src="z17.webp" alt="Master System" >}}

De hecho, la arquitectura de estas máquinas es una especie de evolución del mismo diseño, ya que la **Master System** era la tercera iteración de la **SG-1000**, y la **Game Gear** era una versión portátil de la **Master System**, algo que facilitaba la creación de nuevos títulos, y la posibilidad de usar los cartuchos de las versiones de sobremesa mediante el uso de un adaptador.

### Game Boy

Siendo estrictos, la **Game Boy** no usa un Z80, y de hecho la CPU creada por **Sharp** es más similar al 8080 original, pero dado que hace unas semanas se celebró el 20º Aniversario de la portátil, no podía dejar pasar la ocasión de mencionarla.

{{< fg src="z18.webp" alt="Game Boy" >}}

La verdad es que poco se puede decir de la consola que no se sepa ya, salvo que fue una maravilla de ingeniería de [Gunpei Yokoi](/gunpei-yokoi/), que popularizó los videojuegos como nadie --¿hay alguien que no haya probado el "_Tetris_" de esta consola?--, y que definió perfectamente cómo debía ser una consola portátil, lo que explica que ningún otro sistema le haya hecho sombra hasta la llegada de sus sucesoras.

### Otras consolas

El chip de **Zilog** también dio vida a máquinas tan desconocidas como la **Mega Duck** --también conocida como **Cougar Boy**--, una portátil que pretendió imitar sin demasiado éxito la pequeña de **Nintendo**.

{{< fg src="z19.webp" alt="Mega Duck" >}}

Por otro lado, el Z80 también aparece en otras consolas ejerciendo las labores de coprocesador de audio, como en [Mega Drive](/algunos-detalles-curiosos-sobre-mega-drive/) y **Neo Geo**... que curiosamente comparten el [Motorola 68000](/la-herencia-del-motorola-68000/) como CPU principal.

## Otros sistemas

### Calculadoras de Texas Instruments

Los usuarios de alguna estas calculadoras --TI-73, y de la TI-81, a la TI-86-- seguro que recuerdan con cariño de la suya, ya que seguramente les sacó de algún apuro en la universidad. Parte de su magia se la debían al Z80 que llevaban dentro, que permitían la ejecución de multitud de programas, e incluso de algunos juegos bastante entretenidos.

{{< fg src="z20.webp" alt="Calculadoras" >}}

### Varios

Además de en sistemas derivados de la arquitectura típica de un ordenador, podemos encontrar el Z80 en secuenciadores MIDI --como el robusto **Roland MSQ700**--, en decenas de reproductores de MP3, y otros dispositivos como impresoras, fotocopiadoras, contestadores automáticos, centralitas, modems e incluso en discos duros, algo que demuestra la versatilidad y el buen diseño que hizo **Faggin** en su día.