Alex Gasch Blasco
# Instalación de Apache en el equipo
Durane está actividad realizaremos la instalación del servicio Apache en nuestro ordenador. Además, ajustaremos nuestro **firewall** para permitir el acceso externo al servidor; comprobar el **estado del servidor** tras su instalación; **administrar el proceso de Apache** una vez este completamente configurado y, para finalizar, se definira como configurar un host virtual (esto último es recomendable)

## Instalar Apache
En este apartado se definirán los pasos a seguir para instalar **Apache**.Abre una ventana de terminal desplegando el botón de menú de Ubuntu ( o con la combinación de teclas **Ctrl + ALT + T** ).

Ejecuta el siguiente comando para actualizar el listado de paquetes:
```
sudo apt update
```
Escribe y ejecuta el siguiente comando para instalar Apache:
```
sudo apt install apache2
```

## Ajustar Firewall
En este apartado se definirán los pasos a seguir configurar el firewall de nuestro ordenador y permitir a Apache trabajar correctamente.

Con la misma ventana de terminal, escribe y ejecuta el siguiente comando para enumerar los perfiles de aplicación ufw (no es nada extra, deberias tenerla si has seguido los pasos anteriores).
```
sudo ufw app list
```
>Por pantalla debería salirte algo como esto:
```
Aplicaciones disponibles:
  Apache
  Apache Full
  Apache Secure
  CUPS
```
Habilita el trafico del **puerto 80**, para ello, ejecuta el comando:
```
sudo ufw allow 'Apache'
```
>Puedes verificar que lo has hecho correctamente, escribiendo esto en tu ventana de terminal:
>```
>sudo ufw status
>```

>Esto es lo que aparecerá al ejecutarse correctamente:
>```
>Status: active
>
>To                         Action      From
>--                         ------      ----
>OpenSSH                    ALLOW       Anywhere                  
>Apache                     ALLOW       Anywhere                
>OpenSSH (v6)               ALLOW       Anywhere (v6)             
>Apache (v6)                ALLOW       Anywhere (v6)
>```

## Comprobar su servidor web
En este apartado, se realizarán las comprobaciones para confirmar que Apache se ha instalado y todo funciona correctamente.

Tras toda la instalación del servicio, inicialo con el comando:
```
sudo systemctl status apache2
```
Comprueba el estado de tu servidor ejecutando el comando:
```
sudo systemctl status apache2
```

>Te mostrará lo siguiente por pantalla:
>```
>● apache2.service - The Apache HTTP Server
>     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
>     Active: active (running) since Wed 2022-11-09 01:14:08 CET; 3s ago
>       Docs: https://httpd.apache.org/docs/2.4/
>    Process: 14934 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
>   Main PID: 14938 (apache2)
>      Tasks: 55 (limit: 9390)
>     Memory: 5.0M
>     CGroup: /system.slice/apache2.service
>             ├─14938 /usr/sbin/apache2 -k start
>             ├─14939 /usr/sbin/apache2 -k start
>             └─14940 /usr/sbin/apache2 -k start
>```

>> Otra manera de comprobar que Apache se ha instalado y encendido correctamente es visitando la página web de tu servidor. Para ello tendrás que escribir la **IP** de tu servidor en el navegador. Si no la conoces, puedes averiguarla con el comando:
>>```
>>hostname -I
>>```

## Administrar el proceso de Apache
En este apartado, se pretende dejar en claro algunos comandos de administración básicos con *systemctl*.
  * Para detener su servidor web:
```
sudo systemctl stop apache2
```
  * Para iniciar el servidor web cuando no esté activo:
```
sudo systemctl start apache2
```
  * Para detener y luego iniciar el servicio de nuevo:
```
sudo systemctl restart apache2
```
  * Si solo realiza cambios de configuración, Apache a menudo puede recargarse sin cerrar conexiones:
```
sudo systemctl reload apache2
```
  * Para que Apache no se inicie automaticamente cuando arranque el servidor:
```
sudo systemctl disable apache2
```
  * Para que Apache se inicie automaticamente cuando arranque el servidor:
```
sudo systemctl enable apache2
```

## Configurar un host virtual
En este apartado se explica como configurar un dominio.

Crea un directorio para tu dominio con el siguiente comando:
```
sudo mkdir /var/www/daw22_23
```
Asigna la propiedad del directorio con la variable de entorno _$USER_:
```
sudo chown -R $USER:$USER /var/www/daw22_23
```
Los permisos de los roots web deberían ser correctos si no modificó el valor umask, que establece permisos de archivos predeterminados. Para asegurarse que sus permisos sean correcto y permitir al propietario leer, escribir y ejecutar los archivos, y a la vez conceder solo permisos de lectura y ejecución a los grupos y terceros, puede ingresar el siguiente comando:
```
sudo chmod -R 755 /var/www/daw22_23
```
Crea una pagina de ejemplo (_index.html_) utilizando nano.
```
sudo nano /var/www/daw22_23/index.html
```
>Dentro del archivo escribe las siguientes lineas y después, guarda y cierra el archivo:
>```
><html>
>	<head>
>		<title>Welcome to daw22_23</title>
>	</head>
>	<body>
>		<h1>Todo correcto! Por la gloria del emperador, has accedido a daw22_23</h1>
>	</body>
></html>
>```

Para que apache pueda acceder a este archivo, hay que modificar el documento que contiene la configuración. Pero, para que no hayan problemas, crea uno nuevo:
```
sudo nano /etc/apache2/sites-available/daw22_23.conf
```
>Dentro del documeto escribe las siguientes líneas y después, guarda y cierra el archivo::
>```
><VirtualHost *:80>
>        ServerAdmin gaschblascoalex@gmail.com
>        ServerName daw22_23
>        ServerAlias www.daw22_23
>        DocumentRoot /var/www/daw22_23
>        ErrorLog ${APACHE_LOG_DIR}/error.log
>        CustomLog ${APACHE_LOG_DIR}/acces.log combined
></VirtualHost>
>```

Habilita el archivo con la herramienta **a2ensite**:
```
sudo a2ensite daw22_23.conf
```
Deshabilita el sitio predeterminado definido en **000-default.conf**:
```
sudo a2dissite 000-default.conf
```
>Para comprobar que no haya errores de configuración, ejecuta el siguiente comando:
>```
>sudo apache2ctl configtest
>```

