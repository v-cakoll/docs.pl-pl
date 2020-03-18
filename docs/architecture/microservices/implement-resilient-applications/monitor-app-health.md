---
title: Monitorowanie kondycji
description: Poznaj jeden ze sposobów wdrażania monitorowania kondycji.
ms.date: 03/02/2020
ms.openlocfilehash: d3d2bc72cf29b3d1ac93191e7ff2bd827c9ee68d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401712"
---
# <a name="health-monitoring"></a>Monitorowanie kondycji

Monitorowanie kondycji może umożliwić informacje w czasie zbliżeń do rzeczywistego o stanie kontenerów i mikrousług. Monitorowanie kondycji ma kluczowe znaczenie dla wielu aspektów obsługi mikrousług i jest szczególnie ważne, gdy koordynatorzy wykonują częściowe uaktualnienia aplikacji w fazach, jak wyjaśniono później.

Aplikacje oparte na mikrousługach często używają pulsów lub kontroli kondycji, aby umożliwić monitorom wydajności, harmonogramom i koordynatorom śledzenie wielu usług. Jeśli usługi nie mogą wysłać pewnego rodzaju sygnału "Żyję", na żądanie lub zgodnie z harmonogramem, aplikacja może napotkać ryzyko podczas wdrażania aktualizacji lub może po prostu wykryć błędy zbyt późno i nie być w stanie zatrzymać kaskadowych awarii, które mogą skończyć się poważnymi awariami.

W typowym modelu usługi wysyłają raporty o ich stanie, a te informacje są agregowane w celu zapewnienia ogólnego widoku stanu kondycji aplikacji. Jeśli używasz koordynatora, można podać informacje o kondycji do klastra koordynatora, tak aby klaster może działać odpowiednio. Jeśli inwestujesz w wysokiej jakości raportowanie kondycji dostosowane do aplikacji, możesz znacznie łatwiej wykrywać i rozwiązywać problemy z uruchomioną aplikacją.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Wdrażanie kontroli kondycji w ASP.NET podstawowych usługach

Podczas opracowywania mikrousługi ASP.NET Core lub aplikacji sieci web, można użyć wbudowanej funkcji sprawdzania kondycji, który został wydany w programie ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Podobnie jak wiele funkcji ASP.NET Core, kontrole kondycji są wyposażone w zestaw usług i zagęszawanie.

Usługi sprawdzania kondycji i urządzenia pośredniczenia są łatwe w użyciu i zapewniają funkcje, które umożliwiają sprawdzenie, czy zasób zewnętrzny potrzebny aplikacji (taki jak baza danych programu SQL Server lub zdalny interfejs API) działa poprawnie. Korzystając z tej funkcji, można również zdecydować, co to znaczy, że zasób jest w dobrej kondycji, jak wyjaśnić później.

Aby skutecznie korzystać z tej funkcji, należy najpierw skonfigurować usługi w mikrousługach. Po drugie, potrzebujesz aplikacji frontonu, która zapytań o raporty o kondycji. Ta aplikacja frontonu może być niestandardową aplikacją raportowania lub może być sam koordynator, który może odpowiednio reagować na stany kondycji.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Użyj funkcji HealthChecks w mikrousługach ASP.NET zaplecza

W tej sekcji dowiesz się, jak zaimplementować healthchecks funkcji w przykładowej aplikacji interfejsu API sieci Web ASP.NET Core 3.1 podczas korzystania z [pakietu Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) Implementacja tej funkcji w mikrousługach na dużą skalę, takich jak eShopOnContainers jest wyjaśnione w następnej sekcji.

Aby rozpocząć, należy zdefiniować, co stanowi stan w dobrej kondycji dla każdej mikrousługi. W przykładowej aplikacji definiujemy mikrousługi jest w dobrej kondycji, jeśli jego interfejs API jest dostępny za pośrednictwem protokołu HTTP i powiązanej bazy danych programu SQL Server jest również dostępna.

