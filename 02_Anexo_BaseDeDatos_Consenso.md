# Documentación de la base de datos relacional del proyecto CENTINELA  

### Modelo: `User`
- **Descripción**: Representa a los usuarios del sistema, con funcionalidades extendidas del modelo base de Django.
- **Atributos principales**:
  - `id`: Identificador único auto-generado.
  - `username`: Correo electrónico del usuario utilizado como nombre de usuario.
  - `first_name`, `last_name`: Nombres y apellidos del usuario.
  - `profile_picture`: Imagen de perfil del usuario, con un sistema de nombres de archivo único.
  - `scopus_id`: Identificador opcional del usuario en el sistema Scopus.
- **Relaciones**:
  - `GroupUser`: Define la membresía de los usuarios en diversos grupos.
  - `Post`: Define los posts creados por el usuario.
- **Funcionalidades especiales**:
  - `save()`: Método personalizado para manejar la actualización de imágenes de perfil.

### Modelo: `Post`
- **Descripción**: Publicaciones creadas por los usuarios, que pueden incluir texto y archivos adjuntos.
- **Atributos principales**:
  - `id`: Identificador único auto-generado.
  - `description`: Descripción o contenido de la publicación.
  - `created_at`: Fecha y hora en la que la publicación fue creada.
- **Relaciones**:
  - `PostFile`: Archivos adjuntos a la publicación.

### Modelo: `Group`
- **Descripción**: Representa grupos de usuarios dentro del sistema.
- **Atributos principales**:
  - `id`: Identificador único auto-generado.
  - `title`: Título del grupo.
  - `description`: Descripción extendida del grupo.
- **Relaciones**:
  - `GroupUser`: Relación que conecta a los usuarios con sus grupos.

### Modelo: `RecommendedTopic`
- **Descripción**: Temas recomendados asignables a grupos para discusión o análisis.
- **Atributos principales**:
  - `topic_name`: Nombre del tema recomendado.
- **Relaciones**:
  - `Group`: Grupo al cual el tema está potencialmente asignado.

### Modelo: `NotificationPhaseOne` y `NotificationPhaseTwo`
- **Descripción**: Gestión de notificaciones enviadas a los usuarios en distintas fases del proyecto.
- **Atributos principales**:
  - `notification_type`: Tipo de notificación emitida.
  - `message`: Mensaje detallado de la notificación.
- **Relaciones**:
  - `User`: Usuario receptor de la notificación.
  - `Group`: Grupo relacionado con la notificación.

### Modelo: `TopicAddedUser`
- **Descripción**: Registra la adición de temas por los usuarios a los grupos.
- **Atributos principales**:
  - `added_at`: Fecha y hora en la que el tema fue añadido.
- **Relaciones**:
  - `RecommendedTopic`: Tema que fue añadido.
  - `User`: Usuario que añadió el tema.
  - `Group`: Grupo al que el tema fue añadido.

### Modelo: `UserExpertise`
- **Descripción**: Captura la experticia de un usuario en un tema específico dentro de un grupo.
- **Atributos principales**:
  - `expertise_level`: Nivel de experticia del usuario en el tema.
  - `has_provided_expertise`: Indica si el usuario ha proporcionado su nivel de experticia.
- **Relaciones**:
  - `User`: Usuario al que se refiere la experticia.
  - `Group`: Grupo relacionado.
  - `RecommendedTopic`: Tema sobre el que el usuario tiene experticia.

### Modelo: `UserSatisfaction`
- **Descripción**: Registra la satisfacción de los usuarios respecto a su experiencia en el grupo.
- **Atributos principales**:
  - `satisfaction_level`: Nivel de satisfacción del usuario.
- **Relaciones**:
  - `User`: Usuario que proporciona la evaluación.
  - `Group`: Grupo evaluado.

### Modelo: `FinalTopicOrder`
- **Descripción**: Orden final de los temas discutidos dentro de un grupo, según la evaluación de los usuarios.
- **Atributos principales**:
  - `posFinal`: Posición final asignada al tema dentro del grupo.
- **Relaciones**:
  - `Group`: Grupo al que pertenece el orden de temas.
  - `User`: Usuario que participa en la evaluación de los temas.
  - `RecommendedTopic`: Tema evaluado.


## Esquema General de la Base de Datos
![Ver Esquema General](https://drive.google.com/file/d/1wAjqRYOoiIHJFUuhoiBBwPwpIxnacQcj/view "Haz clic para ver el Esquema General de la Base de Datos")
