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
sudo docker run -d --name servidor_web -p 8181:80 nginx
sudo docker ps -a
```

![MicrosoftTeams-image](../../../../../../Downloads/MicrosoftTeams-image.png)

![MicrosoftTeams-image(1)](../../../../../../Downloads/MicrosoftTeams-image(1).png)

2. Acceso al servidor web

![MicrosoftTeams-image(2)](../../../../../../Downloads/MicrosoftTeams-image(2).png)

3. Imágenes del servicio local

```bash
sudo docker images
```

![MicrosoftTeams-image(3)](../../../../../../Downloads/MicrosoftTeams-image(3).png)

4. Eliminación del contenedor

```bash
sudo docker stop servidor_web
sudo docker rm servidor_web
```

![MicrosoftTeams-image(4)](../../../../../../Downloads/MicrosoftTeams-image(4).png)
