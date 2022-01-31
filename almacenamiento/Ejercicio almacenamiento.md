---
title: Ejercicios Docker
author: Aitor Merino Vázquez, Claudia Trabanco Conde
---

# Ejercicios Docker

> [TOC]
>
> Realizada por Aitor Merino Vázquez y Claudia Trabanco Conde

## Ejercicio almacenamiento

1. Creación de fichero index.html con texto dentro de directorio saludo y arranque de contenedores 1 y 2

```bash
cd saludo
echo <h1>HOLA SOY CLAUDIA</h1> > index.html
cat index.html
```

![MicrosoftTeams-image](Ejercicio%20almacenamiento.assets/MicrosoftTeams-image.png)

```bash
docker run -d --name c1 -v /home/claudia/saludo:/var/www/html -p 8181:80 php:7.4-apache
docker run -d --name c2 -v /home/claudia/saludo:/var/www/html -p 8282:80 php:7.4-apache
```

![MicrosoftTeams-image(2)](Ejercicio%20almacenamiento.assets/MicrosoftTeams-image(2).png)

2. Ver contenido de index.html del contenedor 1 y 2

```bash
docker ps
curl http://localhost:8181
curl http://localhost:8282
```

![MicrosoftTeams-image(3)](Ejercicio%20almacenamiento.assets/MicrosoftTeams-image(3).png)

3. Ver el acceso a index.html después de modificarlo

```bash
nano saludo/index.html
curl http://localhost:8181
curl http://localhost:8282
```

![MicrosoftTeams-image(4)](Ejercicio%20almacenamiento.assets/MicrosoftTeams-image(4).png)

4. Borrar los contenedores y mostrarlo

```bash
docker rm -f c1
docker rm -f c2
docker ps -a
```

![MicrosoftTeams-image(5)](Ejercicio%20almacenamiento.assets/MicrosoftTeams-image(5).png)
