# Instalación de Joomla
## Comandos en terminal
En mi caso, instalaremos _Joomla_ en **Docker**, para ello, lo primero que hago es actualizar los repositorios de mi equipo **Ubuntu mate 20.04**:
```
sudo apt-get update
```
Finalizado el proceso de actualización, instalo el paquete **docker.io**:
```
sudo apt install docker.io
```
Ahora hay que creo una red Docker:
```
docker network create joomla-network
```
Desde el repositorio en línea, descargo la imagen de MySQL.
```
sudo docker pull mysql:5.7
```
Hago lo mismo con la imagen de joomla.
```
sudo docker pull joomla
```
Creo un volumen acoplable para almacenar los datos persistentes de MySQL
```
docker volume create mysql-data
```
>Para comprobar el directorio de datos persistentes, ejecuto el sigiente comando:
>```
>docker volume inspect mysql-data
>```
>Este debería ser el resultado que te sale si tu también lo haces:
>```
>[
>    {
>        "CreatedAt": "2020-09-21T01:38:07Z",
>        "Driver": "local",
>        "Labels": {},
>        "Mountpoint": "/var/lib/docker/volumes/mysql-data/_data",
>        "Name": "mysql-data",
>        "Options": {},
>        "Scope": "local"
>    }
>]
>```
Inicie un contenedor MySQL con almacenamiento de datos persistente.
```
docker run -d --name joomladb  -v mysql-data:/var/lib/mysql --network joomla-network -e "MYSQL_ROOT_PASSWORD=kamisama123" -e MYSQL_USER=joomla -e "MYSQL_PASSWORD=kamisama123" -e "MYSQL_DATABASE=joomla" mysql:5.7
```
Creo un volumen acoplable para almacenar los datos persistentes de Joomla.
```
docker volume create joomla-data
```
>Para comprobar el directorio de datos persistentes, ejecuto el sigiente comando:
>```
>docker volume inspect joomla-data
>```
>Este debería ser el resultado que te sale si tu también lo haces:
>```
>[
>    {
>        "CreatedAt": "2020-09-21T01:52:06Z",
>        "Driver": "local",
>        "Labels": {},
>        "Mountpoint": "/var/lib/docker/volumes/joomla-data/_data",
>        "Name": "joomla-data",
>        "Options": {},
>        "Scope": "local"
>    }
>]
>```

Inicie un contenedor de Joomla con almacenamiento de datos persistente.
```
docker run -d --name joomla -p 80:80 -v joomla-data:/var/www/html --network joomla-network -e JOOMLA_DB_HOST=joomladb -e JOOMLA_DB_USER=joomla -e JOOMLA_DB_PASSWORD=kamisama123 joomla
```
## Instalación de Joomla
