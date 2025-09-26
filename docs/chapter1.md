# Chapter 1: Web Application Basics

## Learning Goals
By the end of this chapter, you will:
- Understand how **HTTP requests/responses** work in modern web applications.
- See how to make **HTTP requests in C#** without using a browser.
- Learn the basics of **HTML** for ASP.NET Core web apps.
- Understand how **ASP.NET Core runs on Kestrel/IIS** in Visual Studio 2022.
- Build a simple **HTTP Request Console App** using .NET 8 minimal APIs.

---

## How Modern Web Apps Work
Modern web apps rely on three main technologies:
1. **HTTP/HTTPS** --> How clients and servers communicate.
2. **HTML & CSS** --> How browsers render content.
3. **ASP.NET Core Middleware & Hosting** --> How your app runs and handles requests.

Unlike old ASP.NET Web Forms (IIS tightly coupled with System.Web), **ASP.NET Core** apps run cross-platform on **Kestrel** (a built-in high-performance web server) and can optionally be reverse-proxied via **IIS or Nginx** in production.

---

## Understanding HTTP Requests
Key HTTP methods you will use:
- **GET** --> Fetch data (e.g., open a web page).
- **POST** --> Send data to the server (e.g., form submissions).
- **PUT/PATCH** --> Update existing data.
- **DELETE** --> Remove data.

A simple request to `https://localhost:5001/hello` might look like: 
```
GET /hello HTTP/1.1
Host: localhost:5001
User-Agent: Mozilla/5.0
Accept: text/html
```
And the response:
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Content-Length: 27

<h1>Hello from ASP.NET Core!</h1>
```

---
## Making HTTP Requests Without a Browser
Instead of using the old `WebRequest`, modern .NET uses **`HttpClient`**:
**Modern C# Console App Example (.NET 8)
```cs
using System.Net.Http;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        using HttpClient client = new HttpClient();
        string result = await client.GetStringAsync("https://www.microsoft.com");
        Console.WriteLine(result.Substring(0, 200));    // Print first 200 chars
    }
}
```
Run with:
```bash
dotnet new console -n WebRequestorApp
dotnet run
```
This will fetch the HTML content from Microsoft's homepage.

---

## HTML Basics Refresher
Modern ASP.NET Core apps use **Razor Pages** or **Blazor**, but you still need to know basic HTML.
Example static HTML page:
```html
```


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

