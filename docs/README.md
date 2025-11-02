# Documentation Index

This file serves as a guide to all documentation in the WikiTest project.

## Documentation Structure

WikiTest uses a hybrid documentation approach with both centralized and contextual documentation.

---

## ?? Centralized Documentation (`/docs`)

### ?? For End Users (`/docs/Users/`)

| Document | Description | Audience |
|----------|-------------|----------|
| [Getting Started](Users/GettingStarted.md) | Quick start guide for new users | End Users |
| [User Guide](Users/UserGuide.md) | Comprehensive user manual | End Users |

### ?? For Developers (`/docs/Developers/`)

| Document | Description | Audience |
|----------|-------------|----------|
| [Architecture](Developers/Architecture.md) | System architecture overview | Developers |
| [Development Setup](Developers/DevelopmentSetup.md) | Local development environment setup | Developers |
| [Job Timing](Developers/JobTiming.md) | Scheduled tasks and background jobs | Developers |

### ?? For Operations (`/docs/Operations/`)

| Document | Description | Audience |
|----------|-------------|----------|
| [Business Logic](Operations/BusinessLogic.md) | Core business rules and workflows | Operations, Developers |
| [Admin Processes](Operations/AdminProcesses.md) | Administrative procedures | Operations, Admins |
| [Monitoring & Support](Operations/MonitoringAndSupport.md) | System monitoring and incident response | Operations, Support |

---

## ?? Contextual Documentation (Component READMEs)

Documentation that lives next to the code it describes:

### Web Application (`/WikiTest.Web/`)

| Location | Description | Topics Covered |
|----------|-------------|----------------|
| [WikiTest.Web/README.md](../WikiTest.Web/README.md) | Application entry point and configuration | Program.cs, DI, Middleware, Configuration |
| [Controllers/README.md](../WikiTest.Web/Controllers/README.md) | Controller patterns and practices | MVC Controllers, Routing, Action Results |
| [Models/README.md](../WikiTest.Web/Models/README.md) | Model conventions and validation | Domain Models, ViewModels, Validation |
| [Views/README.md](../WikiTest.Web/Views/README.md) | Razor syntax and view guidelines | Razor Syntax, Tag Helpers, Layouts |
| [wwwroot/README.md](../WikiTest.Web/wwwroot/README.md) | Static file organization | CSS, JavaScript, Images, LibMan |

---

## ??? Documentation by Topic

### Getting Started
1. Start with [Getting Started](Users/GettingStarted.md)
2. Review [Development Setup](Developers/DevelopmentSetup.md) for local environment
3. Understand the [Architecture](Developers/Architecture.md)

### Development
1. [Development Setup](Developers/DevelopmentSetup.md) - Environment configuration
2. [Architecture](Developers/Architecture.md) - System design
3. [WikiTest.Web/README.md](../WikiTest.Web/README.md) - Application structure
4. Component-specific READMEs for detailed guidance

### Operations & Administration
1. [Business Logic](Operations/BusinessLogic.md) - Understand the rules
2. [Admin Processes](Operations/AdminProcesses.md) - Day-to-day procedures
3. [Monitoring & Support](Operations/MonitoringAndSupport.md) - Keep system healthy

### User Training
1. [Getting Started](Users/GettingStarted.md) - First steps
2. [User Guide](Users/UserGuide.md) - Complete feature walkthrough

---

## ?? Documentation Guidelines

### When to Use Centralized Docs (`/docs`)
- High-level concepts and architecture
- Cross-cutting concerns
- Process documentation
- User-facing documentation
- Documentation for multiple audiences

### When to Use Contextual READMEs
- Component-specific implementation details
- Code patterns and conventions
- Technical API documentation
- Framework-specific guidance
- Examples directly related to nearby code

### Keeping Documentation Current

**When making changes:**
- ? Update relevant documentation alongside code changes
- ? Review both centralized and contextual docs
- ? Update code examples to match implementation
- ? Add new sections for new features
- ? Archive or remove obsolete documentation

**Documentation review checklist:**
1. Does the code change affect any documented behavior?
2. Are code examples still accurate?
3. Do screenshots need updating?
4. Should new sections be added?
5. Are there links that need updating?

---

## ?? Quick Reference

### Common Tasks

| Task | Documentation |
|------|---------------|
| Set up development environment | [Development Setup](Developers/DevelopmentSetup.md) |
| Understand system architecture | [Architecture](Developers/Architecture.md) |
| Add a new controller | [Controllers/README.md](../WikiTest.Web/Controllers/README.md) |
| Create a view | [Views/README.md](../WikiTest.Web/Views/README.md) |
| Add static files | [wwwroot/README.md](../WikiTest.Web/wwwroot/README.md) |
| Configure the application | [WikiTest.Web/README.md](../WikiTest.Web/README.md) |
| Understand business rules | [Business Logic](Operations/BusinessLogic.md) |
| Perform admin tasks | [Admin Processes](Operations/AdminProcesses.md) |
| Troubleshoot issues | [Monitoring & Support](Operations/MonitoringAndSupport.md) |
| Help end users | [User Guide](Users/UserGuide.md) |

---

## ?? Contributing to Documentation

Good documentation is essential! When contributing:

1. **Be Clear**: Write for your audience
2. **Be Concise**: Get to the point quickly
3. **Use Examples**: Show, don't just tell
4. **Stay Current**: Update docs with code changes
5. **Be Consistent**: Follow existing patterns

### Markdown Tips

- Use headings to organize content
- Include code blocks with syntax highlighting
- Add links between related documents
- Use tables for structured information
- Include images/diagrams where helpful

---

## ?? Documentation Feedback

Found an issue or have suggestions?
- Create an issue on [GitHub](https://github.com/sbirvin1s/wikiTest/issues)
- Submit a pull request with improvements
- Contact the development team

---

*Last Updated: [Current Date]*
*Maintained by: WikiTest Development Team*
