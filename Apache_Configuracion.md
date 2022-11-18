Alex Gasch Blasco
# Configuración de Apache en el equipo

## Configurar los VirtualHost
Para configurar los virtualhost, empieza accediendo al directorio (sites-available):
```
cd /etc/apache2/sites-available/
```
>Como apache viene con un archivo de configuración por defecto, copialo un nuevo archivo con tu dominio como nombre para que mayor facilidad.
```
sudo cp 000-default.conf daw22_23
```
Edita el archivo
```
sudo nano daw22_23
```
Te aparecerán muchas lineas de texto, las que te interesa modificar son la del **ServerAdmin, DocumentRoot** y **ServerName**
```
<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	#ServerName www.example.com

	ServerAdmin webmaster@localhost       //cambia la dirección de correo por una tuya
	DocumentRoot /var/www/examen/         //cambia la ruta por /var/www/gci/
	ServerName www.ejercicio3.daw         //escribe la url que quieras para tu dominio

	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```
Edita el archivo hosts y agrega la linea de tu dominio:
```
sudo nano /etc/hosts
```
>Así es como te deberá quedar el archivo tras agregar tu dominio:
>```
>127.0.0.1	localhost
>127.0.1.1	daw
>
># The following lines are desirable for IPv6 capable hosts
>::1     ip6-localhost ip6-loopback
>fe00::0 ip6-localnet
>ff00::0 ip6-mcastprefix
>ff02::1 ip6-allnodes
>ff02::2 ip6-allrouters
>127.0.0.1 daw22_23.es	    //esta es la línea de tu dominio (si no existe ningún otro, asegurate que la IP es 127.0.0.1)
>```
### Activar archivo daw22_23
Por ir terminando la configuración y tener habilitado la configuración del VirtualHost, escribe el siguiente comando:
```
sudo a2ensite daw22_23
```
Por último, reinicia el servicio apache para aplicar los cambios
```
sudo service apache2 reload
```
