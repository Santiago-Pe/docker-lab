# docker-lab
Exercises of Docker


## Guia
version: '3.1'

services:

  wordpress:
    image: wordpress:php7.2-apache
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: mysql
      WORDPRESS_DB_USER: root
      WORDPRESS_DB_PASSWORD: root
      WORDPRESS_DB_NAME: wordpress
    links:
      - mysql:mysql


  mysql:
    image: mysql:8.0.13
    command: --default-authentication-plugin=mysql_native_password
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_ROOT_PASSWORD: root
    volumes:
      - ~/docker/mysql-data:/var/lib/mysql 


## Wordpress account
#### user
dockerLab
#### pasword
dockerLab2020