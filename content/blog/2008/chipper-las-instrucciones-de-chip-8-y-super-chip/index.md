---
title: 'Chipper: Las instrucciones de Chip-8 y Super Chip'
description: 'El meollo de la máquina virtual'
date: Mon, 24 Mar 2008 05:20:47 +0000
draft: false
tags: ['Tecnología']
categories: ['Artículos']
---

A principios de este mes, mostré algo de [información técnica y los orígenes de **Chip-8**](/chipper-documentacion-sobre-chip-8/), así como su primera extensión, llamada **Super Chip** o **SCHIP**. En este artículo, voy a comentar las instrucciones que tienen estas máquinas virtuales, para ver su funcionamiento de una manera sencilla de entender. He intentado agruparlas para que se vean de una manera más ordenada, aunque realmente esto es algo subjetivo, y no debería afectar al funcionamiento interno del emulador.

Aprovecho para recordar que todas tienen 16 bits de longitud, por lo que pongo su código máquina en hexadecimal para cada una de ellas, así como su nombre más o menos aceptado. Para ello, utilizo esta nomenclatura:

*   _nnn_: Una dirección de memoria de 12 bits
*   _nn_: Número de 8 bits (byte)
*   _n_: Número de 4 bits (nibble)
*   _x_, **y**: Registro

## Instrucciones de carga

Este tipo de instrucciones son las más sencillas de implementar, porque se limitan a introducir un valor en un registro, o en la memoria. El **Chip-8** dispone de varias instrucciones de este tipo:

### 6xnn - LD Vx, nn

Esta instrucción guarda el valor _nn_ en el registro especificado por _x_. Hay que recordar que el **Chip-8** dispone de 16 registros de propósito general.

### 8xy0 - LD Vx, Vy

Con esta instrucción podemos guardar el valor de un registro (_Vy_) en otro (_Vx_).

### Fx07 - LD Vx, DT

Carga en _Vx_ el valor del Delay Timer.

### Fx15 - LD DT, Vx

Esta hace lo contrario, ya que guardamos en el Delay Timer el valor de _Vx_.

### Fx18 - LD ST, Vx

Con esta cargamos el Sound Timer con el valor que tenga _Vx_. Hay que tener en cuenta que no hay una instrucción para leer el Sound Timer, ya que este registro simplemente hace que se reproduzca un sonido mientras que su valor sea distinto de cero, decrementándose en una unidad por cada interrupción.

### Annn - LD I, nnn

Guarda en el registro _I_ el valor de 12 bits _nnn_.

### Fx29 - LD F, Vx

Esta instrucción es algo especial, y a la hora de implementarla hay que hacer algunas suposiciones. En la parte de memoria que va desde 0000h a 0200h, se supone que se guarda el intérprete de **Chip-8**, así como algunas variables y constantes internas. En concreto, 80 bytes se reservan para la representación de caracteres hexadecimales, ocupando 5 bytes cada uno.

Lo más sencillo a la hora de implementar el emulador, es guardarlos desde la posición 0000h, por lo que esta operación simplemente devuelve _Vx_\*5.

### Fx33 - LD B, Vx

Después de ejecutar esta instrucción, tenemos en _I_, _I+1_ y _I+2_ la representación BCD del valor que hay en _Vx_.

