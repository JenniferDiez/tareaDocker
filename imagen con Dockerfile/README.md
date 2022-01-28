## Ejercicio - crea una imagen con Dockerfile

### Crear una imagen con un servidor web que sirva un sitio web

1. Pantallazo/bloque de código con el Dockerfile

`$ nano dockerfile`

    | FROM httpd:2.4
    | ADD index.html /usr/local/apache2/htdocs/ |
    | Expose 80 |

![](https://github.com/JenniferDiez/tareaDocker/blob/7ecc66e3ec2e8ea6bb71ee04bdd5b007be3ab6b4/imagen%20con%20Dockerfile/Capturas/ejem1.PNG)

![](https://github.com/JenniferDiez/tareaDocker/blob/7ecc66e3ec2e8ea6bb71ee04bdd5b007be3ab6b4/imagen%20con%20Dockerfile/Capturas/ejem1.1.PNG)

2. Pantallazo donde se vea el comando que crea la nueva imagen.

`$ docker build -t dockerr007/apacheimagen:latest .`

`$ docker run --name ejemplo -d -p 80:80 dockerr007/apacheimagen:latest`

`$ docker ps`

![](https://github.com/JenniferDiez/tareaDocker/blob/7ecc66e3ec2e8ea6bb71ee04bdd5b007be3ab6b4/imagen%20con%20Dockerfile/Capturas/Captura2%20final.PNG)

![](https://github.com/JenniferDiez/tareaDocker/blob/95ad31ed6b0f9293c90c7b024214745a1a087821/imagen%20con%20Dockerfile/Capturas/captura%203.PNG)

![](https://github.com/JenniferDiez/tareaDocker/blob/95ad31ed6b0f9293c90c7b024214745a1a087821/imagen%20con%20Dockerfile/Capturas/docker%203.1.PNG)

3. Pantallazo donde se vea la imagen subida a tu cuenta de Docker Hub.

`$ docker login`

`$ docker push dockerr007/apacheimagen:latest`

![](https://github.com/JenniferDiez/tareaDocker/blob/95ad31ed6b0f9293c90c7b024214745a1a087821/imagen%20con%20Dockerfile/Capturas/Captura4.PNG)

![](https://github.com/JenniferDiez/tareaDocker/blob/70247a2f8e49c3f267f07884f1dc02fdc8fd23b2/imagen%20con%20Dockerfile/Capturas/captura%205.PNG)

![](https://github.com/JenniferDiez/tareaDocker/blob/7ecc66e3ec2e8ea6bb71ee04bdd5b007be3ab6b4/imagen%20con%20Dockerfile/Capturas/dockerhub.PNG)

4. Pantallazo donde se vea la bajada de la imagen - por parte de otra persona del grupo
- y la creación de un contenedor.



5. Pantallazo donde se ve el acceso al navegador con el sitio servido
