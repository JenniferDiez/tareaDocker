## 2. Ejercicio - Trabajo con imágenes

### 2. 2. Servidor de base de datos

1. Arrancar un contenedor que se llame `bbdd` y que ejecute una instancia de la imagen **mariadb** para que sea accesible desde el puerto 3306. Establecer variables de entorno.

   
   
   ​	Lanzamos el comando en primer plano para poder leer los posibles mensajes de error que puedan surgir mientras trabajamos desde otra consola. 
   
   ```bash
   sudo docker run --name bbdd 
   --env MARIADB_ROOT_PASSWORD=root 
   --env MARIADB_DATABASE=prueba 
   --env MARIADB_USER=invitado
   --env MARIADB_PASSWORD=invitado
   mariadb --port 3306
   ```
   
   ![image-20220127202815509](Servidor%20de%20base%20de%20datos.assets/image-20220127202815509.png)
   
   
   
 2. Pantallazo de la conexión al servidor de base de datos con el usuario creado y de la base de datos `prueba` creada automáticamente.

    

       ​	Una vez creado el contenedor, en el cliente de MySQL Workbench nos encontramos con un mensaje de error al intentar realizar la conexión:

   ![image-20220127211130604](Servidor%20de%20base%20de%20datos.assets/image-20220127211130604.png)

   

   Para solventarlo, debemos ingresar el siguiente comando:

   ```bash
   sudo snap connect mysql-workbench-community:password-manager-service
   ```

![image-20220127212604170](Servidor%20de%20base%20de%20datos.assets/image-20220127212604170.png)

Y comprobamos que podemos acceder a la base de datos y que nuestro esquema `prueba` está creado:

   ![image-20220127211413032](Servidor%20de%20base%20de%20datos.assets/image-20220127211413032.png)

   ![image-20220127211623143](Servidor%20de%20base%20de%20datos.assets/image-20220127211623143.png)



3. Pantallazo donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado.

```bash
sudo docker rmi mariadb
```

![image-20220127212140726](Servidor%20de%20base%20de%20datos.assets/image-20220127212140726.png)

