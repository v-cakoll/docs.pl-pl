---
title: Korzystanie z serwera bazy danych uruchomionego jako kontener
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Za pomocą serwera bazy danych uruchomionego jako kontener? tylko w celach deweloperskich! Dowiedz się, dlaczego.
ms.date: 10/02/2018
ms.openlocfilehash: 5fd92a28a09cab041225c4c817a10f5ecfedc038
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639733"
---
# <a name="using-a-database-server-running-as-a-container"></a>Korzystanie z serwera bazy danych uruchomionego jako kontener

Bazy danych (SQL Server, PostgreSQL, MySQL itp.) mogą mieć na regularne autonomicznymi serwerami lokalnymi klastrami lub usługi PaaS w chmurze, takich jak bazy danych SQL Azure. Jednak w przypadku środowiska deweloperskie i testowe, o bazy danych zainstalowany jako kontenerów jest wygodne, ponieważ nie masz wszelkich zależności zewnętrznych, a po prostu `docker-compose up` polecenie uruchamia całej aplikacji. Tych baz danych w postaci kontenerów jest również bardzo przydatne na potrzeby testów integracji, ponieważ baza danych jest uruchomiona w kontenerze i zawsze jest wypełniana przy użyciu tych samych danych przykładowych, aby testy mogą być bardziej przewidywalne.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Program SQL Server uruchomionego jako kontener z bazą danych związanych z mikrousług

W ramach aplikacji eShopOnContainers, to kontener o nazwie sql.data zdefiniowane w [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) pliku z programem SQL Server dla systemu Linux przy użyciu wszystkich baz danych programu SQL Server służące do mikrousług. (Może również mieć jeden kontener programu SQL Server dla każdej bazy danych, ale która wymaga większej ilości pamięci przypisana do platformy Docker). Istotną kwestią w mikrousługach to, czy każda mikrousługa jest właścicielem jego powiązanych danych, w związku z tym powiązanej bazie danych SQL w tym przypadku. Ale bazy danych może być dowolnym miejscu.

