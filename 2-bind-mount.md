# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# docker run -d --name nginx-bind \
# -p 80:80 \
# -v /ruta/completa/nginx/html:/usr/share/nginx/html \
# nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
# Se muestra el contenido de la carpeta html del host. Como está vacía, al ingresar desde el navegador (http://localhost) aparece un error 403 (Forbidden) porque no hay un index.html que servir.

### ¿Qué pasa con el archivo index.html del contenedor?
# El archivo index.html original de la imagen de Nginx queda oculto, ya que el bind mount sobreescribe el contenido del directorio /usr/share/nginx/html con el contenido de la carpeta html del host.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# El servidor Nginx sirve automáticamente el nuevo index.html que está dentro de la carpeta html del host. Al ingresar al navegador (http://localhost) se visualiza el template descargado.


### Eliminar el contenedor
# docker rm -f nginx-bind

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# El contenido del template sigue disponible en la carpeta html del host, por lo que al crear un nuevo contenedor montando el mismo directorio el servidor Nginx vuelve a mostrar automáticamente el sitio web sin necesidad de volver a copiar los archivos.


