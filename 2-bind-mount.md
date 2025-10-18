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
# COMPLETAR CON EL COMANDO
```
docker run -d --name contenedor_p3 -p  80:80 -v C:\Users\DAYANNA\Desktop\nginx\html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
Se presentó el error 403 
<img width="939" height="234" alt="imagen" src="https://github.com/user-attachments/assets/134bf979-2afc-47e5-8d32-95ba24966f7d" />


### ¿Qué pasa con el archivo index.html del contenedor?
Queda oculto e inaccesible, es decir no es un archivo eliminado, pero ya no es visible ni accesible por eso sale el mensaje de error 403

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Se muestra el index.html que se descargó la pa página web 
<img width="1253" height="1012" alt="imagen" src="https://github.com/user-attachments/assets/df73e54c-e0b6-4da2-9582-9ca4729f348d" />


### Eliminar el contenedor
```
docker rm -f contenedor_p3
```

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Se vuelve a cargar el mismo archivo html ya que siempre está leyendo la información directamente de la carpeta de Windows, la cual nunca fue eliminada.


