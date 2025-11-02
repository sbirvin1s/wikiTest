# Controllers Documentation

## Overview

Controllers in WikiTest handle HTTP requests and return responses. They coordinate between models and views.

## Controller Responsibilities

- Receive and validate input
- Call business logic/services
- Select appropriate view
- Return response to client

## Base Controller

All controllers inherit from `Controller` which provides:
- Helper methods for views
- Access to HTTP context
- Model state validation
- Result helpers (View, Json, Redirect, etc.)

## Routing

### Convention-Based Routing

Default route: `{controller=Home}/{action=Index}/{id?}`

### Attribute Routing

```csharp
[Route("api/[controller]")]
public class MyApiController : Controller
{
    [HttpGet("{id}")]
    public IActionResult GetById(int id) { }
}
```

## Action Results

Common return types:
- `ViewResult` - Render a view
- `JsonResult` - Return JSON data
- `RedirectResult` - Redirect to URL
- `StatusCodeResult` - Return HTTP status

## Best Practices

1. Keep controllers thin - move logic to services
2. Use dependency injection for services
3. Validate input using model validation
4. Return appropriate HTTP status codes
5. Handle exceptions with filters
6. Use async/await for I/O operations

## Example Controller

```csharp
public class DocumentController : Controller
{
    private readonly IDocumentService _documentService;
    
    public DocumentController(IDocumentService documentService)
 {
        _documentService = documentService;
  }
    
    public async Task<IActionResult> Index()
    {
      var documents = await _documentService.GetAllAsync();
        return View(documents);
    }
}
```
