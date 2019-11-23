---
title: Korzystanie z serwera bazy danych uruchomionego jako kontener
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Korzystasz z serwera bazy danych działającego jako kontener? tylko na potrzeby programowania! Dowiedz się, dlaczego.
ms.date: 10/02/2018
ms.openlocfilehash: a508ba734525b24e2f3f00408e2c59c8c00f1898
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291306"
---
# <a name="using-a-database-server-running-as-a-container"></a>Korzystanie z serwera bazy danych uruchomionego jako kontener

Możesz mieć bazy danych (SQL Server, PostgreSQL, MySQL itp.) na zwykłych serwerach autonomicznych, w klastrach lokalnych lub w usługach PaaS Services w chmurze, takich jak Azure SQL DB. Jednak w środowiskach deweloperskich i testowych, które bazy danych działają jako kontenery są wygodne, ponieważ nie istnieje żadna zależność zewnętrzna i po prostu uruchomienie `docker-compose up` polecenie uruchamia całą aplikację. Posiadanie tych baz danych jako kontenerów jest również doskonałe dla testów integracji, ponieważ baza danych została uruchomiona w kontenerze i jest zawsze wypełniana tymi samymi przykładowymi danymi, dzięki czemu testy mogą być bardziej przewidywalne.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server działa jako kontener z bazą danych z mikrousługą

