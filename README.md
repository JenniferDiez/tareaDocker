#  Proyecto Docker


**Tabla de Contenidos**

                
+ Ejercicio - Inicial 
+ Ejercicio - Trabajo con imágenes
    + Servidor Web
    + Servidor de base de datos
+ Ejercicio - Almacenamiento
    * Bind mount para compartir datos
+ Ejercicio - redes
    * Despliegue de contenedores en red: Adminer y MariaDB
+ Ejercicio - crea una imagen con Dockerfile
    * Crear una imagen con un servidor web que sirva un sitio web


## Ejercicio - Inicial 

Crear un contenedor demonio a partir de la imagen nginx , el contenedor se debe llamar servidor_web y se debe acceder a él utilizando el puerto 8181 del ordenador donde
tengas instalado docker.

`$ docker run -d --name servidor_web -p 8181:80 nginx `

`$ docker ps`

`$ docker images`

`$ docker stop servidor_web`

`$ docker ps`

`$ docker rm servidor_web`

`$ docker ps -a`

1. Pantallazo donde se vea la creación del contenedor y podamos comprobar que el contenedor está funcionando.

![](https://github.com/Dawclas/Proyecto/blob/39abd8b102a4be6163a0c7411df5530d04b0ff38/Capturas/Captura1.PNG)

2. Pantallazo donde se vea el acceso al servidor web utilizando un navegador web (recuerda que tienes que acceder a la ip del ordenador donde tengas instalado
docker)

![](https://github.com/Dawclas/Proyecto/blob/39abd8b102a4be6163a0c7411df5530d04b0ff38/Capturas/Captura2.PNG)

3. Pantallazo donde se vean las imágenes que tienes en tu registro local.

![](https://github.com/Dawclas/Proyecto/blob/39abd8b102a4be6163a0c7411df5530d04b0ff38/Capturas/Captura3.PNG)

4. Pantallazo donde se vea cómo se elimina el contenedor (recuerda que antes debe
estar parado el contenedor).

![](https://github.com/Dawclas/Proyecto/blob/39abd8b102a4be6163a0c7411df5530d04b0ff38/Capturas/Captura5.1.PNG)

## Ejercicio trabajo con imágenes
### Servidor Web
### Servidor de base de datos
## Ejercicio Almacenamiento
### Bind mount para compartir datos

1. Crea una carpeta llamada *saludo* y dentro de ella crea un fichero llamado *index.html* con el siguiente contenido (Deberás sustituir ese XXXXXx por tu
nombre.):

```html
        <h1>HOLA SOY XXXXXX</h1>
```
`$ mkdir saludo`

`$ cd saludo/`

`$ echo "<h1>HOLA SOY XXXXXX</h1>" > index.html`

![](https://github.com/Dawclas/Proyecto/blob/bb5aa01084466b2d2734703369df72234370834e/capturasBindMount/Captura1.PNG)

2. Una vez hecho esto arrancar dos contenedores basados en la imagen php:7.4-apache que hagan un bind mount de la carpeta *saludo* en la carpeta */var/www/html* del contenedor. Uno de ellos vamos a acceder con el puerto 8181 y el otro con el 8282. Y su nombres serán *c1* y *c2* .

`$ docker run -d --name c1 --mount type=bind,src=/home/clientelinuxx/saludo,dst=/var/www/html -p 8181:80 php:7.4-apache`

`$ docker run -d --name c2 --mount type=bind,src=/home/clientelinuxx/saludo,dst=/var/www/html -p 8282:80 php:7.4-apache`

`$ curl http://localhost:8181 `

`$ curl http://localhost:8282 `

![](https://github.com/Dawclas/Proyecto/blob/bb5aa01084466b2d2734703369df72234370834e/capturasBindMount/Captura2.1.PNG)

![](https://github.com/Dawclas/Proyecto/blob/00bae2308b95006d89fffeb10db06c4f3256ec93/capturasBindMount/Captura2.2.PNG)

3. Modifica el contenido del fichero *~/saludo/index.html*.

`$ echo "<h1>Adios</h1>" > saludo/index.html`

![](https://github.com/Dawclas/Proyecto/blob/00bae2308b95006d89fffeb10db06c4f3256ec93/capturasBindMount/Captura3.PNG)

4. Comprueba que puedes seguir accediendo a los contenedores, sin necesidad de reiniciarlos.

`$ docker exec -it c1 bash`

`$ docker exec -it c2 bash`

`$ curl http://localhost:8181`

`$ curl http://localhost:8282`

![](https://github.com/Dawclas/Proyecto/blob/00bae2308b95006d89fffeb10db06c4f3256ec93/capturasBindMount/Captura4.2.PNG)

5. Borra los contenedores utilizados.

`$ docker rm -f c1`

`$ docker rm -f c2`

![](https://github.com/Dawclas/Proyecto/blob/00bae2308b95006d89fffeb10db06c4f3256ec93/capturasBindMount/Captura5.PNG)
