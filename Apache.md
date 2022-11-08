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

Por pantalla debería salirte algo como esto:
```
Aplicaciones disponibles:
  Apache
  Apache Full
  Apache Secure
  CUPS
```
