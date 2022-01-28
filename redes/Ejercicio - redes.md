<h1>Ejercicio - redes</h1>

Lo  primero es crear una red bridge que tenga de nombre `redbd` para que se puedan conectar a ella los contenedores correspondientes:

```
docker network create redbd
```

Tenemos descargado la imagen MariaDB así que solo crearemos el contenedor:

```
docker run --name bbddredes --network redbd -v /home/docker/datadir:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=root -p 3306:3306 -d mariadb
```

Tras crear el contenedor de base de datos ahora hay que usar el de Adminer para que se conecte a la base de datos:

```
docker run --name adminer --network redbd --link bbddredes:mariadb -p 8080:8080 -d adminer
```

Comprobamos que los contenedores están corriendo:

![Screenshot_12](Ejercicio%20-%20redes.assets/Screenshot_12.png)

Accedemos a Adminer desde `localhost:8080`:

![Screenshot_13](Ejercicio%20-%20redes.assets/Screenshot_13.png)

Procedemos a crear una base de datos mediante Adminer:

![Screenshot_13](Ejercicio%20-%20redes.assets/Screenshot_14.png)

Para comprobar que se ha creado accedemos desde consola usando el siguiente comando para acceder al contenedor interactivamente con la consola bash y el de después para ver la efectiva creación de la base de datos `prueba`:

```bash
docker exec -itm bbddredes bash
```

```mariadb
show databases;
```

![](Ejercicio%20-%20redes.assets/Screenshot_16.png)

Para terminar borramos los contenedores y los volúmenes:

```
docker rm bbddred
docker rm adminer
docker volume ls
docker volume prune
```

![Screenshot_17](Ejercicio%20-%20redes.assets/Screenshot_19.png)

![Screenshot_20](Ejercicio%20-%20redes.assets/Screenshot_20.png)

Con `docker volume prune` borramos todos los volúmenes que no están siendo usados (como habíamos creado otros anteriores al crear contenedores y posteriormente borrarlos, el `brune` también los ha eliminado). 
