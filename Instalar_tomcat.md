Alex Gasch
# Instalar Tomcat en Ubuntu
Para instalar el **Servidor Tomcat Apache en Ubuntu**, instala **OpenJDK** con el comando _sudo apt install openjdk-11-jdk_, y ejecuta _sudo apt install tomcat9 tomcat9-admin_. Después, testea el funcionamiento del servidor Tomcat buscando en el navegador **http://127.0.0.1:8080**. También puedes crear una cuenta de usuario para explorar con el administrador de aplicaciones web del servidor Apache Tomcat.

## Instalar Java
Abre una ventana de terminal y actualiza los repositorios con el comando:
```
sudo apt update
```
Instala servidor Java con el siguiente comando
>Espera a que termine el proceso (puede tardar unos minutos).
```
sudo apt install openjdk-11-jdk
```
Verifica la versión del servidor instalado:
```
java -version
```
>Tiene que salirte la versión **11.0.14.1** o superior.

## Verificar la disponibilidad del paquete Apache Tomcat
Verifica la disponibilidad de Apache Tomcat en el repositorio
```
sudo apt-cache search tomcat
```
>Verifica que la siguiente linea aparece por pantalla al ejecutar el dicho comando (por las últimas líneas).

## Instalar Servidor Apache Tomcat
Despues de encontrar los requisitos del paquete **Apache Tomcat**, inatalalo con el siguiente comando
>Espera a que termine el proceso (puede tardar unos segundos).
```
sudo apt install tomcat9 tomcat9-admin
```

## Revisa los puertos del servidor
Verifica que la línea del 
```
ss -ltn
```
>La línea que buscas es la siguiente:
>```
>LISTEN      0           100                          *:8080                      *:*                
>```

## Abrir los puertos para el Servidor Apache Tomcat
Para habilitar el puerto que deseas, ejecuta el siguiente comando:
```
sudo ufw allow from any to any port 8080 proto tcp
```
>El resultado esperado es:
>```
>Reglas actualizadas
>Reglas actualizadas (v6)
>```

## Verificar resultado
Para verificar que todo el proceso ha salido como toca, vete a la barra de navegación de tu buscador favorito, introduce **http://127.0.0.1:8080**, y si ves en grande y negrita el ansiado _IT WORKS_, has completado la instalación con éxito.
