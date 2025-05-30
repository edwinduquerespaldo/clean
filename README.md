# Clean Architecture Template with .NET

Este es un template de una solución implementada siguiendo los principios de Clean Architecture (Arquitectura Limpia) utilizando .NET. La solución incluye una API REST con SQLite como base de datos y Swagger para la documentación.

## Estructura del Proyecto

La solución está organizada en capas siguiendo los principios de Clean Architecture:

```
CleanArchitecture/
├── src/
│   ├── CleanArchitecture.Domain/           # Capa de Dominio
│   │   └── Entities/                       # Entidades de dominio
│   │       └── Product.cs                  # Ejemplo de entidad
│   │
│   ├── CleanArchitecture.Application/      # Capa de Aplicación
│   │   └── [Servicios de aplicación]       # Casos de uso, DTOs, interfaces
│   │
│   ├── CleanArchitecture.Infrastructure/   # Capa de Infraestructura
│   │   ├── Database/                       # Archivos de base de datos
│   │   │   └── app.db                      # Base de datos SQLite
│   │   └── Persistence/                    # Persistencia de datos
│   │       └── ApplicationDbContext.cs     # Contexto de EF Core
│   │
│   └── CleanArchitecture.Api/             # Capa de Presentación
│       ├── Controllers/                    # Controladores API
│       └── Program.cs                      # Configuración de la aplicación
```

## Capas

### 1. Domain (CleanArchitecture.Domain)
- Contiene las entidades del negocio
- No tiene dependencias con otras capas
- Implementa las reglas de negocio core

### 2. Application (CleanArchitecture.Application)
- Contiene la lógica de aplicación
- Define interfaces para infraestructura
- Depende solo de la capa de Domain

### 3. Infrastructure (CleanArchitecture.Infrastructure)
- Implementa las interfaces definidas en Application
- Contiene la implementación de persistencia con Entity Framework Core
- Configuración y archivos de SQLite
- Manejo de la base de datos y otros detalles externos
- Depende de Domain y Application

### 4. API (CleanArchitecture.Api)
- Controllers RESTful
- Configuración de Swagger/OpenAPI
- Inyección de dependencias
- Depende de todas las otras capas

## Tecnologías Utilizadas

- **.NET 9.0**
- **Entity Framework Core**
- **SQLite**: Base de datos
- **Swagger/OpenAPI**: Documentación de la API
- **Clean Architecture**: Patrón de arquitectura

## Características

- ✅ Implementación de Clean Architecture
- ✅ API RESTful
- ✅ Documentación con Swagger
- ✅ Base de datos SQLite
- ✅ Entity Framework Core
- ✅ Inyección de dependencias
- ✅ Ejemplo CRUD completo
- ✅ Separación clara de responsabilidades
- ✅ Estructura escalable

## Endpoints API

La API proporciona los siguientes endpoints:

- `GET /api/products`: Obtener todos los productos
- `GET /api/products/{id}`: Obtener un producto por ID
- `POST /api/products`: Crear un nuevo producto
- `PUT /api/products/{id}`: Actualizar un producto existente
- `DELETE /api/products/{id}`: Eliminar un producto

## Configuración y Ejecución

1. Clonar el repositorio
```bash
git clone https://github.com/edwinduquerespaldo/clean.git
```

2. Navegar al directorio del proyecto
```bash
cd clean
```

3. Restaurar paquetes NuGet
```bash
dotnet restore
```

4. Ejecutar la aplicación
```bash
cd src/CleanArchitecture.Api
dotnet run
```

5. Acceder a Swagger
```
http://localhost:5294/swagger
```

## Base de Datos

La aplicación utiliza SQLite como base de datos. El archivo de base de datos se crea automáticamente en:
```
src/CleanArchitecture.Infrastructure/Database/app.db
```

Esto sigue los principios de Clean Architecture, manteniendo los detalles de persistencia en la capa de Infraestructura. La conexión a la base de datos se configura en la capa de API a través de appsettings.json, pero el archivo físico y la lógica de persistencia se mantienen en la capa de Infraestructura.

## Principios de Clean Architecture Aplicados

- **Independencia de Frameworks**: El dominio no depende de la existencia de ninguna biblioteca externa
- **Testeable**: La lógica de negocio puede probarse sin la UI, base de datos o servidor web
- **Independiente de la UI**: La UI puede cambiar sin cambiar el resto del sistema
- **Independiente de la Base de Datos**: Se puede cambiar SQLite por cualquier otra base de datos
- **Independiente de cualquier elemento externo**: Las reglas de negocio no saben nada sobre el mundo exterior

## Licencia

MIT
