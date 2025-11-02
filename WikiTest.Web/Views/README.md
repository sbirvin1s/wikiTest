# Views Documentation

## Overview

Views are responsible for presenting content to the user. WikiTest uses Razor syntax for server-side rendering.

## Razor Syntax

### Basic Syntax

```razor
@* This is a comment *@
@model WikiTest.Web.Models.DocumentViewModel

<h1>@Model.Title</h1>
<p>@Model.Content</p>

@{
    var greeting = "Hello";
    <p>@greeting World!</p>
}
```

### Control Structures

```razor
@if (Model.IsPublished)
{
    <span class="badge badge-success">Published</span>
}
else
{
    <span class="badge badge-warning">Draft</span>
}

@foreach (var item in Model.Items)
{
    <li>@item.Name</li>
}
```

## View Organization

### Layout Pages
- `_Layout.cshtml` - Main layout
- `_ValidationScriptsPartial.cshtml` - Validation scripts

### View Structure
```
Views/
??? Shared/           # Shared views and partials
?   ??? _Layout.cshtml
?   ??? _ValidationScriptsPartial.cshtml
?   ??? Error.cshtml
??? Home/         # Home controller views
?   ??? Index.cshtml
?   ??? Privacy.cshtml
??? _ViewStart.cshtml # Sets default layout
```

## Partial Views

Reusable view components:

```razor
@* Render a partial view *@
@await Html.PartialAsync("_DocumentCard", document)

@* Or using tag helper *@
<partial name="_DocumentCard" model="document" />
```

## View Components

For more complex reusable UI:

```csharp
public class RecentDocumentsViewComponent : ViewComponent
{
    public async Task<IViewComponentResult> InvokeAsync(int count)
    {
    // Logic here
        return View(model);
    }
}
```

Usage in view:
```razor
@await Component.InvokeAsync("RecentDocuments", new { count = 5 })
```

## Tag Helpers

### Form Tag Helpers

```razor
<form asp-controller="Document" asp-action="Create" method="post">
    <div class="form-group">
  <label asp-for="Title"></label>
        <input asp-for="Title" class="form-control" />
        <span asp-validation-for="Title" class="text-danger"></span>
    </div>
    
    <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

### Anchor Tag Helpers

```razor
<a asp-controller="Document" asp-action="Details" asp-route-id="@Model.Id">
    View Details
</a>
```

## Sections

Define sections in views for content injection:

```razor
@* In _Layout.cshtml *@
@RenderSection("Scripts", required: false)

@* In view *@
@section Scripts {
    <script src="~/js/custom.js"></script>
}
```

## Best Practices

1. Keep views simple - no business logic
2. Use strongly-typed models (`@model`)
3. Leverage tag helpers for cleaner markup
4. Use partial views for reusable UI
5. Implement proper HTML encoding (automatic with @)
6. Organize views by controller
7. Use layouts for consistent structure
8. Add comments for complex markup

## Strongly Typed Views

Always declare model type:
```razor
@model WikiTest.Web.Models.DocumentViewModel

@* Now you have IntelliSense and type safety *@
<h1>@Model.Title</h1>
```

## HTML Helpers vs Tag Helpers

Tag helpers (preferred):
```razor
<label asp-for="Title"></label>
<input asp-for="Title" />
```

HTML helpers (legacy):
```razor
@Html.LabelFor(m => m.Title)
@Html.TextBoxFor(m => m.Title)
```
