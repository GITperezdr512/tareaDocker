<h1>Ejercicio - trabajo con imágenes</h1>

<h2>Servidor web</h2>

Primero hay que conseguir la imagen requerida: `php:7.4-apache`:

```linux
docker pull php:7.4-apache
```

Una vez lista crearemos el contenedor que correrá esta imagen:

```
sudo docker run -d --name web -p 8080:80 php:7.4-apache
```

Accedemos dinámicamente a Apache para colocar el archivo `index.html` y editarlo (una vez iniciamos la consola nos coloca en la caprte /var/www/html)

```
docker exec -it web bash 
sudo apt-get update
touch index.html
apt-get install nano
nano index.html
```

Tras esto ingresamos en el navegador `localhost:8000/index.html`:

![Screenshot_6](Ejercicios%20-%20trabajo%20con%20im%C3%A1genes.assets/Screenshot_6.png)

