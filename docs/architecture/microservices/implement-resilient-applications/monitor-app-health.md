---
title: Monitorowanie kondycji
description: Poznaj jeden ze sposobów implementacji monitorowania kondycji.
ms.date: 01/30/2020
ms.openlocfilehash: a91e51af66049f9774365cd56b90ab792a4dd4fc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502684"
---
# <a name="health-monitoring"></a>Monitorowanie kondycji

Monitorowanie kondycji może umożliwić niemal w czasie rzeczywistym informacje o stanie kontenerów i mikrousług. Monitorowanie kondycji ma kluczowe znaczenie dla wielu aspektów mikrousług operacyjnych i jest szczególnie ważne, gdy koordynator wykonuje częściowe uaktualnienia aplikacji w fazach, jak wyjaśniono później.

Aplikacje oparte na mikrousługach często używają pulsu lub kontroli kondycji, aby umożliwić ich monitorom wydajności, harmonogramom i programom Orchestrator śledzenie wielu usług. Jeśli usługi nie mogą wysyłać niektórych rodzajów sygnałów "jestem aktywny", na żądanie lub zgodnie z harmonogramem, aplikacja może stanowić zagrożenie podczas wdrażania aktualizacji lub po prostu wykryć błędy zbyt późne i nie może zatrzymać błędów kaskadowych, które mogą zakończyć się w trakcie poważnych awarii.

W typowym modelu usługi wysyłają raporty dotyczące ich stanu, a informacje te są agregowane w celu zapewnienia ogólnego widoku stanu kondycji aplikacji. Jeśli używasz programu Orchestrator, możesz podać informacje o kondycji w klastrze programu Orchestrator, aby klaster mógł odpowiednio działać. Jeśli zainwestowano w Raportowanie kondycji o wysokiej jakości dostosowane do Twojej aplikacji, można łatwiej wykrywać i rozwiązywać problemy związane z uruchomioną aplikacją.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Implementowanie kontroli kondycji w usługach ASP.NET Core Services

Podczas tworzenia ASP.NET Core mikrousług lub aplikacji sieci Web można użyć wbudowanej funkcji kontroli kondycji wydanej w ASP .NET Core 3,1 ([Microsoft. Extensions. Diagnostics. HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Podobnie jak w przypadku wielu funkcji ASP.NET Core, sprawdzanie kondycji obejmuje zestaw usług i oprogramowanie pośredniczące.

Usługi sprawdzania kondycji i oprogramowanie pośredniczące są łatwe w użyciu i zapewniają możliwości umożliwiające sprawdzenie, czy dowolny zasób zewnętrzny wymagany dla aplikacji (na przykład baza danych SQL Server lub zdalny interfejs API) działa poprawnie. Korzystając z tej funkcji, można także zdecydować, co oznacza, że zasób jest w dobrej kondycji, jak wyjaśniono w przyszłości.

Aby efektywnie korzystać z tej funkcji, należy najpierw skonfigurować usługi w mikrousługach. Po drugie potrzebna jest aplikacja frontonu, która wykonuje zapytania dotyczące raportów kondycji. Aplikacja frontonu może być niestandardową aplikacją raportowania lub być samą koordynatorem, który może reagować odpowiednio do Stanów kondycji.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Korzystanie z funkcji HealthChecks w mikrousługach ASP.NET zaplecza

W tej sekcji dowiesz się, jak funkcja HealthChecks, zaimplementowana w [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks), jest używana w przykładowej aplikacji internetowego interfejsu API ASP.NET Core 3,1. Implementacja tej funkcji w mikrousługach o dużej skali, podobnie jak eShopOnContainers, została omówiona w dalszej części. Aby rozpocząć, należy określić, co stanowi prawidłowy stan dla każdej mikrousługi. W przykładowej aplikacji mikrousługi są w dobrej kondycji, jeśli interfejs API mikrousług jest dostępny za pośrednictwem protokołu HTTP i powiązana SQL Server baza danych jest również dostępna.

W programie .NET Core 3,1 z wbudowanymi interfejsami API można skonfigurować usługi, dodać kontrolę kondycji dla mikrousługi i jej zależną SQL Server bazę danych w następujący sposób:

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "OrderingDB-check",
            tags: new string[] { "orderingdb" });
}
```

W poprzednim kodzie Metoda `services.AddHealthChecks()` konfiguruje podstawową kontrolę HTTP, która zwraca kod stanu **200** z "zdrowy".  Ponadto Metoda rozszerzenia `AddCheck()` służy do konfigurowania niestandardowego `SqlConnectionHealthCheck`, który sprawdza kondycję powiązanej SQL Database.

Metoda `AddCheck()` dodaje nową kontrolę kondycji z określoną nazwą i implementacją typu `IHealthCheck`. Można dodać wiele kontroli kondycji za pomocą metody ADDCHECK, aby mikrousługa nie zapewniała stanu "zdrowy" do momentu, gdy wszystkie jego sprawdzenia nie będą w dobrej kondycji.

`SqlConnectionHealthCheck` jest klasą niestandardową implementującą `IHealthCheck`, która przyjmuje parametry połączenia jako parametr konstruktora i wykonuje proste zapytanie w celu sprawdzenia, czy połączenie z bazą danych SQL zostało pomyślnie zakończone. Zwraca `HealthCheckResult.Healthy()`, jeśli zapytanie zostało wykonane pomyślnie, a `FailureStatus` z rzeczywistym wyjątkiem, gdy kończy się niepowodzeniem.

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

Należy pamiętać, że w poprzednim kodzie `Select 1` jest zapytaniem używanym do sprawdzania kondycji bazy danych. Aby monitorować dostępność mikrousług, program Orchestrator, taki jak Kubernetes okresowo przeprowadza kontrolę kondycji, wysyłając żądania przetestowania mikrousług. Ważne jest, aby zachować wydajność zapytań bazy danych, aby te operacje były szybkie i nie powodowały większego użycia zasobów.

Na koniec Dodaj oprogramowanie pośredniczące, które odpowiada na ścieżkę URL `/hc`:

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc", new HealthCheckOptions()
        {
            Predicate = _ => true,
            ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
        });
        //...
    });
    //…
}
```

