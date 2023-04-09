# docker-lab
Exercises of Docker


## Guia
Para levantar un sitio de WordPress localmente usando Docker Compose, sigue estos pasos:

Crea un directorio para tu proyecto y dentro de él, crea un archivo docker-compose.yml.

Dentro del archivo docker-compose.yml, escribe el siguiente código:

yaml
Copy code
version: '3.9'

services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress

  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
volumes:
  db_data: {}
Guarda el archivo y cierra el editor de texto.

Abre la línea de comandos y navega hasta el directorio donde está el archivo docker-compose.yml.

Ejecuta el siguiente comando para levantar los servicios:

Copy code
docker-compose up -d
Una vez que todos los servicios estén en ejecución, abre un navegador web y visita http://localhost:8000. Deberías ver la página de instalación de WordPress.

Sigue las instrucciones en pantalla para configurar tu sitio de WordPress.

¡Eso es todo! Ahora tienes un sitio de WordPress en ejecución localmente usando Docker Compose.