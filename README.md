<h1 align="center"> EDUTASK</h1>

<p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-10-21%20100802.png" alt="Logo de Edutask" width="300">
</p>

<p align="center"><em>📚 Plataforma educativa para organizar clases, tareas y calendario académico.</em></p>

  
<details>
  <summary><h2> Introducción</h2></summary>
  
# Introducción

Nuestro proyecto, llamado Edutask, es una plataforma web educativa hecha para que profesores y estudiantes puedan organizar sus actividades. No es solo un lugar para subir tareas, sino que también tiene herramientas que motivan, como insignias para que te animes y un tutor inteligente. La idea es mejorar la forma en que se enseña y se aprende. Edutask quiere dejar de ser solo una herramienta local para convertirse en una plataforma innovadora que motive a los estudiantes, ayude a los profesores con su trabajo y sea un ejemplo de aprendizaje digital en varios países. Esta plataforma está pensada principalmente para docentes y alumnos de cualquier nivel educativo.

</details>

--- 

<details>  
  <summary><h2> Briefing</h2></summary>
  
Los módulos que más van a ayudar a nuestro proyecto son aplicaciones web para crear la página web de la empresa y cómo configurarla. También el módulo de seguridad informática para que esta página web sea segura y confiable para los usuarios. También la asignatura de servicios en red, ya que con ella podremos ofrecer todos los servicios a los usuarios y a la misma web.
#### **Materiales Necesarios**  
-**Físicos**:
  - Ordenadores con internet
  - Servidor o servicio de hosting para la página web.
  - Teléfonos para probar la plataforma en distintos dispositivos.
  - Periféricos básicos: teclado, mouse, cámara y micrófono.

-**Lógicos (software)**:
  - Sistema operativo (Windows, Linux ).
  - Programas para programar (por ejemplo, Visual Studio Code).
  - Lenguajes: HTML, CSS, JavaScript.
  - Base de datos (MySQL).
  - Git y GitHub para control de versiones y trabajo en equipo.
  - Servicio en la nube o hosting (AWS, Google Cloud, etc.).
  - Certificado SSL para la seguridad de la página.
  - Herramientas de seguridad (firewalls).
  - Plataformas para organizar el proyecto (Trello).

</details>

--- 
<details>
  <summary><h2> Arquitectura del software</h2></summary>

  <details>
    <summary><strong> Base de datos</strong></summary>
    
   <details>
    <summary>Backend</summary>

  ## 1. Descripción general del proyecto web
 
  La página web trata sobre una plataforma educativa que se llama Edutask, diseñada para ayudar a profesores y estudiantes a organizar sus actividades académicas de manera más rápida y clara . Su propósito principal es mejorar la enseñanza y el aprendizaje a través de herramientas como insignias motivacionales y un tutor inteligente y también  permitir la gestión de tareas.


  - Crear cuenta y perfil personalizado (para profesores y estudiantes).
  - Subir y gestionar tareas (crear y entregar y puntuar las actividades).
  - Organizar actividades.
  - Sistema de insignias y recompensas para motivar a los estudiantes.
  - Tutor inteligente para guiar y ayudar a los  estudiantes.
  - Interacción entre usuarios (comentarios y mensajes,).
  - Seguridad de la información (autenticación, privacidad de datos).
  - Panel de control para los profesores (seguimiento del progreso, estadísticas de los alumnos).

  ## 2. Identificación de entidades principales

  - **Usuarios**: información de los  profesores y estudiantes (datos personales, credenciales, roles).
  - **Tareas**: detalles de las actividades creadas, entregadas y puntuadas.
  - **Insignias y recompensas:** logros de los  estudiantes.
  - **Mensajes y comentarios**: comunicación entre usuarios.
  - **Progreso y estadísticas**: datos sobre el rendimiento de los estudiantes.
  - **Historial de actividades**: registro actividades hechas en la plataforma.
  - **Datos de seguridad**: información para autenticación y protección .

| Tema de información almacena | ¿Porqué guardarla en la base de datos? |
| ------------- | ------------- |
| Datos de usuarios | Para identificar y diferenciar a profesores y estudiantes  |
| Tareas y actividades  | Para gestionar, almacenar y permitir la entrega y puntuación de tareas|
| Insignias y recompensas  | Para motivar a los estudiantes y llevar registro de sus logros  |
| Mensajes y comentarios  | Para facilitar la comunicación entre usuarios  |
| Progreso y estadísticas  | Para hacer seguimiento de lo que aprenden los  estudiantes  |
| Historial de actividades  | Para seguridad y seguimiento de actividades hechas  |
| Datos de seguridad  | Para proteger la información y controlar el acceso a la plataforma  |

## 3. Datos que se deben guardar de cada entidad (atributos)

#### Usuarios
ID_usuario → INT (autoincremental, clave primaria)

Nombre → VARCHAR(50)
  
Apellidos → VARCHAR(50)
  
Correo_electronico → VARCHAR(100)
  
Contraseña → VARCHAR(255)
  
Rol → ENUM('profesor','estudiante')
Fecha_registro → DATE
  
Foto_perfil → VARCHAR(255)
  
