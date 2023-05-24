---
title: 'Entrevista a Phil Ruston, creador del V6Z80P'
description: 'Un heredero del Z80 en un ordenador casero bastante potente'
date: Fri, 15 Oct 2010 20:20:02 +0000
draft: false
tags: ['Tecnología']
categories: ['Entrevistas']
---

[English version of the interview](#english-version)

{{< fg src="v1.webp" alt="V6Z80P" >}}

Hace unos días vi en [el estupendo blog de DaDMaN](http://ladrillopixeles.blogspot.com/) una entrada sobre un ordenador casero reconfigurable llamado [V6Z80P](http://ladrillopixeles.blogspot.com/2010/10/un-amiga-con-z80-v6z80p.html), con unas características técnicas [realmente sorprendentes](http://www.retroleum.co.uk/v6z80p/). Me interesó bastante, así que me puse en contacto con su creador, **Phil Ruston**, y aceptó contestar unas preguntas sobre su proyecto. Si os gusta la electrónica y la informática en su estado más puro, os animo a que leáis la entrevista... a mí particularmente me han encantado sus respuestas :wink:

**¿De dónde vino la inspiración para empezar a diseñar ordenadores de 8 bits?**

> Siempre he estado interesado en la electrónica, y esta afición se complementó de manera perfecta con la informática cuando aparecieron los primeros ordenadores personales en los ochenta. Aprendí el código máquina del Z80 cuando era adolescente, y aunque no hice demasiado por aquel entonces --programaba principalmente en el **Commodore 64** y posteriormente en el **Amiga**--, tuvo un gran impacto en mí. Estoy convencido de que muchos programadores de aquella época soñaban con poder diseñar su propio ordenador como yo... y habría sido algo tremendamente caro, pero hoy en día es barato y sencillo (casi virtual) gracias a la lógica programable.

**¿Cuáles fueron los mayores desafíos a la hora de diseñar [tus ordenadores](http://www.retroleum.co.uk/electronics-articles/previous/) (desde el [primer prototipo](http://www.retroleum.co.uk/electronics-articles/previous/z80-project-the-early-years/) hasta el último)?**

> A medida que mi proyecto con el Z80 ha pasado por media docena de fases evolutivas, he sido capaz de mantener la curva de aprendizaje bastante baja. Cuando empecé con esto hace la tira de tiempo, necesitaba equipamiento muy costoso para hacer cosas muy simples --por ejemplo, un grabador y borrador de EPROM por rayos ultravioleta--, como hacer una ROM de prueba para que la CPU ejecutase un programa básico. El Z80 es un chip genial para jugar con él, es muy simple de entender y conectarle dispositivos: puedes constuir un ordenador en una placa de prototipado, y hacer que encienda unos LEDs en muy poco tiempo. Es muy satisfactorio :smile:
> 
> Para las últimas versiones de mi proyecto, a medida que se fue haciendo más complejo, el hecho de conectar las placas entre sí de manera eficiente y sin problemas de ruido se convirtió en un problema. Además, encontrar las versiones DIP de los chips empezó a ser bastante complicado, lo que hizo que tuviese que utilizar componentes SMD, que obviamente no son tan fáciles para prototipado... ¡y los adaptadores DIP son realmente caros!
> 
> Para evitar usar decenas de placas, originalmente usé microcontroladores como "custom chips", pero esto no es muy eficiente, porque es complicado sincronizar todo, y la velocidad que necesita un chip de este tipo para hacer lo mismo que con lógica discreta es bastante sorprendente. Por tanto, mi siguiente paso fue aprender lógica programable... Sin embargo, hay tanta variedad de dispositivos que las cosas son complicadas al principio, pero leyendo artículos para principiantes y los manuales de los chips, pude empezar a trastear. Compré una CPLD pequeña --una **Xilinx** XC9536 CPLDs en formato PLCC--, y la usé para reemplazar grupos de chips de lógica discreta. El [software gratuito de Xilinx](http://www.xilinx.com/support/download/index.htm) te permite introducir directamente los esquemáticos, algo que le viene de perlas a mis conocimientos de electrónica de aficionado :smile: El interface JTAG de programación también era bastante simple como para hacerlo en casa, lo que ayudó bastante.
> 
> La capacidad de las CPLDs es relativamente pequeña, así que el siguiente paso era aprender sobre FPGAs. Aparte de que necesitan reconfigurarse cada vez que se encienden, realmente no hay mucha diferencia. Al igual que las CPLDs --o incluso más--, las FPGAs son bastante quisquillosas --normalmente necesitan 3 voltajes distintos--, y también hay restricciones acerca de las señales que pueden conectarse a ellas, así que necesitas leerte los manuales de cabo a rabo para estar seguro de que no vas a freír tus componentes. Otro problema es que las FPGAs suelen venir en chips con pines muy pequeños, y esto realmente puso al límite las placas que podía hacer en casa. Para mi primer experimento, compré una FPGA XC2S15 Spartan2, y la soldé en una placa casera de desarrollo, pero hoy en día las placas comerciales con FPGAs grandes son fáciles de encontrar, y relativamente asequibles.
> 
> El último gran paso era construir mi primera placa de forma profesional. No estaba para nada familiarizado con la jerga y las convenciones para diseñarla correctamente, pero jugando con [FreePCB](http://www.freepcb.com/) y mirando los requerimientos de varias compañías que las fabrican, fuí capaz de figurarme como hacerlas. Por cierto, ¡los costes son realmente una revelación!

{{< fg src="v2.webp" alt="V4Z80P" >}}

**¿Qué crees que hace a tu ordenador más especial, el hardware en sí o el software que has desarrollado?**

> El hecho de poder diseñar mi propia arquitectura --y la tuya, gracias a la FPGA--, y hacer que funcione como un ordenador independiente, es lo que creo que es el factor que define al V6Z80P. Mi propio diseño ha evolucionado, más que haber sido concebido claramente desde un principio, pero es divertido "seguir los pasos" de los diseñadores de los ordenadores clásicos de 8 bits... y luego ser capaz de ir más allá gracias a la tecnología actual.
> 
> El diseño del hardware del V6Z80P realmente es muy simple, ya que consiste en una FPGA, memoria RAM, y la CPU en un bus, y dos memorias SRAMs conectadas directamente a la FPGA en otros buses dedicados. El software --principalmente el sistema operativo-- también se ha hecho sobre la marcha, y puede hacer llorar a un diseñador experimentado en la materia, pero se ha hecho con el espíritu del aprendizaje y la experimentación, tal y como deben hacerlo los aficionados :smile:

**¿Cuántas unidades del V6Z80P has fabricado? ¿Cuánto tiempo tardas en montar una de ellas?**

> Creo que hay unas cuarenta unidades alrededor del planeta actualmente. El tiempo de montaje varía --si hago más de una, trabajar en serie hace que ahorre algo de tiempo--, pero creo que se tardan unas seis horas en soldar todo, y luego hay que hacer los cables, probarlo, etc. Es imposible para mí hacerlos con fines comerciales, sólo los fabrico para mis queridos entusiastas :smile:

**Algunos de estos ordenadores han llegado a las manos de gente realmente inteligente y con gran talento, como el grupo [Altair](http://www.retroleum.co.uk/20100409/461/). ¿Son todos los usuarios tan activos como ellos?**

> Todavía tengo noticias de mucha gente que ha comprado las placas, y a menudo me hacen sugerencias para hacer nuevas prestaciones, etc...

**En la lista de correo has hablado sobre el eZ80P. ¿Cuándo veremos el primer prototipo de tu ordenador "más potente"? :wink:**

> Tan pronto como tenga una arquitectura básica y sea capaz de ejecutar programas --por ejemplo, actualizaciones de firmware--, lo anunciaré como es debido. Me he dado cuenta de que probablemente no podré usar casi nada de mi arquitectura actual, porque el sistema operativo se hizo a lo largo de dos años, y no creo que nadie quiera esperar tanto para que termine otro diseño :smile:
> 
> Así que efectivamente, cuando pueda hacer funcionar algo útil --¡si alguna vez lo hace!--, estaré contento de empezar a vender eZ80Ps.

{{< yt M8hL3Eiqh_c >}}

**¿Crees que los PCs son innecesariamente complejos actualmente? De pequeño soñaba con ordenadores sencillos de usar con arranque instantáneo...**

> Sí, ese es el problema con el PC: siempre quiere hacer todo, y ser la herramienta universal para resolver cualquier cosa. Además, cualquier avance de hardware se ve anulado por el sistema operativo. Sin una revolución en memoria RAM no volátil, es complicado que las cosas mejoren mucho.
> 
> El otro día leí que la BIOS finalmente era sustituida, haciendo que los arranques sean más rápidos. Pero no estoy completamente convencido del tema :smile:

* * *

## English version

**Where did the inspiration to build your 8-bit computers came from?**

> I've always been interested in electronics and this naturally merged with computers as a hobby when the first home micros came along in the 80's. I first learnt Z80 machine code on the **Spectrum** in my teens, and although I didn't do much with it back then --I did most coding on the **C64** and later the **Amiga**--, it had a big impact on me. I'm sure most coders back then wished they could design their own computer... Of course it would have been extremely expensive but nowadays it's cheap and straightforward (almost virtual) thanks to programmable logic.

**Which were the most difficult challenges when designing [your computers](http://www.retroleum.co.uk/electronics-articles/previous/) (from [the first prototype](http://www.retroleum.co.uk/electronics-articles/previous/z80-project-the-early-years/), to the last one)?**

> As my Z80 project has gone through half a dozen evolutionary phases I've been able to keep the learning curve quite low. When I started way back, I needed some fairly expensive equipment to do quite simple things (EG: a UV EPROM burner and erasure unit) in order to make a test ROM for a Z80 CPU to follow a simple program. The Z80 is a great chip to play with, it's so simple to interface and understand: you can build a computer system on a prototyping breadboard and have it flashing some LEDs in no time at all (very satisfying :smile:
> 
> For the later versions of my Z80 Project, as things got bigger connecting all the boards together neatly and without noise/signal problems became an issue. Also, sourcing DIP versions of useful chips started to become difficult, this meant using surface mounted parts which obviously aren't as friendly for prototyping... DIP adapters seem to be really expensive!
> 
> To keep those early Z80 projects from sprawling over acres of PCBs, I originally used microcontrollers as "custom chips" but this is not very satisfactory, because it's difficult to sync everything, and the speed required in a microcontroller to do the same thing as raw logic can be surprising. Therefore my next step was to learn about programmable logic... There's such a huge variety of devices and things can seem off-puttingly complicated when starting out - but by reading beginners web articles and datasheets I was able to put a toe in the water. I bought some small, cheap **Xilinx** XC9536 CPLDs (in PLCC socket format) and used them to replace groups of discrete logic chips. The (free) [Xilinx Webpack software](http://www.xilinx.com/support/download/index.htm) allows you to enter designs via schematic entry which suited my hobby-electronics / metal bashing style :smile: The JTAG programming interface was also simple to construct at home, which also helped.
> 
> The capacity of the CPLDs was somewhat limiting so the next step up was to learn about FPGAs. Apart from the fact they need configuring each time they power up there isn't a great deal of difference. Like CPLDs (only moreso?) FPGAs are fussy --often requiring 3 separate voltage supplies--, also there's restrictions concerning the signals they'll interface with, so you need to read the datasheets thoroughly to make sure you're not going to fry your components. Another issue is that FPGAs seem to come in packages with very tiny pins and this really pushed the limits of the PCBs I could make at home. For my first FPGA experiment, I bought a tiny XC2S15 Spartan2 FPGA and soldered it onto an ultra simple home-etched development board, but these days professional dev boards with huge FPGAs are common and affordable.
> 
> The last big step was getting my first professionally produced PCB made. I wasn't at all familiar with the jargon and conventions of proper PCB layout, but by playing about with [FreePCB](http://www.freepcb.com/) and looking at the specifications required by various manufacturing companies I was able to work it out. BTW: The costs involved can be quite an eye-opener!

{{< fg src="v2.webp" alt="V4Z80P" >}}

**What do you think that makes your computer more "special", the hardware itself or the software you have developed?**

> Being able to design my (and your) own architecture (via the FPGA) and have it act as a standalone computer is probably what I think of as the defining factor of the V6Z80P. My own architecture has evolved rather than being designed clearly at the start, but it's fun to "follow in the footsteps" of the designers of the classic 8-bit home micros (and then be able to push it further with the modern tech).
> 
> The actual hardware design of the V6Z80P is really pretty simple, all it really is is an FPGA, RAM and CPU on one bus and two more SRAMs connected direct to the FPGA on their own busses. The software --mainly the OS-- again has being made on-the-fly and would make an experienced OS designer weep, but its been made in the spirit learning and experimentation, which is how hobbies should be :smile:

**How many units of the V6Z80P have been built? How much time do you spend building one of them?**

> I think there's about 40 dotted around the planet by now. Build time varies (if I'm making more than one, production-line style saves a bit of time) but I guess it takes me about 6 hours to solder a V6Z80P together (then there's the cables, testing etc). It's impossible for me to make them in any commercially profitable sense, I just make them for fellow enthusiasts :smile:

**Some of these computers have arrived at very smart and talented people, such as [Altair](http://www.retroleum.co.uk/20100409/461/). Are the users of these machines as much active as them?**

> I still hear from a lot of the people who bought the boards, often they'll make suggestions for new features, etc.

**In the mailing list you talk about the eZ80P. When are we seeing the first prototype of your "most powerful" computer? :wink:**

> As soon as it has a basic architecture and way of running programs (EG: firmware updates), I'll announce it properly. I've come to realize I probably wont be able to use much of my existing FPGA architecture on it, because OSCA was made over a couple of years and I dont think anyone will want to wait that long for me to complete another design :smile:
> 
> So yeah, when it can do something (if it ever does!) is probably when I'll be happy to start selling eZ80Ps.

{{< yt M8hL3Eiqh_c >}}

**Do you think that PCs are unnecessarily complex today? I was dreaming about simple (but powerful) computers with zero boot time when I was a kid...**

> Yeah, that's the trouble with the PC - it always wants to do everything and be the universal tool for all occasions. But whatever hardware advances are made, the OS bloats out and nullifies them. Without a breakthrough in fast non-volatile RAM its hard to see things improving much.
> 
> I was reading the other day about the BIOS finally being replaced and this being the key to faster start-ups. I'm not entirely convinced :smile: