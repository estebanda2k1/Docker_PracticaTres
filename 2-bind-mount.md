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

```
docker run -d --name contenedor_dos -p  80:80 -v C:\Users\Esteban\Desktop\nginx\html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?

Salio el error 403, esto se debe a que no hay ningun archivo html que abra.


### ¿Qué pasa con el archivo index.html del contenedor?

El contenedor busca, pero al no encontrarlo salta el error 403


### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Carga el index.html que se descagó de la página web

<img width="1599" height="720" alt="image" src="https://github.com/user-attachments/assets/fd313bab-6a35-4638-a1e0-161149f43d05" />

### Eliminar el contenedor
```
docker rm -f contenedor_dos
```

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Vuelve a cargar el mismo archivo html.


