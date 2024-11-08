I. Título: Docker Compose
II. Tiempo de duración: 1 hora
III. Fundamentos:

Servicio phpMyAdmin

  phpmyadmin:
phpmyadmin:: Este es el nombre del segundo servicio, que es phpMyAdmin, una herramienta web para gestionar bases de datos MySQL.

    image: phpmyadmin/phpmyadmin:latest
image: phpmyadmin/phpmyadmin:latest: Aquí especificas la imagen de Docker que deseas utilizar para este servicio. phpmyadmin/phpmyadmin:latest indica que usarás la versión más reciente de la imagen oficial de phpMyAdmin.

    ports:
      - "8080:80"
ports:: Define el mapeo de puertos entre el contenedor de phpMyAdmin y tu máquina local.
- "8080:80": El puerto 80 del contenedor (puerto por defecto para las aplicaciones web) estará accesible en el puerto 8080 de tu máquina local. Por lo tanto, podrás acceder a phpMyAdmin a través de http://localhost:8080.

    environment:
environment:: Define las variables de entorno para el servicio de phpMyAdmin.

      PMA_HOST: mysql
PMA_HOST: mysql: Establece el nombre del servicio MySQL (definido anteriormente) como el host al que phpMyAdmin se conectará. Esto permite que phpMyAdmin sepa dónde encontrar la base de datos MySQL.

      PMA_USER: usuario
PMA_USER: usuario: Proporciona el nombre de usuario que phpMyAdmin utilizará para conectarse a MySQL. En este caso, es el usuario que definiste anteriormente (usuario).

      PMA_PASSWORD: nathaly
PMA_PASSWORD: nathaly: Proporciona la contraseña del usuario que phpMyAdmin utilizará para conectarse a MySQL, que es nathaly.


IV. Conocimientos previos.

Los volúmenes en Docker son una forma de persistir y gestionar datos generados y utilizados por contenedores. Aquí hay algunas razones por las que se utilizan volúmenes:

1. Persistencia de datos
Retención de datos: Cuando un contenedor se detiene o se elimina, los datos almacenados en el sistema de archivos del contenedor se pierden. Los volúmenes permiten que los datos persistan incluso si el contenedor se reinicia o se elimina. Esto es especialmente importante para bases de datos, donde no deseas perder tus datos al actualizar o eliminar un contenedor.
2. Desacoplamiento de datos y contenedores
Separación lógica: Usar volúmenes permite desacoplar los datos de la aplicación. Puedes tener múltiples contenedores que acceden al mismo volumen, facilitando la gestión y el acceso a datos compartidos sin que los datos estén "atados" a un contenedor específico.
3. Mejora en el rendimiento
Eficiencia: Los volúmenes pueden ofrecer un mejor rendimiento en comparación con el almacenamiento en el sistema de archivos de un contenedor, especialmente cuando se realizan operaciones de lectura y escritura intensivas. Esto se debe a que los volúmenes están diseñados para ser gestionados de manera más eficiente por Docker.
4. Facilidad de copia de seguridad y migración
Copia de seguridad de datos: Puedes fácilmente crear copias de seguridad y restaurar datos almacenados en volúmenes. Docker proporciona comandos que permiten copiar datos desde y hacia volúmenes, lo que facilita la administración de copias de seguridad.
5. Compatibilidad con herramientas de desarrollo
Desarrollo local: En un entorno de desarrollo, puedes utilizar volúmenes para mapear directorios locales a contenedores, lo que permite que los cambios realizados en tu máquina local se reflejen instantáneamente dentro del contenedor. Esto es útil para el desarrollo de aplicaciones, ya que no necesitas reconstruir el contenedor cada vez que cambias tu código.
6. Soporte para múltiples plataformas de almacenamiento
Tipos de almacenamiento: Docker permite usar diferentes tipos de volúmenes, incluidos volúmenes locales, volúmenes en la nube y volúmenes en red. Esto proporciona flexibilidad para elegir cómo y dónde se almacenan tus datos.



V. Objetivos a alcanzar
Crear contenedores a travez de los archivos YML.

VI. Equipo necesario:
Computador con sistema operativo Windows/Linux. 
Play with Docker  
Comandos de Linux  
Internet 

VII. Material de apoyo.

Documentación de docker. 
Guía de asignatura  
El docente
Comando 

VIII. Procedimiento:

Primero creo el archivo, si es en una carpeta mejor , pero ya una vez creado se va al visual y se busca ese archivo.

![Screenshot 2024-11-05 120129](https://github.com/user-attachments/assets/ce7d68b7-1fc3-42fe-9cc1-f9e91928dedd)

 Ya en el archivo se crea los contenedores
services:
  postgres:
    image: postgres:latest
    container_name: my_postgres_container
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: mi_base_de_datos
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: my_pgadmin_container
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@admin.com
      PGADMIN_DEFAULT_PASSWORD: secret
    ports:
      - "5050:80"
    depends_on:
      - postgres
    volumes:
      - pgadmin_data:/var/lib/pgadmin

volumes:
  postgres_data:
  pgadmin_data:

Una vez ejecutado, se dirige al puerto y se abre el admin.

![Screenshot 2024-11-05 120322](https://github.com/user-attachments/assets/97ad8e25-5a05-4c87-bd11-0b3d92effd71)

IX. Resultados esperados:


![Screenshot 2024-11-05 122118](https://github.com/user-attachments/assets/d20d3835-9619-4bd0-a27a-0cc8b259c661)