W eShopOnContainers istnieje kontener o nazwie SQL. dane zdefiniowane w pliku [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , który działa SQL Server dla systemu Linux ze wszystkimi bazami danych SQL Server, które są zbędne dla mikrousług. (Możliwe jest również posiadanie jednego kontenera SQL Server dla każdej bazy danych, ale może to wymagać większej ilości pamięci przypisanej do platformy Docker). Ważnym punktem w mikrousług jest to, że każda mikrousługa jest właścicielem powiązanych danych, w związku z czym w tym przypadku jest związana z nią baza danych SQL. Jednak bazy danych mogą znajdować się w dowolnym miejscu.

Kontener SQL Server w przykładowej aplikacji jest skonfigurowany przy użyciu następującego kodu YAML w pliku Docker-Compose. yml, który jest wykonywany podczas uruchamiania `docker-compose up`. Należy pamiętać, że kod YAML ma skonsolidowane informacje o konfiguracji z pliku Generic Docker-Compose. yml oraz pliku Docker-Compose. override. yml. (Zazwyczaj należy oddzielić ustawienia środowiska od podstawowej lub statycznej informacji powiązanej z obrazem SQL Server).

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

W podobny sposób, zamiast używać `docker-compose`, następujące polecenie `docker run` może uruchomić ten kontener:

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Jednak w przypadku wdrażania aplikacji z wieloma kontenerami, takich jak eShopOnContainers, wygodniejsze jest użycie polecenia `docker-compose up`, aby wdrożyć wszystkie wymagane kontenery dla aplikacji.

Po pierwszym uruchomieniu tego kontenera SQL Server Kontener inicjuje SQL Server przy użyciu podania hasła. Gdy SQL Server jest uruchomiony jako kontener, możesz zaktualizować bazę danych, łącząc się za pośrednictwem dowolnego zwykłego połączenia SQL, takiego jak z SQL Server Management Studio, Visual Studio lub C\# Code.

Aplikacja eShopOnContainers inicjuje każdą mikrousługą bazę danych z przykładowymi danymi, umieszczając je w danych podczas uruchamiania, jak wyjaśniono w poniższej sekcji.

Posiadanie SQL Server działającego jako kontenera nie jest samo przydatne w przypadku pokazu, w którym może nie mieć dostępu do wystąpienia SQL Server. Jak zauważono, jest to również idealne rozwiązanie w środowiskach deweloperskich i testowych, dzięki czemu można łatwo uruchomić testy integracji zaczynające się od czystego obrazu SQL Server i znanych danych, umieszczając nowe przykładowe dane.

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Uruchamianie obrazu SQL Server Docker w systemie Linux, Mac lub Windows** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Łączenie i SQL Server on Linux zapytań przy użyciu narzędzia sqlcmd** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Umieszczanie danych testowych przy uruchamianiu aplikacji sieci Web

Aby dodać dane do bazy danych podczas uruchamiania aplikacji, można dodać kod podobny do poniższego do metody Configure w klasie startowej projektu interfejsu API sieci Web:

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

Poniższy kod w niestandardowej klasie CatalogContextSeed wypełnia dane.

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

Po uruchomieniu testów integracji istnieje możliwość generowania danych spójnych z testami integracji. Możliwość tworzenia wszystkiego od podstaw, w tym wystąpienia SQL Server działającego w kontenerze, doskonale sprawdza się w środowiskach testowych.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core bazę danych inMemory, a SQL Server działa jako kontener

Innym dobrym wyborem w przypadku uruchamiania testów jest użycie dostawcy bazy danych inMemory Entity Framework. Możesz określić tę konfigurację w metodzie ConfigureServices klasy Start w projekcie interfejsu API sieci Web:

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

Istnieje ważna połowa, chociaż. Baza danych w pamięci nie obsługuje wielu ograniczeń, które są specyficzne dla konkretnej bazy danych. Na przykład możesz dodać unikatowy indeks do kolumny w modelu EF Core i napisać test do bazy danych w pamięci, aby sprawdzić, czy nie zezwala na dodanie zduplikowanej wartości. Ale w przypadku korzystania z bazy danych w pamięci nie można obsłużyć unikatowych indeksów w kolumnie. W związku z tym baza danych znajdująca się w pamięci nie zachowuje się dokładnie tak samo jak rzeczywista SQL Server baza danych — nie emuluje ograniczeń specyficznych dla bazy danych.

Nawet w takim przypadku baza danych znajdująca się w pamięci jest nadal przydatna do testowania i tworzenia prototypów. Jeśli jednak chcesz utworzyć dokładne testy integracji, które uwzględniają zachowanie określonej implementacji bazy danych, musisz użyć prawdziwej bazy danych, takiej jak SQL Server. W tym celu uruchomienie SQL Server w kontenerze jest doskonałym wyborem i jest bardziej dokładne niż dostawca bazy danych inMemory EF Core.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Używanie usługi pamięci podręcznej Redis działającej w kontenerze

Można uruchamiać Redis w kontenerze, szczególnie w przypadku projektowania i testowania oraz dla scenariuszy weryfikacji koncepcji. Ten scenariusz jest wygodny, ponieważ możesz mieć wszystkie zależności działające w kontenerach — nie tylko dla lokalnych maszyn deweloperskich, ale dla środowisk testowych w potokach ciągłej integracji/ciągłego dostarczania.

Jednak po uruchomieniu Redis w środowisku produkcyjnym lepiej jest wyszukać rozwiązanie wysokiej dostępności, takie jak Redis Microsoft Azure, które działa jako PaaS (platforma jako usługa). W kodzie należy jedynie zmienić parametry połączenia.

Redis udostępnia obraz platformy Docker z Redis. Ten obraz jest dostępny z poziomu usługi Docker Hub pod tym adresem URL:

<https://hub.docker.com/\_/redis/>

Można bezpośrednio uruchomić kontener Docker Redis, wykonując następujące polecenie Docker CLI w wierszu polecenia:

```console
docker run --name some-redis -d redis
```

Obraz Redis obejmuje Uwidacznianie: 6379 (port używany przez Redis), więc łączenie kontenerów standardowych będzie automatycznie dostępne dla połączonych kontenerów.

W programie eShopOnContainers Usługa Service w koszyku. API używa pamięci podręcznej Redis działającej jako kontener. Ten koszyk. kontener danych jest definiowany jako część pliku Docker-Compose. yml z wielokontenerem, jak pokazano w następującym przykładzie:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Ten kod w Docker-Compose. yml definiuje kontener o nazwie koszyk. dane oparte na obrazie Redis i publikują port 6379 wewnętrznie, co oznacza, że będzie dostępny tylko z innych kontenerów uruchomionych w ramach hosta platformy Docker.

Na koniec w pliku Docker-Compose. override. yml, The koszyk. API mikrousługi dla przykładu eShopOnContainers definiuje parametry połączenia do użycia dla tego kontenera Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Jak wspomniano wcześniej, nazwa "koszyka mikrousług" jest rozpoznawana przez system DNS w sieci wewnętrznej platformy Docker.

>[!div class="step-by-step"]
>[Poprzedni](multi-container-applications-docker-compose.md)
>[Następny](integration-event-based-microservice-communications.md)
