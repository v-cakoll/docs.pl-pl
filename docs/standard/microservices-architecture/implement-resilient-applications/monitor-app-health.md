---
title: Monitorowanie kondycji
description: Zapoznaj się z jednym ze sposobów wdrażania, monitorowania kondycji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 90beb8073cd169b0a68dc0025d8cd815ccb5a308
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464011"
---
# <a name="health-monitoring"></a>Monitorowanie kondycji

Monitorowanie kondycji można zezwolić na niemal w czasie rzeczywistym informacje o stanie mikrousług i kontenerów. Monitorowanie kondycji mają kluczowe znaczenie dla wielu aspektów Obsługa mikrousług i jest szczególnie ważne podczas koordynatorów wykonywania uaktualnień aplikacji częściowej w fazach, zgodnie z opisem w dalszej części.

Aplikacje oparte na Mikrousługach często używają pulsów lub kontroli kondycji, aby umożliwić ich monitory wydajności, harmonogramów i koordynatorów śledzić wiele różnych usług. Jeśli usługi nie może wysłać jakiegoś rodzaju sygnału "Jestem aktywności", na żądanie lub zgodnie z harmonogramem, aplikacja może stoją w obliczu ryzyka podczas wdrażania aktualizacji lub może po prostu za późno wykrywanie błędów i nie można zatrzymać występują kaskadowe awarie, które mogą znaleźć się w głównych awarii.

W typowym modelu usług wysyłać raporty o ich stanie, a te informacje mają charakter do zapewnienia całościowego widoku stanu kondycji aplikacji. Jeśli używasz programu orchestrator można określić informacje o kondycji klastra usługi orchestrator w co klaster może działać w związku z tym. Użytkownik inwestujący w raportowania stanu wysokiej jakości, który jest dostosowany do Twojej aplikacji, można wykryć i znacznie łatwiejsze Rozwiązywanie problemów dla uruchomionej aplikacji.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Kontroli kondycji implementacji w usługach platformy ASP.NET Core

Podczas tworzenia aplikacji mikrousług lub sieci web platformy ASP.NET Core, można użyć funkcji kontroli kondycji wbudowanych, wydanej w ASP .NET Core 2.2. Podobnie jak wiele w ASP.NET Core funkcje, kondycji, które testy mają zestaw usług i oprogramowanie pośredniczące.

Usługi sprawdzania kondycji i oprogramowanie pośredniczące są łatwe w użyciu i oferuje możliwości, dzięki którym możesz Sprawdź, czy dowolny zasób zewnętrzny potrzebne dla aplikacji (np. bazy danych programu SQL Server lub zdalnemu interfejsowi API) działa poprawnie. Podczas korzystania z tej funkcji można również określić, co oznacza że zasobu jest w dobrej kondycji, jak możemy wyjaśnić później.

Aby skutecznie korzystać z tej funkcji, musisz najpierw skonfigurować usługi w programie mikrousługi. Po drugie potrzebujesz aplikacji frontonu, który odpytuje raportów kondycji. Fronton aplikacji może być niestandardowych aplikacji do raportowania lub może być orchestrator sam można odpowiednio reagować na stany kondycji.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Funkcja HealthChecks w mikrousługi zaplecza programu ASP.NET

W tej sekcji dowiesz się, jak funkcja HealthChecks jest używana w przykładowej aplikacji 2.2 internetowego interfejsu API platformy ASP.NET Core. Implementacja tej funkcji w mikrousługach dużej skali, jak w ramach aplikacji eShopOnContainers zostało wyjaśnione w dalszej części. Aby rozpocząć, musisz zdefiniować, co stanowi stan kondycji dla poszczególnych mikrousług. W przykładowej aplikacji mikrousług są w dobrej kondycji, jeśli dostępna jest również powiązanej bazie danych programu SQL Server i mikrousług interfejsu API jest dostępny za pośrednictwem protokołu HTTP.

.NET Core 2.2, za pomocą wbudowanych interfejsów API można skonfigurować usługi, dodać sprawdzanie kondycji dla mikrousług i jego zależnych bazy danych programu SQL Server w ten sposób:

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
    // Add a health check for a SQL database
    .AddCheck("MyDatabase", new SqlConnectionHealthCheck(Configuration["ConnectionStrings:DefaultConnection"]));
}
```

W poprzednim kodzie `services.AddHealthChecks()` metoda konfiguruje podstawowe sprawdzenie protokołu HTTP, która zwraca kod stanu **200** za pomocą "Dobra kondycja".  Dodatkowo `AddCheck()` — metoda rozszerzenia konfiguruje niestandardowy `SqlConnectionHealthCheck` kontrole kondycji SQL Database powiązane.

`AddCheck()` Metoda dodaje nowe sprawdzenie kondycji o określonej nazwie i implementacji typu `IHealthCheck`. Możesz dodać wiele kondycji umożliwia sprawdzenie za pomocą metody AddCheck, więc mikrousługi nie będzie zapewniać "" dobrej kondycji, dopóki wszystkie jego kontrole są w dobrej kondycji.

`SqlConnectionHealthCheck` Klasa niestandardowa, która implementuje są `IHealthCheck`, która pobiera parametry połączenia jako parametr konstruktora i wykonuje proste zapytanie, aby sprawdzić, czy połączenie z bazą danych SQL jest pomyślne. Zwraca `HealthCheckResult.Healthy()` Jeśli kwerenda zostanie wykonana pomyślnie, a jeśli tak, to a `FailureStatus` z faktyczny wyjątek, gdy zakończy się niepowodzeniem.

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

Należy pamiętać, że w poprzednim kodzie `Select 1` zapytanie użyte do sprawdzenia kondycji bazy danych. Aby monitorować dostępność mikrousługi, koordynatorów, takich jak Kubernetes i usługi Service Fabric okresowo sprawdzać kondycję, wysyłając żądania do testowania mikrousług. Należy zachować wydajność zapytań bazy danych tak, aby te operacje są szybkie i nie powodują lepszego wykorzystania zasobów.

Na koniec Utwórz oprogramowania pośredniczącego, które odpowiada na ścieżkę adresu url "HC":

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecks("/hc");
    //…
} 
```