Estado → BOOLEAN

#### Tareas:
  ID_tarea → INT (autoincremental, clave primaria)
  
  Titulo → VARCHAR(100)
  
  Descripcion → TEXT
  
  Fecha_creacion → DATE
  
  Fecha_limite → DATE
  
  ID_profesor → INT (clave foránea)
  
  Estado → ENUM('pendiente','entregada','calificada')
  
  Puntuacion_maxima → INT
  
#### Entrega de tareas:
  ID_entrega → INT (autoincremental, clave primaria)
  
  ID_tarea → INT (clave foránea)
  
  ID_estudiante → INT (clave foránea)
  
  Fecha_entrega → DATE
  
  Archivo_entregado → VARCHAR(255)
  
  Puntuacion_obtenida → INT
  
  Comentarios_profesor → TEXT
  
#### Insignias:
  ID_insignia → INT (autoincremental, clave primaria)
  
  Nombre → VARCHAR(50)
  
  Descripcion → TEXT
  
  Icono → VARCHAR(255)
  
  Fecha_otorgada → DATE
  
  ID_estudiante → INT (clave foránea)
  
#### Mensajes:
  ID_mensaje → INT (autoincremental, clave primaria)
  
  ID_emisor → INT (clave foránea)
  
  ID_receptor → INT (clave foránea)
  
  ID_tarea → INT (clave foránea, puede ser NULL)
  
  Texto → TEXT
  
  Fecha_hora → DATETIME

#### Progreso y estadisticas:
  ID_estadistica → INT (autoincremental, clave primaria)
  
  ID_estudiante → INT (clave foránea)
  
  ID_tarea → INT (clave foránea)
  
  Puntuacion_obtenida → INT
  
  Tiempo_dedicado → INT (en minutos)
  
  Fecha → DATE

#### Historial de actividades:
  ID_historial → INT (autoincremental, clave primaria)

  ID_usuario → INT (clave foránea)

  Accion → VARCHAR(100)

  Fecha_hora → DATETIME

  Detalles → TEXT

#### Datos de seguridad:
  ID_seguridad → INT (autoincremental, clave primaria)
  
  ID_usuario → INT (clave foránea)
  
  Token_sesion → VARCHAR(255)
  
  Fecha_creacion → DATETIME
  
  Fecha_expiracion → DATETIME
  
  IP_acceso → VARCHAR(45)

  ## 4. Relaciones entre las entidades

  #### 1. Usuarios ↔ Tareas
Un profesor (usuario con rol profesor) puede crear muchas tareas.
    
Cada tarea es creada por un solo profesor.
    
Relación: 1 profesor — N tareas
    
  #### 2. Usuarios ↔ Entregas de tareas
Un estudiante puede hacer muchas entregas (una por cada tarea asignada).
    
Cada entrega pertenece a un solo estudiante.
    
Relación: 1 estudiante — N entregas
    
  #### 3. Tareas ↔ Entregas de tareas
Cada tarea puede tener muchas entregas (de diferentes estudiantes).
    
Cada entrega está asociada a una sola tarea.
    
Relación: 1 tarea — N entregas
    
  #### 4. Usuarios ↔ Insignias
Un estudiante puede tener muchas insignias.
    
Cada insignia está asociada a un solo estudiante.
    
Relación: 1 estudiante — N insignias
    
  #### 5. Usuarios ↔ Mensajes
Un usuario puede enviar muchos mensajes.
    
Un usuario puede recibir muchos mensajes.
    
Relación: 1 usuario — N mensajes enviados
    
    Relación: 1 usuario — N mensajes recibidos
    
  #### 6. Tareas ↔ Mensajes
Un mensaje puede estar relacionado con una tarea (por ejemplo, conversación sobre una tarea).
    
No todos los mensajes tienen que estar vinculados a una tarea.
    
Relación: 1 tarea — N mensajes (0 o más mensajes)
    
  #### 7. Usuarios ↔ Progreso y estadísticas
Un estudiante tiene muchas entradas de progreso (por cada tarea o actividad).
    
Cada registro de progreso pertenece a un solo estudiante.
    
Relación: 1 estudiante — N registros de progreso
    
  #### 8. Tareas ↔ Progreso y estadísticas
Cada registro de progreso está asociado a una sola tarea.
    
Una tarea puede tener muchos registros de progreso.
    
Relación: 1 tarea — N registros de progreso
    
  #### 9. Usuarios ↔ Historial de actividades
Un usuario puede tener muchos registros en el historial (acciones que realiza en la plataforma).
    
Relación: 1 usuario — N registros de historial


## 5. Ejemplo de datos (simulación)
#### Entidad: Usuario 
- Nombre: Juan Pérez

- Email: juanp@gmail.com

- Rol: Estudiante

- Fecha de registro: 10/09/2025

#### Entidad: Profesor
- Nombre: María López

- Email: maria.lopez@colegio.edu

- Asignatura: Matemáticas

- Fecha de alta: 05/09/2025

#### Entidad: Curso
- Nombre del curso: Matemáticas 2º Bachillerato

- Profesor asignado: María López

- Fecha de inicio: 15/09/2025