W programie .NET Core 3.1 za pomocą wbudowanych interfejsów API można skonfigurować usługi, dodać sprawdzanie kondycji mikrousługi i zależnej bazy danych programu SQL Server w ten sposób:

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check",
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]),
            HealthStatus.Unhealthy,
            new string[] { "orderingdb" });
}
```

W poprzednim kodzie `services.AddHealthChecks()` metoda konfiguruje podstawowe sprawdzanie HTTP, który zwraca kod stanu **200** z "Zdrowy".  Ponadto metoda `AddCheck()` rozszerzenia konfiguruje `SqlConnectionHealthCheck` niestandardowy, który sprawdza kondycję powiązanej bazy danych SQL.

Metoda `AddCheck()` dodaje nową kontrolę kondycji o określonej nazwie `IHealthCheck`i implementacji typu . Można dodać wiele kontroli kondycji przy użyciu AddCheck metody, więc mikrousługi nie zapewni stan "w dobrej kondycji", dopóki wszystkie jego kontrole są w dobrej kondycji.

`SqlConnectionHealthCheck`jest niestandardową klasą, która implementuje `IHealthCheck`, która przyjmuje parametry połączenia jako parametr konstruktora i wykonuje prostą kwerendę, aby sprawdzić, czy połączenie z bazą danych SQL zakończyło się pomyślnie. Zwraca, `HealthCheckResult.Healthy()` jeśli kwerenda została wykonana `FailureStatus` pomyślnie i z rzeczywistym wyjątkiem, gdy nie powiedzie się.

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

Należy zauważyć, `Select 1` że w poprzednim kodzie jest kwerenda używana do sprawdzania kondycji bazy danych. Aby monitorować dostępność mikrousług, koordynatorów, takich jak Kubernetes okresowo wykonywać kontrole kondycji przez wysyłanie żądań do testowania mikrousług. Ważne jest, aby zachować wydajność zapytań bazy danych, aby te operacje były szybkie i nie skutkują wyższym wykorzystaniem zasobów.

Na koniec dodaj firmę pośredniczą, która odpowiada na ścieżkę `/hc`adresu URL:

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

Po wywołaniu `<yourmicroservice>/hc` punktu końcowego uruchamia wszystkie kontrole kondycji, `AddHealthChecks()` które są skonfigurowane w metodzie w Startup klasy i pokazuje wynik.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementacja HealthChecks w eShopOnContainers

Mikrousługi w eShopOnContainers polegać na wielu usług, aby wykonać swoje zadanie. Na przykład `Catalog.API` mikrousługi z eShopOnContainers zależy od wielu usług, takich jak Azure Blob Storage, SQL Server i RabbitMQ. W związku z tym ma `AddCheck()` kilka kontroli kondycji dodane przy użyciu metody. Dla każdej usługi zależnej implementacji niestandardowej, `IHealthCheck` która definiuje jego odpowiedni stan kondycji należy dodać.

Projekt open source [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) rozwiązuje ten problem, udostępniając niestandardowe implementacje sprawdzania kondycji dla każdej z tych usług przedsiębiorstwa, które są zbudowane na zasadzie .NET Core 3.1. Każdy sprawdzanie kondycji jest dostępna jako pojedynczy pakiet NuGet, który można łatwo dodać do projektu. eShopOnContainers używa ich w znacznym stopniu we wszystkich swoich mikrousług.

Na przykład w `Catalog.API` mikrousługach dodano następujące pakiety NuGet:

![Zrzut ekranu przedstawiający pakiety AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Rysunek 8-7**. Niestandardowe kontrole kondycji zaimplementowane w interfejsie Catalog.API przy użyciu aspNetCore.Diagnostics.HealthChecks

W poniższym kodzie implementacje sprawdzania kondycji są dodawane dla każdej usługi zależnej, a następnie oprogramowanie pośredniczą jest skonfigurowany:

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

Na koniec dodaj healthcheck pośredniczy, aby nasłuchiwać punktu końcowego "/hc":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Zapytanie mikrousług, aby zgłosić ich stan kondycji

Po skonfigurowaniu kontroli kondycji zgodnie z opisem w tym artykule i masz mikrousługi uruchomione w platformie Docker, można bezpośrednio sprawdzić z przeglądarki, czy jest w dobrej kondycji. Musisz opublikować port kontenera w hoście platformy Docker, aby uzyskać dostęp `localhost`do kontenera za pośrednictwem zewnętrznego adresu IP hosta platformy Docker lub za pośrednictwem , jak pokazano na rysunku 8-8.

![Zrzut ekranu przedstawiający odpowiedź JSON zwróconą przez kontrolę kondycji.](./media/monitor-app-health/health-check-json-response.png)

**Rysunek 8-8**. Sprawdzanie stanu kondycji pojedynczej usługi za pomocą przeglądarki

W tym teście widać, `Catalog.API` że mikrousługi (uruchomione na porcie 5101) jest w dobrej kondycji, zwracając stan HTTP 200 i informacje o stanie w JSON. Usługa sprawdziła również kondycję zależności bazy danych programu SQL Server i RabbitMQ, więc sprawdzanie kondycji zgłosiło się jako w dobrej kondycji.

## <a name="use-watchdogs"></a>Korzystanie z watchdogs

Watchdog jest oddzielna usługa, która może oglądać kondycję i załadować w usługach `HealthChecks` i zgłosić kondycję mikrousług przez wykonywanie zapytań z biblioteki wprowadzone wcześniej. Może to pomóc w zapobieganiu błędy, które nie zostaną wykryte na podstawie widoku pojedynczej usługi. Watchdogs są również dobrym miejscem do obsługi kodu, który może wykonywać akcje korygujące dla znanych warunków bez interakcji użytkownika.

EShopOnContainers przykład zawiera stronę sieci web, która wyświetla przykładowe raporty z kontroli kondycji, jak pokazano na rysunku 8-9. Jest to najprostszy watchdog można mieć, ponieważ pokazuje tylko stan mikrousług i aplikacji sieci web w eShopOnContainers. Zazwyczaj watchdog również podejmuje działania, gdy wykrywa stany niezdrowe.

Na szczęście [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) udostępnia również pakiet [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet, który może służyć do wyświetlania wyników sprawdzania kondycji ze skonfigurowanych identyfikatorów URI.

![Zrzut ekranu przedstawiający stan kondycji systemu kontroli kondycji eShopOnContainers stanu kondycji.](./media/monitor-app-health/health-check-status-ui.png)

**Rysunek 8-9**. Przykładowy raport z kontroli kondycji w eShopOnContainers

Podsumowując, ta usługa watchdog wysyła zapytanie o punkt końcowy "/hc" każdej mikrousługi. Spowoduje to wykonanie wszystkich kontroli kondycji zdefiniowanych w nim i zwrócenie ogólnego stanu kondycji w zależności od wszystkich tych kontroli. HealthChecksUI jest łatwy do użycia z kilku wpisów konfiguracji i dwa wiersze kodu, który musi zostać dodany do Startup.cs usługi watchdog.

Przykładowy plik konfiguracji dla interfejsu użytkownika sprawdzania kondycji:

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

Startup.cs plik, który dodaje HealthChecksUI:

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>Kontrole kondycji podczas korzystania z koordynatorów

Aby monitorować dostępność mikrousług, koordynatorów, takich jak Kubernetes i sieci szkieletowej usług okresowo wykonywać kontrole kondycji przez wysyłanie żądań do testowania mikrousług. Gdy koordynator określa, że usługa/kontener jest w złej kondycji, zatrzymuje routingu żądań do tego wystąpienia. Zwykle tworzy również nowe wystąpienie tego kontenera.

Na przykład większość koordynatorów można użyć kontroli kondycji do zarządzania wdrożeniami zero-downtime. Tylko wtedy, gdy stan usługi/kontenera zmieni się w kondycję będzie koordynator uruchomić routingu ruchu do wystąpienia usługi/kontenera.

Monitorowanie kondycji jest szczególnie ważne, gdy koordynator wykonuje uaktualnienie aplikacji. Niektórzy koordynatorzy (jak azure service fabric) usługi aktualizacji w fazach — na przykład mogą zaktualizować jedną piątą powierzchni klastra dla każdego uaktualnienia aplikacji. Zestaw węzłów, który jest uaktualniany w tym samym czasie jest określany jako *domena uaktualnienia*. Po uaktualnieniu każdej domeny uaktualnienia i udostępnieniu jej użytkownikom ta domena uaktualnienia musi przejść testy kondycji, zanim wdrożenie przejdzie do następnej domeny uaktualnienia.

Innym aspektem kondycji usługi jest raportowanie metryk z usługi. Jest to zaawansowana zdolność modelu kondycji niektórych koordynatorów, takich jak sieć szkieletowa usług. Metryki są ważne podczas korzystania z koordynatora, ponieważ są one używane do równoważenia użycia zasobów. Metryki również może być wskaźnikiem kondycji systemu. Na przykład może mieć aplikację, która ma wiele mikrousług, a każde wystąpienie zgłasza metrykę żądań na sekundę (RPS). Jeśli jedna usługa używa więcej zasobów (pamięci, procesora itp.) niż inna usługa, koordynator może przenosić wystąpienia usługi w klastrze, aby spróbować utrzymać równomierne wykorzystanie zasobów.

Należy zauważyć, że sieć szkieletowa usług Azure udostępnia własny [model monitorowania kondycji,](/azure/service-fabric/service-fabric-health-introduction)który jest bardziej zaawansowany niż proste kontrole kondycji.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Zaawansowane monitorowanie: wizualizacja, analiza i alerty

Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raportowanie wydajności usługi i alerty po wykryciu problemu. Można użyć różnych rozwiązań dla tego aspektu monitorowania.

Można użyć prostych aplikacji niestandardowych pokazujących stan usług, takich jak strona niestandardowa pokazana podczas wyjaśniania [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Możesz też użyć bardziej zaawansowanych narzędzi, takich jak [Usługa Azure Monitor,](https://azure.microsoft.com/services/monitor/) aby podnieść alerty na podstawie strumienia zdarzeń.

Na koniec, jeśli przechowujesz wszystkie strumienie zdarzeń, możesz użyć usługi Microsoft Power BI lub innych rozwiązań, takich jak Kibana lub Splunk, aby zwizualizować dane.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **HealthChecks i HealthChecks interfejsu interfejsu pod kątem ASP.NET core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Wprowadzenie do monitorowania kondycji sieci szkieletowej usług** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitor** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Poprzedni](implement-circuit-breaker-pattern.md)
>[następny](../secure-net-microservices-web-applications/index.md)
