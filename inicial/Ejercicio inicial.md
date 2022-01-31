---
title: Ejercicios Docker
author: Aitor Merino Vázquez, Claudia Trabanco Conde
---

# Ejercicios Docker

> [TOC]
>
> Realizada por Aitor Merino Vázquez y Claudia Trabanco Conde

## Ejercicio inicial

1. Creación y comprobación de funcionamiento del contenedor Nginx

```bash
docker run -d --name servidor_web -p 8181:80 nginx
docker ps -a
```

![MicrosoftTeams-image](Ejercicio%20inicial.assets/MicrosoftTeams-image.png)

![MicrosoftTeams-image(1)](Ejercicio%20inicial.assets/MicrosoftTeams-image(1).png)

2. Acceso al servidor web

![MicrosoftTeams-image(2)](Ejercicio%20inicial.assets/MicrosoftTeams-image(2).png)

3. Imágenes del servicio local

```bash
docker images
```

![MicrosoftTeams-image(3)](Ejercicio%20inicial.assets/MicrosoftTeams-image(3).png)

4. Eliminación del contenedor

```bash
docker stop servidor_web
docker rm servidor_web
```

![MicrosoftTeams-image(4)](Ejercicio%20inicial.assets/MicrosoftTeams-image(4).png)