- Fecha de fin: 30/06/2026

#### Entidad: Tarea
- Título: Ejercicios de Álgebra

- Descripción: Resolver los problemas del capítulo 3 del libro.

- Fecha de creación: 20/09/2025

- Fecha de entrega: 25/09/2025

- Estado: Pendiente


#### Entidad: Entrega
- Estudiante: Juan Pérez

- Tarea: Ejercicios de Álgebra

- Fecha de entrega: 24/09/2025

- Archivo: ejercicios_algebra_juanp.pdf

- Calificación: 8/10


#### Entidad: Insignia
- Nombre: “Constancia”

- Descripción: Se da por entregar todas las tareas a tiempo.

- Estudiante: Juan Pérez

- Fecha de obtención: 30/09/2025

## 6. Reflexiones, dificultades y dudas que tienes sobre la base de datos

Nos ha costado más el apartado de Identificación de entidades principales porque aún no tenemos del todo claro cómo será el proyecto y nos ha costado pensar todo esa parte, 
también en el apartado de descripción general del proyecto web por lo que hemos dicho antes no tenemos del todo claro dónde queremos llegar con el proyecto tenemos algunas dudas aun con eso. 

#### ¿Qué no tienes claro sobre la información que hay que guardar?
La verdad que lo tenemos todo bastante claro sobre esto .

</details>

<details>
<summary>Diseño de la base de datos</summary>
Este es diseño de la base de datos de EduTask hemos organizado la información de manera clara y funcional. Hemos creado tablas para profesores, usuarios, insignias, clases, tareas y entregas, definiendo sus relaciones para que los datos se conecten bien. 
  
 **ANTES:**
  
  <p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-11-14%20102226.png" alt="Logo de Edutask" width="500">
</p>


  **DESPUÉS:**
  
   <p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Diagrama%20base%20de%20datos.png" alt="Logo de Edutask" width="500">
</p>


</details>

<details>
<summary><strong> Arquitectura del sistema</strong></summary>
  
  | Componente del sistema            | Tecnología / Framework                              | Versión          | Puerto                 | Descripción de uso o requisitos                                                                 | Documentación / Info |
|----------------------------------|------------------------------------------------------|------------------|------------------------|-------------------------------------------------------------------------------------------------|-----------------------|
| **Hardware**                      | VPS (4 vCPU, 8GB RAM, 200GB SSD)                    | —                | —                      | Recursos necesarios para alojar backend, base de datos y servidor web de Edutask.               | https://digitalocean.com |
| **Sistema operativo**            | Ubuntu Server (libre)                               | 22.04 LTS        | —                      | SO libre y estable para servidores web. Corre Node.js, Nginx y servicios backend.               | https://ubuntu.com |
| **Interfaz de usuario (Frontend)** | HTML5, CSS3, JavaScript, React.js                    | —                | 3000 (desarrollo)      | Estructura visual del sistema: login, panel, tareas, configuración.                             | https://react.dev |
| **Lógica de negocio (Backend)** | Node.js + Express.js                                 | Node 18 / Exp 4  | 4000                   | Procesa login, usuarios, tareas, cursos; maneja roles y peticiones API.                         | https://expressjs.com |
| **Servidor web**                 | Nginx                                                | 1.24 (Ubuntu)    | 80 / 443               | Publica el frontend y actúa como reverse proxy hacia el backend.                                | https://nginx.org |
| **Base de datos**                | MySQL                                               | 8.0              | 3306                   | Guarda usuarios, roles, cursos, tareas, entregas y calificaciones.                               | https://dev.mysql.com/doc |
| **Sistema gestor de BD**        | phpMyAdmin                                           | 5.x              | 8080 / 80              | Administración visual: creación de tablas, consultas, backups y usuarios.                       | https://phpmyadmin.net |
| **Servicios de APIs**           | API REST                                            | —                | 4000 (backend)         | Comunicación entre frontend y backend: login, registro, tareas, entregas, cursos.               | https://restfulapi.net |

</details>
</details>

<details>
<summary><strong> Objetivos</strong></summary>
Esto son los objetivos de Edutask para crear su página web para que todo funcione correctamente junto a sus plazos aproximados y el estado de la tarea:

