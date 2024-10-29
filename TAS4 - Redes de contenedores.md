
I. Título

Redes de contenedores 

II. Tiempo de duración

45 minutos

III. Fundamentos:


Beneficios de los contenedores:


- Rapidez en la implementación:
Los contenedores permiten empaquetar aplicaciones junto con todas sus dependencias en un entorno autocontenido, lo que facilita su implementación en cualquier sistema compatible con contenedores.
La capacidad de ejecutar múltiples contenedores en una misma máquina física sin conflicto, permite una implementación más rápida y eficiente de aplicaciones.


- Aislamiento ligero:
Los contenedores utilizan tecnologías de virtualización a nivel de sistema operativo para proporcionar aislamiento entre aplicaciones.
A diferencia de las máquinas virtuales, los contenedores comparten el mismo núcleo del sistema operativo del host, lo que resulta en un menor consumo de recursos y un inicio más rápido.


- Facilidad para escalar:
Los contenedores son altamente escalables, lo que significa que pueden ser fácilmente replicados o eliminados según la demanda.
Las herramientas de orquestación de contenedores, como Docker Swarm o Kubernetes, permiten gestionar automáticamente el escalado de contenedores en función de la carga de trabajo.


Redes de contenedores:


- Tipos de redes en Docker:
Docker proporciona varios tipos de redes para conectar contenedores entre sí y con el mundo exterior.
La red de puente (bridge) es la red predeterminada en Docker y permite que los contenedores se comuniquen entre sí en el mismo host.
La red de superposición (overlay) permite conectar contenedores distribuidos en diferentes hosts en un clúster Docker.
La red en modo host (host) elimina el aislamiento de red entre el contenedor y el host, lo que puede ser útil en ciertos casos de uso.



- Configuración de redes personalizadas:


Además de los tipos de redes predeterminados, Docker permite crear redes personalizadas para satisfacer las necesidades específicas de tu aplicación.
Puedes configurar aspectos como el rango de direcciones IP, la asignación de puertos, las políticas de seguridad y la conectividad con redes externas.

Comandos básicos de Linux relacionados con Docker:


- Navegación de directorios:
cd: Cambia el directorio de trabajo.
ls: Lista el contenido de un directorio.
pwd: Muestra el directorio de trabajo actual.


- Gestión de archivos y directorios:
mkdir: Crea un nuevo directorio.
rm: Elimina archivos o directorios.
cp: Copia archivos o directorios.
mv: Mueve o renombra archivos o directorios.


- Permisos y usuarios:
chmod: Cambia los permisos de archivos o directorios.
chown: Cambia el propietario y/o el grupo de archivos o directorios.
sudo: Ejecuta comandos con privilegios de superusuario.

IV. Conocimientos previos.

Uso de imágenes Docker:


Las imágenes en Docker son plantillas de solo lectura que contienen todo lo necesario para ejecutar un contenedor, incluyendo el sistema operativo, las bibliotecas, las dependencias y el código de la aplicación.
Se pueden obtener imágenes de varios lugares, como el Docker Hub (un repositorio público de imágenes Docker), registros privados o mediante la creación de imágenes personalizadas.
Docker utiliza un sistema de capas para almacenar imágenes de manera eficiente. Cada capa representa un cambio en el sistema de archivos, lo que permite compartir capas comunes entre imágenes, reduciendo así el espacio de almacenamiento y el tiempo de descarga.


Dockerfile y construcción de imágenes:


Un Dockerfile es un archivo de texto plano que contiene una serie de instrucciones que Docker utiliza para construir una imagen Docker.
Estas instrucciones pueden incluir comandos para copiar archivos en la imagen, instalar dependencias, configurar variables de entorno, definir puntos de entrada, entre otros.
Al utilizar un Dockerfile, se puede automatizar el proceso de construcción de imágenes y garantizar la consistencia entre los diferentes entornos de desarrollo, prueba y producción.



Seguridad y gestión de recursos:

La seguridad en Docker es crucial para garantizar que los contenedores y las aplicaciones que ejecutan sean seguros y confiables.
Docker proporciona varias características de seguridad, como el aislamiento de recursos utilizando namespaces y cgroups del kernel de Linux, la capacidad de ejecutar contenedores como usuarios no privilegiados, y la posibilidad de limitar los recursos que un contenedor puede utilizar, como CPU, memoria y red.
Además, Docker recomienda seguir las mejores prácticas de seguridad, como minimizar el tamaño de las imágenes, escanearlas en busca de vulnerabilidades conocidas, y aplicar parches regularmente.

V. Objetivos a alcanzar

Configurar una red personalizada en Docker para establecer una comunicación segura y eficiente entre el contenedor de pgAdmin, una interfaz de administración para PostgreSQL, y el contenedor de la base de datos PostgreSQL. 

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

VIII. Procedimiento
IX. Resultados esperados:
X. Bibliografía
