---
title: 'Entrevista a Francisco Javier Peña (Utopian) de Retroworks'
description: 'Un desarrollador que exprime a tope el ZX Spectrum'
date: Tue, 30 Nov 2010 15:26:58 +0000
draft: false
tags: ['Desarrollo', 'Juegos', 'Retro']
categories: ['Entrevistas']
---

{{< fg src="u1.webp" alt="Utopian" >}}

Lo bueno de asistir a eventos como [RetroMadrid](/tag/retromadrid/), es que te permiten conocer gente que comparte tus gustos y aficiones, y también a los que están detras de los títulos que se presentan cada año. Una de estas personas es **Javier Peña** --más conocido en el mundillo como **utopian**--, que después de la disolución de **CEZ GS**, pasó a formar parte del grupo **Retroworks**.

Su afición a la programación la comparte entre la "[escena](http://escena.org/)" --pertenece al grupo [rgba](http://www.rgba.org/)--, y los ordenadores _vintage_, como el **Spectrum** o el **MSX**. Su afición a estas máquinas de 8 bits le ha llevado a programar algunos juegos, debutando hace tres años con "[Cannon Bubble](http://computeremuzone.com/ficha.php?id=14)". Después, ha estado colaborando en otros títulos, y recientemente ha visto la luz su genial shoot'em up "[Genesis: Dawn of a new day](http://www.retroworks.es/php/game.php?id=8)". Quería hacerle una entrevista desde hace tiempo, y he aprovechado este lanzamiento para hacerle unas preguntillas...

**La primera pregunta creo que se la estará planteando mucha gente. ¿Porqué hacer juegos para máquinas obsoletas, y no aprovechar al máximo las que hay hoy en día?**

> Pues precisamente porque nos gustan esas máquinas. Mi infancia está ligada al **Spectrum**: al que tenía mi primo, al de mi compañero de clase, al que tras muchos años conseguí unas Navidades... Siempre alucinaba con los juegos que cargaba en él, y soñaba con que era capaz de hacer algo como eso y ganarme la vida desarrollando juegos. Con el tiempo, he tenido la posibilidad de aprender lo suficiente como para hacer juegos para el ordenador que marcó mi vida, y es algo que me encanta. Me gusta la sensación de mantener vivo un ordenador de hace casi 30 años.
> 
> ¿Y por qué no aprovechar las máquinas de hoy? Principalmente hay dos motivos: el primero es que disfruto con las máquinas obsoletas, y el segundo es que desarrollar para una máquina actual requeriría una cantidad de esfuerzo que no puedo dedicar, teniendo en cuenta que tengo una familia, dos hijos, un trabajo, etc. Precisamente una de las grandes ventajas de un ordenador obsoleto es que te limita en todos los aspectos: tienes poca CPU, tienes poca memoria, tienes pocos recursos para hacer lo que quieres. Así que te tienes que centrar en hacer algo divertido, que enganche, y no puedes dedicarte a montar un engine 3D con todas las virguerías posibles, ni un motor de físicas hiperrealista: simplemente no te cabe. Y eso te da la posiblidad de hacer algo de calidad con una cantidad limitada de tiempo y de gente.

**¿Cuál es tu entorno de desarrollo? ¿Prefieres utilizar compiladores cruzados y herramientas actuales, o eso de programar directamente en un Spectrum tiene más magia?**

> Yo ni me plantearía programar directamente en un **Spectrum**. Sé que sería más purista, pero con todas las facilidades que nos da un **PC** de hoy día no me veo haciéndolo "_a la antigua usanza_". Mi entorno es un **PC** con **Linux**, mi editor de texto favorito --con syntax highlighting, eso sí :wink:--, y compiladores y ensambladores cruzados: [z88dk](http://www.z88dk.org/) para código C y [Pasmo](http://www.arrakis.es/~ninsesabe/pasmo/) para ensamblador. Luego me monto un makefile, y entre eso, los emuladores y un par de herramientas a medida ya tengo suficiente.
> 
> Ojo, el que desarrolle sobre **PC** no quiere decir que me olvide de la máquina real... ¡en absoluto! Siempre pruebo todo lo que puedo en mis ordenadores de casa, pero es algo que suelo hacer en momentos concretos del desarrollo, para asegurarme de que lo que veo en el emulador encaja con lo que ocurre en la máquina real, que no he introducido incompatibilidades extrañas, etc.

**¿De qué juego estás más orgulloso? ¿Cuál supuso el mayor reto?**

> Siempre me siento más orgulloso del que acabo de terminar, así que en este caso es "_Genesis: Dawn of a new day_". Me ha supuesto un tiempo de desarrollo muy alto (¡casi tres años!), así que después de tanto tiempo casi se me hacía raro publicarlo :smile:
> 
> Las primeras reacciones no han podido ser más positivas. Una de las anécdotas que más me ha marcado ha sido el tiempo récord que ha tardado el juego en aparecer en los foros rusos: yo creo que a los 5 minutos de publicarlo en la web ya estaba la noticia.
> 
> En todos mis juegos he tenido algún reto importante a superar. Si tuviese que destacar alguno, tal vez sería "_Cannon Bubble_", por ser el primero y el que supuso mi principal aprendizaje a la hora de hacer un juego desde el principio hasta el final.

{{< fg src="u2.webp" alt="Cannon Bubble" >}}

**Un detalle que me llama la atención, es la gran cantidad de gente que se dedica al desarrollo de juegos para ordenadores de 8 bits en nuestro país, especialmente para el Spectrum. ¿Cuál crees que es el motivo de esto? ¿Por qué precisamente esa generación de ordenadores?**

> Por un lado creo que es una cuestión generacional: todos los que tuvimos ordenadores de 8 bits en la época somos ahora gente adulta, con una vida más o menos estabilizada y algo de tiempo libre. Además, los ordenadores de 8 bits siempre incitaron de alguna forma al usuario a hacer algo con él, más allá de jugar. Los listados en BASIC, los propios manuales llenos de información técnica, todo te invitaba a programar algo. Esto hace que muchos de aquellos jugones ahora tengan los suficientes conocimientos para lanzarse a desarrollar, cosa que no es tan habitual en ordenadores de 16 bits, que a final de cuentas tuvieron un menor mercado.
> 
> Y ya no hablemos de las consolas, que sencillamente no te daban la posibilidad de pensar en hacer otra cosa que no fuese jugar :smile:

**Como dices, antes las máquinas incitaban más a trastear que las de ahora. ¿Crees que los ordenadores de hoy en día están creando una generación que solo se interesa por jugar?**

> Yo diría que sí, en particular porque la barrera de entrada para hacer algo "vistoso" se pone cada vez más alta. ¿Cómo consigues motivar a alguien para que haga un juego nuevo para la **PS3**? Antes de ser capaz de mover algo necesita tener conocimientos de un API brutal, matemáticas como para ir a la universidad, o conocimientos avanzados de diseño 3D, por no decir que directamente no es posible hacer eso **legalmente** en tu consola. Así es muy difícil que un niño que recibe su consola por Navidad tenga el mínimo interés, simplemente porque ni siquiera sabe que es posible hacerlo.

**Una cosa que me sorprende, es el hecho de que os molestéis en sacar copias físicas de los juegos, acudiendo incluso a una empresa duplicadora de cintas en el Reino Unido, en vez de hacer algo más casero. ¿Lo hacéis como "fan service", o también para tener vuestro pequeño "trofeo"? :wink:**

> Un poco por las dos cosas :smile. Es una enorme satisfacción ver tu juego en la caja, con su cinta serigrafiada, sus instrucciones y ese aspecto de estar recién comprada en tu tienda de toda la vida...
> 
> No deja de ser una vuelta a esa infancia que es parte de nuestra motivación, y en el fondo te hace pensar por un momento que si fuésemos hacia atrás en el tiempo con una de esas cintas y se la presentásemos a la redacción de **MicroHobby**, lo mismo hasta nos daban una buena puntuación :smile:
> 
> También nos gusta la idea del "fan service" que comentas. Aparte de desarrolladores, somos consumidores, y para mí sigue siendo diferente la apreciación de un juego cuando lo tienes en tus manos y puedes manosearlo, frente a la simple descarga, que es algo más "fría", digamos.

**Echando un vistazo a los títulos que se han publicado en los últimos años para plataformas "vintage", me ha parecido curioso que hayan salido tan pocos "shoot'em ups". ¿Crees que es por el género en sí, o por las complicaciones a la hora de desarrollar un juego de este tipo?**

> Pues yo veo varios motivos. Uno es la complejidad técnica que tienen: hacerse una buena rutina de scroll no es trivial, y la mayoría de los que estamos ahora desarrollando para plataformas antiguas vamos aprendiendo sobre la marcha, con lo que pasa mucho tiempo hasta que llegamos a ser capaces de hacerlo, siempre y cuando tengamos ganas de hacerlo (que ese es otro tema).
> 
> E incluso siendo capaces, luego hay que hacer un juego completo alrededor, ¡casi "ná"! IA de los enemigos, niveles suficientes, una cantidad salvaje de gráficos si quieres que el juego tenga una mínima variedad, músicas, jugabilidad, etc, etc. Yo he visto en [WoS](http://www.worldofspectrum.org/) varias demos técnicas de gente que ha sido capaz de montar un muy buen motor y un nivel con enemigos, más o menos trabajado. Pero ahí es donde acaba lo divertido, a partir de ahí necesitas ser lo bastante cabezón como para dedicarte a la parte más sufrida, que es seguir haciendo el juego hasta que lo tienes 100% terminado y publicarlo, y es fácil dejarlo por mero aburrimiento. Para hacerte una idea, en marzo de 2009 ya teníamos el motor y un nivel en un estado bastante jugable, y lo enseñamos en **RetroMadrid**. Desde entonces hasta ahora todo el tiempo se ha dedicado a crear el juego.
> 
> Aún así, algún juego se ha visto, con joyas como "[Star Sabre](http://starsabre.bigblog.com.au/index.do)" para **CPC** o "[J.E.T.P.A.C.](http://imanok.msxblue.com/games.html)" y "[Space Manbow 2](http://es.msx.org/Manbow-2.articlepage71.html)" para **MSX**. En general, cuando consigues llegar hasta el final, el resultado merece la pena :smile:

**Desde hace unos años, ha participado en MadriSX/RetroMadrid, un evento en el que nos juntamos muchos usuarios aficionados a la informática clásica. Después de haber estado en la última RetroMadrid FEST, ¿cuál es tu percepción de esta feria? ¿Crees que la gente en general tiene una visión acertada de la "informática clásica"?**

> Para mí **RetroMadrid** es uno de los "_pegamentos_" que une a los aficionados a la informática clásica. Es un evento que ha crecido hasta niveles inimaginables hace unos años, y un lugar de encuentro fantástico con gente que apenas puedes ver en ese día, aparte de la mejor oportunidad de hacerte con los últimos desarrollos en formato físico. Precisamente por su crecimiento corre el riesgo de morir de éxito, pero me consta que en la organización son conscientes de este riesgo, y se trabaja un montón para que, a pesar del tamaño, siga atrayéndonos a los usuarios más clásicos, aparte de al público en general.
> 
> Acerca de la visión sobre la informática clásica: yo creo que va mejorando, gracias al trabajo de las diferentes asociaciones y grupos que nos dedicamos a esto. Aún queda trabajo por recorrer, pero cada vez se nos ve menos como unos "_frikis sin vida social_", y más como un grupo de gente con una afición concreta, igual que los coleccionistas de sellos o los clubes de amigos del 600.
> 
> Como anécdota curiosa, para la última **RetroMadrid** participé en [un reportaje que hicieron los informativos de Antena 3](http://pre.antena3noticias.com/PortalA3N/ciencia-y-tecnologia/feria-Retro-Madrid-arqueologia-industrial-que-gana-adeptos/10165992). Me llamó la atención un comentario que hizo la periodista sobre mí: "_34 años y padre de dos niños_", y le pregunté el motivo. Su idea era precisamente que el espectador estableciese vínculos con el entrevistado, al vernos como el vecino del portal de enfrente. Y lo curioso es que, tiempo después, me envió un correo diciéndome que había hablado con una persona del departamento de prensa de **Nintendo**, y que justo le gustó ese detalle, que me presentasen como un padre de familia y no como un "_friki_" cualquiera.

{{< yt DMGAotVjtBs >}}

**Una pregunta clásica: ¿crees que se ha perdido la magia en los juegos actuales, o nos dejamos cegar por la nostalgia?**

> Creo que simple y llanamente ha cambiado el concepto, o hemos cambiado nosotros :smile:. Si te fijas, ahora con los juegos indie, la avalancha de juegos "casual" y la recuperación de clásicos, parece como si estuviésemos asistiendo a una nostalgia recuperadora de lo antiguo. Yo creo que ahora tenemos dos tipos diferentes de juego, muy diferenciados: el juego que busca un entretenimiento sencillo y más inmediato, que suele funcionar mejor con las fórmulas clásicas, y el juego "_complejo/espectacular_", que busca por un lado la espectacularidad gráfica, y por otro empieza a ser más complejo de desarrollar, tanto que empiezas a ver equipos de desarrollo que parecen estudios de cine de lo grandes que son.

**¿Qué piensan tus hijos de tu afición? ¿Les gusta trastear con tus juegos?**

> Pues de momento los tengo un poco apartados de los ordenadores, especialmente de los antiguos, no me los vayan a romper X-D. Aún son pequeños para poder disfrutarlos, pero espero que dento de unos años les gusten, y no me digan que los gráficos son cutres, o que tienen pocos colores o no son en 3D :smile:

**Gracias por tu tiempo, y suerte con tus proyectos... por cierto, ¿nos puedes adelantar algo del próximo?**

> Gracias a tí por la publicidad :wink:
> 
> El próximo proyecto... aparte de intentar portar el "_Genesis_" a alguna otra plataforma, sinceramente no tengo mucho que contar, y no es por no contarlo --que también :yum:--, es que aún no tengo nada decidido. Quiero dedicar un poco de tiempo a experimentar un par de ideas, a ver cuál de ellas me motiva lo bastante como para lanzarme a implementarla.