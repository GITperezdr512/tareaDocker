<h1>Ejercicio - trabajo con imágenes</h1>



<h2>Servidor web</h2>

Primero hay que conseguir la imagen requerida: `php:7.4-apache`:

```linux
docker pull php:7.4-apache
```

Una vez lista crearemos el contenedor que correrá esta imagen:

```
sudo docker run -d --name web -p 8000:80 php:7.4-apache
```

Accedemos dinámicamente a Apache para colocar el archivo `index.html` y editarlo (una vez iniciamos la consola nos coloca en la caprte /var/www/html)

```
docker exec -it web bash 
apt-get update
apt-get install nano
nano index.html
```

Tras esto ingresamos en el navegador `localhost:8000/index.html`:

![Screenshot_6](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_6.png)

Pasamos a crear el script PHP que mostrará el mes actual. Es el siguiente:

```
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

```
docker ps -a -s
```

![Screenshot_12](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_12-16427475890082.jpg)

Para finalizar esta primera parte borramos el contenedor:

```
docker stop 8b
docker rm 8b
```



<h2>Servidor de base de datos</h2>

Para esta segunda parte hay que descargar una imagen de `mariadb`

```
docker run --name bbdd -e MARIADB_ROOT_PASSWORD=root -e MARIADB_DATABASE=prueba -e MARIADB_USER=invitado -e MARIADB_PASSWORD=invitado -p 3336:3306 -d mariadb
```

Ahora tenemos que crear la base de datos:

``` 

```

