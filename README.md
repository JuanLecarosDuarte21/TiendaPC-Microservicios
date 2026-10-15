# TiendaPC - Sistema de Microservicios

## Descripción del proyecto

TiendaPC es un proyecto académico que simula una plataforma de comercio electrónico dedicada a la venta de componentes de computadoras.

El sistema está organizado en ocho microservicios desarrollados con Java y Spring Boot. Cada microservicio administra una funcionalidad específica y utiliza una base de datos MySQL independiente.

## Objetivo

Desarrollar una solución basada en arquitectura de microservicios, aplicando programación orientada a objetos, servicios REST, persistencia con Spring Data JPA y control de versiones mediante Git y GitHub.

## Tecnologías utilizadas

- Java 21
- Spring Boot 4.0.8
- Spring Web
- Spring Data JPA
- MySQL 8
- Maven
- Jakarta Validation
- Git y GitHub
- Visual Studio Code
- Postman para pruebas de API

## Arquitectura del sistema

| Microservicio | Puerto | Función |
|---|---|---|
| ms-usuarios | 8081 | Administración de usuarios |
| ms-productos | 8082 | Gestión de productos |
| ms-inventario | 8083 | Control de existencias |
| ms-carrito | 8084 | Administración del carrito de compras |
| ms-pedidos | 8085 | Registro y seguimiento de pedidos |
| ms-pagos | 8086 | Gestión de pagos |
| ms-envios | 8087 | Seguimiento de envíos |
| ms-notificaciones | 8088 | Registro de notificaciones |

Los microservicios cuentan con sus propias aplicaciones Spring Boot y bases de datos. La comunicación automática entre servicios no forma parte de la implementación actual.

## Repositorios de GitHub

| Microservicio | Repositorio |
|---|---|
| Usuarios | [ms-usuarios](https://github.com/JuanLecarosDuarte21/ms-usuarios) |
| Productos | [ms-productos](https://github.com/JuanLecarosDuarte21/ms-productos) |
| Inventario | [ms-inventario](https://github.com/JuanLecarosDuarte21/ms-inventario) |
| Carrito | [ms-carrito](https://github.com/JuanLecarosDuarte21/ms-carrito) |
| Pedidos | [ms-pedidos](https://github.com/JuanLecarosDuarte21/ms-pedidos) |
| Pagos | [ms-pagos](https://github.com/JuanLecarosDuarte21/ms-pagos) |
| Envíos | [ms-envios](https://github.com/JuanLecarosDuarte21/ms-envios) |
| Notificaciones | [ms-notificaciones](https://github.com/JuanLecarosDuarte21/ms-notificaciones) |

## Estructura de los microservicios

Los proyectos utilizan una estructura por capas:

- **model:** entidades y atributos del sistema.
- **repository:** operaciones de persistencia mediante Spring Data JPA.
- **service:** lógica de negocio.
- **controller:** endpoints REST.
- **config:** carpeta destinada a configuraciones adicionales.

## Persistencia y relaciones JPA

Cada microservicio utiliza MySQL para almacenar sus datos.

En el microservicio `ms-pedidos` se implementaron relaciones JPA entre las entidades `Pedido` y `DetallePedido`.

- `@OneToMany`: un pedido puede contener varios detalles.
- `@ManyToOne`: varios detalles pueden pertenecer a un mismo pedido.
- `CascadeType.ALL`: permite persistir detalles junto con el pedido.
- `@JoinColumn`: define la columna de relación `pedido_id`.

Los identificadores de usuarios y productos se almacenan como referencias numéricas a otros microservicios, sin relaciones JPA directas entre bases de datos independientes.

## Requisitos para ejecutar el proyecto

- Java 21 instalado.
- MySQL instalado y ejecutándose.
- Git para clonar los repositorios.
- Conexión a Internet para descargar las dependencias Maven.

## Instrucciones de ejecución

1. Clonar el repositorio del microservicio que se desea ejecutar.
2. Abrir el proyecto en Visual Studio Code.
3. Crear en MySQL la base de datos indicada en su archivo `application.properties`.
4. Configurar las credenciales de MySQL mediante variables de entorno.
5. Ejecutar el proyecto con Maven.

En Windows PowerShell, configurar la contraseña:

```powershell
$env:DB_PASSWORD = "TU_CONTRASEÑA_MYSQL"
```

Ejecutar el microservicio:

```powershell
.\mvnw.cmd spring-boot:run
```

Compilar y ejecutar las pruebas configuradas:

```powershell
.\mvnw.cmd clean package
```

Los comandos deben ejecutarse desde la carpeta raíz del microservicio correspondiente.

## Control de versiones

Los repositorios individuales utilizan tres ramas principales de trabajo:

- `main`: versión principal.
- `develop`: desarrollo.
- `feature/documentacion`: documentación.

## Pruebas y validación

El proyecto contempla pruebas de endpoints REST mediante Postman y verificación de persistencia en MySQL.

Se ha comprobado el inicio de los microservicios durante su desarrollo. Las pruebas integrales y las evidencias finales de las operaciones CRUD permanecen pendientes de completar.

## Alcance actual

TiendaPC representa una implementación académica de ocho servicios REST independientes. No incluye todavía una integración completa entre servicios, una pasarela de pagos real ni un sistema de envío de correos electrónicos reales.

## Autor

JuanLecarosDuarte21

## Contexto

Proyecto desarrollado con fines académicos para una evaluación de arquitectura de microservicios.
