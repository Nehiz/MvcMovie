# Nehik's Movies - ASP.NET Core MVC Application

A full-featured ASP.NET Core 8.0 MVC web application for managing and browsing a personal movie collection. Built following the Microsoft ASP.NET Core MVC tutorial series with custom enhancements.

## Features

✅ **Complete CRUD Operations**
- Create, Read, Update, and Delete movies
- Full form validation with data annotations
- Antiforgery protection for data modification

✅ **Advanced Search & Filtering**
- Search movies by title (case-insensitive)
- Filter by genre with dynamic dropdown
- Filter by release year (year or newer)
- Combined filtering capabilities

✅ **Data Validation**
- Required field validation
- String length constraints
- Regular expressions for genre and rating
- Price range validation (1-100)
- Client-side and server-side validation

✅ **Professional Styling**
- Bootstrap CSS framework integration
- Custom padding for form inputs
- Responsive design
- Clean, modern UI

✅ **Database & Persistence**
- SQLite database with Entity Framework Core
- Code-first migrations
- Automatic data seeding
- 7 pre-loaded sample movies

## Technology Stack

- **Framework**: ASP.NET Core 8.0
- **Language**: C# 12
- **ORM**: Entity Framework Core 8.0
- **Database**: SQLite
- **View Engine**: Razor
- **Styling**: Bootstrap 5
- **Validation**: Data Annotations + jQuery Validation

## Prerequisites

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [Git](https://git-scm.com/)

## Getting Started

### Clone the Repository
```bash
git clone https://github.com/Nehiz/MvcMovie.git
cd MvcMovie
```

### Build the Project
```bash
dotnet build
```

### Apply Database Migrations
```bash
dotnet ef database update
```

### Run the Application
```bash
dotnet run
```

The application will start on `http://localhost:5207`

## Project Structure

```
MvcMovie/
├── Controllers/
│   ├── HomeController.cs
│   ├── HelloWorldController.cs
│   └── MoviesController.cs
├── Models/
│   ├── Movie.cs
│   ├── MovieGenreViewModel.cs
│   ├── SeedData.cs
│   └── ErrorViewModel.cs
├── Views/
│   ├── Movies/
│   │   ├── Index.cshtml
│   │   ├── Create.cshtml
│   │   ├── Edit.cshtml
│   │   ├── Details.cshtml
│   │   └── Delete.cshtml
│   ├── Shared/
│   │   └── _Layout.cshtml
│   └── Home/
├── Data/
│   └── MvcMovieContext.cs
├── Migrations/
│   ├── 20260330194357_InitialCreate.cs
│   ├── 20260330203044_Rating.cs
│   └── 20260330203750_DataAnnotations_Validation.cs
├── wwwroot/
│   ├── css/
│   └── lib/
└── Program.cs
```

## Movie Model

The Movie entity includes the following properties:

- **Id** - Unique identifier (Primary Key)
- **Title** - Movie title (Required, 3-60 characters)
- **ReleaseDate** - Release date (Required)
- **Genre** - Movie genre (Required, 1-30 characters, starts with uppercase)
- **Price** - Price in USD (1-100 range, formatted as decimal)
- **Rating** - Movie rating (Required, 1-5 characters, regex validated)

### Validation Rules

```csharp
[StringLength(60, MinimumLength = 3)]
[Required]
public string? Title { get; set; }

[RegularExpression(@"^[A-Z]+[a-zA-Z\s]*$")]
[Required]
[StringLength(30)]
public string? Genre { get; set; }

[Range(1, 100)]
[DataType(DataType.Currency)]
public decimal Price { get; set; }

[RegularExpression(@"^[A-Z]+[a-zA-Z0-9""'\s-]*$")]
[StringLength(5)]
[Required]
public string? Rating { get; set; }
```

## Seed Data

The application automatically seeds 7 sample movies on first run:

1. When Harry Met Sally (1989)
2. Ghostbusters (1984)
3. Ghostbusters 2 (1986)
4. Rio Bravo (1959)
5. Inception (2010)
6. The Shawshank Redemption (1994)
7. Pulp Fiction (1994)

## Usage Guide

### Viewing Movies
- Navigate to **My Movies** page to see all movies
- Use the filter options to search by title, genre, or year

### Creating a Movie
1. Click **Create New**
2. Fill in all required fields
3. Click **Create** to save

### Editing a Movie
1. Click **Edit** on any movie
2. Modify the fields as needed
3. Click **Save** to update

### Deleting a Movie
1. Click **Delete** on any movie
2. Review the movie details
3. Click **Delete** to confirm removal

## Database Migrations

View all applied migrations:
```bash
dotnet ef migrations list
```

Add a new migration:
```bash
dotnet ef migrations add MigrationName
```

Update database:
```bash
dotnet ef database update
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/Movies` | List all movies |
| GET | `/Movies/Details/{id}` | View movie details |
| GET | `/Movies/Create` | Show create form |
| POST | `/Movies/Create` | Create new movie |
| GET | `/Movies/Edit/{id}` | Show edit form |
| POST | `/Movies/Edit/{id}` | Update movie |
| GET | `/Movies/Delete/{id}` | Show delete confirmation |
| POST | `/Movies/Delete/{id}` | Delete movie |

## Security Features

- **CSRF Protection**: `[ValidateAntiForgeryToken]` on all state-changing operations
- **Null Validation**: Input validation on movie IDs
- **Model Binding**: `[Bind]` attribute restricts properties that can be modified
- **SQL Injection Prevention**: EF Core parameterized queries
- **Input Validation**: Data annotations enforce business rules

## Development

### Run in Development Mode
```bash
dotnet run --launch-profile "https"
```

### Watch Mode (Auto-rebuild)
```bash
dotnet watch run
```

### View Entity Framework Logs
Logs are automatically output to the console during database operations.

## Future Enhancements

- [ ] User authentication and authorization
- [ ] Movie ratings and reviews
- [ ] Favorite movies collection
- [ ] Movie recommendations
- [ ] API endpoints for mobile apps
- [ ] Advanced search with full-text search
- [ ] Import/Export functionality

## License

This project is open source and available under the MIT License.

## Author

**Nehik** - [GitHub Profile](https://github.com/Nehiz)

## References

- [Microsoft ASP.NET Core MVC Tutorial](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app)
- [Entity Framework Core Documentation](https://docs.microsoft.com/en-us/ef/core/)
- [ASP.NET Core Security](https://docs.microsoft.com/en-us/aspnet/core/security/)

---

**Last Updated**: March 30, 2026  
**Framework Version**: ASP.NET Core 8.0  
**Status**: ✅ Complete and Functional
