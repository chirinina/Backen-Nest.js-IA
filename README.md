<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg" alt="Donate us"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow" alt="Follow us on Twitter"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Project setup

```bash
$ npm install
```

## Compile and run the project

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Run tests

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```


---

## Arquitectura General

```mermaid
flowchart LR
    Client[Cliente HTTP] --> API[NestJS API]
    API --> Auth[JWT Auth]
    API --> Posts[Posts Module]
    API --> Users[Users Module]
    API --> Categories[Categories Module]
    API --> DB[(PostgreSQL)]
    API --> AI[OpenAI Service]
    API --> Docs[Swagger Docs]
```

---

## Stack Tecnológico

| Tecnología                                                                                                          | Propósito                              |
| ------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| <img src="https://nestjs.com/img/logo-small.svg" width="28"/> **NestJS**                                            | Framework backend modular y escalable  |
| <img src="https://www.postgresql.org/media/img/about/press/elephant.png" width="28"/> **PostgreSQL**                | Base de datos relacional               |
| <img src="https://raw.githubusercontent.com/typeorm/typeorm/master/resources/logo_big.png" width="28"/> **TypeORM** | ORM para integración con PostgreSQL    |
| <img src="https://jwt.io/img/pic_logo.svg" width="28"/> **JSON Web Token**                                          | Autenticación basada en tokens         |
| <img src="https://swagger.io/swagger/media/assets/images/swagger_logo.svg" width="28"/> **Swagger**                 | Documentación interactiva de API       |
| <img src="https://raw.githubusercontent.com/openai/openai-logos/master/openai-logo.svg" width="28"/> **OpenAI**     | Generación de contenido con IA         |
| <img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" width="28"/> **Docker**                  | Contenerización y entorno reproducible |

---

## Evolución Funcional

### 1. Base del Proyecto

* Configuración inicial del entorno.
* Estructura modular.
* Configuración de ESLint, Prettier y TypeScript.
* Soporte para variables de entorno.

---

### 2. Gestión de Usuarios

* Implementación completa de CRUD.
* Validaciones con DTO.
* Hash de contraseñas con bcrypt.
* Serialización de respuestas.
* Integración con base de datos relacional.

---

### 3. Persistencia y Migraciones

* Integración con PostgreSQL.
* Configuración de TypeORM.
* Scripts de migración.
* Docker Compose para entorno local.

---

### 4. Publicaciones y Categorías

* Relaciones entre entidades.
* Asociación de usuarios con publicaciones.
* Integración bidireccional de categorías.
* Servicios desacoplados por módulo.

---

### 5. Seguridad

* Implementación de autenticación JWT.
* Estrategia Passport.
* Protección de endpoints.
* Validación global.
* Refuerzo de cabeceras HTTP con Helmet.
* Separación de payload tipado.

```mermaid
sequenceDiagram
    participant User
    participant API
    participant JWT
    participant DB

    User->>API: Login
    API->>DB: Validate credentials
    API->>JWT: Generate token
    JWT-->>User: Access Token
    User->>API: Request with Token
    API->>JWT: Validate token
    API-->>User: Protected Resource
```

---

### 6. Documentación y Estándares

* Integración de Swagger.
* Estandarización de DTO.
* Validaciones centralizadas.
* Serialización consistente.

---

### 7. Integración con Inteligencia Artificial

* Implementación de módulo AI.
* Servicio para generación de contenido dinámico.
* Integración desacoplada mediante proveedor dedicado.

---

### 8. Optimización y Producción

* Scripts de compilación para producción.
* Configuración segura de entorno.
* Mejora de cabeceras HTTP.
* Preparación para despliegue escalable.

---

## Modelo Relacional Simplificado

```mermaid
erDiagram
    USERS ||--o{ POSTS : creates
    POSTS ||--o{ CATEGORIES : belongs_to
    USERS {
        uuid id
        string email
        string password
    }
    POSTS {
        uuid id
        string title
        text content
    }
    CATEGORIES {
        uuid id
        string name
    }
```

---
