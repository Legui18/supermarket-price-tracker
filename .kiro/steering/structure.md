
# Estructura de la solución (Clean Architecture)

SupermarketPriceTracker.sln

- src/SupermarketPriceTracker.Domain: entidades, enums, reglas puras. Sin dependencias externas.
- src/SupermarketPriceTracker.Application: interfaces (repositories, ISupermarketScraper),
  servicios, DTOs. Depende solo de Domain.
- src/SupermarketPriceTracker.Infrastructure: EF Core, repositories, scrapers, HttpClient.
  Depende de Application.
- src/SupermarketPriceTracker.Worker: Worker Service que ejecuta el scraping programado.
- src/SupermarketPriceTracker.WebAPI: controladores, Swagger, configuración de DI.
- tests/SupermarketPriceTracker.Tests: pruebas xUnit.

Regla de dependencias: las flechas apuntan hacia Domain. Domain no conoce a nadie.
