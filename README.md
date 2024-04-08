# ChessPortal

## Backend (Spring Boot):

1. **Spring Security**: Para la autenticación y autorización de usuarios, evitando SQL injection y protegiendo las rutas de acceso a la API.
2. **Spring Data JPA con Hibernate**: Para la interacción con la base de datos MySQL y gestionar la persistencia de datos de usuarios y partidas.
3. **MySQL**: Base de datos relacional para almacenar información de usuarios y partidas.
4. **Spring MVC o Spring Webflux (según tus necesidades)**: Para exponer endpoints RESTful que manejen las solicitudes del cliente, como inicio de sesión, registro de usuarios, búsqueda de partidas, creación de salas, guardar y cargar partidas.
5. **JWT (JSON Web Tokens)**: Para generar tokens de autenticación seguros y manejar la sesión de los usuarios de forma segura.
6. **Spring AOP (Aspect-Oriented Programming)**: Para implementar aspectos de seguridad y controlar el acceso a las operaciones críticas, como la creación y carga de partidas.

## Frontend (React):

1. **React Router**: Para la navegación entre diferentes páginas, como la página de inicio de sesión, registro, búsqueda de partida y juego.
2. **Axios**: Para realizar solicitudes HTTP al backend y manejar la comunicación con la API REST.
3. **Formik y Yup**: Para manejar formularios y validación de datos durante el registro y inicio de sesión de usuarios.
4. **JWT Decode**: Para decodificar y manejar los tokens JWT recibidos del backend durante el proceso de autenticación.
5. **React Context o Redux (opcional)**: Para gestionar el estado global de la aplicación, como la información del usuario autenticado y el estado del juego.### 

## Otras Tecnologías (opcional):

1. **WebSocket (por ejemplo, usando Spring Websocket)**: Para implementar la comunicación en tiempo real entre los jugadores durante una partida de ajedrez.
2. **Biblioteca de ajedrez en JavaScript (por ejemplo, chess.js)**: Para manejar la lógica del juego de ajedrez en el frontend y realizar validaciones de movimientos de manera local antes de enviarlos al backend.

## Funciones de cada tecnología:

- **Spring Security**: Autenticación, autorización y prevención de ataques de seguridad.
- **Spring Data JPA con Hibernate**: Persistencia de datos de usuarios y partidas en la base de datos MySQL.
- **MySQL**: Almacenamiento de información de usuarios y partidas.
- **Spring MVC o Spring Webflux**: Exposición de endpoints RESTful para manejar las solicitudes del cliente.
- **JWT**: Generación y manejo de tokens de autenticación seguros.
- **React Router**: Navegación entre diferentes vistas de la aplicación.
- **Axios**: Comunicación con el backend a través de solicitudes HTTP.
- **Formik y Yup**: Manejo de formularios y validación de datos en el frontend.
- **JWT Decode**: Decodificación de tokens JWT recibidos del backend.
- **WebSocket**: Comunicación en tiempo real entre jugadores durante una partida.
- **Biblioteca de ajedrez en JavaScript**: Lógica del juego de ajedrez en el frontend.

### Spring Boot:

```scss
src
└── main
 ├── java
 │ └── com
 │ └── tuempresa
 │ └── ajedrez
 │ ├── config
 │ │ └── SecurityConfig.java
 │ ├── controller
 │ │ ├── AuthController.java
 │ │ ├── GameController.java
 │ │ └── UserController.java
 │ ├── dto
 │ │ ├── AuthRequest.java
 │ │ ├── AuthResponse.java
 │ │ ├── GameRequest.java
 │ │ ├── GameResponse.java
 │ │ ├── UserRequest.java
 │ │ └── UserResponse.java
 │ ├── exception
 │ │ ├── CustomExceptionHandler.java
 │ │ ├── ResourceNotFoundException.java
 │ │ └── ValidationErrorException.java
 │ ├── model
 │ │ ├── User.java
 │ │ ├── Game.java
 │ │ └── Move.java
 │ ├── repository
 │ │ ├── UserRepository.java
 │ │ ├── GameRepository.java
 │ │ └── MoveRepository.java
 │ ├── service
 │ │ ├── UserService.java
 │ │ ├── GameService.java
 │ │ └── MoveService.java
 │ └── util
 │ └── JwtTokenUtil.java
 └── resources
 ├── application.properties
 ├── schema.sql
 └── data.sql
```

- **config**: Esta carpeta contiene las configuraciones de la aplicación, como la configuración de seguridad (SecurityConfig).
- **controller**: Aquí se encuentran los controladores REST que manejan las solicitudes HTTP entrantes. Por ejemplo, AuthController para autenticación, UserController para operaciones de usuario y GameController para operaciones de juego.
- **dto**: Los objetos de transferencia de datos (DTO) se encuentran aquí. Estos objetos son utilizados para intercambiar datos entre el frontend y el backend de manera estructurada.
- **exception**: Clases para manejar excepciones personalizadas y errores de la aplicación.
- **model**: Las entidades de la base de datos se encuentran aquí. Por ejemplo, User, Game y Move.
- **repository**: Las interfaces de repositorio de Spring Data JPA se encuentran aquí para acceder a la base de datos. Cada repositorio se encarga de interactuar con una entidad específica.
- **service**: Los servicios de la aplicación se encuentran aquí. Estos servicios contienen la lógica de negocio de la aplicación y actúan como intermediarios entre los controladores y los repositorios.
- **util**: Clases de utilidad, como JwtTokenUtil para generar y validar tokens JWT.
- **resources**: Los recursos de la aplicación, como archivos de configuración (application.properties), scripts de inicialización de base de datos (schema.sql, data.sql), etc.

### Frontend:

```scss
frontend
├── public
│   ├── index.html
│   └── ...
├── src
│   ├── assets
│   │   └── ...
│   ├── components
│   │   ├── Auth
│   │   │   ├── Login.js
│   │   │   └── Register.js
│   │   ├── Game
│   │   │   ├── Board.js
│   │   │   └── ...
│   │   └── ...
│   ├── services
│   │   ├── AuthService.js
│   │   ├── GameService.js
│   │   └── ...
│   ├── App.js
│   ├── index.js
│   └── ...
├── package.json
└── ...

```



- **public**: Contiene archivos estáticos como HTML, imágenes, etc. El archivo `index.html` es el punto de entrada de la aplicación React.
- **src**: Contiene el código fuente de la aplicación React.
  - **assets**: Almacena recursos estáticos como imágenes, iconos, etc.
  - **components**: Aquí se encuentran todos los componentes de React organizados por funcionalidad. Por ejemplo, los componentes relacionados con la autenticación (Login, Register) se encuentran en el directorio Auth, y los componentes relacionados con el juego de ajedrez (Board, Piece, etc.) se encuentran en el directorio Game.
  - **services**: Contiene los servicios de React que manejan la comunicación con el backend a través de solicitudes HTTP. Por ejemplo, AuthService.js para operaciones de autenticación y GameService.js para operaciones relacionadas con el juego.
  - **App.js**: El componente principal que define la estructura de la aplicación React y las rutas.
  - **index.js**: El punto de entrada de la aplicación React donde se renderiza el componente principal `App`.
