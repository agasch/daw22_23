# Instalación de Joomla
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
>
