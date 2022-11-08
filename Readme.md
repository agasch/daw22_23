Alex Gasch Blasco

# GitHub
## Introducción
### Que es GitHub
**Github** es un portal creado para alojar el código de las aplicaciones de cualquier desarrollador, y que fue comprada por **Microsoft** en *junio del 2018*. La plataforma está creada para que los desarrolladores suban el código de sus aplicaciones y herramientas, y que como usuario no sólo puedas descargarte la aplicación, sino también entrar a su perfil para leer sobre ella o colaborar con su desarrollo.

### Que ofrece
Github permite que los desarrolladores alojen proyectos creando repositorios de **forma gratuita**. Pero hay que tener una cosa en mente, y es que para poder subir gratis los proyectos deberán ser de *código abierto*. Y no quieres que tu aplicación sea de código abierto, la plataforma también tiene una versión de pago para alojar proyectos de forma privada.

En Github también puedes entrar a los proyectos de los demás y colaborar para mejorarlos. Esto quiere decir que los usuarios pueden opinar, dejar sus comentarios sobre el código, colaborar y contribuir mejorando el código. También pueden reportar errores para que los desarrolladores lo mejoren.

Github también ofrece una serie de herramientas propias con las que complementar las ventajas que ya tiene el sistema Git de por sí solo. Por ejemplo, puedes crear una Wiki para cada proyecto, de forma que puedas ofrecer toda la información sobre él y anotar todos los cambios de las diferentes versiones.

## Tutorial de instalacion

Abre una ventana de terminal y actualiza los paquetes:
```
sudo apt update
```

Escribe el comando para instalar git:
```
sudo apt install git
```

Comprueba que la version es la correcta:
```
git --version
```

Crea un directorio en el Escritorio y accede a él.
```
mkdir GitHub
cd GitHub
```

Crea un documento de prueba
```
touch prueba.c
gedit prueba.c
```

Se abrirá un editor de texto en el que debes escribir el siguiente código:
```
#include <stdio.h>
int main(){
    printf(“Hola DAW”);
    return 0;
}
```

Guarda y cierra el archivo. Ejecuta los siguientes comandos:
```
git config --global user.email "gaschblascoalex@gmail.com"
git config --global user.name "agasch"
```

Procede a iniciar un nuevo repositorio en GitHub y subir el directorio actual.
```
git init
git add .
git commit -m "Subida del archivo de prueba"
git push
```

## Referencias
[https://www.xataka.com/basics/que-github-que-que-le-ofrece-a-desarrolladores](https://www.xataka.com/basics/que-github-que-que-le-ofrece-a-desarrolladores)