| ID  | Prioridad | Objetivo (Requisito)                       | Funcionalidad                                                  | Disparador                                   | Fecha Entrega | Estado    |
|-----|-----------|---------------------------------------------|----------------------------------------------------------------|-----------------------------------------------|---------------|-----------|
| ID0 | Alta     | Registrar usuarios.                         | Sistema de registro y login guardando datos individuales.      | Página "Iniciar sesión" / botón "Crear cuenta" | 20/02/2026    | Pendiente |
| ID1 | Alta      | Permitir el acceso a la página principal.   | Mostrar panel principal con tarjetas de asignaturas.           | Inicio de sesión correcto.                    | 27/02/2026    | Pendiente |
| ID2 | Alta      | Gestión de tareas para estudiantes.         | Lista de tareas con estados (pendiente, entregado).            | Clic en la sección "Tareas".                  | 05/03/2026    | Pendiente |
| ID3 | Alta      | Permitir entrega de tareas online.          | Subida de archivos o texto desde la plataforma.                | Clic en "Entregar tarea".                     | 08/03/2026    | Pendiente |
| ID4 | Media     | Mostrar tareas pendientes con prioridad.    | Pantalla “Pendientes” con tarjetas y barra de progreso.        | Usuario entra en “Pendientes”.                | 12/03/2026    | Pendiente |
| ID5 | Media     | Creación de tareas (solo profesores).       | Formulario con título, fecha límite y descripción.             | Clic en “Crear tarea”.                        | 15/03/2026    | Pendiente |
| ID6 | Baja      | Mostrar calendario académico.               | Calendario con entregas y exámenes.                           | Clic en "Calendario".                         | 20/03/2026    | Pendiente |
| ID7 | Media      | Sistema de insignias motivacionales.        | Insignias automáticas según progreso.                         | Entrega o finalización de tareas.             | 01/04/2026    | Pendiente |
| ID8 | Media     | Asistente / Tutor inteligente.              | Consejos personalizados de hábitos y prioridades.              | Sección “Profesor Inteligente”.               | 10/04/2026    | Pendiente |
| ID9 | Media      | Configuración de usuario.                   | Editar nombre, contraseña, foto y preferencias.                | Clic en "Configuración".                      | 14/04/2026    | Pendiente |

</details>


<details>
<summary><strong> Arquitectura del sistema</strong></summary>
Esto es el hardware y software que vamos a utilizar para crear y probar nuestro proyecto Edutask. Se compone de varios dispositivos con sus respectivos usos:
  
  | Componente del sistema            | Tecnología / Framework                              | Versión          | Puerto                 | Descripción de uso o requisitos                                                                 | Documentación / Info |
|----------------------------------|------------------------------------------------------|------------------|------------------------|-------------------------------------------------------------------------------------------------|-----------------------|
| **Hardware**                      | VPS (4 vCPU, 8GB RAM, 200GB SSD)                    | —                | —                      | Recursos necesarios para alojar backend, base de datos y servidor web de Edutask.               | https://digitalocean.com |
| **Sistema operativo**            | Ubuntu Server (libre)                               | 22.04 LTS        | —                      | SO libre y estable para servidores web. Corre Node.js, Nginx y servicios backend.               | https://ubuntu.com |
| **Interfaz de usuario (Frontend)** | HTML5, CSS3, JavaScript, React.js                    | —                | 3000 (desarrollo)      | Estructura visual del sistema: login, panel, tareas, configuración.                             | https://react.dev |
| **Lógica de negocio (Backend)** | Node.js + Express.js                                 | Node 18 / Exp 4  | 4000                   | Procesa login, usuarios, tareas, cursos; maneja roles y peticiones API.                         | https://expressjs.com |
| **Servidor web**                 | Nginx                                                | 1.24 (Ubuntu)    | 80 / 443               | Publica el frontend y actúa como reverse proxy hacia el backend.                                | https://nginx.org |
| **Base de datos**                | MySQL                                               | 8.0              | 3306                   | Guarda usuarios, roles, cursos, tareas, entregas y calificaciones.                               | https://dev.mysql.com/doc |
| **Sistema gestor de BD**        | phpMyAdmin                                           | 5.x              | 8080 / 80              | Administración visual: creación de tablas, consultas, backups y usuarios.                       | https://phpmyadmin.net |
| **Servicios de APIs**           | API REST                                            | —                | 4000 (backend)         | Comunicación entre frontend y backend: login, registro, tareas, entregas, cursos.               | https://restfulapi.net |


</details>
<details>
<summary><strong> Tecnologías implementadas y servicios</strong></summary>
  
### **1. Servidor WEB**
#### **HTML5 Y CSS3**

**HTML5** estructura el contenido.
**CSS3** define estilos, colores y diseño.
Son tecnologías universales, compatibles con todos los navegadores y esenciales para un proyecto web moderno.
#### **PHP**

PHP permite crear páginas dinámicas, conectarse con la base de datos y gestionar el login, usuarios, clases, tareas, etc.
Es ideal para proyectos educativos por su simplicidad y compatibilidad con Apache y MySQL.

#### **Apache**
Es uno de los servidores web más usados del mundo:Lo usamos porque es compatible con PHP, también es bastante estable.
Por estas razones es perfecto para alojar una web como Edutask.

#### **Cloudflare**

Nuestro dominio es “edutask.tallerdekirby.es”, un derivado de “tallerdekirby.es” 
Esta web está gestionada por cloudflare para proporcionar seguridad, rendimiento y configuración avanzada de DNS.

### **2. Base de datos**
#### **MySQL**
Es una base de datos perfecta para nuestro proyecto Edutask, ya que nos permite guardar usuarios, clases, tareas, los estados de estas, notas y preferencias.

#### **phpMyAdmin**
Ofrece un panel visual para administrar la base de datos sin tener que usar comandos. Con este programa podremos crear tablas, exportar backup o ver errores de una manera sencilla y visual.

