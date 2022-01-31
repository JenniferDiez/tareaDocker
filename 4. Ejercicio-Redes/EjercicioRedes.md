---
author: Celia Corrales García
title: Ejercicios Docker - entregables
---

# Ejercicios Docker - entregables

> Trabajo realizado por Celia Corrales García

## Ejercicio - redes

### Despliegue de contenedores en red: Adminer y MariaDB

1. Crea una red bridge redbd

   ````bash
   docker network create redbd
   ````

   ![image-20220117100506479](image-20220117100506479.png)

   

   ````bash
   docker network inspect redbd
   ````

   

   ![image-20220117100545715](image-20220117100545715.png)

   

2. Crea un contenedor con una imagen de mariaDB dentro de la red, que se ejecutará en segundo plano y será accesible a través del puerto 3306.

   ````bash
   docker run -d --name mariadb --network -p 3306:3306 -v /my/own/datadir:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=admin mariadb
   ````

   ![image-20220128085821018](image-20220128085821018.png)

   

3. Crea un contenedor Adminer que se pueda conectar con el contenedor de la BD.

   ````bash
   docker run -d --name adminer --link mariadb:mariadb --network redbd -p 8080:8080 adminer
   docker ps -a
   ````

   ![image-20220128085902030](image-20220128085902030.png)

   ![image-20220128090043757](image-20220128090043757.png)

   

4. Comprueba que el contenedor Adminer puede conectar con el contendor mysql accediendo a la URL http://localhost:8080

![image-20220128090201791](image-20220128090201791.png)

-Pantallazo donde se vea la creación de la base de datos con la interfaz web Adminer

![image-20220128090720205](image-20220128090720205.png)



-Pantallazo  donde  se  entre  a  la  consola  del  servidor  web  en  modo  texto  y  se
compruebe que se ha creado la BD:

````bash
docker exec -it mariadb /bin/bash
````



![image-20220128092214854](image-20220128092214854.png)



-Pantallazo de borrado de los contenedores la red y los volúmenes utilizados

`````bash
docker rm -f $(docker ps -a)
docker rm -R /my/own/datadir 
`````



![image-20220128092330920](image-20220128092330920.png)

![image-20220128092722495](image-20220128092722495.png)
