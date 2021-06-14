# Documentando con Alberto Laboratorio02
## Mi segundo procedimiento

>Elementos necesarios para el desarrollo del Laboratorio01:

- Ubuntu version 20.04.2.0 (puede ser una version inferior o superior)
- Docker Desktop
- Ngnix Latest

Pasos a seguir para la creacion del Laboratio01:

>1. Creacion directorio Laboratorio02
`````
"mkdir Laboratorio02"
`````
>2. Creacion de **Dockerfile** dentro del directorio prueba_docker
`````
"vim Dockerfile"
`````
>3. Configuracion de **DockerFile** / Esto lo podemos encontrar en el sitio de NGNIX-latest
`````
FROM nginx:latest

COPY ./index.html /usr/share/nginx/html/index.html
`````
>5. Creacion de **index.html** dentro del directorio Laboratorio02
`````
"vim index.html"
`````
>6. Configuracion de **index.php**
`````
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>LABORATORIO 02 NGNIX</title>
</head>
<body>
  <h2>ALBERTO NGNIX VERSION 01</h2>
</body>
</html>

`````
>7. Construccion de la imagen , tageamos ***(-t)*** segun el nombre que queramos poner y construimos
`````
"docker build -t ngnix:albertov01 ."

`````
>8. Verificamos si la imagen a sido creado de manera correcta
`````
"docker images"

REPOSITORY   TAG                    IMAGE ID       CREATED       SIZE
ngnix      albertov01            dbd437bf19fd     5 hours ago     133MB

`````
>9. Luego corremos el contenedor , ademas de eso aplicamos el ***-dp*** (d): para correr el contenedor en segundo plano y (p): para asignar el puerto que queramos. Por ultimo colocamos el nombre que deseamos para poder identificarlo con facilidad.
`````
"docker run -dp 81:80 --name=albertov01 ngnix:albertov01"

alberto@alberto-VirtualBox:~/Laboratorio02/src$ docker run -dp 81:80 --name=albertov01 ngnix:albertov01
4dc80059a5a2afdcf2469276c8e6b57100636d16261632920d408ae587890f6f

`````
>10. Se ejecuta el comando docker ps para ver en detalle el contendor corriendo
`````
"docker ps"

alberto@alberto-VirtualBox:~/prueba_docker/src$ docker ps
CONTAINER ID   IMAGE                     COMMAND                  CREATED          STATUS          PORTS                               NAMES
4dc80059a5a2   ngnix:albertov01   "docker-php-entrypoi…"   12 minutes ago   Up 12 minutes   0.0.0.0:81->80/tcp, :::81->80/tcp   albertov01

`````
>11. Por ultimo consultamos la pagina web del contenedor con el puerto e ip correspondiente.
`````
"192.168.1.13:81"
`````
