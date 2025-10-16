## Esquema para el ejercicio
![Imagen](esquema-4-ejercicio.PNG)

### Crear la red
PS C:\Users\Italo> docker network create net-wp

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
PS C:\Users\Italo> docker run -d --name mysql --network net-wp -e MYSQL_ROOT_PASSWORD=rootpassword123 -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wordpress -e MYSQL_PASSWORD=wppassword123 -e MYSQL_CHARSET=utf8mb4 -e MYSQL_COLLATION=utf8mb4_unicode_ci mysql:8

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
PS C:\Users\Italo> docker run -d --name wordpress --network net-wp -p 80:80 -e WORDPRESS_DB_HOST=mysql -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_USER=wordpress -e WORDPRESS_DB_PASSWORD=wppassword123 -e WORDPRESS_TABLE_PREFIX=wp_ wordpress:latest

De acuerdo con el trabajo realizado, en el esquema del ejercicio el puerto a es 80

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.

<img width="784" height="901" alt="image" src="https://github.com/user-attachments/assets/d463e93b-c645-4593-921e-36787342e958" />
<img width="805" height="448" alt="image" src="https://github.com/user-attachments/assets/b30c3133-1217-4f58-9ddc-46e476e5676d" />



Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:80/ 
recordar que a es el puerto que usó para el mapeo con wordpress
<img width="1863" height="888" alt="image" src="https://github.com/user-attachments/assets/400b2a22-f51a-4261-9e89-869cdb195791" />


### Eliminar el contenedor wordpress
PS C:\Users\Italo> docker rm -f wordpress

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:80/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
Al eliminar y recrear el contenedor WordPress, el sitio web se mantiene intacto porque toda la información (publicaciones, usuarios, configuraciones) se almacena en la base de datos MySQL, no en el contenedor. El contenedor WordPress solo contiene los archivos temporales y el código de la aplicación, que se regenera al recrearlo. Mientras mantengas el contenedor MySQL ejecutándose, se puede recrear WordPress repetidamente sin perder el contenido.

