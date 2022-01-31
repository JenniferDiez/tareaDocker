## Ejercicio - crea una imagen con Dockerfile

### Crear una imagen con un servidor web que sirva un sitio web

1. Pantallazo/bloque de código con el Dockerfile

`$ nano dockerfile`

    | FROM httpd:2.4 |
    | ADD public_html /usr/local/apache2/htdocs/ |
    | Expose 80 |

![](https://github.com/JenniferDiez/tareaDocker/blob/71e623c28a8915e848ffd41fd10271483f898653/imagen%20con%20Dockerfile/capturas/cap%201.png)

2. Pantallazo donde se vea el comando que crea la nueva imagen.

`$ docker build -t dockerr007/paginaapache:latest .`

`$ docker run --name ejemplo -d -p 80:80 dockerr007/paginaapache:latest`

`$ docker ps`

![](https://github.com/JenniferDiez/tareaDocker/blob/71e623c28a8915e848ffd41fd10271483f898653/imagen%20con%20Dockerfile/capturas/captura%201.png)

![](https://github.com/JenniferDiez/tareaDocker/blob/71e623c28a8915e848ffd41fd10271483f898653/imagen%20con%20Dockerfile/capturas/captura%202.png)

3. Pantallazo donde se vea la imagen subida a tu cuenta de Docker Hub.

`$ docker login`

`$ docker push dockerr007/paginaapache:latest`

![](https://github.com/JenniferDiez/tareaDocker/blob/71e623c28a8915e848ffd41fd10271483f898653/imagen%20con%20Dockerfile/capturas/captura%203.png)

![](https://github.com/JenniferDiez/tareaDocker/blob/71e623c28a8915e848ffd41fd10271483f898653/imagen%20con%20Dockerfile/capturas/captura%204.png)

![](https://github.com/JenniferDiez/tareaDocker/blob/71e623c28a8915e848ffd41fd10271483f898653/imagen%20con%20Dockerfile/capturas/captura%204.1.png)

4. Pantallazo donde se vea la bajada de la imagen - por parte de otra persona del grupo y la creación de un contenedor.

   ```bash
   docker login
   docker pull dockerr007/apacheimagen2:latest
   docker run -d --name contenedorDockerHub -p 80:80 dockerr007/apacheimagen2:latest
   ```

![](https://github.com/JenniferDiez/tareaDocker/blob/73c2c5ae90f7e79ed8479a8bbd7287e4dd30858d/imagen%20con%20Dockerfile/capturas/image-20220128092805456.png)

![](https://github.com/JenniferDiez/tareaDocker/blob/73c2c5ae90f7e79ed8479a8bbd7287e4dd30858d/imagen%20con%20Dockerfile/capturas/image-20220128092904328.png)


5. Pantallazo donde se ve el acceso al navegador con el sitio servido

   ```bash
   docker start -i contenedorDockerHub
   docker ps
   ```

![](https://github.com/JenniferDiez/tareaDocker/blob/73c2c5ae90f7e79ed8479a8bbd7287e4dd30858d/imagen%20con%20Dockerfile/capturas/image-20220128102800267.png)

![](https://github.com/JenniferDiez/tareaDocker/blob/7053e84e1ac187f79dd351db1d0059bd85347950/imagen%20con%20Dockerfile/capturas/Captura%20pagina.PNG)

