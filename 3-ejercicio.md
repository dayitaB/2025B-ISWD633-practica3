## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

En el esquema del ejercicio carpeta del contenedor (a) es 
/var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
La base de datos que se va a montar junto al contenedor

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

```
docker run -d --name contenedor_mysql -p 3306:3306 -v C:\Users\DAYANNA\Desktop\ejercicio3\db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=12345 -e MYSQL_DATABASE=wordpress_db -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin123 --network net-wp mysql:8
```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Los archivos y directorios necesarios que MySQL crea automáticamente para la base de datos que fueron generador por el contenedor al iniciar

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name contenedor_wordpress -p 9500:80 -v "C:\Users\DAYANNA\Desktop\ejercicio3\www:/var/www/html" -e WORDPRESS_DB_HOST=contenedor_mysql:3306 -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin123 -e WORDPRESS_DB_NAME=wordpress_db --network net-wp wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1255" height="928" alt="imagen" src="https://github.com/user-attachments/assets/28b1e168-274e-479a-a96a-785804866928" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Se mantiene igual el contenedor, es decir que Wordpress conservó todo

