## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es C:\Users\Esteban\Desktop\ejercicio3\db

### ¿Qué contiene la carpeta db del host?
Va a contener la base de datos que vamos a montar con el contenedor, ya que le vamos a asignar

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name contenedor_mysql -p 3306:3306 -v C:\Users\Esteban\Desktop\ejercicio3\db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=12345 -e MYSQL_DATABASE=base_wordpress -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin123 --network net-wp mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Se  esta guardando, permanentemente las bases de datos que cree, en el disco que asigné.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es .../ejercicio3/www


### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name contenedor_wordpress -p 9500:80 -v "C:\Users\Esteban\Desktop\ejercicio3\www:/var/www/html" -e WORDPRESS_DB_HOST=contenedor_mysql:3306 -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin123 -e WORDPRESS_DB_NAME=base_wordpress --network net-wp wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1599" height="624" alt="image" src="https://github.com/user-attachments/assets/15b13800-811d-46ac-a032-99d77cbf2def" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
Se mantiene igual el contenedor, se puede decir que Wordpress conservó todo

<img width="1599" height="607" alt="image" src="https://github.com/user-attachments/assets/442d4ac7-4035-46fb-8a99-6ff5e5a2c9b5" />


