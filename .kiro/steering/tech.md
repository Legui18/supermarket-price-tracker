
# Stack y reglas técnicas

- Lenguaje y plataforma: C# con .NET 10 (LTS). No mezclar versiones entre proyectos.
- Base de datos: SQL Server con EF Core 10. Migraciones con `dotnet ef`.
- API: ASP.NET Core Web API con Swagger.
- Tareas programadas: Worker Service con PeriodicTimer. No usar Hangfire.
- Scraping: HttpClient contra APIs públicas. Playwright solo si no hay otra opción.
- Pruebas: xUnit. Toda lógica de negocio nueva debe tener pruebas.
- Resiliencia: Polly para reintentos en llamadas HTTP.
- Logs: ILogger con logs estructurados.
- Respetar robots.txt y términos de uso. Máximo 1 petición por segundo por tienda,
  con User-Agent identificable. No guardar datos personales.

# Reglas de código

- Un Repository por entidad, con interfaz en Application e implementación en Infrastructure.
- Cero lógica de negocio en controladores: solo reciben, llaman a un servicio y devuelven.
- Inyección de dependencias para todo. Nada de `new` de servicios.
- Async/await con CancellationToken en todo método que haga I/O.
- Nombres en inglés para código; textos de usuario en español.
- Un commit por tarea, con mensaje en formato convencional (feat, fix, docs, test, chore).
- Nunca escribir contraseñas ni cadenas de conexión reales en el código ni en archivos versionados.