Gdy punkt końcowy `<yourmicroservice>/hc` jest wywołana, uruchamia wszystkie kontrole kondycji, które są skonfigurowane w `AddHealthChecks()` metody w klasie uruchamiania i wyświetla wynik.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementacja HealthChecks w ramach aplikacji eShopOnContainers

Mikrousługi w ramach aplikacji eShopOnContainers zależy od wielu usług w celu wykonania swojego zadania. Na przykład `Catalog.API` mikrousługi w ramach aplikacji eShopOnContainers zależy od wielu usług, takich jak Azure Blob Storage, SQL Server i oprogramowania RabbitMQ. W związku z tym, ma kilka kontroli kondycji dodane przy użyciu `AddCheck()` metody. Dla każdej usługi zależne niestandardowego `IHealthCheck` wdrożenia, który definiuje jej stan kondycji odpowiednimi musi zostać dodany.

Projekt typu open-source [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) rozwiązuje ten problem, dostarczając implementacje sprawdzania kondycji niestandardowe dla każdego z tych usług dla przedsiębiorstw, które są zbudowane na podstawie platformy .NET Core 2.2. Każdy sprawdzenie kondycji jest dostępny jako poszczególnych pakietów NuGet, który można łatwo dodać do projektu. ramach aplikacji eShopOnContainers używane są często w wszystkie jego mikrousług.

Na przykład w `Catalog.API` mikrousłudze oraz NuGet następujące pakiety zostały dodane:

![Widok projektu Catalog.API, gdy pakiety AspNetCore.Diagnostics.HealthChecks NuGet do których istnieją odwołania w Eksploratorze rozwiązań](./media/image6.png)

**Rysunek 8-7**. Zaimplementowane w Catalog.API przy użyciu AspNetCore.Diagnostics.HealthChecks niestandardowe kontrole kondycji

W poniższym kodzie implementacji kontroli kondycji są dodawane do poszczególnych usług zależnych, a następnie jest skonfigurować oprogramowanie pośredniczące:

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

Na koniec Dodaj oprogramowanie pośredniczące test kondycji do nasłuchiwania na punkt końcowy "HC":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Zapytanie mikrousługi do raportów dotyczących stanu kondycji

Po skonfigurowaniu kontrole kondycji, zgodnie z opisem w tym artykule i masz mikrousług uruchamiane na platformie Docker, możesz bezpośrednio sprawdzić z przeglądarki, jeśli jest w dobrej kondycji. Należy opublikować port kontenera na hoście platformy Docker, dzięki czemu można korzystać z kontenera, za pośrednictwem zewnętrzny adres IP hosta platformy Docker lub za pomocą `localhost`, jak pokazano na rysunku 8-8.

![Widok w przeglądarce odpowiedź JSON zwracany przez kontrolę kondycji](./media/image7.png)

**Rysunek 8-8**. Sprawdzanie stanu kondycji jednej usługi w przeglądarce

W tym teście możesz zobaczyć, że `Catalog.API` mikrousługi (uruchomiony na porcie 5101) jest w dobrej kondycji, zwracając stanu HTTP 200 i informacje o stanie w formacie JSON. Usługa również sprawdzane kondycji jej zależności bazy danych programu SQL Server i oprogramowania RabbitMQ, więc sprawdzenie kondycji zgłaszane jako w dobrej kondycji.

## <a name="use-watchdogs"></a>Użyj watchdogs

Strażnika jest oddzielną usługą, którą można obejrzeć kondycji i obciążenia usług i kondycji raport na temat mikrousług, badając z `HealthChecks` biblioteki wprowadzone wcześniej. Może to pomóc uniknąć błędów, które nie są wykrywane na podstawie widoku jednej usługi. Watchdogs również są dobrym miejscem do śledzenia hostowanie kodu, które może wykonywać działania korygujące znane warunki bez interakcji z użytkownikiem.

