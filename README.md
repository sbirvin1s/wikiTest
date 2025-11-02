# WikiTest

A comprehensive ASP.NET Core MVC web application with integrated documentation.

## Project Structure

```
WikiTest/
??? WikiTest.sln    # Solution file
??? WikiTest.Web/           # Main MVC web application
?   ??? Controllers/   # MVC Controllers
?   ??? Models/          # Data models and ViewModels
?   ??? Views/         # Razor views
?   ??? wwwroot/            # Static files (CSS, JS, images)
?   ??? Program.cs                # Application entry point
?   ??? appsettings.json          # Configuration
?   ??? README.md    # Web project documentation
??? docs/        # Centralized documentation
    ??? Users/     # End-user documentation
    ?   ??? GettingStarted.md
    ?   ??? UserGuide.md
    ??? Developers/       # Developer documentation
    ?   ??? Architecture.md
    ?   ??? DevelopmentSetup.md
    ?   ??? JobTiming.md
    ??? Operations/             # Operations documentation
??? BusinessLogic.md
        ??? AdminProcesses.md
        ??? MonitoringAndSupport.md
```

## Documentation Philosophy

This project follows a dual documentation approach:

### 1. Centralized Documentation (`/docs`)
Located in the `docs/` directory, organized by audience:
- **Users**: End-user guides and tutorials
- **Developers**: Technical architecture, setup, and development guides
- **Operations**: Admin processes, monitoring, and support procedures

### 2. Contextual Documentation
Documentation that "lives next to where it's used":
- `WikiTest.Web/Controllers/README.md` - Controller patterns and practices
- `WikiTest.Web/Models/README.md` - Model conventions and validation
- `WikiTest.Web/Views/README.md` - Razor syntax and view guidelines
- `WikiTest.Web/wwwroot/README.md` - Static file organization
- `WikiTest.Web/README.md` - Application configuration and startup

## Quick Start

### Prerequisites
- .NET 8.0 SDK or later
- Visual Studio 2022 / VS Code / Rider

### Running the Application

```bash
# Clone the repository
git clone https://github.com/sbirvin1s/wikiTest
cd wikiTest

# Restore dependencies
dotnet restore

# Build the solution
dotnet build

# Run the web application
cd WikiTest.Web
dotnet run
```

The application will be available at:
- HTTP: http://localhost:5000
- HTTPS: https://localhost:5001

## Development

### Building the Solution

```bash
dotnet build
```

### Running Tests

```bash
dotnet test
```

### Cleaning Build Artifacts

```bash
dotnet clean
```

## Technology Stack

- **Framework**: ASP.NET Core 8.0
- **Pattern**: Model-View-Controller (MVC)
- **UI**: Razor Views with Bootstrap 5
- **Language**: C# 12

## Documentation Locations

### For End Users
See `/docs/Users/` for:
- Getting started guide
- User manual
- FAQ and troubleshooting

### For Developers
See `/docs/Developers/` for:
- System architecture
- Development setup
- Coding standards
- Job timing and scheduled tasks

Also check component-specific READMEs in:
- `WikiTest.Web/Controllers/README.md`
- `WikiTest.Web/Models/README.md`
- `WikiTest.Web/Views/README.md`
- `WikiTest.Web/wwwroot/README.md`

### For Operations
See `/docs/Operations/` for:
- Business logic overview
- Admin processes and procedures
- Monitoring and support
- Deployment guidelines

## Contributing

1. Create a feature branch from `main`
2. Make your changes
3. Update relevant documentation
4. Submit a pull request

### Documentation Updates

When making changes:
- Update centralized docs (`/docs`) for high-level concepts
- Update contextual READMEs when changing component behavior
- Keep code examples current with actual implementation

## Project Goals

This project demonstrates:
- Clean MVC architecture
- Comprehensive documentation practices
- Separation of concerns
- Documentation that serves multiple audiences
- Living documentation that stays close to the code

## License

[Your License Here]

## Contact

- **Repository**: https://github.com/sbirvin1s/wikiTest
- **Issues**: https://github.com/sbirvin1s/wikiTest/issues

---

## Additional Resources

- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core)
- [C# Documentation](https://docs.microsoft.com/dotnet/csharp)
- [Bootstrap Documentation](https://getbootstrap.com/docs)
