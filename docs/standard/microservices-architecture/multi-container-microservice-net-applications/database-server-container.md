---
title: "Za pomocą serwera bazy danych z uruchomionym jako kontener"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Za pomocą serwera bazy danych z uruchomionym jako kontener"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7e5f33c4e7edf9d0d4551c5125976fcb8fda392f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-database-server-running-as-a-container"></a>Za pomocą serwera bazy danych z uruchomionym jako kontener

Masz baz danych (SQL Server, PostgreSQL, MySQL itp.) na serwerach autonomicznych regularne w klastrach lokalnie lub w usługach PaaS w chmurze, takich jak bazy danych SQL Azure. Jednak dla środowisk projektowania i testowania, uruchomione jako kontenery baz danych jest wygodne, ponieważ nie ma żadnych zależności zewnętrznych i po prostu działa rozwiązania docker compose polecenie uruchamia całej aplikacji. O tych baz danych jako kontenery jest również doskonałe rozwiązanie dla testów integracji, ponieważ baza danych jest uruchomiona w kontenerze i jest zawsze wypełniane przy użyciu tego samego przykładowych danych, więc testów może być bardziej przewidywalne.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Program SQL Server uruchomiony jako kontener z bazą danych związanych z mikrousługi

W eShopOnContainers, ma kontenera o nazwie sql.data zdefiniowane w [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) pliku z programem SQL Server dla systemu Linux w przypadku wszystkich baz danych programu SQL Server wymagane dla mikrousług. (Można również mieć jeden kontener programu SQL Server dla każdej bazy danych, ale która wymaga więcej pamięci przypisana do Docker). Istotne w mikrousług jest czy każdego mikrousługi właścicielem jego danych powiązanych w związku z tym pokrewne bazę danych SQL w takim przypadku. Jednak bazy danych może być dowolnego miejsca.

SQL Server, kontenera w przykładowej aplikacji jest skonfigurowana z następującym kodem yaml programu w pliku docker-compose.yml, który zostanie wykonany po uruchomieniu rozwiązania docker-compose się. Należy pamiętać, że kod yaml programu ma skonsolidowane informacje o konfiguracji z pliku ogólnego docker-compose.yml i pliku docker compose.override.yml. (Zazwyczaj będzie odrębnych ustawień środowiska z podstawowej lub statycznej informacje związane z obrazu programu SQL Server.)

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

Następujące docker, uruchom polecenie można uruchomić tego kontenera:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

Jednak jeśli wdrażasz aplikacji kontenera usługi takie jak eShopOnContainers jest bardziej wygodne docker tworzą się polecenie, aby go wdraża wszystkich kontenerów wymagane dla aplikacji.

Po uruchomieniu tego kontenera programu SQL Server po raz pierwszy kontenera inicjuje programu SQL Server z musisz podać hasło. Gdy program SQL Server działa jako kontener, można zaktualizować bazy danych, nawiązując połączenie za pomocą dowolnego regularne połączenia SQL, takich jak SQL Server Management Studio, Visual Studio lub C\# kodu.

Aplikacji eShopOnContainers inicjuje każda baza danych mikrousługi z przykładowymi danymi przez wstępne wypełnienie go z danymi podczas uruchamiania, jak wyjaśniono w poniższej sekcji.

O programu SQL Server uruchomionego jako kontener nie jest po prostu ułatwia pokaz gdzie możesz utracić dostęp do wystąpienia programu SQL Server. Jakie zostały zanotowane jest również doskonałe rozwiązanie dla środowisk projektowych i testowych, aby łatwo można uruchamiać testy integracji, zaczynając od czystego obrazu programu SQL Server i znane dane przez wstępne wypełnienie nowego przykładowych danych.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Uruchom obrazu programu SQL Server Docker na systemie Linux, Mac lub Windows**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **Połącz i zapytania programu SQL Server w systemie Linux przy użyciu narzędzia sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Wstępne wypełnianie danymi testu podczas uruchamiania aplikacji sieci Web

Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można dodać kod podobnie do następującej metody konfiguracji w klasie uruchomienia projektu interfejsu API sieci Web:

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

