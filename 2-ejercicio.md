### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:15-alpine3.21
PS C:\Users\Italo> docker run -d --name postgres-container -e POSTGRES_PASSWORD=dc12 -e POSTGRES_USER=postgres -e POSTGRES_DB=postgres postgres:15-alpine3.21

# Verificar que no hay puertos expuestos:
PS C:\Users\Italo> docker port postgres-container

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

PS C:\Users\Italo> docker run -d --name pgadmin-container -p 8080:80 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=admin123 dpage/pgadmin4

La figura presenta el esquema creado en donde los puertos son:
- a: (completar con el valor)
- b: (completar con el valor)
- c: (completar con el valor)

![Imagen](esquema-2-ejercicio.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
<img width="1880" height="868" alt="image" src="https://github.com/user-attachments/assets/935db8c2-26de-4dfc-9ca4-0ba5bdaaa7cd" />

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
PS C:\Users\Italo> docker exec -it postgres-container psql -U postgres -c "CREATE DATABASE info;"
PS C:\Users\Italo> docker exec -it postgres-container psql -U postgres -d info -c "CREATE TABLE personas (id SERIAL PRIMARY KEY, nombre VARCHAR(255) NOT NULL);"
PS C:\Users\Italo> docker exec -it postgres-container psql -U postgres -d info -c "INSERT INTO personas (nombre) VALUES ('Duncan Licuy'),('Ana Paula'),('Eliot Cazar');"
## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
PS C:\Users\Italo> docker exec -it postgres-container psql -U postgres -d info
<img width="343" height="79" alt="image" src="https://github.com/user-attachments/assets/440c5365-7cc9-4fb0-b260-508267915312" />

### Realizar un select *from personas
<img width="859" height="116" alt="image" src="https://github.com/user-attachments/assets/e06eb882-75fb-4f40-b053-f68fbe3ec00c" />