### **3. Almacenamiento y Backup**
#### **TrueNAS**
TrueNAS es un sistema operativo especializado para almacenamiento en red. Lo usamos porque dentro de él se pueden gestionar copias de seguridad de una manera intuitiva.

#### **Rsync**
Rsync se usa para automatizar copias de seguridad y sincronizar directorios entre servidores. Las ventajas que ofrece son por ejemplo que es seguro y rápido, copia datos para copias de seguridad incrementales y porque tendremos un backup. Perfecto para evitar perder datos del proyecto.

### **4. DNS Interno / Filtrado**

#### **Pi-hole**
Pi-hole actúa como servidor DNS interno. Otras funciones que nos vienen perfectas para el proyecto es que filtra la publicidad, acelera la navegación, también puede gestionar dominios locales y facilita el acceso a los servidores.

### **5. Seguridad y Red**
#### **pfSense**
pfSense es un firewall profesional open-source. Puede proteger los servicios internos, controla el tráfico y aplica reglas de seguridad. Sin pfSense, los servidores quedarían expuestos y sin control.

#### **DHCP Server**
Asigna automáticamente las IP internas (por ejemplo 192.168.135.20).
Esto evita configuraciones manuales y errores.






</details>
<details>
<summary><strong> Listado de Tareas</strong></summary>
  
### **TareaID0  Registrar usuarios**

- Descripción: Crear el sistema para que los usuarios puedan registrarse e iniciar sesión.
- Cómo se hace: Se hacen formularios de registro y login. El backend guarda los datos en la base de datos y valida que el usuario exista.

 ### **TareaID1 Acceso a la página principal**

- Descripción: Mostrar la página principal con las asignaturas después de iniciar sesión.
- Cómo se hace: El backend revisa las credenciales y envía al usuario al panel principal donde React muestra las asignaturas.

### **Tarea ID2  Gestión de tareas para estudiantes**

- Descripción: Crear una lista donde el estudiante vea sus tareas con su estado.
- Cómo se hace: El frontend pide a la API las tareas y las muestra organizadas por estado (pendiente, entregado).

 ### **Tarea ID3  Entrega de tareas online**

- Descripción: Permitir que el estudiante suba un archivo o escriba un texto para entregar su tarea.
- Cómo se hace: Se crea un formulario con opción de subir archivos y una ruta en la API para guardar la entrega.

### **Tarea ID4  Mostrar tareas pendientes con prioridad**

- Descripción: Hacer una pantalla que muestre las tareas pendientes resaltadas según prioridad.
- Cómo se hace: El frontend ordena las tareas y las muestra con tarjetas, colores o barras para que se vean las más importantes.

### **Tarea ID5  Creación de tareas (profesores)**

- Descripción: Crear un formulario para que los profesores puedan añadir nuevas tareas.
- Cómo se hace: Se diseña un formulario con título, fecha límite y descripción, y el backend guarda la tarea mediante la API.

### **Tarea ID6  Calendario académico**
- Descripción: Mostrar un calendario con las fechas importantes.
- Cómo se hace: Se usa un componente de calendario y se cargan las fechas desde la base de datos usando la API.

### **Tarea ID7  Sistema de insignias motivacionales**

- Descripción: Dar insignias automáticamente cuando los estudiantes cumplen  objetivos.
- Cómo se hace: Se crean reglas simples en el backend que revisan el progreso del estudiante y asignan la insignia correspondiente.

 ### **Tarea ID8  Tutor inteligente**

- Descripción: Dar consejos personalizados según las tareas y el rendimiento del estudiante.
- Cómo se hace: El sistema revisa los datos del usuario (tareas, atrasos, hábitos) y genera recomendaciones.

### **Tarea ID9  Configuración de usuario**

- Descripción: Permitir que el usuario modifique sus datos personales.
- Cómo se hace: Se crea una sección de ajustes con formularios que actualizan la información mediante la API.

### **Tarea ID10  Configurar Cloudflare para el dominio**

- Descripción: Enlazar el dominio edutask.tallerdekirby.es con Cloudflare.
- Cómo se hace: Se añade el dominio a Cloudflare, se cambian los DNS del registrador y se crean los registros A/AAAA apuntando a la IP pública (77.231.11.106).

### **Tarea ID11  Abrir y redirigir tráfico desde la IP pública**

- Descripción: Permitir que el tráfico desde Internet llegue a la red del centro.
- Cómo se hace:Se configuran reglas de firewall para aceptar tráfico entrante desde 77.231.11.106 y dirigirlo hacia el pfSens.

### **Tarea ID12  Configurar pfSense como firewall principal**

- Descripción: pfSense gestionará la red local y el filtrado de tráfico.
- Cómo se hace:Se definen reglas de firewall para cada servidor (WEB, DB, TRUENAS, DNS) y se activan las interfaces.

### **Tarea ID13  Configurar DHCP**

- Descripción: Asignar IPs automáticas dentro del rango 192.168.135.X/24.
- Cómo se hace: En pfSense se habilita DHCP, se define el rango y se reservan IPs fijas para cada servidor.

### **Tarea ID14  Configurar el servidor WEB**

