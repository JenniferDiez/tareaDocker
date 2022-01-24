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