¿Qué es eso del [BCD](http://es.wikipedia.org/wiki/BCD)? Se trata de un sistema numérico que emplea 4 bits por cifra, y que es bastante útil a la hora de representar números en displays de 7 segmentos, o a la hora de trabajar con números decimales. En el caso del **Chip-8**, se suele utilizar para representar puntuaciones en pantalla, con la ayuda de la instrucción anterior. Por lo tanto, después de ejecutar esta instrucción, en _I_ tendremos las centenas de _Vx_, en I+1 las decenas, y en I+2 las unidades.

### Fx55 - LD \[I\], Vx

Aunque el **Chip-8** tiene una pila, no hay operaciones específicas para meter y sacar datos en ella, y sólo se usa en las llamadas a subrutinas para guardar el contador de programa. Sin embargo, esta instrucción y la siguiente pueden servir para guardar el valor de cualquier registro. En concreto, esta guarda en memoria, a partir de I, los valores de los registros de _V0_ hasta _Vx_.

### Fx65 - LD Vx, \[I\]

Como cabría esperar, esta instrucción recupera de memoria, a partir de I, los valores de los registros de _V0_ a _Vx_

## Instrucciones aritmético-lógicas

Como cabría esperar, la operaciones que podemos hacer con el **Chip-8** no son demasiado complejas, pero son suficientes para hacer pequeños juegos. En concreto, podemos sumar y restar, hacer comparaciones lógicas, desplazar bits, e incluso generar valores aleatorios.

### 7xnn - ADD Vx, nn

Esta instrucción es bastante sencilla, ya que suma el valor de _Vx_ y _nn_, y lo guarda en _Vx_.

### 8xy4 - ADD Vx, Vy

Como cabría esperar, después de ejecutar este opcode, se suma _Vx_ y _Vy_, y se guarda el resultado en _Vx_. La novedad, es que en _VF_ --el registro que se suele reservar para los flags-- se guarda en acarreo de la operación.

### Fx1E - ADD I, Vx

Esta instrucción es útil para el direccionamiento indexado, ya que en _I_ tenemos el resultado de sumar el propio registro más _Vx_.

### 8xy5 - SUB Vx, Vy

Ahora vamos con la resta. En concreto, en esta ocasión guardamos en _Vx_ el resultado de substraer _Vx_ y _Vy_. Lo curioso es que _VF_ se pone a 1 si _Vx_ es mayor o igual que _Vy_, es decir, si el resultado es positivo o cero.

### 8xy7 - SUBN Vx, Vy

A diferencia de la anterior, en esta ocasión guardamos en _Vx_ la resta entre _Vy_ y _Vx_. Ahora _VF_ se pone a 1 si _Vy_\>=_Vx_.

### 8xy1 - OR Vx, Vy

En esta instrucción, se hace el OR lógico bit a bit entre _Vx_ y _Vy_, y se guarda en _Vx_.

### 8xy2 - AND Vx, Vy

Como cabría esperar, se realiza el AND lógico bit a bit entre _Vx_ y _Vy_, y se guarda en _Vx_

### 8xy3 - XOR Vx, Vy

Esta es la última operación lógica, y es similar a las anteriores, salvo por el hecho de que se realiza el OR exclusivo.

### 8xy6 - SHR Vx {,Vy}

Esta es la primera operación de desplazamiento de bits. En concreto, esta coge _Vx_, y desplaza los bits hacia la derecha, guardándose en _VF_ el valor del bit menos significativo previo al desplazamiento.

### 8xyE - SHL Vx {,Vy}

Esta es la instrucción hermana de la anterior, haciéndose en este caso el desplazamiento hacia la izquierda de _Vx_. Hay que tener en cuenta que _VF_ coge el valor del bit más significativo previo al desplazamiento. Lo que todavía no tengo claro, es si alguna vez se tiene en cuenta el valor de _Vy_ en estas dos operaciones...

### Cxnn - RND Vx, nn

Esta instrucción carga un valor aleatorio en _Vx_ entre 0 y 255, y después se hace un AND lógico con el valor de nn.

## Instrucciones de salto y llamada

Este tipo de instrucciones controlan el flujo del programa, implementan bucles,... por lo que son especialmente importantes.

### 0nnn - SYS addr

Esta instrucción es ignorada por los intérpretes modernos de **Chip-8**, ya que originalmente ejecutaba código nativo a partir de la dirección _nnn_.

### 1nnn - JP nnn

Este es el salto más básico, ya que el contador de programa (_PC_) se carga con el valor de _nnn_.

### Bnnn - JP V0, nnn

Esta instrucción es similar a la anterior, pero la dirección de salto se calcula sumando nnn y _V0_.

### 3xnn - SE Vx, nn

Si _Vx_ es igual a _nn_, se salta la siguiente instrucción, es decir, se incrementa en dos unidades el contador de programa.

### 4xnn - SNE Vx, nn

Con esta instrucción, se hace el salto si _Vx_ no es igual a _nn_.

### 5xy0 - SE Vx, Vy

La condición para saltar la siguiente instrucción es que _Vx_ sea igual a _Vy_.

### 9xy0 - SNE Vx, Vy

A diferencia de la anterior, se salta la siguiente instrucción si _Vx_ no es igual a _Vy_.

### 2nnn - CALL nnn

Se hace una llamada a una subrutina localizada en _nnn_. Previamente, se guarda el valor del contador de programa en la dirección inferior que apunta el registro de la pila (_SP_). Es decir, se guarda en _SP_\-1 la parte baja de _PC_, y en _SP_\-2 la parte alta.

### 00EE- RET

Esta es la instrucción que hay que poner al final de una subrutina para volver. Para ello, se recupera el valor de _PC_ --primero la parte alta y luego la baja--, y se incrementa el valor de _SP_.

## Instrucciones de entrada

En el caso del **Chip-8**, la entrada se limita a leer del teclado. Se dispone de tres instrucciones de carga y salto para ello:

### Ex9E - SKP Vx

Se salta la siguiente instrucción si el valor que se lee de teclado es igual a _Vx_.

### ExA1 - SKNP Vx

Esta es a la inversa: se salta la siguiente instrucción si el valor que se lee de teclado no es igual a _Vx_.

### Fx0A - LD Vx, K

Se para la ejecución del programa hasta que se pulsa una tecla, y luego se carga su valor en _Vx_.

## Instrucciones gráficas

Sólo se dispone de un par de instrucciones para dibujar en pantalla, pero el manejo de sprites permite hacer prácticamente cualquier cosa que nos imaginemos... en 1 bit :wink:

### 00E0 - CLS

Si alguna vez hemos usado el lenguaje **BASIC**, sabremos inmediatamente que esta instrucción borra la pantalla.

### Dxyn - DRW Vx, Vy, n

Esta instrucción pinta en las coordenadas (_Vx_, _Vy_), el sprite definido por los siguientes _n_ bytes en la posición indexada por _I_. Hay que recordar que se pinta por XOR, cambiando el estado de los pixels. Si en algún momento se detecta una "colisión", es decir, si se va a dibujar un pixel y ya estaba a uno, _VF_ se pone a 1.

En mi opinión, esta es la instrucción más compleja de implementar, y puede dar lugar a algún dolor de cabeza hasta que se hace correctamente.

## Instrucciones de SCHIP

Para soportar las características extendidas de **SCHIP**, se añadieron algunas instrucciones, y se cambió la última que hemos visto, para hacerla un poco más potente.

### 00FD - EXIT

Esta instrucción hace que se salga del intérprete, bastante útil para devolver el control del dispositivo en las calculadoras, una vez terminado el juego.

### 00FE - LOW

Deshabilita el modo de pantalla extendido, volviéndose a una resolución de 64x32 píxeles.

### 00FF - HIGH

Se dice al intérprete que la resolución es de 128x64 píxeles.

### Fx75 - LD R, Vx

Se guardan los valores de _V0_ a _Vx_ en los registros de usuario de la calculadora **HP-48**. No se suele implementar en los emuladores.

### Fx85 - LD Vx, R

Esta instrucción recupera los valores de los registros de usuario de la **HP-48**, y tampoco se implementa.

### 00Cn - SCD n

Se hace un scroll de n líneas en la pantalla hacia abajo. Las primeras _n_ líneas de la pantalla se ponen a 0.

### 00FB - SCR

Esta vez el scroll es de 4 píxeles hacia la derecha. Las 4 primeras columnas de píxeles se pierden.

### 00FC - SCL

Igual que la anterior, pero con scroll hacia la izquierda.

### Fx30 - LD HF, Vx

Esta instrucción es similar a **LD F, Vx**, pero ahora los sprites son de 10 bytes de altura, y sólo están representados los números, no las letras de la A a la F.

### Dxy0 - DRW Vx, Vy, n

Se añade la particularidad de que si _n_ es igual a 0, se dibuja un sprite de 16x16 píxeles.

## ¿Y ahora?

La verdad es que este artículo es un poco rollete si no se hace algo práctico, así que en el próximo vamos a ver algunos de los posibles lenguajes en los que se puede programar el emulador, y voy a mostrar los principales entornos de desarrollo para ver cuál se ajusta mejor a nuestras necesidades.