- Descripción: Levantar un servidor Apache/PHP para alojar la web de Edutask.
- Cómo se hace: Se instala Apache, PHP y las dependencias. Se sube el frontend y backend (si corresponde) y se habilita el acceso por HTTP/HTTPS.

### **Tarea ID15  Configurar el servidor DB con MySQL**

- Descripción: Instalar MySQL y phpMyAdmin para gestionar la base de datos.
- Cómo se hace: Se instala MySQL, se crean usuarios, permisos y la base de datos de Edutask. Luego se habilita phpMyAdmin para gestión visual.

### **Tarea ID16 Configurar TRUENAS para copias y almacenamiento**

- Descripción: Usar TRUENAS para sincronización y backups mediante rsync.
- Cómo se hace:Se instala TRUENAS, se crean datasets y se activan tareas rsync para copiar los datos de la web y base de datos.

### **Tarea ID17  Configurar DNS interno con Pi-Hole**

- Descripción: Pi-Hole gestionará DNS local y filtrado básico.
- Cómo se hace: Se instala Pi-Hole, se asigna una IP fija y se configura como servidor DNS para toda la red.






</details>
</details>

---
<details>
  <summary><h2> Red</h2></summary>
  
  <details>
<summary><strong> Diagrama de la red</strong></summary>
      - Este es nuestro diagrama de red de Edutask, donde se muestra cómo se organiza toda la infraestructura del proyecto. Desde la entrada del dominio a través de Cloudflare hasta la red interna gestionada por pfSense, se distribuyen los diferentes servicios importantes como el servidor web, la base de datos, el sistema de almacenamiento con TrueNAS y el servidor DNS con Pi-hole.
    <p align="center">
<img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-11-11%20104109.png" alt="Diagrama de la red" width="700">
  </p>

  - Este es nuestro diagrama de red de Edutask, donde se muestra cómo se organiza toda la infraestructura del proyecto. Desde la entrada del dominio a través de Cloudflare hasta la red interna gestionada por pfSense, se distribuyen los diferentes servicios importantes como el servidor web, la base de datos, el sistema de almacenamiento con TrueNAS y el servidor DNS con Pi-hole.
</details>


</details>

---
<details>
  <summary><h2> Organización</h2></summary>
  
#### Diagrama de Gantt:
  
  <p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Diagrama%20de%20gantt.png" alt="Logo de Edutask" width="700">
</p>
  https://docs.google.com/spreadsheets/d/11hAp5gZndAwbAvoBHB6q7AiIfCZhdHiujqfQJX5VaoE/edit?usp=sharing
  
</details>

---
<details>
  <summary><h2> Web</h2></summary>

<details>
<summary><strong> Mockup</strong></summary>
    



 
 
