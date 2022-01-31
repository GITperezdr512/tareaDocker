---
title: Ejercicios Docker
author: Aitor Merino Vázquez, Claudia Trabanco Conde
---

# Ejercicios Docker

> [TOC]
>
> Realizada por Aitor Merino Vázquez y Claudia Trabanco Conde

## Ejercicio Dockerfile

1. Contenido del Dockerfile y creación de la imagen

```bash
docker build -t servidor_apache2 .
```

![MicrosoftTeams-image](Ejercicio%20Dockerfile.assets/MicrosoftTeams-image.png)

2. Imagen subida a Dockerhub

```bash
docker tag serverclau:latest clauclase/dockerhub:latest
docker push clauclase/dockerhub:latest
```

![MicrosoftTeams-image(1)](Ejercicio%20Dockerfile.assets/MicrosoftTeams-image(1).png)

3. Bajada de imagen y creación de contenedor

```bash
docker pull clauclase/dockerhub:latest
docker images
```

![docker_pull](Ejercicio%20Dockerfile.assets/docker_pull-16436192178352.png)

```bash
docker run --name servermerino -d -p 80:80 clauclase/dockerhub:latest
docker ps -a
```

![docker_run_servermerino](Ejercicio%20Dockerfile.assets/docker_run_servermerino-16436191379241.png)

4. Acceso al sitio web

![docker_servermerino](Ejercicio%20Dockerfile.assets/docker_servermerino.png)
