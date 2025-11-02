# Program.cs Documentation

## Overview

`Program.cs` is the entry point for the ASP.NET Core application. It configures services and the HTTP request pipeline.

## Application Structure

### Service Configuration (Before `app.Build()`)

This section registers services with the dependency injection container:

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add MVC services
builder.Services.AddControllersWithViews();

// Add custom services
builder.Services.AddScoped<IDocumentService, DocumentService>();
```

### Middleware Pipeline (After `app.Build()`)

This section configures how the application handles HTTP requests:

```csharp
var app = builder.Build();

// Configure the HTTP request pipeline
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Home/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthorization();

app.MapControllerRoute(
    name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");

app.Run();
```

## Configuration

### Reading Configuration

Access configuration from `appsettings.json`:

```csharp
// Get connection string
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");

// Get specific setting
var setting = builder.Configuration["MySetting"];

// Bind to options class
builder.Services.Configure<MyOptions>(
    builder.Configuration.GetSection("MyOptions"));
```

### Environment-Specific Configuration

- `appsettings.json` - Base configuration
- `appsettings.Development.json` - Development overrides
- `appsettings.Production.json` - Production overrides

## Dependency Injection

### Service Lifetimes

```csharp
// Transient: Created each time requested
builder.Services.AddTransient<IMyService, MyService>();

// Scoped: Created once per request
builder.Services.AddScoped<IMyService, MyService>();

// Singleton: Created once for application lifetime
builder.Services.AddSingleton<IMyService, MyService>();
```

## Common Services

### MVC Services

```csharp
// Controllers with Views
builder.Services.AddControllersWithViews();

// API Controllers only
builder.Services.AddControllers();

// Razor Pages
builder.Services.AddRazorPages();
```

### Database Context

```csharp
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(connectionString));
```

### Authentication

```csharp
builder.Services.AddAuthentication(CookieAuthenticationDefaults.AuthenticationScheme)
    .AddCookie(options =>
    {
        options.LoginPath = "/Account/Login";
        options.LogoutPath = "/Account/Logout";
    });
```

### Authorization

```csharp
builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("AdminOnly", policy => 
    policy.RequireRole("Admin"));
});
```

## Middleware Order

The order of middleware is critical:

1. **Exception Handling**: `UseExceptionHandler` / `UseDeveloperExceptionPage`
2. **HTTPS Redirection**: `UseHttpsRedirection`
3. **Static Files**: `UseStaticFiles`
4. **Routing**: `UseRouting`
5. **CORS**: `UseCors` (if needed)
6. **Authentication**: `UseAuthentication`
7. **Authorization**: `UseAuthorization`
8. **Custom Middleware**: Your custom middleware
9. **Endpoints**: `MapControllers` / `MapControllerRoute`

## Routing Configuration

### Convention-Based Routing

```csharp
app.MapControllerRoute(
 name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");

// Additional routes
app.MapControllerRoute(
    name: "api",
    pattern: "api/{controller}/{action}/{id?}");
```

### Endpoint Routing

```csharp
app.MapControllers(); // Attribute routing
app.MapRazorPages(); // Razor Pages
```

## Environment Detection

```csharp
if (app.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
}
else
{
    app.UseExceptionHandler("/Home/Error");
app.UseHsts();
}
```

## Logging Configuration

```csharp
builder.Logging.ClearProviders();
builder.Logging.AddConsole();
builder.Logging.AddDebug();
builder.Logging.AddEventSourceLogger();

// Set minimum level
builder.Logging.SetMinimumLevel(LogLevel.Information);
```

## Best Practices

1. Keep Program.cs organized and readable
2. Use extension methods for complex service registration
3. Order middleware correctly
4. Use environment-specific configuration
5. Register services with appropriate lifetimes
6. Configure logging appropriately per environment
7. Use strongly-typed configuration (Options pattern)
8. Handle secrets securely (User Secrets, Azure Key Vault)

## Custom Middleware

```csharp
// Inline middleware
app.Use(async (context, next) =>
{
    // Do something before
    await next.Invoke();
  // Do something after
});

// Middleware class
app.UseMiddleware<CustomMiddleware>();
```

## Startup Performance

Tips for faster startup:

1. Use lazy loading for services when possible
2. Minimize work in Configure method
3. Use AddControllers() instead of AddMvc() if not using views
4. Profile startup time in development
