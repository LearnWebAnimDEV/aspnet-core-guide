# Chapter 1: Web Application Basics

Learn the fundamentals of ASP.NET Core Web Applications.

## Topics Covered
- Introduction to ASP.NET Core
- MVC Architecture
- Request/Response Pipeline
- Hosting Models

---

## Interactive Code Example
```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/", () => "Hello, ASP.NET Core!");

app.Run();
```

Try running this example on [.NET Fiddle](https://dotnetfiddle.net/) or in your local environment.

---

## Quick Quiz

1. What is the purpose of the `MapGet` method?
2. Explain the request/response pipeline.
3. What does the `app.Run()` method do?

*Answers at the bottom of the page.*

---

### Answers
1. Maps a route to a request handler.
2. The middleware sequence that processes incoming requests.
3. Starts the web application and begins listening for requests.

---

