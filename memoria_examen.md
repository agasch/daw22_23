Alex Gasch Blasco
# Examen
Para no repetirme, desde este punto digo que lo hago todo en una misma ventana de terminal, así que no repetire en cada apartado "Abro una ventana de terminal".
##  Apartado 2
Abro una ventana de terminal y ejecuto el siguiente comando:
```
sudo ssh usuario@192.168.0.168
```
Al ejecutarlo, me sale la siguiente lineas (es lo más normal porque es la primera vez que intento conectarme a ese ordenador):
```
The authenticity of host '192.168.0.168 (192.168.0.168)' can't be established.
ECDSA key fingerprint is SHA256:iWkyi99XmZvsg5KHNJYRhUmMeitc3CltsPGZtX88Pfw.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
Escribo **yes** y procedo a escribir la contraseña del usuario.
```
usuario@192.168.0.168's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.13.0-30-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

Se pueden aplicar 172 actualizaciones de forma inmediata.
101 de estas son actualizaciones de seguridad estándares.
Para ver estas actualizaciones adicionales ejecute: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update
New release '22.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


2 updates could not be installed automatically. For more details,
see /var/log/unattended-upgrades/unattended-upgrades.log
Your Hardware Enablement Stack (HWE) is supported until April 2025.
Last login: Fri Nov 18 15:54:32 2022 from 192.168.0.136
usuario@usuario-OptiPlex-380:~$               //ya estoy dentro del otro equipo con el usuario de esta
```
Accedo al directorio _/var/www/_
```
cd /var/www/
```
Ahora creo un directorio con mi nombre con el comando:
```
mkdir alex_gasch
```
Me da error porque "no tengo permisos" así que ejecuto el siguiente comando:
```
sudo mkdir alex_gasch
```
Como ahora sí que he podido, procedo a acceder a él.
```
cd alex_gasch/
```
Para crear un archivo en el directorio, ejecuto el comando:
```
sudo nano ejercicio2.txt
```
En la ventana de edición del archivo escribo: "Conseguido". Utilizo el juego de teclas Ctrl+o (para guardar las modificaciones), y Ctrl+x (para salir del archivo).

## Apartado 3
Para descargar la imagen en remoto, he consultado un par de paginas web (que dejo el enlace a ellas en este documento). Para poder realizarlo, se usa el siguiente comando:
```
sudo curl -o daw.png https://iesalandalus.org/ciclos/semipresencial/daw-sp/daw.png
```
>Lo que se verá por pantalla será lo siguiente:
>```
>  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
>                                 Dload  Upload   Total   Spent    Left  Speed
>100   707  100   707    0     0   5795      0 --:--:-- --:--:-- --:--:--  5795
>curl: (6) Could not resolve host: ciclos
>```

### Resultado de los apartados 2 y 3
![image](https://user-images.githubusercontent.com/113713815/202740502-95fa498d-2e2c-418e-9e40-2c1f91cedc62.png)

## Apartado 4
Primero que nada, cierro sesión en el ssh con el comando:
```
 exit
```
>Lo que se ve por pantalla:
>```
>cerrar sesión
>Connection to 192.168.0.168 closed.
>```
Crea un directorio para tu dominio con el siguiente comando:
```
sudo mkdir /var/www/examen_agasch
```
Asigno la propiedad del directorio con la variable de entorno $USER:
```
sudo chown -R $USER:$USER /var/www/examen_agasch
```
Le doy permisos:
```
sudo chmod -R 755 /var/www/examen_agasch
```
Ahora, creo la página index.html utilizando nano.
```
sudo nano /var/www/examen_agasch/index.html
```
>Dentro del documento escribo los siguiente:
>```
>html>
>  <head></head>
>  <body>
>        <h1>ALEX GASCH BLASCO</h1>
>  </body>
></html>
>```

Para que apache pueda acceder a este archivo, copio el contenido del archivo de configuracion de apache por defecto a uno nuevo:
```
cd /etc/apache2/sites-available/
sudo cp 000-default.conf examen_agasch.conf
```
Ahora, accedo a el para editarlo y modificar unas líneas:
```
sudo nano examen_agasch.conf
```
>Edito las lineas:
>```
>DocumentRoot /var/www/examen_agasch       //en la que escribo el nombre del direcctorio que he creado en el paso anterior.
>ServerName daw.ejercicio4.com            //escribe la url que quiero para el dominio
>```

