Alex Gasch y Sergio Azogue
# Practica de SSH
**SSH** es una herramienta esencial para ser un administrador de sistemas experto. SSH, o *Secure Shell*, es un protocolo que se utiliza para iniciar sesión de forma segura en sistemas remotos. Es la forma más común de acceder a servidores Linux remotos. En esta guía, analizaremos cómo usar SSH para 
conectarse a un sistema remoto.

>Requisitos necesarios: antes de meternos en materia, tendrás que haber completado con exito el resto de las actividades anteriores para completar esta (por lo menos hasta la actividad  **_Apache: Configuración_**)
 
## Parte del servidor
### Crear nuevo usuario
Para crear un usuario en tu equipo, ejecuta el siguiente comando:
```
adduser NOMBRE_DE_USUARIO
```
>Esto es lo que te aparecerá por pantalla:
>```
>Changing the user information for agasch
>Enter the new value, or press ENTER for the default
>        Full Name [ ]:         //campo opcional
>        Room Number [ ]:       //campo opcional
>        Work Phone [ ]:        //campo opcional
>        Home Phone [ ]:        //campo opcional
>        Other [ ]:             //campo opcional
>Is the information correct? [Y/n]   //si toda la información (rellenada o no) es correcta, pulsa Y
>```

>>Si no hiciste la instalación y configuración de **Apache**, deberás realizarla y luego seguir con esta practica.

### Buscar la IP del ordenador
Para averiguar cual es la ip de tu ordenador, escribe y ejecuta el siguiente comando:
```
ip a
```

## Parte del cliente
En este apartado se te indicarán los pasos a seguir para que desde el cliente, puedas conectarte al servidor **ssh**, instalar **apache** en el servidor, pasar una web a un lugar del servidor, crear un virtualhost, modificar los host del local para para que con la dirección elegida vaya a la ip del servidor, comprobar que te te puedes conectar a la pagina y a abrir un browser en el buscador.

Pero empecemos por el principio, instala el servicio **ssh** con el siguiente comando:
```
sudo apt install ssh
```
### Conectarse al servidor mediante ssh
Para establecer una conexion el servidor, ejecuta el siguiente comando:
```
ssh nombre_usuario@ip_servidor
```
>En este caso, lo que se veria por pantalla sería:
>ssh agasch@192.168.0.136

>**Como curiosidad, si ejecutamos el comando _whoami_, nos aparecerá el nombre del usuario con el que estamos conectados**.

### Instalar Apache en el servidor 
Para instalar **Apache** en el servidor, esigue los pasos descritos en [este documento](https://github.com/agasch/daw22_23/blob/master/Apache_Introduccion.md).
### Crear un virtualhost
Para crear un virtualhost, sigue los pasos indicados el [este documento](https://github.com/agasch/daw22_23/blob/master/Apache_Configuracion.md).
### Modificar los host locales para que con la dirección elegida vaya a la ip del servidor
Cierra la sesión ssh.
```
exit
```
Accede al archivo _hosts_
```
sudo nano /etc/hosts
```
>Agrega al final del archivo la direccion **IP del servidor** y el **ServerName** elegido:
>```
>127.0.0.1       localhost
>127.0.1.1       daw
>
># The following lines are desirable for IPv6 capable hosts
>::1     ip6-localhost ip6-loopback
>fe00::0 ip6-localnet
>ff00::0 ip6-mcastprefix
>ff02::1 ip6-allnodes
>ff02::2 ip6-allrouters
>192.168.0.136 holabuenastardes.com  //IP_server y ServerName
>```

Si lo has hecho todo bien, al abrir un navegador y buscar el Servername, te aparecerá la misma página
