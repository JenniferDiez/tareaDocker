---
author: Celia Corrales García
title: Ejercicios Docker - entregables
---

# Ejercicios Docker - entregables

> Trabajo realizado por Celia Corrales García



## Ejercicio - trabajo con imágenes

### Servidor web

1. Arrancar un contenedor que ejecute la imagen php:7.4-apache, llamado web, por el puerto 8000.

   ````bash
   docker run -d --name web -p 8000 php:7.4-apache
   ````
   
   ![image-20220114091054798](Ejercicios-Docker--ServidorWeb.assets/image-20220114091054798.png)



2. Colocar en el directorio raíz del contenedor un archivo index.html que contenga 'HOLA SOY XXXXX' (nombre y apellidos).

   ````bash
   docker start web
   docker exec -it web bash
   ````
   
   
   
   ![image-20220114092417174](Ejercicios-Docker--ServidorWeb.assets/image-20220114092417174.png)
   
   

````bash
apt update
apt-get install nano
nano index.html
tail index.html
````

![image-20220114092448845](Ejercicios-Docker--ServidorWeb.assets/image-20220114092448845.png)

![image-20220114092516408](Ejercicios-Docker--ServidorWeb.assets/image-20220114092516408.png)

![image-20220114092533153](Ejercicios-Docker--ServidorWeb.assets/image-20220114092533153.png)

![image-20220114092559831](Ejercicios-Docker--ServidorWeb.assets/image-20220114092559831.png)



3. Colocar en el mismo directorio otro archivo llamado llamado mes.php que muestre el mes actual, y ver la salida del script en el navegador.

   ````bash
   tail mes.php
   ````

   

   ![image-20220114094026052](capturasServidorWeb/image-20220114094026052.png)

   
   
   4. Borrar el contenedor.
   
      ````bash
      exit stop web
      docker rm web
      ````

![image-20220128095531600](Ejercicios-Docker--ServidorWeb.assets/image-20220128095531600.png)

