# Development Setup

## Prerequisites

- .NET 8.0 SDK or later
- Visual Studio 2022 or VS Code
- Git

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/sbirvin1s/wikiTest
cd wikiTest
```

### Build the Solution

```bash
dotnet restore
dotnet build
```

### Run the Application

```bash
cd WikiTest.Web
dotnet run
```

The application will be available at:
- HTTP: `http://localhost:5000`
- HTTPS: `https://localhost:5001`

## Development Workflow

### Creating a New Feature

1. Create a feature branch from `main`
2. Implement your changes
3. Write tests (if applicable)
4. Submit a pull request
5. Request code review

### Code Style

- Follow C# coding conventions
- Use meaningful variable and method names
- Add XML documentation comments for public APIs
- Keep methods focused and single-purpose

## Debugging

### Visual Studio
- Press F5 to start debugging
- Set breakpoints by clicking in the left margin

### VS Code
- Use the included launch configuration
- Install C# Dev Kit extension

## Common Tasks

### Adding a New Controller

```csharp
public class MyController : Controller
{
    public IActionResult Index()
    {
 return View();
    }
}
```

### Adding a New View

Create a corresponding view in `Views/[ControllerName]/[ActionName].cshtml`

## Troubleshooting

- **Build errors**: Run `dotnet clean` followed by `dotnet restore`
- **Port conflicts**: Change ports in `appsettings.json` or `launchSettings.json`
