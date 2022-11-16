Alex Gasch Blasco
# Configuración de Apache en el equipo

## Configurar los VirtualHost
Para configurar los virtualhost, escribe el siguiente comando:
```
sudo nano /etc/httpd/conf/httpd.conf
```
>En el documento que se abrirá, escribe las siguientes líneas de código:
>```
><VirtualHost *:80>
>     ServerName daw22_23       //establece la raíz del dominio y con esta direccion es la que emplearás en el navegador para acceder a tu aplicacion
>     DocumentRoot /var/www/html/daw22_23     //establece la direccion a donde apunta el dominio configurado
></VirtualHost>
>```

Reinicia el servidor Apache para establecer los cambios:
```
sudo systemctl restart apache2
```
### Que pasa con nuestro VirtualHost?
Modifica el archivo **host** para que el dominio sea resuelto por nuestra propia máquina:
```
sudo nano /etc/hosts
```
>Agrega el dominio anterior
>```
>
>```
