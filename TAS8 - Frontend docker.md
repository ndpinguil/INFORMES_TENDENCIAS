I. Título: Frontend Docker

II. Tiempo de duración: 1 hora

III. Fundamentos:

![image](https://github.com/user-attachments/assets/eb710494-2f85-45cf-944a-d57a4abfa2bc)

El despliegue de un backend utilizando Docker es una práctica ampliamente adoptada en la industria del desarrollo de software debido a las numerosas ventajas que ofrece en términos de portabilidad, consistencia y seguridad. Docker permite encapsular aplicaciones y sus dependencias en contenedores ligeros, garantizando que el software se ejecute de manera consistente en cualquier entorno, ya sea en desarrollo, pruebas o producción.

IV. Conocimientos previos.

![image](https://github.com/user-attachments/assets/a0845251-8b9d-4fc6-ba0b-6b8bce92441f)

Los conocimientos necesarios para realizar esta práctica incluyen conceptos de Docker, como la creación, configuración y ejecución de contenedores e imágenes Docker, el uso de bind mounts y volúmenes para la persistencia de datos, y la creación y gestión de redes Docker para permitir la comunicación entre contenedores. También es necesario tener conocimientos en administración de bases de datos, específicamente en la configuración y gestión básica de PostgreSQL y el uso de pgAdmin para administrar bases de datos PostgreSQL.

En el desarrollo de aplicaciones, se requiere experiencia en el desarrollo de aplicaciones back-end con Spring Boot, incluyendo la configuración de bases de datos y la gestión de migraciones con Flyway, así como en el desarrollo de aplicaciones front-end con React, incluyendo la configuración y construcción de proyectos. Además, se necesita conocimiento en el uso de Maven para construir proyectos Java y en la creación de Dockerfiles para definir cómo se deben construir las imágenes Docker tanto para el back-end como para el front-end. Finalmente, es crucial saber cómo configurar puertos en Docker para hacer accesibles las aplicaciones desde el host y verificar que los contenedores están correctamente conectados y que los servicios son accesibles.

V. Objetivos a alcanzar

Demostrar cómo desplegar una aplicación completa utilizando contenedores Docker para gestionar tanto el back-end como el front-end. 

VI. Equipo necesario:
Computador con sistema operativo Windows/Linux. 
Play with Docker  
CMD
Internet 

VII. Material de apoyo.

Documentación de docker. 
Guía de asignatura  
El docente
Comando 

VIII. Procedimiento

Clonar el repositorio
git clone https://github.com/maguaman2/securityfe
cd securityfe

``

Crear el Dockerfile
A continuación, cree un archivo llamado Dockerfilee
# Official base image
FROM node:13.12.0-alpine

# Set working directory
WORKDIR /app

# Add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

# Install app dependencies
COPY package.json ./ 
COPY package-lock.json ./ 
RUN npm install --silent
RUN npm install react-scripts@3.4.1 -g --silent

# Add app source
COPY . ./ 

# Start app
CMD ["npm", "start"]

Explicación del Dockerfile:
DESDE el nodo:13.12.0-alpine:Tú
directorio_trabajo /aplicación: Desafío
ENV PATH /app/node_modules/.bin:$PATH : Añade el
COPIA paquete.json ./ yCOPY package-lock.json ./ : Copia los
EJECUTAR npm install --silent : Instala las dependencias de la aplicación.
EJECUTE npm install react-scripts@3.4.1 -g --silent : Instala react-scripts, necesario para ejecutar la aplicación React.
COPIAR . ./ : Copia el resto del código de la aplicación al contenedor.
CMD ["npm", "start"] : Inicia la aplicación en el contenedor.

![Screenshot 2024-11-22 091320](https://github.com/user-attachments/assets/97760f2b-1f28-48cb-8130-96ea45cadf0d)


Construir la imagen Docker
Una vez que haya creado el Dockerfile, debe construir la imagen de Docker. Ejecute el siguiente comando en la carpeta raíz del proyecto:
docker build -t myappfe:latest .

Este comando construye la imagen de Docker y la etiqueta como myappfe:latest.
 Ejecutar el contenedor
Una vez que la imagen se haya creado correctamente, puede ejecutar un contenedor a partir de esta imagen. El siguiente comando crea un contenedor, lo conecta a una red y lo exponen en el puerto 3000:
docker run -d --network red_de_los_contenedores -p 3000:3000 myappfe

Explicación de los parámetros:
-d : Ejecuta el contenedor en segundo plano (modo separado).
--network red_de_los_contenedores : Conecta el contenedor a una red específica llamada red_de_los_contenedores.
-p 3000:3000 : Mapea el puerto 3000 del contenedor al puerto 3000 de la máquina local.
myappfe : Nombre de la imagen de Docker que se ejecutará.


Verificar la aplicación en funcionamiento
Abrir el navegador a la siguiente URL:
http://localhost:3000

Debería ver la interfaz de la aplicación React mostrando la lista de usuarios de la base de datos, lo cual es el mismo resultado que obtendría al acceder a:
http://localhost:8081/users

IX. Resultados esperados:


![Screenshot 2024-11-22 091327](https://github.com/user-attachments/assets/e9794ef9-3b14-4198-af70-8dfeecf96182)

![Screenshot 2024-11-12 125634](https://github.com/user-attachments/assets/49c5140b-6c72-41a4-bb2b-5319c1e562ea)

![Screenshot 2024-11-22 091310](https://github.com/user-attachments/assets/b7370d94-8686-4939-9e1c-2144fb475e48)

X. Bibliografía

Notion. (n.d.). Notion.Site. Retrieved November 27, 2024, from https://wobbly-zephyr-621.notion.site/2-2-Desplegar-aplicaci-n-FrontEnd-280e4945e08c496f8de5c393c58c9d3f



