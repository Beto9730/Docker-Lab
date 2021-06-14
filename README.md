# Documentando con Alberto
## Mi segundo procedimiento

>Elementos necesarios para el desarrollo del Laboratorio01:

- Ubuntu version 20.04.2.0 (puede ser una version inferior o superior)
- Docker Desktop

Pasos a seguir para la creacion del Laboratio01:

>1. Creacion directorio prueba_docker
`````
"mkdir prueba_docker"
`````
>2. Creacion de **Dockerfile** dentro del directorio prueba_docker
`````
"vim Dockerfile"
`````
>3. Configuracion de **DockerFile** / Esto lo podemos encontrar en el sitio oficial de PHP en DockerHub
`````
FROM php:7.4.20-apache-buster

COPY src/ /var/www/html/
`````
>4. Creacion del directorio src dentro del directorio prueba_docker
`````
"mkdir src"
`````
>5. Creacion de **index.php** dentro del directorio src
`````
"vim index.php"
`````
>6. Configuracion de **index.php**
`````
<?php
for ($x = 0; $x <= 10; $x++) {

        if ($x <= 1) {
                echo "$x VERSION 15 ALBERTO  <br>";

        }elseif ($x > 1) {
                echo "$x VERSION 15 ALBERTO  <br>";
        }

}
?>
`````
>7. Construccion de la imagen , tageamos ***(-t)*** segun el nombre que queramos poner y construimos
`````
"docker build -t hola-php:v15-albertov15 ."

`````
>8. Verificamos si la imagen a sido creado de manera correcta
`````
"docker images"

REPOSITORY   TAG                    IMAGE ID       CREATED       SIZE
hola-php     v15-albertov15         5816a6b3dc53   5 hours ago   414MB

`````
>9. Luego corremos el contenedor , ademas de eso aplicamos el ***-dp*** (d): para correr el contenedor en segundo plano y (p): para asignar el puerto que queramos. Por ultimo colocamos el nombre que deseamos para poder identificarlo con facilidad.
`````
"docker run -dp 81:80 --name=albertov15 hola-php:v01-albertov15"

alberto@alberto-VirtualBox:~/prueba_docker/src$ docker run -dp 97:80 --name=albertov15 hola-php:v15-albertov15
4dc80059a5a2afdcf2469276c8e6b57100636d16261632920d408ae587890f6f

`````
>10. Se ejecuta el comando docker ps para ver en detalle el contendor corriendo
`````
"docker ps"

alberto@alberto-VirtualBox:~/prueba_docker/src$ docker ps
CONTAINER ID   IMAGE                     COMMAND                  CREATED          STATUS          PORTS                               NAMES
4dc80059a5a2   hola-php:v15-albertov15   "docker-php-entrypoi…"   12 minutes ago   Up 12 minutes   0.0.0.0:97->80/tcp, :::97->80/tcp   albertov15

`````
>11. Por ultimo consultamos la pagina web del contenedor con el puerto e ip correspondiente.
`````
"192.168.1.13:81"
`````