La página está organizada de forma clara y ordenada el color principal de la web son colores claros como el blanco y el azul , en nuestra web la tipografia es open sans. Las clases están puestas en cuadros distribuidos en dos filas y dos columnas, todo sea fácil de encontrar.
A la izquierda hay una barra fija con iconos para moverse por la página (inicio, tareas, calendario, etc.). La parte del medio es para lo más importante que son  las clases que es lo que se tiene que ver mas.
Cada asignatura tiene un color diferente (azul, naranja, rojo y verde), lo que ayuda a reconocerlas rápido y hace que la página se vea más clara. El fondo blanco hace que los colores resalten más.
La letra es sencilla y moderna, hace que se vea ordenado. La página tiene botones como “Entrar” y “Crear Clase” que son fáciles de ver y usar. También hay iconos en la barra lateral que ayudan a saber para qué sirve cada sección sin tener que leer mucho. Cada clase tiene una estrellita para marcarla como favorita, lo que añade una función extra sin complicar el diseño.


  
  [Mockup](https://www.canva.com/design/DAG1F7t7cgo/vUko967jFhBP_onj2v1dsA/edit?utm_content=DAG1F7t7cgo&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
  
<p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-11-05%20091436.png" alt="Página Inicio" width="700">
</p>
  - Esta es la pantalla de inicio de nuestra web. En la parte superior se encuentra nuestro logotipo, y justo debajo aparece nuestro eslogan  con tipografía Open Sans y color de letra gris.
Debajo del eslogan hay un recuadro para iniciar sesión, donde el usuario debe introducir su correo electrónico y contraseña. También se incluye una opción para recuperar la contraseña, cuya pantalla explicaremos a continuación.
Finalmente, debajo de todo, hay una opción para seleccionar el rol de estudiante o profesor, que el usuario deberá marcar antes de continuar.

<p align="center">
<img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-11-05%20094302.png" alt="Página recuperar contraseña" width="700">
  </p>
  -En esta pantalla, es para aquellos usuarios que quieran acceder a nuestra web y no se acuerden de su contraseña. En esta página la podrán recuperar. En la parte de arriba podemos ver que aparece el logo en grande y, como antes, debajo nuestro eslogan de color gris. Luego hay un recuadro que pone “Recuperar contraseña” en azul con tipografía Open Sans. Debajo de eso te pide que pongas tu correo electrónico para que luego haya un botón que pone “Enviar código”, que también está en color azul pero más claro. Esto hace que te llegue un código al correo que has puesto. Después hay un texto que te dice que introduzcas el código que te han enviado, y está en color gris con la tipografía Open Sans. Después de este paso, dice que pongas tu nueva contraseña y luego que la vuelvas a introducir para ya poder iniciar sesión con el botón de la parte de abajo, que está en color azul y la letra de dentro en color blanco para que resalte.

 <p align="center">
<img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-11-05%20100944.png" alt="Página Principal" width="700">
  </p> 
  - Esta es la página principal que ve el usuario después de iniciar sesión. En el centro aparecen las clases organizadas en cuadrados, cada una con un color diferente para reconocerlas rápidamente. Las tarjetas muestran el nombre de la asignatura, el curso y un botón   para acceder. También incluyen una estrella para marcar clases como favoritas. A la izquierda aparece una barra lateral fija con los apartados más importantes: inicio, tareas, calendario, insignias y configuración. Esta barra permite moverse por la web de forma fácil y directa.

 <p align="center">
<img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-11-05%20102754.png" alt="Página Tareas" width="700">
  </p> 
- En esta página se muestran todas las tareas que el estudiante tiene en las distintas clases. La parte superior tiene un buscador y botones de filtro (todas, pendientes, entregadas…), y hace mas facil encontrar una actividad concreta.
 Las tareas aparecen en forma de lista, con columnas que indican el nombre de la tarea, la asignatura, la fecha límite y el estado (pendiente, entregado o retrasado). Esto ayuda a organizarse mejor y ver rápidamente qué tareas son más urgentes. Como tambien se puede ver hay un boton para crear tareas por si lo necesitas..
</details>

  <details>
    <summary><strong> Mapa de navegabilidad</strong></summary>






El mapa de navegabilidad muestra cómo se organiza la estructura de la página web Edutask y los caminos que puede seguir el usuario dentro de ella. Desde la pantalla inicial de inicio de sesión, el usuario puede acceder a las distintas secciones según su rol (profesor o estudiante).

En el centro del mapa se encuentra la página principal, donde se muestran las clases, y desde ahí se puede acceder fácilmente al resto de apartados: Tareas, Calendario, Insignias, Profesor Inteligente y Configuración.
Cada flecha del mapa indica las conexiones entre pantallas y cómo se pasa de una función a otra, lo que ayuda a entender el recorrido completo dentro de la web.

Gracias a esta estructura, la navegación resulta clara, intuitiva y fluida. Tanto profesores como estudiantes pueden orientarse sin dificultad, accediendo de forma rápida a sus clases, actividades y herramientas principales.

[Mapa de navegación](https://www.figma.com/design/bCnEgSv1KONrkjPDBV6TZc/Mapa-navegaci%C3%B3n-Edutask?node-id=0-1&t=nvBzSE5BChtoyJh0-1)
</details>
</details>




---
<details>
  
  <summary><h2> Conclusiones</h2></summary>
</details>

---
<details>
  
  <summary><h2> Bibliografía</h2></summary>
</details>

---
<details>
  
  <summary><h2> Arduino</h2></summary>
  
<p align="center">
<img src="images.jpg" alt="Mi banner" width="800" height="200">
  </p>
  
  **2.1 ¿Qué es Arduino?**
- Arduino es una placa electrónica con un microcontrolador que se puede programar para controlar luces motores sensores y otros dispositivos se utiliza junto con un programa en la computadora para escribir instrucciones y automatizar tareas siendo útil para aprender electrónica y crear proyectos interactivos

**2.2 ¿Cuáles son sus características más importantes?**
- Las características más importantes de Arduino son: tiene un microcontrolador programable. Permite leer sensores y controlar luces y motores. Es fácil de programar y usa un lenguaje sencillo basado en C. Tiene hardware abierto. Se puede elegir entre varios modelos como Uno, Nano o Mega. 

**2.3 ¿Cuál es el origen de Arduino?**
- Arduino fue creado en 2005 en el Instituto IVREA, en Italia, como una herramienta para estudiantes de diseño sin conocimientos técnicos en electrónica y programación. Sus fundadores son: Massimo Banzi, David Cuartielles, Tom Igoe, Gianluca Martino y David Mellis desarrollaron Arduino como una plataforma de hardware libre y de bajo costo, con el objetivo de facilitar la creación de proyectos interactivos.
El nombre "Arduino" proviene de un bar en Ivrea frecuentado por los fundadores, que también toma el nombre de un rey italiano.

**2.4 ¿Qué modelos de Arduino hay? Haz una tabla donde especifiques para cada modelo: microcontrolador, voltaje, pines digitales, entradas analógicas, memoria, reloj.**
| Modelo               | Microcontrolador             | Voltaje | Pines digitales | Entradas analógicas | Memoria Flash | Frecuencia |
|----------------------|------------------------------|---------|------------------|-----------------------|---------------|------------|
| Arduino Uno R3       | ATmega328P                   | 5V      | 14               | 6                     | 32 KB         | 16 MHz     |
| Arduino Mega 2560    | ATmega2560                   | 5V      | 54               | 16                    | 256 KB        | 16 MHz     |
| Arduino Nano         | ATmega328P                   | 5V      | 22               | 8                     | 32 KB         | 16 MHz     |
| Arduino Leonardo     | ATmega32u4                   | 5V      | 20               | 12                    | 32 KB         | 16 MHz     |
| Arduino Due          | AT91SAM3X8E (ARM Cortex-M3)  | 3.3V    | 54               | 12                    | 512 KB        | 84 MHz     |
| Arduino Micro        | ATmega32u4                   | 5V      | 20               | 12                    | 32 KB         | 16 MHz     |
| Arduino MKR1000      | SAMD21 Cortex-M0+            | 3.3V    | 8                | 7                     | 256 KB        | 48 MHz     |
| Arduino Nano 33 IoT  | SAMD21 Cortex-M0+            | 3.3V    | 14               | 8                     | 256 KB        | 48 MHz     |


**2.5 ¿Para qué sirve un Arduino?**

- La principal utilidad que se le da a un arduino es la automatización que esto sirve para controlar las luces por ejemplo de una casa, sensores, motores etc.. que esto puede hacer que podamos abrir una puerta de un parking de un garaje con un mando pero también se les puede dar otras funciones como para el aprendizaje básico de de la programación o en un nivel mas avanzado tambien lo podriamos utilizar en el área de IoT que lo que podemos hacer con esto es recoger los datos de los sensores de los arduino y mandarlos a la nube.
En resumen esta tecnología cada vez está creciendo más gracias a la integración que está teniendo en diferentes ámbitos ya que si nos paramos a pensar estamos rodeados de esta tecnología.

<p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-12-05%20130922.png" alt="Logo de Edutask" width="300">
</p>



**2.6 ¿Qué lenguaje utiliza?**

- Arduino usa un lenguaje C/C++, pero adaptado para que sea más fácil de entender y usar ya que esto muchas veces se utiliza para el aprendizaje o para gente que está empezando a programar. Se usa principalmente en el entorno llamado Arduino IDE, donde escribes y juntas la información envías el código a la placa.
Este lenguaje solo permite controlar un par de objetos básicos como: Luces Leds,Rgb, Motores servos o DC,Sensores de temperatura,humedad o ultrasonido, Pantallas Lcd o Oled y por ultimo para comunicaciones como Bluetooth, Wi-fi etc….

**2.7 ¿Qué es el Arduino IDE?**

- Es el programa que usas en el ordenador para escribir, compilar y cargar código en una placa Arduino y este software es totalmente gratuito.

<p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-12-05%20131216.png" alt="Logo de Edutask" width="300">
</p>

<details>
  
  <summary><h2> Blink y Semáforo</h2></summary>

**Blink**

**(1) Objetivo de la práctica**

En una placa de arduino ESP32 tenemos que conseguir que un led parpadee constantemente .

**(2) Material y explicacion de cada componente**
- Un led
- Dos Jumpers
- Una Resistencia
  
**(3) Esquema del circuito como se muestra mas abajo**
  <p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-12-12%20124527.png" alt="Logo de Edutask" width="300">

**(4) How To + Codigo explicado: uso de las variables, funciones y demas componentes del codigo**
  <p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-12-12%20131122.png" alt="Logo de Edutask" width="300">

**(5) Video de la practica**

[Ver video](IMG_9943.MOV)


**(6) Imagen para la entrada del blog o proyecto**
  <p align="center">
  <img src="https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/IMG_9942.jpeg" alt="Logo de Edutask" width="300">


**¿Qué son el void setup() and void loop()?**
- void setup(): Se ejecuta una sola vez cuando tu Arduino se ENCIENDE o se reinicia. Se usa para configurar las salidas y las entradas, inicializar variables o iniciar comunicación como por ejemplo el serial o los sensores.


- void loop(): Este bloque se ejecuta repetidamente y sin fin mientras Arduino tenga energía. En loop() pones el código que quieres que repita continuamente, como parpadear un LED o leer sensores.


**¿Qué quiere decir la línea: #define LED_BUITIN 2 ?**
- La línea significa que se crea una constante llamada LED_BUILTIN y que cada vez que aparezca ese nombre en el código, el compilador lo reemplazará por el número 2 antes de compilar. Sirve para indicar que el LED integrado de la placa está conectado al pin 2, a si que en vez de escribir el número directamente en el programa, se usa un nombre más claro y fácil de entender.



**¿Qué quiere decir la línea delay(1000); ?**

- Delay(1000):significa que el programa se detiene durante 1000 milisegundos que es lo mismo que  1 segundo, antes de continuar con la siguiente instrucción.


**Semáforo**
**(1) Objetivo de la práctica**
- En una placa de arduino ESP32 tenemos que conseguir tres leds de color verde,amarillo,rojo se encinedan a timepos diferentes recrando un semaforo.

**(2) Material y explicación de cada componente**
- 3 Jumpers
- 3 Resistencias
- 3 Leds

**(3) Esquema del circuito como se muestra mas abajo**

  <p align="center">
  <img src="Captura de pantalla 2025-12-12 135336.png" alt="Logo de Edutask" width="300">


</p>
</details>


  


  




  




  



  




