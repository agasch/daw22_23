Alex Gasch y Sergio Azogue
# Practica de SSH
**SSH** es una herramienta esencial para ser un administrador de sistemas experto. SSH, o *Secure Shell*, es un protocolo que se utiliza para iniciar sesión de forma segura en sistemas remotos. Es la forma más común de acceder a servidores Linux remotos. En esta guía, analizaremos cómo usar SSH para 
conectarse a un sistema remoto.

>Requisitos necesarios: antes de meternos en materia, tendrás que haber completado con exito el resto de las actividades anteriores para completar esta (por lo menos hasta la actividad  **_Apache: Configuración_**)
 
## Parte del servidor
Lo único que debes hacer si estás realizando la parte del servidor, es crear un usuario con el siguiente comando:
```
adduser NOMBRE_DE_USUARIO
```
Esto es lo que te aparecerá por pantalla:
```
Changing the user information for agasch
Enter the new value, or press ENTER for the default
        Full Name [ ]:         //campo opcional
        Room Number [ ]:       //campo opcional
        Work Phone [ ]:        //campo opcional
        Home Phone [ ]:        //campo opcional
        Other [ ]:             //campo opcional
Is the information correct? [Y/n]   //si toda la información (rellenada o no) es correcta, pulsa Y
```
>Si no hiciste la instalación y configuración de **Apache**, deberás realizarla y luego seguir con esta practica.

## Parte del cliente
En este apartado se te indicarán los pasos a seguir para que desde el cliente, puedas conectarte al servidor **ssh**, instalar **apache** en el servidor, pasar una web a un lugar del servidor, crear un virtualhost, modificar los host del local para para que con la dirección elegida vaya a la ip del servidor, comprobar que te te puedes conectar a la pagina y a abrir un browser en el buscador.

Pero empecemos por el principio, instala el servicio **ssh** con el siguiente comando:
```
sudo apt install ssh client
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
>Si el servidor ya tenia instalado apache por las actividades anteriores, deberás desinstalarlo mediante el siguiente comando:
```
sudo apt remove apache2 
```
Para instalar en el servidor el servicio **Apache**, debes ejecutar el siguiente comando:
```
sudo apt install apache2
```