Po wywołaniu `<yourmicroservice>/hc` punktu końcowego program uruchamia wszystkie kontrole kondycji, które są skonfigurowane w metodzie `AddHealthChecks()` w klasie startowej i wyświetla wynik.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementacja HealthChecks w eShopOnContainers

Mikrousługi w eShopOnContainers polegają na wielu usługach do wykonywania zadań. Na przykład `Catalog.API` mikrousługa z eShopOnContainers zależy od wielu usług, takich jak Azure Blob Storage, SQL Server i RabbitMQ. W związku z tym ma kilka testów kondycji dodanych za pomocą metody `AddCheck()`. Dla każdej usługi zależnej należy dodać niestandardową implementację `IHealthCheck`, która definiuje jej odpowiedni stan kondycji.

Projekt Open Source [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) rozwiązuje ten problem, dostarczając niestandardowe implementacje sprawdzania kondycji dla każdej z tych usług przedsiębiorstwa, które są oparte na platformie .net Core 3,1. Każde Sprawdzanie kondycji jest dostępne jako pojedynczy pakiet NuGet, który można łatwo dodać do projektu. eShopOnContainers używa ich w szerokim stopniu we wszystkich mikrousługach.

Na przykład w mikrousłudze `Catalog.API` dodano następujące pakiety NuGet:

