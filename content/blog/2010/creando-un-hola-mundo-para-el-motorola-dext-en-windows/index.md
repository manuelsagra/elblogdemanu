---
title: 'Creando un "Hola Mundo" para el Motorola Dext en Windows'
description: 'Bastante sencillo, aunque requiere descargar algunas herramientas'
date: Mon, 11 Jan 2010 04:30:17 +0000
draft: false
tags: ['Android', 'Desarrollo']
categories: ['Artículos']
---

{{< fg src="m1.webp" alt="Hello World Android" >}}

Una de las cosas que más me gustan de tener un teléfono con **Android**, es la facilidad para poder crear aplicaciones en un entorno de desarrollo muy completo, y poder depurarlas fácilmente y de forma gratuita en el propio teléfono. En el caso concreto del **Motorola DEXT**, tuve que lidiar con algún que otro problemilla por el hecho de usar **Windows 7** de 64 bits --por eso me animé a escribir esta pequeña guía--, pero el resto de consejos de este artículo son aplicables para el resto de móviles que utilicen el Sistema Operativo apadrinado por **Google**.

## Instalando y configurando el entorno

El primer paso, es tener una versión reciente del kit de desarrollo de **Java** instalada. Para ello, [descargamos el software de la página de Sun](http://java.sun.com/javase/downloads/widget/jdk6.jsp), y lo instalamos como un programa más. A continuación, hay que hacer lo mismo con [Eclipse](http://www.eclipse.org/downloads/). En este caso, nos vale la edición más sencilla, y la "instalación" se limita a descomprimir el archivo en nuestro disco duro.

El siguiente paso es bajar el [SDK de Android](http://developer.android.com/sdk/index.html), y configurarlo. Una vez que lo hayamos descomprimido, hay que descargar algunos paquetes con el **SDK-Setup.exe**, y teniendo en cuenta que vamos a desarrollar para un teléfono que está basado en **Android 1.5**, necesitamos lo siguiente:

{{< fg src="m2.webp" alt="Hello World Android" >}}

Si la descarga os da problemas, marcad en las opciones que se fuerce el uso de "http" en vez de "https". Por cierto, el driver USB no nos vale para el **Motorola DEXT**... más adelante comentaré cómo solucionar este problema.

A continuación, hay que configurar el **Android Development Kit** en **Eclipse**. Para ello, vamos a "Help > Install New Software...", y añadimos el siguiente repositorio:

```
https://dl-ssl.google.com/android/eclipse/
```

De nuevo, podemos cambiar "https" por "http" si nos da problemas. Después de instalar las herramientas, reiniciamos **Eclipse**, y configuramos el SDK de **Android** que hayamos descomprimido anteriormente.

{{< fg src="m3.webp" alt="Hello World Android" >}}

El último paso consiste en crear un dispositivo virtual de **Android** (AVD), que nos servirá para probar nuestros programas en el **PC**. Para ello, pinchamos en el icono en forma de móvil que tendremos ahora en **Eclipse**, y le damos a "New". Lo importante es que tenga **Android 1.5**, y una resolución HVGA. Luego podemos afinar el resto de características (cámara, acelerómetro,...), pero para crear un proyecto básico, nos vale con esto:

{{< fg src="m4.webp" alt="Hello World Android" >}}

## ¡Hola Mundo!

Crear un proyecto es sencillo. En el diálogo que sale en la opción "File > New > Project...", seleccionamos "Android Project". Luego, rellenamos una serie de datos básicos:

{{< fg src="m5.webp" alt="Hello World Android" >}}

Como se trata de un proyecto muy básico, de momento no os preocupéis de lo que significa una "Activity", ni de crear un "Test Project"... esas cosas vendrán más adelante :wink:

Cuando hayáis creado el proyecto, modificad el fichero que se ha creado en "src/com.elblogdemanu.holamundo" por esto:

```java
package com.elblogdemanu.holamundo;

import android.app.Activity;
import android.os.Bundle;
import android.widget.TextView;

public class HolaMundo extends Activity {
    /* Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        TextView tv = new TextView(this);
        tv.setText("¡Hola Mundo!");
        setContentView(tv);
    }
}
```

Ahora, si le dais al botón de ejecutar --o a <kbd>Control</kbd> + <kbd>F11</kbd>--, y seleccionáis "Android Application", veremos algo similar en pantalla después de un ratito... ¡nuestra primera aplicación en **Android**!

{{< fg src="m6.webp" alt="Hello World Android" >}}

## Preparando el móvil

Para tener esta aplicación en nuestro **Motorola DEXT**, todavía quedan un par de cosillas por hacer. Lo primero, es habilitar la opción "Depuración USB" que está en "Ajustes > Aplicaciones > Desarrollo". Después viene instalar el driver USB de **Motorola**, pero esto tiene algo de miga si estamos en **Windows 7**.

Dependiendo de nuestro sistema operativo, tenemos dos opciones para la descarga (necesita registro gratuito previo):

*   [Versiones de 32 bits](http://developer.motorola.com/docstools/USB_Drivers/Handset_USB_Driver/)
*   [Versiones de 64 bits](http://developer.motorola.com/docstools/USB_Drivers/Handset_USB_Driver_64/)

El problema de la versión actual, es que el instalador no reconoce adecuadamente **Windows 7**:

{{< fg src="m7.webp" alt="Hello World Android" >}}

Para poder usarlo, tenemos que descomprimirlo manualmente, y luego usar los ficheros resultantes cuando el Sistema Operativo nos pregunte por la ubicación del driver. Para conseguir lo primero, tenemos que abrir una ventana de comandos (`cmd.exe`), y ejecutar lo siguiente en la carpeta en la que hayamos bajado el driver:

```powershell
msiexec /a fichero.msi /qb TARGETDIR="driver"
```

Una vez que tengamos el driver instalado, y conectemos el móvil al ordenador, si volvemos a ejecutar el programa en **Eclipse**... ¡lo veremos en nuestro móvil! Fácil, ¿verdad? Pues ahora [documentaros](http://developer.android.com/guide/topics/fundamentals.html) bien, y [publicad](http://www.android.com/market/) algo interesante :wink: