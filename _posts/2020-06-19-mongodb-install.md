---
layout: post
title:  "Instalación de MongoDB"
categories: [MongoDB, M001,  mac osx]
image: assets/images/mongo.png
author: drno
---

Mientras espero que el antivirus de mi maquina virtual windows termine el escaneado completo, para conectarme a la vpn del trabajo, retomare el curso M001 de mongodb por la Mongo University. 

Uno de los primeros assets es instalar el server, usare el community la pobresa no me deja usar la version entreprise :sweat:, pero como ya saben para aprender las bases no necesitamos más.

Primer paso bajar el instalador, como estoy en un mac osx, pues me bajo el instalador de mac osx (es obvio).

Para ello nos descargamos el archivo desde el sitio de [mongodb](https://www.mongodb.com/try/download/community){:target="_blank"}, con el archivo en nuestro sistema lo instalamos como cualquier otro programa, pues no.

Lo interesante del server es que cada servicio o programa estan separados y nos viene una carpeta bin, ¿Que rayos hacer con esto?.

Contenido de la carpeta bin:

```` python
bin|⇒ ll
total 626640
-rwxr-xr-x@ 1 drno  staff    13M Jun 11 10:35 bsondump
-rwxr-xr-x@ 1 drno  staff   7.5K Jun 11 10:49 install_compass
-rwxr-xr-x@ 1 drno  staff    45M Jun 11 10:44 mongo
-rwxr-xr-x@ 1 drno  staff    71M Jun 11 10:49 mongod
-rwxr-xr-x@ 1 drno  staff    18M Jun 11 10:35 mongodump
-rwxr-xr-x@ 1 drno  staff    18M Jun 11 10:35 mongoexport
-rwxr-xr-x@ 1 drno  staff    17M Jun 11 10:35 mongofiles
-rwxr-xr-x@ 1 drno  staff    18M Jun 11 10:35 mongoimport
-rwxr-xr-x@ 1 drno  staff    17M Jun 11 10:35 mongoreplay
-rwxr-xr-x@ 1 drno  staff    18M Jun 11 10:35 mongorestore
-rwxr-xr-x@ 1 drno  staff    37M Jun 11 10:42 mongos
-rwxr-xr-x@ 1 drno  staff    17M Jun 11 10:35 mongostat
-rwxr-xr-x@ 1 drno  staff    17M Jun 11 10:35 mongotop

````

Movere los archivos a /usr/local/bin para no tener que modificar los paths o si lo dejan en otro sitios hay que modificar el path para poder usar los programas desde nuestra terminal, lo que consideren adecuado.

Luego ejecutar
```` python
    mongo --nodb
````

Si todo va bien deberiamos tener una salida en nuestra terminal como esta:
```` python
~|⇒ mongo --nodb
MongoDB shell version v4.2.8
> 
````

Listo!!! ya tenemos mongodb instalado.