![Zrzut ekranu przedstawiający pakiety NuGet AspNetCore. Diagnostics. HealthChecks.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Rysunek 8-7**. Niestandardowe kontrole kondycji zaimplementowane w wykazie. interfejs API przy użyciu AspNetCore. Diagnostics. HealthChecks

W poniższym kodzie są dodawane implementacje sprawdzania kondycji dla poszczególnych usług zależnych, a następnie oprogramowanie pośredniczące jest skonfigurowane:

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

Na koniec Dodaj oprogramowanie pośredniczące HealthCheck, aby nasłuchiwać punktu końcowego "/HC":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Zbadaj mikrousługi, aby zgłosić ich stan kondycji

Po skonfigurowaniu kontroli kondycji zgodnie z opisem w tym artykule, gdy w programie Docker jest uruchomiona mikrousługa, możesz bezpośrednio sprawdzić ją z poziomu przeglądarki, jeśli jest w dobrej kondycji. Należy opublikować port kontenera na hoście platformy Docker, aby można było uzyskać dostęp do kontenera za pomocą adresu IP zewnętrznego hosta platformy Docker lub za pomocą `localhost`, jak pokazano na rysunku 8-8.

![Zrzut ekranu przedstawiający odpowiedź JSON zwróconą przez kontrolę kondycji.](./media/monitor-app-health/health-check-json-response.png)

**Rysunek 8-8**. Sprawdzanie stanu kondycji pojedynczej usługi z poziomu przeglądarki

W tym teście można zobaczyć, że `Catalog.API` mikrousługa (działająca na porcie 5101) jest w dobrej kondycji, zwracając stan HTTP 200 i informacje o stanie w formacie JSON. Usługa sprawdza również kondycję SQL Server zależność bazy danych i RabbitMQ, więc Sprawdzenie kondycji zgłoszone w dobrej kondycji.

## <a name="use-watchdogs"></a>Użyj licznika alarmów

Licznik alarm jest oddzielną usługą, która może oglądać kondycję i ładować w ramach usług oraz zgłaszać informacje o mikrousługach za pomocą zapytania z zamieszczoną wcześniej biblioteką `HealthChecks`. Może to pomóc zapobiec błędom, które nie zostaną wykryte w oparciu o Widok jednej usługi. Licznik alarmy jest również dobrym miejscem do kodu hosta, który może wykonywać akcje naprawcze dla znanych warunków bez interakcji z użytkownikiem.

Przykład eShopOnContainers zawiera stronę sieci Web, która wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano na rysunku 8-9. Jest to najprostsza wartość licznika alarmowego, która może być dostępna, ponieważ pokazuje jedynie stan mikrousług i aplikacji sieci Web w eShopOnContainers. Zazwyczaj licznik alarmowy wykonuje także akcje w przypadku wykrycia stanu złej kondycji.

Na szczęście [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) udostępnia również pakiet NuGet [AspNetCore. HealthChecks. UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) , który może służyć do wyświetlania wyników kontroli kondycji ze skonfigurowanych identyfikatorów URI.

![Zrzut ekranu stanu eShopOnContainers kondycji interfejsu użytkownika kontroli kondycji.](./media/monitor-app-health/health-check-status-ui.png)

**Rysunek 8-9**. Przykładowy raport sprawdzania kondycji w eShopOnContainers

Podsumowując, ta usługa alarm wysyła zapytanie do każdego punktu końcowego mikrousługi "/HC". Spowoduje to wykonanie wszystkich kontroli kondycji zdefiniowanych w ramach tego programu i zwrócenie ogólnej kondycji w zależności od wszystkich tych sprawdzeń. HealthChecksUI jest łatwe do użycia w kilku wpisach konfiguracji i dwóch wierszach kodu, które należy dodać do Startup.cs usługi alarm.

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

Plik Startup.cs, który dodaje HealthChecksUI:

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

## <a name="health-checks-when-using-orchestrators"></a>Sprawdzanie kondycji w przypadku korzystania z programu Orchestrator

Aby monitorować dostępność mikrousług, program Orchestrator, taki jak Kubernetes, i Service Fabric okresowo przeprowadza kontrolę kondycji, wysyłając żądania przetestowania mikrousług. Gdy koordynator ustali, że usługa/kontener jest w złej kondycji, zatrzyma żądania routingu do tego wystąpienia. Zwykle tworzy również nowe wystąpienie tego kontenera.

Na przykład większość programów Orchestrator może korzystać z kontroli kondycji w celu zarządzania wdrożeniami bez przestojów. Tylko wtedy, gdy stan usługi/kontenera zmienia się w dobrej kondycji, program Orchestrator rozpocznie kierowanie ruchu do wystąpień usługi/kontenera.

Monitorowanie kondycji jest szczególnie ważne, gdy koordynator wykonuje uaktualnienie aplikacji. Niektóre programu Orchestrator (takie jak Azure Service Fabric) Update Services w fazach — na przykład mogą zaktualizować jedną piątą powierzchnię klastra dla każdej aktualizacji aplikacji. Zestaw węzłów, które są uaktualnione w tym samym czasie, jest określany jako *domena uaktualnienia*. Po uaktualnieniu każdej domeny uaktualnienia i udostępnieniu jej użytkownikom ta domena uaktualnienia musi przekazywać kontrolę kondycji, zanim wdrożenie przejdzie do następnej domeny uaktualnienia.

Innym aspektem kondycji usługi jest raportowanie metryk z usługi. Jest to zaawansowana funkcja modelu kondycji niektórych koordynatorów, taka jak Service Fabric. Metryki są ważne w przypadku korzystania z programu Orchestrator, ponieważ służą do zrównoważenia użycia zasobów. Metryki mogą również stanowić wskaźnik kondycji systemu. Przykładowo może istnieć aplikacja, która ma wiele mikrousług, a każde wystąpienie raportuje metrykę żądań na sekundę (RPS pliku). Jeśli jedna usługa korzysta z większej liczby zasobów (pamięci, procesora itp.) niż inna usługa, program Orchestrator może przenieść wystąpienia usługi w klastrze, aby spróbować zachować nawet wykorzystanie zasobów.

Należy pamiętać, że usługa Azure Service Fabric oferuje własny [model monitorowania kondycji](/azure/service-fabric/service-fabric-health-introduction), który jest bardziej zaawansowany niż proste kontrole kondycji.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Zaawansowane monitorowanie: wizualizacja, analiza i alerty

Ostatnia część monitorowania polega na wizualizowaniu strumienia zdarzeń, raportowaniu wydajności usługi i wysyłaniu alertów w przypadku wykrycia problemu. Do tego aspektu monitorowania można użyć różnych rozwiązań.

Możesz użyć prostych aplikacji niestandardowych pokazujących stan usług, takich jak niestandardowa strona wyświetlana przy objaśnianiu [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Można też użyć bardziej zaawansowanych narzędzi, takich jak [Azure monitor](https://azure.microsoft.com/services/monitor/) , aby zgłosić alerty na podstawie strumienia zdarzeń.

Na koniec, Jeśli przechowujesz wszystkie strumienie zdarzeń, możesz użyć programu Microsoft Power BI lub innych rozwiązań, takich jak Kibana lub Splunk, aby wizualizować dane.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Interfejs użytkownika HealthChecks i HealthChecks dla ASP.NET Core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Wprowadzenie do Service Fabric monitorowania kondycji** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitor** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Poprzednie](implement-circuit-breaker-pattern.md)
>[dalej](../secure-net-microservices-web-applications/index.md)
