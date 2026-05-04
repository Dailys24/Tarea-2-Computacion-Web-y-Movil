# Proyecto Tarea 2 - Clean Architecture

Este proyecto es una implementación base en Node.js utilizando los principios de **Clean Architecture** o (Arquitectura Limpia).

##Objetivo del Proyecto
El objetivo principal de esta estructura es lograr una separación estricta de responsabilidades, asegurando que las reglas de negocio (el núcleo del sistema) sean totalmente independientes de los frameworks, bases de datos o la interfaz de usuario. Esto permite que el software sea altamente testeable, mantenible y escalable.

## Arquitectura y Estructura de Carpetas

Nuestra arquitectura se divide en tres capas principales dentro del directorio `src/`, respetando la Regla de Dependencia:

### 1. Domain (Dominio)
Es el núcleo del sistema. No tiene dependencias externas ni conoce sobre Node.js o la Web.
- **/entities:** Contiene los objetos y reglas de negocio puras (Ej: Modelos de `Usuario` o `Producto`).
- **/repositories:** Contiene las interfaces (contratos) que dictan cómo se deben comportar los almacenamientos de datos, sin implementar la lógica real.

### 2. Application (Aplicación)
Orquesta el flujo de los datos hacia y desde el dominio.
- **/use-cases:** Aquí residen las acciones específicas que el sistema puede realizar (Ej: `CrearUsuario`, `ProcesarPago`). Consumen el dominio, pero ignoran la infraestructura.

### 3. Infrastructure (Infraestructura)
La capa más externa. Contiene todo el código que interactúa con el mundo exterior.
- **/controllers:** Reciben las peticiones HTTP (req, res), extraen los datos y llaman a los casos de uso correspondientes.
- **/routes:** Definen los endpoints de la API REST.
- **/database:** Implementaciones reales de la conexión a la base de datos respetando los contratos del dominio.
- **/config:** Variables de entorno y configuraciones generales del servidor.

## Cómo ejecutar el proyecto
1. Instalar dependencias: `npm install`
2. Iniciar el punto de entrada: `node src/app.js`