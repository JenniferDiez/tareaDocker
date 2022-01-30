## 5. Ejercicio - Crear una imagen con Dockerfile

4. Pantallazo donde se vea la bajada de la imagen y la creación de un contenedor.

   ```bash
   docker login
   docker pull dockerr007/apacheimagen2:latest
   docker run -d --name contenedorDockerHub -p 80:80 dockerr007/apacheimagen2:latest
   ```

   ![image-20220128102523618](Ejercicio%20-%20Crear%20una%20imagen%20con%20Dockerfile.assets/image-20220128102523618.png)

5. Pantallazo donde se vea el acceso al navegador con el sitio servido.

   ```bash
   docker start -i contenedorDockerHub
   docker ps
   ```

   ![image-20220128102800267](Ejercicio%20-%20Crear%20una%20imagen%20con%20Dockerfile.assets/image-20220128102800267.png)

   