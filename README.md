# Capítulo V: Introducción

## 5.1. Software Configuration Management.
### 5.1.1. Software Development Environment Configuration.
El entorno de desarrollo fue configurado utilizando herramientas ampliamente adoptadas en proyectos open source.

### Herramientas por tipo de actividad

| Actividad                         | Herramienta(s) utilizada(s)                    | Tipo     | Enlace de referencia                                                                 |
|-----------------------------------|------------------------------------------------|----------|----------------------------------------------------------------------------------------|
| Project Management                | Trello, GitHub Projects                        | SaaS     | [Trello](https://trello.com) / [GitHub Projects](https://github.com)                 |
| Requirements Management           | Google Docs, Google Sheets                     | SaaS     | [Google Docs](https://docs.google.com)                                               |
| Product UX/UI Design              | Figma                                          | SaaS     | [Figma](https://figma.com)                                                           |
| Software Development              | WebStorm, Visual Studio Code, Node.js, Git, Angular    | Local    | [WebStorm](https://www.jetbrains.com/webstorm/) / [VS Code](https://code.visualstudio.com) / [Node.js](https://nodejs.org) / [Git](https://git-scm.com) / [Angular](https://angular.dev)|
| Software Deployment               | Vercel, Netlify, Railway, Render               | SaaS     | [Vercel](https://vercel.com) / [Netlify](https://www.netlify.com) / [Railway](https://railway.app) |
| Software Documentation            | Google Docs, Markdown, Swagger, Structurizer   | SaaS/Local| [Google Docs](https://docs.google.com) / [Swagger](https://swagger.io)               |

### 5.1.2. Source Code Management.
Se utilizó Git como sistema de control de versiones y GitHub como plataforma de hospedaje. El proyecto fue dividido en múltiples repositorios:

Landing Page: https://github.com/flow-sense/landing (link de ejemplo)

Web Services: https://github.com/flow-sense/api (link de ejemplo)

Frontend Web App: https://github.com/flow-sense/frontend (link de ejemplo)

Se adoptó el workflow GitFlow, basado en el modelo de Vincent Driessen (“A successful Git branching model”), para organizar las ramas de trabajo. Este flujo permite una separación clara entre las versiones estables, los desarrollos activos y las correcciones urgentes. Las ramas empleadas son:

- main: contiene la versión estable y liberada del producto. Cada merge a esta rama representa una versión deployada.

- develop: rama principal de desarrollo donde se integran los feature branches.

- feature/<nombre>: para cada nueva funcionalidad, se crea una rama individual. Ejemplo: feature/login-auth, feature/task-tracking.

- release/<version>: rama temporal que permite realizar pruebas y ajustes antes de pasar a producción. Ejemplo: release/v1.1.0.

- hotfix/<descripcion>: ramas para corregir errores críticos encontrados en producción. Ejemplo: hotfix/fix-null-user.

Cada release se nombra siguiendo Semantic Versioning 2.0.0, utilizando el formato MAJOR.MINOR.PATCH:

- Cambios incompatibles: 2.0.0

- Nuevas funcionalidades compatibles: 2.1.0

- Correcciones de bugs: 2.1.1

Se usaron etiquetas (tags) en Git para marcar los releases formales: v1.0.0, v1.1.0-beta, etc.

Además, para mantener un historial claro y legible en el repositorio, se aplicó la convención [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/), con el siguiente formato:

| **<'tipo'>(alcance): descripcion breve** |
|------------------------------------------|

Donde el <"tipo"> puede ser: feat, fix, docs, style, refactor, test, chore, entre otros.

**Ejemplos de commits:**

- feat(auth): implement Google login integration

- fix(api): prevent crash on empty request body

- refactor(ui): simplify dashboard component hierarchy

### 5.1.3. Source Code Style Guide & Conventions

Para mantener la consistencia del código fuente se adoptaron las siguientes guías y convenciones:

- **HTML/CSS**: [W3 HTML Style Guide](https://www.w3schools.com/html/html5_syntax.asp), [Google HTML/CSS Guide](https://google.github.io/styleguide/htmlcssguide.html)
- **JavaScript/TypeScript**: [Google TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html), ESLint + Prettier
- **Java**: [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html), aplicado si se emplea Spring Boot
- **Especificaciones BDD (si aplica)**: [Gherkin Syntax](https://cucumber.io/docs/gherkin/)

Además, se adoptaron las siguientes prácticas:
- Uso del idioma inglés para nombrar funciones, variables, clases y archivos.
- Aplicación de principios SOLID y clean code.
- Separación modular del código, fomentando la reutilización de componentes y funciones puras.
 
### 5.1.4. Software Deployment Configuration

El proceso de despliegue fue automatizado usando plataformas como **Vercel**, **Netlify** o **Railway**. El frontend y la landing page fueron desplegados directamente desde los repositorios de GitHub mediante integración continua (CI). Para el backend se configuró un entorno en Railway o Render.

#### Pasos generales de despliegue:

1. Un push a las ramas `main` o `release/*` activa un proceso de despliegue automático.
2. Se incluyeron archivos de configuración según la plataforma:
   - `vercel.json` para Vercel
   - `netlify.toml` para Netlify
   - `Dockerfile` en caso de uso de contenedores
3. Las variables de entorno fueron configuradas directamente en la plataforma correspondiente (por ejemplo, claves de API, bases de datos, credenciales).
4. Las APIs fueron desplegadas y expuestas mediante HTTPS, y documentadas utilizando herramientas como **Swagger** o **Postman**.

## 5.2. Landing Page, Services & Applications Implementation.

### 5.2.1. Sprint 1

Durante esta etapa se priorizaron funcionalidades esenciales que permiten cubrir el flujo base tanto para usuarios del segmento freelancer como para visitantes de la Landing Page. El sprint tuvo una duración estimada de una semana y se trabajó bajo un enfoque ágil tipo Scrum.

El equipo dedicó especial atención a la identificación del Sprint Goal, siguiendo el enfoque propuesto por Scrum.org, basado en outcome, impact, customer y event. El objetivo se redactó con un enfoque en negocio y usuario, en formato SMART:

Sprint 1 Goal:

`Our focus is on delivering a functional and user-friendly landing page. We believe it delivers immediate understanding and engagement to new users. This will be confirmed when visitors can easily navigate, explore plans, read testimonials, and switch between freelancer and company information.`

Los objetivos principales del Sprint 1 fueron:

Implementar navegación fluida y accesible entre secciones de la Landing Page.

Desarrollar la función de alternar información entre empresas y freelancers.

Desplegar la sección de testimonios y tecnologías utilizadas.

Optimizar el diseño y estructura de la página.

Estas decisiones se basaron en las siguientes User Stories priorizadas:

E8-US22 Navegación fluida entre secciones

E8-US23 Alternar entre información para clientes

E8-US24 Comparativa de planes

E8-US25 Mostrar tecnologías utilizadas

E8-US26 Ver testimonios de otros usuarios

E8-US27 Cambiar información según segmento

#### 5.2.1.1. Sprint Planning 1.

### Sprint Planning Meeting Summary

| Elemento                             | Detalle                                                                                                                 |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| **Sprint #**                         | Sprint 1                                                                                                                |
| **Sprint Planning Background**       | Inicio de desarrollo de la Landing Page y funcionalidades clave                                                         |
| **Date**                             | 2025-04-18                                                                                                              |
| **Time**                             | 05:00 PM                                                                                                                |
| **Location**                         | Reunión virtual vía Google Meet                                                                                         |
| **Prepared By**                      | Amir Castro                                                                                                             |
| **Attendees**                        | Pietro Osores, Joaquín, Stephano, Carlos                                                                                |
| **Sprint 0 – Review Summary**        | Se finalizó la planificación general del proyecto y diseño UI inicial.                                                  |
| **Sprint 0 – Retrospective Summary** | Se identificó la necesidad de roles claros y mayor documentación interna.                                               |
| **Sprint 1 – Goal**                  | Tener un MVP funcional de la Landing Page que permita navegación, cambio de información y visualización de testimonios. |
| **Sprint 1 – Velocity**              | 20 Story Points (estimado)                                                                                              |
| **Sprint 1 – Sum of Story Points**   | 20 Story Points         

#### 5.2.1.2. Aspect Leaders and Collaborators.

### Leadership and Collaboration Matrix (LACX)

| Team Member          | GitHub Username | Gestión de Proyectos | Landing Page | Despliegue | IA/Data Analysis |
| -------------------- | --------------- | -------------------- | ------------ | ---------- | ---------------- |
| Pietro \[Apellido]   |  Maximoff19  | L                    | C            | C          | C                |
| Amir \[Apellido]     | \[A COMPLETAR]  | C                    | C            | L          | L                |
| Carlos \[Apellido]   | \[A COMPLETAR]  | C                    | L            | C          | C                |
| Stephano \[Apellido] | \[A COMPLETAR]  | C                    | L            | C          | C                |
| Joaquín \[Apellido]  | \[A COMPLETAR]  | L                    | C            | C          | L                |

> **L**: Leader (responsable del aspecto)  
> **C**: Collaborator (colaborador activo)

#### 5.2.1.3. Sprint Backlog 1.

Durante el Sprint 1, el objetivo principal fue construir una versión funcional de la Landing Page, centrada en proporcionar una experiencia de usuario intuitiva y accesible. Esto incluyó la navegación fluida entre secciones, la posibilidad de alternar entre información para empresas y freelancers, y la visualización de testimonios. El equipo utilizó un tablero Kanban (por ejemplo, Trello) para organizar y seguir el progreso de las tareas, donde cada User Story fue descompuesta en uno o más work-items o tareas técnicas.

### Sprint Backlog - Sprint 1
En esta sección se muestran los tasks que se realizaron en el presente sprint y se adjunta una captura en Trello y el link al tablero.

Link de Trello: [https://trello.com/invite/b/6725085eef376b7a366078a5/ATTI35c5a7b65f9c3eade04684aff95452e5810D9665/backlog]

![image](https://github.com/user-attachments/assets/0296d3ac-00d0-46cd-98eb-961a2b17e848)

| User Story ID | User Story Title                   | Task ID | Work-Item / Task                        | Description                                                    | Estimation (hrs) | Assigned To | Status    |
| ------------- | ---------------------------------- | ------- | --------------------------------------- | -------------------------------------------------------------- | ---------------- | ----------- | --------- |
| E8-US38       | Navegación fluida entre secciones  | TSK-01  | Implementar navegación con anclajes     | Menú que permite navegar entre secciones                       | 4                | Carlos      | Done |
| E8-US39       | Alternar información para clientes | TSK-02  | Configurar botón de alternar            | Cambia contenido entre empresas y freelancers                  | 3                | Amir        | Done    |
| E8-US40       | Comparativa de planes              | TSK-03  | Crear tabla comparativa de planes       | Tabla que muestra diferencias entre planes                     | 3                | Carlos      | Done      |
| E8-US41       | Mostrar tecnologías utilizadas     | TSK-04  | Diseño de sección de tecnologías        | Íconos y descripciones de tecnologías utilizadas               | 2                | Stephano    | Done      |
| E8-US42       | Ver testimonios de otros usuarios  | TSK-05  | Maquetar sección de testimonios         | Testimonios dinámicos y alternables                            | 3                | Joaquín     | Done |
| E8-US43       | Cambiar información según segmento | TSK-06  | Configurar CTA dinámico                 | Botón que cambia entre información para empresas y freelancers | 3                | Pietro        | Done     |

#### 5.2.1.4. Development Evidence for Sprint Review.
Después de finalizar el Sprint 1, hemos logrado implementar algunas de las secciones de nuestra Landing Page, aunque con algunos desperfectos en cuanto a diseño. A continuación, te invitamos a explorar nuestros avances a través de imágenes que muestran el resultado obtenido.

*Seccion de navegacion* : Nos ayudara a redirigirnos a secciones especificas de la lading page y Banner que contendra un boton (Call to Action) que te llevara a registrarte a nuestra aplicación.

![image](https://github.com/user-attachments/assets/6b423628-1a00-458c-99d8-433be0d35a5f)

*Funcionality*: Seccion donde los visitantes de la lading page podrán ver como es que funciona nuestra aplicacion y que les ofrece.

![image](https://github.com/user-attachments/assets/8937f486-207b-4790-b23f-d5b9a0ee6e64)

*Ventajas*: sección de las ventajas para nuestro usuarios

![image](https://github.com/user-attachments/assets/d40476c8-a3bf-4f53-aa01-fcb44e904004)


*Seccion de testimonios*: sección de testimonios

![image](https://github.com/user-attachments/assets/c37b9324-6e02-42fd-acb6-be57e824349f)


*footer*: contenido extra, como telefono,correo y redes para que puedan comunicarse con la empresa devinsons.

![image](https://github.com/user-attachments/assets/8a44b971-2a40-4821-9e2a-190769713a50)


#### 5.2.1.5. Execution Evidence for Sprint Review.

Durante este sprint 1 el equipo se enfocó en el desarrollo de la landing page por lo cual no se requirio pruebas de testing.

#### 5.2.1.6. Services Documentation Evidence for Sprint Review.

En el primer sprint, hemos realizado el diseño, la programación y el despligue de la Landing Page que presentará nuesta apliación web "FlowSenses"

<table> 
  <tr>
    <td> <strong>End Point </strong></td>
    <td align="center"> <strong>Funciones</strong> </td>
  </tr>

  <tr>
    <td> https://1asi0729-2510-4317-g5-flow-senses.github.io/LandingPage/ </td>
    <td> Desplegar Landing Page de FlowSenses</td>
  </tr>
</table>

#### 5.2.1.7. Software Deployment Evidence for Sprint Review.


#### 5.2.1.8. Team Collaboration Insights during Sprint.

![image](https://github.com/user-attachments/assets/d22050d7-56cb-4b38-a9e7-2e27a832051d)

![image](https://github.com/user-attachments/assets/cdee531a-e551-4689-a800-f5b360fcf5e3)

#### 5.2.2.1 Sprint Planning 2

### Sprint Planning Meeting Summary

| Elemento                             | Detalle                                                                                                                 |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Sprint #**                       | Sprint 2                                                                                                                |
| **Sprint Planning Background**     | Continuación del desarrollo de la Landing Page y despliegue de la primera versión funcional del Frontend Web Application.|
| **Date**                          | 2025-05-01                                                                                                              |
| **Time**                          | 04:30 PM                                                                                                                |
| **Location**                      | Reunión virtual vía Google Meet                                                                                         |
| **Prepared By**                   | Amir Castro                                                                                                             |
| **Attendees**                    | Pietro Osores, Amir Castro, Joaquín, Stephano, Carlos                                                                   |
| **Sprint 1 – Review Summary**     | Se completó la navegación fluida, alternancia de contenido y sección de testimonios.                                     |
| **Sprint 1 – Retrospective Summary** | Se mejoró la comunicación entre roles y la gestión de tareas.                                                         |
| **Sprint 2 – Goal**               | Desplegar la primera versión del Frontend Web Application y optimizar el diseño y la experiencia de usuario.             |
| **Sprint 2 – Velocity**           | 25 Story Points (estimado)                                                                                              |
| **Sprint 2 – Sum of Story Points**| 25 Story Points                                                                                                         |

---

#### 5.2.2.2 Aspect Leaders and Collaborators

### Leadership and Collaboration Matrix (LACX)

| Team Member          | GitHub Username | Gestión de Proyectos | Landing Page | Frontend Web App | Despliegue | Testing & QA |
| -------------------- | --------------- | -------------------- | ------------ | ---------------- | ---------- | ------------ |
| Pietro Osores        | Maximoff19  | L                    | C            | L                | C          | C            |
| Amir Castro          | \[A COMPLETAR]  | C                    | C            | C                | C          | L            |
| Carlos \[Apellido]   | \[A COMPLETAR]  | C                    | L            | C                | L          | C            |
| Stephano \[Apellido] | \[A COMPLETAR]  | C                    | L            | C                | C          | C            |
| Joaquín \[Apellido]  | \[A COMPLETAR]  | L                    | C            | C                | C          | L            |

> **L**: Leader (responsable del aspecto)  
> **C**: Collaborator (colaborador activo)

---

#### 5.2.2.3 Sprint Backlog 2

Durante el Sprint 2, el objetivo principal fue desarrollar las interfaces internas de la aplicación Flow Sense, construyendo una experiencia de usuario intuitiva para freelancers que incluye pantallas como registro, inicio de sesión, recuperación de contraseña, resumen diario, gestión de tareas, facturación, cronómetro, proyectos, ajustes, recordatorios y calendario. Estas interfaces se implementaron como diseños visuales de front end, sin lógica de backend, para proporcionar una base sólida para futuras integraciones funcionales. El equipo continuó utilizando Trello como herramienta de control de tareas basada en tableros tipo Kanban, donde cada user story fue descompuesta en uno o más work-items o tareas técnicas, organizadas en columnas como "To Do", "In Progress", "Review" y "Done". Este sprint marcó la transición desde la Landing Page completada en el Sprint 1 hacia las funcionalidades centrales de la aplicación, enfocándose en la usabilidad y consistencia visual.

### Sprint Backlog - Sprint 2

En esta sección se muestran los tasks que se realizaron en el presente sprint y se adjunta una captura en Trello y el link al tablero.

Link de Trello: [https://trello.com/invite/b/682791874c5c711da6745a87/ATTIe2eeebc64ea4934773404641fad9ecc3391B75D4/sprint-backlog-2]

![image](https://github.com/user-attachments/assets/4ad32d4d-d836-4203-9f98-6fd5f255f587)

| User Story ID | User Story Title | Task ID | Work-Item / Task | Description | Estimation (hrs) | Assigned To | Status |
|---------------|------------------|---------|------------------|-------------|------------------|-------------|--------|
| E10-US28 | Registro con selección de plan | TSK-07 | Maquetar formulario de registro | Diseñar formulario con campos para nombre, correo, contraseña, confirmación y selección de planes | 5 | Carlos | Done |
| E10-US28 | Registro con selección de plan | TSK-08 | Implementar validación visual | Mostrar mensajes de error visuales para contraseñas no coincidentes | 3 | Amir | Review |
| E10-US29 | Recuperación de contraseña | TSK-09 | Diseñar pantalla de forgot password | Maquetar pantalla con campo de correo y botón "Send Link" | 3 | Stephano | Done |
| E10-US30 | Visualización del resumen diario en la pantalla de inicio | TSK-10 | Diseñar card de Day Summary | Crear card con horas trabajadas, tareas completadas y porcentaje de productividad | 3 | Joaquín | Done |
| E10-US31 | Gestión de tareas con filtrado y búsqueda | TSK-11 | Maquetar pantalla de tareas | Diseñar pantalla con buscador, filtros por cliente/proyecto y toolbar (All, Pending, Completed) | 6 | Pietro | In Progress |
| E10-US31 | Gestión de tareas con filtrado y búsqueda | TSK-12 | Diseñar componente de tarea | Crear fila de tarea con título, importancia, empresa, descripción, etiquetas y botones de edición/eliminación | 4 | Carlos | Review |
| E10-US32 | Descarga de facturas | TSK-13 | Diseñar card de facturas | Maquetar card con ID, cliente, fecha, monto, estado y botón "Download" | 3 | Amir | Done |
| E10-US33 | Interacción con el cronómetro en la pantalla de time tracking | TSK-14 | Diseñar cronómetro interactivo | Crear componente de cronómetro con botones "Iniciar" y "Reiniciar" | 2 | Stephano | Done |
| E10-US34 | Visualización de proyectos en la pantalla de clients/projects | TSK-15 | Maquetar lista de proyectos | Diseñar cards con nombre de proyecto, cliente y estado (Done/No Done) | 3 | Joaquín | Done |
| E10-US35 | Actualización de perfil en la pantalla de settings | TSK-16 | Diseñar formulario de settings | Maquetar formulario con campos para nombre, correo, tarifa por hora y botón "Save" | 3 | Pietro | Done |
| E10-US36 | Visualización de recordatorios en la pantalla de inicio | TSK-17 | Diseñar card de recordatorios | Crear card con lista de recordatorios y botón "Add Reminder" | 3 | Carlos | Done |
| E10-US36 | Visualización de recordatorios en la pantalla de inicio | TSK-18 | Diseñar modal de nuevo recordatorio | Maquetar formulario/modal para agregar un nuevo recordatorio | 3 | Amir | In Progress |
| E10-US37 | Interacción con el calendario en la pantalla de calendar/schedule | TSK-19 | Maquetar calendario interactivo | Diseñar calendario con mes actual, botones de navegación y eventos/tareas resaltados | 5 | Stephano | In Progress |
| E10-US37 | Interacción con el calendario en la pantalla de calendar/schedule | TSK-20 | Diseñar vista de día seleccionado | Crear lista de eventos/tareas que aparece al seleccionar un día | 3 | Joaquín | Review |



#### 5.2.2.4 Development Evidence for Sprint Review

Durante el Sprint 2, el equipo logró desplegar la primera versión funcional del Frontend Web Application, optimizando la navegación y experiencia de usuario. A continuación, se muestran imágenes y evidencia de las funcionalidades implementadas.

![Image](https://github.com/user-attachments/assets/859605e5-dc91-4d25-b8c2-db3f4fb755af)

![Image](https://github.com/user-attachments/assets/90a31749-a5a2-43bb-be4e-e6245ea5cf9b)

![Image](https://github.com/user-attachments/assets/0be42d20-03ca-49d8-a425-164634aa8fee)

![Image](https://github.com/user-attachments/assets/7fe24bf8-d6d6-484b-ac05-6f36b1ec4b8d)

![Image](https://github.com/user-attachments/assets/2940fe2c-ddbc-4bfa-8c6c-af476f234af7)

![Image](https://github.com/user-attachments/assets/8671ffe3-4028-4856-abb5-682674119fc0)

![Image](https://github.com/user-attachments/assets/d7021458-3022-4dcb-bd88-d75028f4c9f4)

![Image](https://github.com/user-attachments/assets/eb6b13c6-4d26-4359-a589-02503a7b42f6)

![Image](https://github.com/user-attachments/assets/c49ad655-600a-4d9f-9d8f-758de37e2f8b)

![Image](https://github.com/user-attachments/assets/caa730d3-449a-430e-87ad-699b1263785f)

---

#### 5.2.2.5 Execution Evidence for Sprint Review

Durante este sprint, el equipo realizó pruebas funcionales y de integración para garantizar la estabilidad y usabilidad del sistema. Se llevaron a cabo correcciones inmediatas tras la detección de errores.

---

#### 5.2.2.6 Services Documentation Evidence for Sprint Review


En el segundo sprint, hemos realizado el diseño, la programación y el despligue de la Landing Page que presentará nuesta apliación web "FlowSenses"

<table> 
  <tr>
    <td> <strong>End Point </strong></td>
    <td align="center"> <strong>Funciones</strong> </td>
  </tr>

  <tr>
    <td> https://1asi0729-2510-4317-g5-flow-senses.github.io/LandingPage/ </td>
    <td> Desplegar Landing Page de FlowSenses</td>
  </tr>
</table>

---

#### 5.2.2.7 Software Deployment Evidence for Sprint Review

La primera versión del Frontend Web Application fue desplegada exitosamente en el servidor de producción y está disponible para pruebas de usuarios.

---

#### 5.2.2.8 Team Collaboration Insights during Sprint