Następujący kod w klasie CatalogContextSeed niestandardowe wypełnienie danych.

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

Po uruchomieniu testów integracji sposób generowania danych zgodne z testów integracji jest użyteczne. Możliwość tworzenia wszystko od początku, w tym wystąpienia programu SQL Server działające w kontenerze, jest doskonały dla środowisk testowych.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Baza danych Core InMemory EF i na serwerze SQL działa jako kontener

Inny dobry wybór w przypadku uruchamiania testów jest używanie dostawcy bazy danych programu Entity Framework InMemory. Tę konfigurację można określić w metodzie ConfigureServices Klasa początkowa w projekcie interfejsu API sieci Web:

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

Istnieje jednak ważne catch. Bazy danych w pamięci nie obsługuje wiele ograniczeń, które są specyficzne dla określonej bazy danych. Może na przykład Dodaj unikatowy indeks dla kolumny w modelu podstawowej EF i zapisu testu bazy danych w pamięci do sprawdzenia, czy jego nie zezwala na dodawanie zduplikowane wartości. Jednak podczas korzystania z bazy danych w pamięci nie może obsłużyć unikatowe indeksy w kolumnie. W związku z tym bazy danych w pamięci nie zachowują się tak samo jak rzeczywistych bazy danych SQL Server — nie nie emulować ograniczenia dotyczące bazy danych.

Mimo tego bazy danych w pamięci jest nadal przydatne w przypadku testowania i tworzenia prototypów. Ale jeśli chcesz utworzyć integracji dokładne testy, które wziąć pod uwagę zachowanie wykonania określonej bazy danych, należy użyć rzeczywistych bazy danych, takich jak SQL Server. W tym celu programem SQL Server w kontenerze jest doskonałym wyborem i dokładność niż EF Core InMemory dostawcy bazy danych.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Przy użyciu usługi pamięć podręczna Redis uruchomione w kontenerze

Możesz uruchomić Redis w kontenerze, szczególnie w przypadku projektowania i testowania i weryfikacja koncepcji. Ten scenariusz jest wygodne, ponieważ może mieć wszystkie zależności uruchomionych na kontenery — nie tylko maszyn rozwoju lokalnego, ale dla środowiska testowego w potokach użytkownika elementu konfiguracji/CD.

Po uruchomieniu Redis w środowisku produkcyjnym zaleca się poszukaj rozwiązania wysokiej dostępności, takich jak Redis Microsoft Azure, w którym jest uruchomiona jako PaaS (platforma jako usługa). W kodzie wystarczy zmienić parametry połączenia.

Redis zawiera obraz Docker z pamięci podręcznej Redis. Ten obraz jest dostępny z Centrum Docker pod tym adresem URL:

<https://Hub.docker.com/_/redis/>

Kontener Docker Redis można uruchomić bezpośrednio, wykonując następujące polecenie Docker interfejsu wiersza polecenia z wiersza polecenia:

```
  docker run --name some-redis -d redis
```

Obraz Redis obejmuje Uwidacznianie: 6379 (port używany przez Redis), więc standardowe łączenie kontenera udostępnienie jej automatycznie do połączonego kontenerów.

W eShopOnContainers mikrousługi basket.api korzysta z pamięci podręcznej Redis uruchomione jako kontener. Tego kontenera basket.data jest określony jako część pliku wielu kontenera docker-compose.yml, jak pokazano w poniższym przykładzie:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Ten kod w docker-compose.yml definiuje kontener o nazwie basket.data na podstawie obrazu redis i publikowania portu 6379 wewnętrznie, co oznacza, że będzie on dostępny tylko w innych kontenery uruchomiony w ramach hosta Docker.

Ponadto w pliku docker compose.override.yml mikrousługi basket.api przykładowej eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[Poprzednie] (kilku-container — aplikacje — docker-compose.md) [dalej] (integracji — zdarzenie — na podstawie mikrousługi communications.md)
