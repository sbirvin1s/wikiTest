# Static Files Documentation

## Overview

The `wwwroot` folder contains static files served directly to clients:
- CSS stylesheets
- JavaScript files
- Images
- Fonts
- Other static assets

## Directory Structure

```
wwwroot/
??? css/          # Stylesheets
?   ??? site.css      # Custom site styles
??? js/      # JavaScript files
???? site.js    # Custom site scripts
??? lib/      # Third-party libraries (via LibMan)
?   ??? bootstrap/    # Bootstrap framework
?   ??? jquery/       # jQuery library
?   ??? jquery-validation/ # jQuery validation
??? images/           # Image assets
??? favicon.ico       # Site favicon
```

## Referencing Static Files

### In Razor Views

```razor
@* CSS *@
<link rel="stylesheet" href="~/css/site.css" asp-append-version="true" />

@* JavaScript *@
<script src="~/js/site.js" asp-append-version="true"></script>

@* Images *@
<img src="~/images/logo.png" alt="Logo" />
```

The `~` character represents the `wwwroot` folder.

### Cache Busting

Use `asp-append-version="true"` to append a version hash:
```razor
<link rel="stylesheet" href="~/css/site.css" asp-append-version="true" />
```
Generates: `/css/site.css?v=abc123...`

## Managing Client Libraries

### Using LibMan (Library Manager)

Install libraries via `libman.json`:

```json
{
  "version": "1.0",
  "defaultProvider": "cdnjs",
  "libraries": [
    {
      "library": "bootstrap@5.3.0",
      "destination": "wwwroot/lib/bootstrap/"
    }
  ]
}
```

### Commands

```bash
# Restore libraries
dotnet libman restore

# Install new library
dotnet libman install jquery@3.6.0 --destination wwwroot/lib/jquery

# Clean libraries
dotnet libman clean
```

## CSS Organization

### Custom Styles

Add custom styles to `css/site.css`:

```css
/* Custom site styles */
.document-card {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 15px;
    margin-bottom: 15px;
}

.document-title {
    font-size: 1.5rem;
    font-weight: bold;
    color: #333;
}
```

### CSS Modules

For larger applications, organize CSS by feature:
```
css/
??? site.css          # Global styles
??? components/       # Component styles
?   ??? navbar.css
?   ??? footer.css
??? pages/            # Page-specific styles
    ??? home.css
    ??? documents.css
```

## JavaScript Organization

### Custom Scripts

Add custom JavaScript to `js/site.js`:

```javascript
// Site-wide JavaScript
(function() {
    'use strict';
    
    // Initialize tooltips
    var tooltips = document.querySelectorAll('[data-bs-toggle="tooltip"]');
    tooltips.forEach(function(tooltip) {
   new bootstrap.Tooltip(tooltip);
    });
    
    // Custom functionality
    console.log('WikiTest initialized');
})();
```

### Module Pattern

For larger applications:
```
js/
??? site.js           # Main entry point
??? modules/     # Feature modules
?   ??? documents.js
?   ??? search.js
??? utils/    # Utility functions
    ??? helpers.js
```

## Image Optimization

### Best Practices

1. Use appropriate formats:
   - JPG for photographs
   - PNG for graphics with transparency
   - SVG for icons and logos
   - WebP for modern browsers

2. Optimize file sizes:
   - Compress images before upload
   - Use appropriate dimensions
   - Serve responsive images

3. Naming conventions:
   - Use lowercase
   - Use hyphens for spaces
   - Be descriptive: `user-avatar-placeholder.png`

## Static File Middleware

Configured in `Program.cs`:

```csharp
app.UseStaticFiles();
```

### Custom Configuration

For caching, security headers, etc.:

```csharp
app.UseStaticFiles(new StaticFileOptions
{
    OnPrepareResponse = ctx =>
    {
        // Set cache headers
        ctx.Context.Response.Headers.Append(
            "Cache-Control", "public,max-age=31536000");
    }
});
```

## Security Considerations

1. Never store sensitive data in wwwroot
2. Validate uploaded files before saving
3. Use HTTPS for all resources
4. Implement Content Security Policy (CSP)
5. Keep libraries up to date

## Performance Tips

1. Minify CSS and JavaScript in production
2. Combine files to reduce requests
3. Use CDNs for common libraries
4. Enable compression (GZIP/Brotli)
5. Implement browser caching
6. Use image sprites for small icons
7. Lazy load images below the fold
