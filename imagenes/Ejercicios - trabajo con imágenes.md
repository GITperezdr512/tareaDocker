---
title: Ejercicios docker
author: Daniel Pérez Rodríguez
---



# Ejercicios Docker

> [TOC]
>
> Realizada por Daniel Pérez

## Servidor web

Primero hay que conseguir la imagen requerida: `php:7.4-apache`:

```bash
docker pull php:7.4-apache
```

Una vez lista crearemos el contenedor que correrá esta imagen:

```bash
sudo docker run -d --name web -p 8000:80 php:7.4-apache
```

Accedemos dinámicamente a Apache para colocar el archivo `index.html` y editarlo (una vez iniciamos la consola nos coloca en la carp /var/www/html)

```bash
docker exec -it web bash 
apt-get update
apt-get install nano
nano index.html
```

Tras esto ingresamos en el navegador `localhost:8000/index.html`:

![Screenshot_6](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_6.png)

Pasamos a crear el script PHP que mostrará el mes actual. Es el siguiente:

```php+HTML
<html>
        <head>
        </head>
        <body>
                <p>Este es el mes actual:
                <?php echo strftime("%B"); ?>
                </p>
        </body>
</html>
```

![Screenshot_11](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_11-16427475550091.jpg)

Después de añadir estos archivos se puede notar un aumento en el tamaño del contenedor:

```bash
docker ps -a -s
```

![Screenshot_12](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_12-16427475890082.jpg)

Para finalizar esta primera parte borramos el contenedor:

```bash
docker stop 8b
docker rm 8b
```



## Servidor de base de datos

Para esta segunda parte hay que descargar una imagen de `mariadb`

```bash
docker pull mariadb
```

Ahora tenemos que crear la base de datos:

``` bash
docker run --name bbdd -e MARIADB_ROOT_PASSWORD=root -e MARIADB_DATABASE=prueba -e MARIADB_USER=invitado -e MARIADB_PASSWORD=invitado -p 3336:3306 -d mariadb
```

Para hacer las pruebas es necesario crear el contenedor de phpMyAdmin añadiendo el 'flag' `--link`:

```bash
pull phpmyadmin
docker run --name myadmin -d -e PMA_ARBITRARY=1--link bbdd:mariadb -p 8080:80 phpmyadmin
```

Se usa la variable PMA_ARBITRARY=1 para poder indicar el servidor al que se conectará.

Tras esto nos introducimos en phpMyAdmin con nuestro usuario invitado:

![Screenshot_9](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_9.png)

![Screenshot_10](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_10.png)

En la segunda imagen se puede apreciar como se ha creado correctamente la base de datos `prueba` (no ha hecho falta usar el comando `mysql show databases`).

Como última tarea vemos la imposibilidad de borrar la imagen `mariadb` mientras está en ejecución:

```bash
docker rmi mariadb
```

![Screenshot_11](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_11.png)

