---
layout: post
title:  "Administración de Directorios Linux"
categories: [ linux, directorios, covid19 ]
image: assets/images/folder.jpg
author: drno
---

Al momento de conectarme a la maquina virtual para este post, se me presento el siguiente error.

<img src="{{site.baseurl}}/assets/images/lad/lad01.png" alt="Remote Hodt Indetification Has Changed" />

Este error se presenta cuando nos queremos conectar a la maquina virtual y esta ha cambiado su IP, cuando nos conectamos por primera vez aceptamos su key con una firma especifica y esta ha cambiado debido al cambio de ip.

Para poder solventar esto es muy facil, en la terminal de OSX en mi caso particular, colocamos lo siguiente:

``` python
    ssh-keygen -R [ip de la VM]
```
Como salida del comando tendremos algo como lo siguiente:

``` python
   ssh-keygen -R  192.168.0.16
   # Host 192.168.0.16 found: line 1
   /Users/ooo/.ssh/known_hosts updated.
   Original contents retained as /Users/ooo/.ssh/known_hosts.old
```

Listo posterior a eso nos conectamos por SSH a nuestra vm.

``` python
    ssh [ip vm] 
```

Algunos comandos para la gestion de directorios. 

* **pwd**: Muestra nuestra ubicación actual en el árbol de directorios Print Working Directory 

``` python
    
    debian@debian:~$ pwd
    /home/debian

```
La salida del comando pwd en este caso nos indica que estamos en **/home/debian** el directorio home del usuario actual.

* **ls**: Muestra el contenido de las carpetas, con el parametro **-l** mostrarmos mas información del contenido en la carpeta, usualmente algunas distros tienen un alias para este conjunto. **ll** es como hacer un **ls -l**

``` python
    debian@debian:~$ ls
    documentos  imagenes  musica  videos
    debian@debian:~$ ls -l
    total 16
    -rw-r--r-- 1 debian debian    0 May  4 17:50 archivoSecreto.txt
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 documentos
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 imagenes
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 musica
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 videos
    debian@debian:~$ 
```


* **cd**: Cambia nuestra ubicación en el árbol de directorios (Change Directory), para cambiarnos de directorio colocamos el comando seguido de la ruta a la que queremos movernos, para movernos rapidamente al directio home del usuario usamos el comando sin ruta.

``` python
    debian@debian:~$ tree .
    .
    |-- archivoSecreto.txt
    |-- documentos
    |-- imagenes
    |-- musica
    |   |-- bolitosMix.mp3
    |   |-- electronicas
    |   `-- rock
    `-- videos
        |-- Comedia
        |-- PollitosEnFuga.mkv
        `-- Terror

    8 directories, 3 files
    debian@debian:~$ 
```
Para mostrar la estructura de directorios por la cual nos podemos mover use el comando **tree** este comando no viene ionstalado por defecto en debian, para instalarlo usar el comando siguiente ***apt install tree.***

``` python

    debian@debian:~$ cd musica/electronicas/
    debian@debian:~/musica/electronicas$ cd ..
    debian@debian:~/musica$ cd .
    debian@debian:~/musica$ pwd
    /home/debian/musica
    debian@debian:~/musica$ cd 
    debian@debian:~$ pwd
    /home/debian
    debian@debian:~$ 
```
Si colocamos **.** (punto) como argumento eso estamos indicando que nos vamos a mover al directorio actual, esto basicamente no nos movera del directorio pero si pasamos **..** (dos puntos) entonces nos movemos al directorio padre.


* **touch**: Crea o lee archivos desde la terminal, importante mencionar que cuando leemos un archivo con touch este modifica la fecha de edicción.

``` python

    debian@debian:~$ ls -l
    total 16
    -rw-r--r-- 1 debian debian    0 May  4 17:50 archivoSecreto.txt
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 documentos
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 imagenes
    drwxr-xr-x 4 debian debian 4096 May  4 17:51 musica
    -rw-r--r-- 1 debian debian    0 May  4 18:08 otroArchivo
    -rw-r--r-- 1 debian debian    0 May  4 18:08 unArchivo.txt
    drwxr-xr-x 4 debian debian 4096 May  4 17:52 videos
    debian@debian:~$ 
```
Creare un arhivo llamado "Archivito" sin extension es intencional.

``` python

    debian@debian:~$ ls -l
    total 16
    -rw-r--r-- 1 debian debian    0 May  4 18:10 Archivito
    -rw-r--r-- 1 debian debian    0 May  4 17:50 archivoSecreto.txt
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 documentos
    drwxr-xr-x 2 debian debian 4096 May  4 17:46 imagenes
    drwxr-xr-x 4 debian debian 4096 May  4 17:51 musica
    -rw-r--r-- 1 debian debian    0 May  4 18:08 otroArchivo
    -rw-r--r-- 1 debian debian    0 May  4 18:08 unArchivo.txt
    drwxr-xr-x 4 debian debian 4096 May  4 17:52 videos
    debian@debian:~$

```
El archivo se ha creado mmmmm, pero como se si es un archivo, escrivamos algo dentro del el (el manejo de ficheros de texto sera otro post)

``` python 

    debian@debian:~$ cat Archivito 
    hola mundo
    este es una archivo de texto plano :) 

    fin:


    debian@debian:~$ 

```
**cat** es un comando para ver el contenido del archivo esto se explicara en este [post]({{ site.baseurl }}{% link _posts/2020-05-04-content-files.md %}).



* **mkdir**: Crea carpetas desde la terminal.

* **cp**: Copiar archivos y carpetas.

* **mv**: Mover archivo o caperta, permite cambiar nombre de los archivos y carpetas en la ruta final.

* **rm**: Eliminar archivos o carpetas, cuando las carpetas tienen contenido usamos el parametro **-r** para hacer borrado de forma recursiva.




