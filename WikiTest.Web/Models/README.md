# Models Documentation

## Overview

Models represent the data and business logic of the application.

## Types of Models

### Domain Models
Represent core business entities
- Map to database tables (if using ORM)
- Contain business logic
- Validate data

### View Models
Data transfer objects for views
- Combine data from multiple sources
- Shape data for specific views
- May include UI-specific properties

### Input Models (DTOs)
Capture user input
- Used with form submissions
- Include validation attributes
- May differ from domain models

## Data Annotations

Common validation attributes:

```csharp
public class DocumentModel
{
    [Required(ErrorMessage = "Title is required")]
    [StringLength(200, MinimumLength = 3)]
    public string Title { get; set; }
    
    [Required]
    [Display(Name = "Document Content")]
    public string Content { get; set; }
    
    [EmailAddress]
    public string AuthorEmail { get; set; }
    
    [Range(1, 100)]
  public int CategoryId { get; set; }
}
```

## Model Validation

- Validation occurs automatically in controller actions
- Check `ModelState.IsValid` before processing
- Return view with model to show validation errors

## Best Practices

1. Keep models focused and cohesive
2. Use appropriate validation attributes
3. Separate concerns (domain vs view models)
4. Make properties nullable when appropriate
5. Use descriptive names
6. Add XML documentation comments

## Example Domain Model

```csharp
/// <summary>
/// Represents a document in the system
/// </summary>
public class Document
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }
    public DateTime CreatedDate { get; set; }
    public string AuthorId { get; set; }
    public bool IsPublished { get; set; }
}
```

## Example View Model

```csharp
/// <summary>
/// View model for displaying document list
/// </summary>
public class DocumentListViewModel
{
    public List<DocumentSummary> Documents { get; set; }
    public int TotalCount { get; set; }
    public int CurrentPage { get; set; }
    public int PageSize { get; set; }
}
```
