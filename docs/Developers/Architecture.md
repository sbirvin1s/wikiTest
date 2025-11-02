# Architecture Overview

## Technology Stack

### Backend
- **Framework**: ASP.NET Core MVC
- **Language**: C# (.NET 8.0)
- **Pattern**: Model-View-Controller (MVC)

### Frontend
- **Framework**: Razor Views
- **Styling**: Bootstrap 5
- **JavaScript**: jQuery (included with template)

## Project Structure

```
WikiTest.Web/
??? Controllers/     # MVC Controllers
??? Models/ # Data models and ViewModels
??? Views/       # Razor views
??? wwwroot/     # Static files (CSS, JS, images)
??? Program.cs       # Application entry point
??? appsettings.json # Configuration
```

## Design Patterns

### MVC Pattern
The application follows the Model-View-Controller pattern:
- **Models**: Represent data and business logic
- **Views**: Handle UI presentation
- **Controllers**: Manage request flow and coordination

### Dependency Injection
Built-in DI container manages service lifetimes and dependencies.

## Middleware Pipeline

The request pipeline includes:
1. Exception handling
2. HTTPS redirection
3. Static files
4. Routing
5. Authorization
6. MVC endpoint routing

## Configuration

Configuration is managed through:
- `appsettings.json` - General settings
- `appsettings.Development.json` - Development-specific settings
- Environment variables
- User secrets (for sensitive data)