Próbki w ramach aplikacji eShopOnContainers zawiera strona internetowa, która wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano w rysunek 8 do 9. Jest to najprostsza strażnika, który może mieć, ponieważ tylko pokazuje stan mikrousług i aplikacji sieci web w ramach aplikacji eShopOnContainers. Strażnika również potrzebuje zazwyczaj akcje w przypadku wykrycia złej kondycji stanów.

Na szczęście [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) udostępnia również [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) pakietu NuGet, który może służyć do wyświetlania sprawdzenie kondycji powstały na skutek skonfigurowanego identyfikatorów URI.

![Widok przeglądarki aplikacji WebStatus, przedstawiający stan kondycji wszystkich mikrousługi w ramach aplikacji eShopOnContainers](./media/image8.png)

**Rysunek 8 – 9**. Przykładowy raport ze sprawdzania kondycji w ramach aplikacji eShopOnContainers

W podsumowaniu ta usługa strażnika wysyła zapytanie do endpoint "HC" poszczególne mikrousługi. Spowoduje to wykonania sprawdzenia kondycji wykona zdefiniowaną i zwracać o ogólnej kondycji, w zależności od tych sprawdzeń. HealthChecksUI jest bardzo łatwe mogą korzystać z kilku pozycji konfiguracji i dwa wiersze kodu, który musi zostać dodane do pliku Startup.cs usługi strażnika.

Przykładowy plik konfiguracji dla kondycji Sprawdź interfejsu użytkownika:

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

Plik Startup.CS, który dodaje HealthChecksUI:

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

## <a name="health-checks-when-using-orchestrators"></a>Kontrole kondycji w przypadku korzystania z koordynatorami

Aby monitorować dostępność mikrousługi, koordynatorów, takich jak Kubernetes i usługi Service Fabric okresowo sprawdzać kondycję, wysyłając żądania do testowania mikrousług. Gdy koordynatora ustali, że kontenerze/usługi jest zła, przestanie kierowania żądań do tego wystąpienia. Również zazwyczaj tworzy nowe wystąpienie tego kontenera.

Na przykład większość koordynatorów można użyć kontroli kondycji Zarządzanie wdrożeniami bez jakichkolwiek przestojów. Tylko wtedy, gdy stan zmiany/z kontenera usługi w dobrej kondycji będzie koordynatora start routingu ruchu do/z kontenera usługi wystąpień.

Monitorowanie kondycji jest szczególnie ważne w przypadku, gdy koordynatora wykonuje uaktualnienie aplikacji. Niektórych koordynatorów (np. usługi Azure Service Fabric) aktualizacji usługi w fazach — na przykład może zaktualizować co piątej powierzchni klastra dla uaktualnienie każdej aplikacji. Zestaw węzłów, który jest uaktualniony, w tym samym czasie jest określany jako *domeny uaktualnień*. Po każdej z domen został uaktualniony i jest dostępna dla użytkowników, że domena uaktualnienia musi upłynąć kontrole kondycji wdrożenia przechodzi do następnej domeny uaktualnienia.

Innym aspektem kondycja usługi zgłasza metryki z usługi. Jest to zaawansowana funkcja model kondycji niektórych koordynatorów, takich jak usługi Service Fabric. Metryki są ważne w przypadku, gdy za pomocą programu orchestrator, ponieważ są one używane do równoważyć obciążenie zasobów. Metryki można także wskaźnik określający kondycji systemu. Na przykład Niewykluczone, że aplikacja, która ma wiele mikrousług i każde wystąpienie raporty Metryka żądania na sekundę (RPS). Jeśli jedna usługa używa więcej zasobów (pamięci, procesora, itp.), od innej usługi, koordynatora można poruszanie wystąpień usługi w klastrze w celu utrzymania nawet wykorzystanie zasobów.

Należy pamiętać, że usługi Azure Service Fabric udostępnia swoje własne [monitorowanie kondycji modelu](/azure/service-fabric/service-fabric-health-introduction), co jest bardziej zaawansowane niż kontrole kondycji proste.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Zaawansowane monitorowanie: wizualizacja, analizy i alerty

Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raporty dotyczące wydajności i alerty po wykryciu problemu. Można użyć różnych rozwiązań dla systemów monitorowania.

Można użyć prostej aplikacji niestandardowych, przedstawiający stan usług, takich jak niestandardowa strona wyświetlana podczas wyjaśniających [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Lub za pomocą bardziej zaawansowanych narzędzi, takich jak Azure Application Insights można zgłaszać alerty w oparciu o strumień zdarzeń.

Na koniec jeśli są przechowywane wszystkie strumienie zdarzeń, służy Microsoft Power BI ani innych rozwiązań, takich jak Kibana lub Splunk umożliwiają wizualizację danych.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **HealthChecks i HealthChecks UI dla platformy ASP.NET Core**
    [https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )

-   **Wprowadzenie do monitorowania kondycji usługi Service Fabric**
    [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

-   **Usługi Azure Application Insights**
    [https://azure.microsoft.com/services/application-insights/](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [https://www.microsoft.com/en-us/cloud-platform/operations-management-suite](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Poprzednie](implement-circuit-breaker-pattern.md)
>[dalej](../secure-net-microservices-web-applications/index.md)