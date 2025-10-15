# Variables de Entorno
### ¿Qué son las variables de entorno?
Son variables disponibles para tu programa/aplicación de forma dinámica durante el tiempo de ejecución. El valor de estas variables puede proceder de diversas fuentes: archivos de texto, gestores secretos de terceros, scripts de llamada, etc.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

PS C:\Users\Italo> docker run -d --name nginx-container -e username=duncan_licuy -e role=admin nginx:alpine

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
<img width="934" height="208" alt="image" src="https://github.com/user-attachments/assets/33bb421a-5a80-4fc4-86e3-118520beed04" />


### Crear un contenedor con la imagen de mysql, mapear todos los puertos
PS C:\Users\Italo> docker run -d --name mysql-container -p 3306:3306 -p 33060:33060 -e MYSQL_ROOT_PASSWORD=dc29 mysql:latest
 # Para mapear todos los puertos expuestos por MySQL:
PS C:\Users\Italo> docker run -d --name mysql-container -P -e MYSQL_ROOT_PASSWORD=dc29 mysql:lates
 La opción -P (mayúscula) mapea automáticamente todos los puertos expuestos por el contenedor a puertos aleatorios en el host.
 # Para ver los puertos mapeados:
 PS C:\Users\Italo> docker port mysql-container
### ¿El contenedor se está ejecutando?
<img width="1471" height="77" alt="image" src="https://github.com/user-attachments/assets/f3194586-6479-498b-9a10-4e46f4f48e88" />


### Identificar el problema
PS C:\Users\Italo> docker ps -a

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

### ¿Qué bases de datos existen en el contenedor creado?
PS C:\Users\Italo> docker exec -it mysql-container mysql -u root -p
<img width="707" height="159" alt="image" src="https://github.com/user-attachments/assets/dc277a9e-445e-4189-8924-dfc28d4f3e23" />

