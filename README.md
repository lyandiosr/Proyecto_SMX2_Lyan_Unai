  ![Edutask](https://github.com/lyandiosr/Proyecto_SMX2_Lyan_Unai/blob/main/Captura%20de%20pantalla%202025-10-21%20100802.png)


<details>
  <summary><h2> Introducció</h2></summary>
  
Nuestro proyecto, llamado Edutask, es una plataforma web educativa hecha para que profesores y estudiantes puedan organizar sus actividades. No es solo un lugar para subir tareas, sino que también tiene herramientas que motivan, como insignias para que te animes y un tutor inteligente. La idea es mejorar la forma en que se enseña y se aprende. Edutask quiere dejar de ser solo una herramienta local para convertirse en una plataforma innovadora que motive a los estudiantes, ayude a los profesores con su trabajo y sea un ejemplo de aprendizaje digital en varios países. Esta plataforma está pensada principalmente para docentes y alumnos de cualquier nivel educativo.Los módulos que más van a ayudar a nuestro proyecto son aplicaciones web para crear la página web de la empresa y cómo configurarla. También el módulo de seguridad informática para que esta página web sea segura y confiable para los usuarios

</details>

<details>
  <summary><h2> Briefing</h2></summary>
  
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

<details>
  <summary><h2> Arquitectura del software</h2></summary>


  <details>
    <summary><strong> Backend</strong></summary>


  ## 1. Descripción general del proyecto web
  #### **¿De qué trata tu web? Explica brevemente el propósito de tu página web (por ejemplo: tienda online, blog, red social, catálogo, etc.).**
  La página web trata sobre una plataforma educativa que se llama Edutask, diseñada para ayudar a profesores y estudiantes a organizar sus actividades académicas de manera más rápida y clara . Su propósito principal es mejorar la enseñanza y el aprendizaje a través de herramientas como insignias motivacionales y un tutor inteligente y también  permitir la gestión de tareas.

  #### **¿Qué funcionalidades ofrecerá a los usuarios? Lista las principales funciones (ej.: crear cuenta, hacer pedidos, subir fotos, dejar comentarios, etc.).**
  - Crear cuenta y perfil personalizado (para profesores y estudiantes).
  - Subir y gestionar tareas (crear y entregar y puntuar las actividades).
  - Organizar actividades.
  - Sistema de insignias y recompensas para motivar a los estudiantes.
  - Tutor inteligente para guiar y ayudar a los  estudiantes.
  - Interacción entre usuarios (comentarios y mensajes,).
  - Seguridad de la información (autenticación, privacidad de datos).
  - Panel de control para los profesores (seguimiento del progreso, estadísticas de los alumnos).

  ## 2. Identificación de entidades principales
  #### **¿Qué elementos importantes hay en tu web que necesitan almacenarse?**
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
#### ¿Qué partes te han resultado más difíciles de pensar?
-Nos ha costado más el apartado de Identificación de entidades principales porque aún no tenemos del todo claro cómo será el proyecto y nos ha costado pensar todo esa parte, 
también en el apartado de descripción general del proyecto web por lo que hemos dicho antes no tenemos del todo claro dónde queremos llegar con el proyecto tenemos algunas dudas aun con eso. 

#### ¿Qué no tienes claro sobre la información que hay que guardar?
-La verdad que lo tenemos todo bastante claro sobre esto .
</details>
</details>

<details>
  <summary><h2> Web</h2></summary>

  <details>
    <summary><strong> Mockup</strong></summary>

  #### 1. Equilibrio del diseño, colores, estructura.
  - La página está organizada de forma clara y ordenada. Las clases están puestas en cuadros distribuidos en dos filas y dos columnas, todo sea fácil de encontrar.
     A la izquierda hay una barra fija con iconos para moverse por la página (inicio, tareas, calendario, etc.). La parte del medio es para lo más importante que son  las clases que es lo que se tiene que ver mas.

#### 2. Colores y tipografía.
- Cada asignatura tiene un color diferente (azul, naranja, rojo y verde), lo que ayuda a reconocerlas rápido y hace que la página se vea más clara. El fondo blanco hace que los colores resalten más.
   La letra es sencilla y moderna, hace que se vea ordenado.

#### 3. Componentes de interfaz (botones, enlaces...).
- La página tiene botones como “Entrar” y “Crear Clase” que son fáciles de ver y usar. También hay iconos en la barra lateral que ayudan a saber para qué sirve cada sección sin tener que leer mucho. Cada clase tiene una estrellita para marcarla como favorita, lo que      añade una función extra sin complicar el diseño.
  [Mockup](https://www.canva.com/design/DAG1F7t7cgo/vUko967jFhBP_onj2v1dsA/edit?utm_content=DAG1F7t7cgo&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
</details>

  <details>
    <summary><strong> Mapa de navegabilidad</strong></summary>
    
# Mapa Navegación

[Mapa de navegación](https://www.figma.com/design/bCnEgSv1KONrkjPDBV6TZc/Mapa-navegaci%C3%B3n-Edutask?node-id=0-1&t=nvBzSE5BChtoyJh0-1)
</details>






  


  




  




  



  