Kontener w przykładowej aplikacji dla programu SQL Server jest skonfigurowany przy użyciu poniższego kodu YAML w pliku docker-compose.yml, który zostanie wykonany po uruchomieniu `docker-compose up`. Należy pamiętać, że kodu YAML ma skonsolidowanych informacji o konfiguracji z pliku docker-compose.yml ogólny i pliku docker-compose.override.yml. (Zazwyczaj będzie oddzielne ustawienia środowiska z podstawowej lub statyczna informacje związane z obrazu programu SQL Server.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

W podobny sposób, zamiast `docker-compose`, następujące `docker run` polecenia można uruchomić tego kontenera:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Jednakże, Jeżeli wdrażasz aplikację obsługującą wiele kontenerów, takich jak ramach aplikacji eShopOnContainers jest bardziej wygodne do użycia `docker-compose up` polecenia, aby go służy do wdrażania wszystkich wymaganych kontenerów dla aplikacji.

Po uruchomieniu tego kontenera programu SQL Server po raz pierwszy kontener inicjuje programu SQL Server przy użyciu hasła, które należy podać. Gdy program SQL Server działa jako kontener, można zaktualizować bazy danych, nawiązując połączenie za pomocą dowolnego regularne połączenia SQL, takich jak SQL Server Management Studio, Visual Studio lub C\# kodu.

Aplikacja w ramach aplikacji eShopOnContainers inicjuje każdej mikrousługi bazy danych, z przykładowymi danymi rozmieszczania je z danymi podczas uruchamiania, zgodnie z opisem w poniższej sekcji.

O programu SQL Server uruchomionego jako kontener nie jest po prostu użyteczne pokaz których możesz nie mieć dostępu do wystąpienia programu SQL Server. Jak wspomniano to również doskonałe rozwiązanie dla środowisk programowania i testowania, aby łatwo można uruchamiać testy integracji, zaczynając od czysty obraz programu SQL Server i znane dane przez wstępne wypełnienie nowe dane przykładowe.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Uruchamianie obrazu platformy Docker programu SQL Server w systemie Linux, Mac lub Windows** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Połączenie i wykonywać zapytania programu SQL Server w systemie Linux przy użyciu narzędzia sqlcmd** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Rozmieszczanie za pomocą danych testowych podczas uruchamiania aplikacji sieci Web

Aby dodać dane do bazy danych, podczas uruchamiania aplikacji, można dodać kod, podobnie do następującej metody Konfiguruj w klasie uruchamiania projektu interfejsu API sieci Web:

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

Poniższy kod w niestandardowej klasy CatalogContextSeed zostaną wyświetlone wszystkie dane.

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

Kiedy uruchamiasz testy integracji, sposób, aby wygenerować dane spójne z testów integracji jest przydatne. Możliwość tworzenia wszystkiego, od początku, w tym wystąpienia programu SQL Server działającego w kontenerze, to doskonałe rozwiązanie dla środowisk testowych.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory Database a baza danych programu SQL Server uruchomionego jako kontener

Innym dobrym wyborem podczas przeprowadzania testów polega na użyciu dostawca bazy danych programu Entity Framework InMemory. Tę konfigurację można określić w metodzie ConfigureServices klasy uruchamiania w projekcie interfejsu API sieci Web:

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...

}
```

Istnieje jednak ważne catch. Bazy danych w pamięci nie obsługuje wiele ograniczeń, które są specyficzne dla konkretnej bazy danych. Na przykład możesz dodać unikatowego indeksu dla kolumny w modelu platformy EF Core i napisać test względem bazy danych w pamięci w celu sprawdzenia, czy on nie zezwala na dodawanie zduplikowane wartości. Jednak podczas korzystania z bazy danych w pamięci nie może obsługiwać indeksy unikatowe dla kolumny. W związku z tym, bazy danych w pamięci nie zachowywać się tak samo jak rzeczywista baza danych programu SQL Server — nie nie emulować ograniczeń określonej bazy danych.

Nawet w takim przypadku baza danych w pamięci nadal jest użyteczne do testowania i tworzenia prototypów. Ale jeśli chcesz utworzyć testy integracji dokładne, które weź pod uwagę zachowanie wykonania konkretnej bazy danych, należy użyć rzeczywistego bazy danych, takich jak program SQL Server. W tym celu programem SQL Server w kontenerze jest doskonały wybór i bardziej precyzyjne niż dostawca bazy danych programu EF Core InMemory.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Za pomocą usługi pamięć podręczna Redis uruchomionej w kontenerze

Możesz uruchomić pamięci podręcznej Redis w kontenerze, szczególnie w przypadku tworzenia i testowania oraz scenariuszy weryfikacji koncepcji. Ten scenariusz jest wygodne, ponieważ masz wszystkie zależności systemem kontenerów — nie tylko dla maszyn lokalnych rozwoju, ale dla środowisk testowych w potoków ciągłej integracji/ciągłego wdrażania.

Po uruchomieniu usługi Redis w środowisku produkcyjnym zaleca się wyszukać rozwiązanie o wysokiej dostępności, takich jak Redis platformy Microsoft Azure, która jest uruchamiana jako usługi PaaS (platforma jako usługa). W kodzie wystarczy zmienić parametry połączenia.

Usługa redis zapewnia obrazu platformy Docker przy użyciu usługi Redis. Ten obraz jest dostępny z usługi Docker Hub pod tym adresem URL:

<https://hub.docker.com/\_/redis/>

Można bezpośrednio uruchomić kontener platformy Docker, Redis, wykonując następujące polecenie interfejsu wiersza polecenia platformy Docker w wierszu polecenia:

```
  docker run --name some-redis -d redis
```

Obraz usługi Redis zawiera udostępniają: 6379 (port używany przez usługi Redis), więc standardowa łączenie kontenera udostępnienie jej automatycznie do połączonego kontenerów.

W ramach aplikacji eShopOnContainers mikrousługi basket.api korzysta z pamięci podręcznej Redis uruchomionego jako kontener. Ten kontener basket.data jest zdefiniowana jako części pliku z obsługą wielu kontenerów platformy docker-compose.yml, jak pokazano w poniższym przykładzie:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Ten kod w docker-compose.yml definiuje kontener o nazwie basket.data na podstawie obrazu usługi redis i publikowania port 6379 wewnętrznie, co oznacza, że będą dostępne tylko z innych kontenerów w ramach hosta platformy Docker.

Na koniec w pliku docker-compose.override.yml mikrousług basket.api dla przykładu w ramach aplikacji eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Jak wspomniano wcześniej, nazwa mikrousług "basket.data" został rozwiązany przez firmy docker wewnętrznej sieci DNS.

>[!div class="step-by-step"]
>[Poprzednie](multi-container-applications-docker-compose.md)
>[dalej](integration-event-based-microservice-communications.md)
