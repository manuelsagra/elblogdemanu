---
title: 'Configurando un servidor web LEMP con Debian 8'
description: 'Controlando como sirve la web tu hosting'
date: Tue, 22 Sep 2015 19:46:58 +0000
draft: false
tags: ['Internet']
categories: ['Varios']
---

{{< fg src="d1.webp" alt="LEMP" >}}

Este blog comenzó en **Wordpress.com** [hace casi una década](/hello-world/), pero no tardé en llevarlo a un servidor y a un dominio propios. Desde entonces, he pasado por varias compañías de hosting compartido, hasta que finalmente hace un par de años contraté un _Cloud VPS_ en [Gigas](https://gigas.com/). Desde ese momento, no he tenido prácticamente ningún problema, aunque una decisión que tomé al principio -junto con una metedura de pata reciente- me ha pasado factura.

Siempre me ha gustado trastear con **Linux** y configurar a mano los servidores, pero cuando contraté el servicio me regalaron una licencia de [Plesk](https://en.wikipedia.org/wiki/Plesk) y decidí usarla. Durante este tiempo, la configuración del servidor web, correo, y otros servicios ha sido muy sencilla gracias a este producto, pero también es cierto que hacer que algún que otro ajuste para mejorar el rendimiento era relativamente complejo por la arquitectura que mezclaba **Apache** y **nginx**, entre otros productos.

El problema real tuvo lugar hace unos días, cuando actualicé de _Wheezy_ a _Jessie_ sin tener en cuenta que **Plesk** no estaba soportado en la última versión de **Debian**, montando un infierno de dependencias de paquetes que dejó el servidor inoperativo. Sin embargo, la ocasión era perfecta para hacer una instalación limpia y tener todo configurado a mi gusto.

Además, no quería tener el típico conjunto **Apache** + **PHP** + **MySQL**, sino algo más potente... sobre todo después de leer el estupendo artículo de [Javier Pastor](https://twitter.com/javipas) titulado [WordPress a toda pastilla con Nginx+PageSpeed, MariaDB, HHVM y más en Ubuntu 12.04](http://www.javipas.com/2014/09/19/wordpress-a-toda-pastilla-con-nginxpagespeed-mariadb-hhvm-y-mas-en-ubuntu-12-04/) hace unos meses, una completa guía que me ha servido para tener mi servidor virtual funcionando como Dios manda. Como en mi caso no he usado **Ubuntu** sino **Debian**, y me he encontrado algún que otro problema en el proceso, he decidido publicar esta entrada para ayudar a la gente que se decida a probar esta configuración.

Después de tener una instalación actualizada de **Debian 8** en nuestro servidor -[un proceso sencillo](https://www.debian.org/releases/stable/installmanual) pero que va más allá de este artículo-, debemos realizar los siguientes pasos para tener la arquitectura que propone **Javier**.

## Instalando Nginx con PageSpeed

{{< fg src="d2.webp" alt="LEMP" >}}

Como dice la página de **Google** sobre [PageSpeed](https://developers.google.com/speed/pagespeed/module/build_ngx_pagespeed_from_source?hl=es) -un módulo para autoconfigurar el servidor web y optimizar los contenidos-, para tener [nginx](http://nginx.org/) con esta funcionalidad debemos compilar desde el código fuente. Podemos seguir la receta que sale en esa página, con la ventaja de estar usando la versión más reciente, o bien seguir [estas otras instrucciones](https://www.howtoforge.com/tutorial/nginx-with-ngx_pagespeed-on-debian-8-jessie/) para crear un paquete **Debian** parcheado. De esta manera tendremos una versión algo más antigua, pero más adaptada a nuestra distribución de **Linux**.

Después de instalarlo, el servidor ya estará operativo, y si hacemos un `curl` a **localhost** veremos un mensaje de bienvenida... aunque no estará funcionando el módulo pagespeed. Para ello, debemos añadir las opciones necesarias en **/etc/nginx/nginx.conf**:

```
server {
    # ...
    pagespeed on;
    pagespeed RewriteLevel CoreFilters;
    pagespeed FileCachePath "/var/cache/ngx_pagespeed/";
    pagespeed EnableFilters combine_css,combine_javascript,remove_comments,collapse_whitespace,rewrite_images;

    server_names_hash_bucket_size 64;
    # ...
}
```

Y también debemos crear el directorio correspondiente con los permisos necesarios. Para ello, ejecutamos esto en un terminal con permisos de administrador:

```bash
mkdir /var/cache/ngx_pagespeed/
chown www-data:www-data /var/cache/ngx_pagespeed/
```

## Instalar MariaDB

{{< fg src="d3.webp" alt="LEMP" >}}

Desde que **Oracle** se hizo con [MySQL](https://www.mysql.com/), muchos desarrolladores vieron las orejas al lobo, y junto al fundador de la popular base de datos realizaron un fork para crear [MariaDB](https://mariadb.org/). La idea es que permanezca libre y que sea totalmente compatible con **MySQL**.

Para instalarla en **Debian** sólo hay que ejecutar este comando:

```bash
apt-get install mariadb-server
```

También se puede instalar desde los repositorios de la aplicación, pero esta vez he decidido apostar por los de la propia distribución. Eso sí, como comentar **Javier**, es recomendable ejecutar `mysql_secure_installation` después para asegurar nuestra base de datos.

## Instalar HHVM

{{< fg src="d4.webp" alt="LEMP" >}}

[Hip Hop Virtual Machine](http://hhvm.com/) es un proyecto de **Facebook** para hacer un intérprete de **PHP** que vuele. Para instalarlo en nuestro servidor, sólo hay que seguir [las instrucciones de esta página](https://github.com/facebook/hhvm/wiki/Prebuilt-Packages-on-Debian-8) para hacerlo desde el repositorio oficial:

```bash
apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0x5a16e7281be7a449
echo deb http://dl.hhvm.com/debian jessie main | tee /etc/apt/sources.list.d/hhvm.list
apt-get update
apt-get install hhvm
```

A continuación tenemos que integrarlo con el servidor web. Para ello, ejecutamos lo siguiente:

```bash
apt-get install libboost-dev libboost-regex-dev libboost-system-dev libboost-program-options-dev libboost-filesystem-dev libboost-thread-dev
/usr/share/hhvm/install_fastcgi.sh
```

Si queremos usarlo como intérprete en línea de comandos (algo no obligatorio), podemos hacer un enlace simbólico:

```bash
ln -s $(which hhvm) /usr/local/bin/php
```

Para evitar problemas con la conexión a la base de datos, editamos el fichero **/etc/hhvm/php.ini** y añadimos esta línea:

```
hhvm.mysql.socket = /var/run/mysqld/mysqld.sock
```

Y ya sólo nos queda habilitar el servicio en el arranque con:

```bash
systemctl enable hhvm.service
```

## Configurar una web con Wordpress

{{< fg src="d5.webp" alt="LEMP" >}}

Después de reiniciar los servicios para que carguen la nueva configuración, ya tenemos todas las piezas necesarias para hacer funcionar [Wordpress](http://es.wordpress.org/) o cualquier otra página que haga uso de **PHP** y **MySQL**. Aunque podemos usar los directorios que nos ha creado **nginx** por defecto, os aconsejo crear configuraciones separadas para cada uno de los dominios que vayamos a alojar en nuestro servidor. Para ello, podemos crear los directorios necesarios de la siguiente manera:

```bash
mkdir -p /var/www/nombredeldominio.com/{logs,public_html}
```

Obviamente, tendréis que cambiar **nombredeldominio.com** por el vuestro. Luego hay que dar los permisos necesarios. Como el usuario que usa por defecto **nginx** es `www-data`, esto lo hacemos de la siguiente manera:

```bash
chown -R www-data:www-data /var/www/
```

Este comando es útil añadirlo a un alias en nuestro **~/.bashrc**, ya que será necesario ejecutarlo si subimos o editamos manualmente ficheros de nuestras webs.

Por otro lado, tendremos que crear la configuración de nuestra nueva web en **/etc/nginx/sites-available/nombredeldominio.com**, con el siguiente contenido adaptado a vuestro dominio:

```
server {
    listen 80;
    server_name www.nombredeldominio.com;
    return 301 $scheme://nombredeldominio.com$request_uri;
}

server {
 server_name nombredeldominio.com;
 listen 80;
 root /var/www/nombredeldominio.com/public_html;
 access_log /var/www/nombredeldominio.com/logs/access.log;
 error_log /var/www/nombredeldominio.com/logs/error.log;
 index index.php;

 include hhvm.conf;

 location / {
    try_files $uri $uri/ /index.php?q=$uri&$args;
 }

 location ~* \.(jpg|jpeg|gif|css|png|js|ico|png|svg|zip|woff|gz)$ {
    access_log off;
    expires 1y;
 }

 location ~ /\.ht {
    deny all;
 }

 location ~ \.php$ {
    fastcgi_index index.php;
    fastcgi_keep_conn on;
    include /etc/nginx/fastcgi_params;
    fastcgi_pass 127.0.0.1:9000;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
 }
}
```

Nuevamente, con nuestro dominio dónde corresponda. Para que esté disponible, sólo tenemos que hacer un enlace simbólico de este fichero en **/etc/nginx/sites-enabled**.

A continuación, tenemos que crear la base de datos. Para ello, nos conectamos con `mysql -uroot -p`, introducimos la contraseña que hayamos elegido en la instalación, y ejecutamos los siguientes comandos:

```sql
CREATE DATABASE wpdb;
GRANT ALL PRIVILEGES ON wpdb.* TO wpuser@localhost IDENTIFIED BY 'wppassword';
FLUSH PRIVILEGES;
exit
```

Donde **wpdb** será el nombre de nuestra base de datos, **wpuser** el usuario, y **wppassword** la contraseña de acceso. Estos datos tenemos que elegirlos y anotarlos para cuando hagamos la instalación de **Wordpress**.

Ahora nos queda descomprimir [la versión más reciente de Wordpress](http://wordpress.org/latest.tar.gz) en el directorio de **/var/www** correspondiente, ajustar los permisos de los ficheros, ir a nuestro navegador, y completar la instalación.

Deberíamos notar que va bastante rápido todo, aunque todavía se puede mejorar un poquito más...

## Bonus: acelerando la respuesta con Varnish Cache

{{< fg src="d6.webp" alt="LEMP" >}}

Este paso no es necesario, sobre todo en webs con poco tráfico, pero si los recursos de nuestro servidor lo permiten (sobre todo si vamos sobrados de memoria RAM), podemos poner por delante de **nginx** un servidor de caché como [Varnish](https://www.varnish-cache.org/).

Para instalarlo, seguimos [las instrucciones oficiales](https://www.varnish-cache.org/installation/debian) para tener la última versión. Luego tenemos que cambiar la configuración para que **Varnish** redirija todas las peticiones no cacheadas a **nginx**. Para ello, cambiamos los puertos de los servidores configurados en **/etc/nginx/sites-available** a, por ejemplo, 8080. Por cierto, un consejo: poned `listen localhost:8080;` si no queréis que se pueda acceder desde el exterior por este puerto, y añadid `port_in_redirect off;` a **/etc/nginx/nginx.conf** para evitar el redireccionamiento de puertos.

A **Varnish** tenemos que decirle que escuche en el 80, y que el backend está en el 8080. Además, tenemos que hacer unos pequeños ajustes para que **Wordpress** funcione de forma óptima. Para ello, tenemos que editar **/etc/default/varnish**, y cambiar el bloque descomentado por esto:

```
DAEMON_OPTS="-a :80 \
             -T localhost:6082 \
             -f /etc/varnish/default.vcl \
             -S /etc/varnish/secret \
             -s malloc,512m"
```

La memoria asignada en la última línea dependerá de la que tengamos disponible en nuestro servidor. Lo que no dicen en muchos sitios, es que como **Debian 8** utiliza **systemd** -ahora empiezo a entender porqué la gente lo odia-, tenemos que copiar **/lib/systemd/system/varnish.service** a **/etc/systemd/system/**, y cambiar el puerto y la memoria asignada también en ese fichero. Luego tenemos que recargar la configuración con:

```bash
systemctl reload varnish.service
```

También tenemos que modificar el fichero **/etc/varnish/default.vcl** para que las cookies de **Wordpress** no den problemas, y permitir que desde la web se puedan eliminar de la caché los contenidos modificados. En mi caso, ha quedado así:

```
vcl 4.0;

backend default {
    .host = "127.0.0.1";
    .port = "8080";
}

acl purge {
        "localhost";
        "IP_DEL_SERVIDOR"; #Cambiad esto por la vuestra!!!!
}

sub vcl_recv {
        if (req.method == "PURGE") {
                if (client.ip !~ purge) {
                        return (synth(405));
                }
                if (req.http.X-Purge-Method == "regex") {
                        ban("req.url ~ " + req.url + " && req.http.host ~ " + req.http.host);
                        return (synth(200, "Banned."));
                } else {
                        return (purge);
                }
        }

        if (req.url ~ "wp-admin|wp-login") {
                return (pass);
        }

        set req.http.cookie = regsuball(req.http.cookie, "wp-settings-\d+=[^;]+(; )?", "");
        set req.http.cookie = regsuball(req.http.cookie, "wp-settings-time-\d+=[^;]+(; )?", "");
        set req.http.cookie = regsuball(req.http.cookie, "wordpress_test_cookie=[^;]+(; )?", "");

        if (req.http.cookie == "") {
                unset req.http.cookie;
        }

        if (req.url ~ "/feed") {
		return (pass);
	}
}

sub vcl_backend_response {
        if (beresp.ttl == 120s) {
                set beresp.ttl = 1h;
        }
}

sub vcl_deliver {
	unset resp.http.Server;
	unset resp.http.X-Powered-By;
	unset resp.http.X-Page-Speed;
	unset resp.http.Via;
	unset resp.http.X-Varnish;
}
```

Tras reiniciar los servicios, nuestras páginas y recursos deberían cargar mucho más rápido, y deberíamos haber ganado algunos puntos en [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/?hl=es). Sólo nos quedaría instalar el plugin [Varnish HTTP Purge](https://wordpress.org/plugins/varnish-http-purge/) para que se actualice automáticamente la caché cuando se modifiquen los contenidos.

Obviamente, todo esto se puede afinar dependiendo de las necesidades de cada uno... pero eso ya os lo dejo como deberes para sacar nota :)