I. Título:  Despliegue con Docker de Backend

II. Tiempo de duración: 2 Horas

III. Fundamentos:

El despliegue de un backend utilizando Docker es una práctica ampliamente adoptada en la industria del desarrollo de software debido a las numerosas ventajas que ofrece en términos de portabilidad, consistencia y seguridad. Docker permite encapsular aplicaciones y sus dependencias en contenedores ligeros, garantizando que el software se ejecute de manera consistente en cualquier entorno, ya sea en desarrollo, pruebas o producción.

Ventajas de Docker en la Seguridad del Proyecto:

Aislamiento de Aplicaciones: Docker proporciona un entorno aislado para cada aplicación, reduciendo el riesgo de que vulnerabilidades en una parte del sistema afecten a otras partes. Este aislamiento se logra mediante la virtualización a nivel de sistema operativo, creando contenedores independientes con sus propias instancias de librerías y dependencias.

Consistencia y Reproducibilidad: Con Docker, el entorno de desarrollo es idéntico al de producción, eliminando problemas de configuración que podrían introducir vulnerabilidades. Al garantizar que el código se ejecuta en el mismo entorno en todas las fases del desarrollo, se minimizan las diferencias que pueden dar lugar a errores de seguridad difíciles de detectar.

Actualizaciones y Parches: Docker facilita la actualización y parcheo de componentes de software, permitiendo construir nuevas imágenes de contenedor con las versiones actualizadas de las dependencias y el código de la aplicación. Esto asegura que las vulnerabilidades conocidas se puedan mitigar rápidamente mediante la distribución de nuevas imágenes.

Control de Versiones y Despliegues Automatizados: Docker se integra fácilmente con sistemas de control de versiones y herramientas de integración continua (CI/CD), permitiendo despliegues automatizados y más seguros. Estos despliegues automatizados pueden incluir pruebas de seguridad y análisis estáticos para detectar vulnerabilidades antes de que el código llegue a producción.

Reducción de la Superficie de Ataque: Al usar imágenes de contenedor minimalistas, es posible reducir la superficie de ataque al incluir sólo los componentes necesarios para ejecutar la aplicación. Esto minimiza el número de posibles puntos de entrada para atacantes.

Gestión de Dependencias: Docker permite una gestión eficiente de las dependencias, asegurando que solo las versiones seguras y aprobadas de librerías y herramientas se utilicen en los contenedores. Esto es crucial para prevenir la introducción de dependencias vulnerables en el entorno de producción.


IV. Conocimientos previos.
Los contenedores ofrecen varios beneficios clave para la implementación y gestión de aplicaciones. En primer lugar, la rapidez en la implementación se logra gracias a que los contenedores permiten empaquetar aplicaciones junto con todas sus dependencias en un entorno autocontenido, facilitando su implementación en cualquier sistema compatible con contenedores. Además, la capacidad de ejecutar múltiples contenedores en una misma máquina física sin conflicto permite una implementación más rápida y eficiente de aplicaciones.

El aislamiento ligero es otra ventaja importante. Los contenedores utilizan tecnologías de virtualización a nivel de sistema operativo para proporcionar aislamiento entre aplicaciones. A diferencia de las máquinas virtuales, los contenedores comparten el mismo núcleo del sistema operativo del host, lo que resulta en un menor consumo de recursos y un inicio más rápido.

La facilidad para escalar es crucial en entornos dinámicos. Los contenedores son altamente escalables, lo que significa que pueden ser fácilmente replicados o eliminados según la demanda. Herramientas de orquestación de contenedores, como Docker Swarm o Kubernetes, permiten gestionar automáticamente el escalado de contenedores en función de la carga de trabajo.

En cuanto a las redes de contenedores, Docker proporciona varios tipos para conectar contenedores entre sí y con el mundo exterior. La red de puente (bridge) es la red predeterminada en Docker y permite que los contenedores se comuniquen entre sí en el mismo host. La red de superposición (overlay) permite conectar contenedores distribuidos en diferentes hosts en un clúster Docker. La red en modo host (host) elimina el aislamiento de red entre el contenedor y el host, lo que puede ser útil en ciertos casos de uso.

Además de los tipos de redes predeterminados, Docker permite la configuración de redes personalizadas para satisfacer las necesidades específicas de las aplicaciones. Puedes configurar aspectos como el rango de direcciones IP, la asignación de puertos, las políticas de seguridad y la conectividad con redes externas, proporcionando así una gran flexibilidad y control sobre el entorno de red de los contenedores.


V. Objetivos a alcanzar

Garantizar la portabilidad del software, asegurando que el backend y todas sus dependencias se empaqueten en contenedores que puedan ejecutarse de manera consistente en cualquier entorno, ya sea de desarrollo, pruebas o producción, sin importar las diferencias en la configuración del sistema operativo subyacente.

Aumentar la seguridad a través del aislamiento, proporcionando un entorno aislado para cada aplicación, reduciendo el riesgo de que una vulnerabilidad en una parte del sistema afecte a otras partes. Este aislamiento se logra mediante la virtualización a nivel de sistema operativo, creando contenedores independientes con sus propias instancias de librerías y dependencias.



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


1. Base de datos
Ejecutar los contenedores para PostgreSQL y pgAdmin.
Crear la red necesaria.
Configurar la base de datos para el proyecto.

2. Generar artefacto .jar del proyecto de Spring Boot
Clonar el proyecto de Spring Boot desde GitHub:

Modificar el archivo application.yml con los datos de conexión a la base de datos PostgreSQL creada anteriormente:
datasource:
  url: jdbc:postgresql://server-name:5432/nathalyposgressocketTimeout=3
  username: nathaly-postgres-configurado
  password: 1234-postgres-configurado
  driverClassName: org.postgresql.Driver
Generar el archivo .jar usando un contenedor de Maven. Ajusta la ruta del proyecto y la red según tu configuración:
docker run -it --rm --name my-maven-project --network db_default -v /ruta/al/proyecto:/usr/src/mymaven -w /usr/src/mymaven maven:3.3-jdk-8 mvn clean package
Este comando debe mostrar "Build Success" al final.

![Screenshot 2024-11-12 125217](https://github.com/user-attachments/assets/21563776-d090-432a-b982-2765d0b97669)


Crear un archivo Dockerfile en la carpeta principal del proyecto:

![Screenshot 2024-11-26 203317](https://github.com/user-attachments/assets/6babdd72-8736-4fe7-8ace-b0255ce289e3)


3. Crear imagen con la app de Spring Boot
Desde la carpeta principal del proyecto (donde está el Dockerfile)
4. Crear contenedor
Ejecutar el contenedor con la imagen creada:

![Screenshot 2024-11-26 203612](https://github.com/user-attachments/assets/6e8b36b7-9dbe-4e88-aa80-35f7a74bac5b)


Para comprobar que está corriendo, usa:

![Screenshot 2024-11-26 203619](https://github.com/user-attachments/assets/87a14909-2fe1-4416-8fee-3eb0060354ee)


5. Probar funcionamiento
Abrir un navegador y acceder a la URL localhost:8081/users. Debería mostrar un JSON con la información de un usuario.

IX. Resultados esperados:

![Screenshot 2024-11-12 125634](https://github.com/user-attachments/assets/82bd938b-5938-417d-b43f-24fca62805cf)


X. Bibliografía

Notion. (n.d.). Notion.Site. Retrieved May 19, 2024, from https://wobbly-zephyr-621.notion.site/2-1-Despliegue-postgres-y-spring-boot-ae6e75ce6c89447588d319eb4a631e04
