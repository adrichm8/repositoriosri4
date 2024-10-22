# repositoriosri4

 DOCKER NETWORK
 **Crear unha rede en docker**  
  Se emplea el comando `docker network create red4`.

 **Crear dous contenedores unidos a esa rede**  
  Se emplea el comando `docker run -d --name contenedorp4 --network red4 alpine sleep 1000` para crear el primer contenedor y el segundo contenedor `docker run -d --name contenedorp42 --network red4 alpine sleep 1000`.

 **Comprobar que os contenedores están na rede**  
  Se emplea el comando `docker network inspect red4`.

 **Comprobar que os contenedores poden verse entre eles**  
  Se emplea el comando `docker exec -it contenedorp4 ping contenedorp42`. A continuación aparecerán varios mensajes que dan información cada segundo del ping formado al haber una conexión entre os contenedores.

 **Listar os contenedores conectados á rede**  
  Se utiliza el mismo comando que en el apartado 3: `docker network inspect red4`.

 **Listar as propiedades da rede**  
  Se utiliza el mismo comando que en el apartado 3: `docker network inspect red4`.

 **Crea outra rede**  
  Se emplea el comando `docker network create red42`.

 **Lanza dous contenedores novos conectados a esa nova rede**  
  Se emplea el comando `docker run -d --name contenedorp43 --network red42 alpine sleep 1000` y el segundo contenedor `docker run -d --name contenedorp44 --network red42 alpine sleep 1000`.

 **Comproba as posibles conexións entre os 4 contenedores**  
  Se emplea el comando, por ejemplo, `docker exec -it contenedorp4 ping contenedorp43`. Da erróneo.

DOCKER COMPOSE

- **Segue os pasos da guía de iniciación de docker-compose, e explica coas túas palabras os pasos que segues e qué fan**  
  - **Paso 1: Configuración**  
    Crear un directorio para el proyecto `mkdir dockercompose`, crear el archivo con `touch app.py`.
  
  - **Paso 2: Definir servicios en un archivo compose**  
    Crear el archivo con `touch compose.yml`.
  
  - **Paso 3: Crea y ejecuta tu aplicación con compose**  
    Ejecutar los servicios con `docker compose up`, acceder a la aplicación abriendo el navegador y visitando `http://localhost:8000`, verificar imágenes locales con `docker image ls` y detener la aplicación con `docker compose down`.
  
   **Paso 4: Edición para usar compose watch**  
    
   **Paso 5: Reconstruir y ejecutar la aplicación con compose watch**  
  
   **Paso 6: Actualizar la aplicación modificando el saludo en app.py**  
  
   **Paso 7: Dividir los servicios creando infra.yaml con un touch**  
  
   **Paso 8: Experimentar con otros comandos**  
    Por ejemplo, modificando `compose.yml`, ejecutando servicios en segundo plano como `docker compose up -d`, ver los contenedores en ejecución con `docker compose ps`, etc.

**Agora que sabes algo máis de docker-compose, crea un arquivo (ou varios arquivos) de configuración que ó ser lanzados cun `docker-compose up`, resulten nunha rede docker á que estean conectados 3 contenedores, explica os parámetros do .yaml usado:**
   **version**: Indica la versión de Docker Compose que se está utilizando. La versión 3.8 es compatible con las características más recientes.
  
   **services**: Define los diferentes contenedores que componen tu aplicación. Cada servicio se ejecuta en su propio contenedor.
  
   **web**: Este servicio representa la aplicación web (Flask).
  
   **ports**: Mapea el puerto 5000 del contenedor al puerto 5000 de la máquina host. Esto permite que puedas acceder a tu aplicación en `http://localhost:5000`.
  
   **networks**: Conecta este servicio a la red `my_network`.
  
   **depends_on**: Especifica que el contenedor `web` depende de que los contenedores `db` y `cache` estén disponibles. Esto asegura que se inicien en el orden correcto, aunque no garantiza que los servicios estén listos para aceptar conexiones.
  
   **image**: Utiliza la imagen oficial de MySQL con la etiqueta 5.7.
  
   **environment**: Define variables de entorno necesarias para MySQL:
     **MYSQL_ROOT_PASSWORD**: Establece la contraseña del usuario root.
     **MYSQL_DATABASE**: Crea automáticamente una base de datos con el nombre `myd`.
  
   **cache**: Este servicio representa el servicio de caché Redis.
  
   **my_network**: Crea una red llamada `my_network` utilizando el driver bridge, que es la configuración de red predeterminada en Docker. Esto permite que los contenedores se comuniquen entre sí.

**Busca e proba 4 parámetros e configuracións diferentes que podes incluir no arquivo compose, explica qué fan. (por exemplo diferentes cousas que facer coa opción RUN):**
   **environment**: Se utiliza para definir variables de entorno dentro del contenedor.
  
   **volumes**: Se utiliza para montar un directorio de la máquina host en el contenedor. Esto es útil para compartir datos o persistir cambios realizados en el contenedor.
  
   **depends_on**: Se utiliza para definir dependencias entre servicios. Asegura que un servicio se inicie antes que otro.
  
   **restart**: Se utiliza para definir la política de reinicio de los contenedores. Puede ser útil para asegurar que un servicio esté siempre disponible.


