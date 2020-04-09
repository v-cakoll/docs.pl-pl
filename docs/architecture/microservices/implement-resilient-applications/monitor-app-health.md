---
title: Monitorowanie kondycji
description: Poznaj jeden ze sposobów wdrażania monitorowania kondycji.
ms.date: 03/02/2020
ms.openlocfilehash: 88354ae0ae59dbfbe40dbe1b25320f8f93d042ce
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988859"
---
# <a name="health-monitoring"></a>Monitorowanie kondycji

Monitorowanie kondycji może zezwolić w czasie zbliżonym do rzeczywistego informacji o stanie kontenerów i mikrousług. Monitorowanie kondycji ma kluczowe znaczenie dla wielu aspektów mikrousług operacyjnych i jest szczególnie ważne, gdy koordynatorzy wykonują częściowe uaktualnienia aplikacji w fazach, jak wyjaśniono później.

Aplikacje oparte na mikrousługach często używają pulsu lub kontroli kondycji, aby umożliwić ich monitory wydajności, harmonogramy i koordynatorów, aby śledzić wiele usług. Jeśli usługi nie mogą wysłać jakiegoś sygnału "Żyję", na żądanie lub zgodnie z harmonogramem, aplikacja może napotkać ryzyko podczas wdrażania aktualizacji lub może po prostu wykryć awarie zbyt późno i nie być w stanie zatrzymać kaskadowych awarii, które mogą skończyć się poważnymi awariami.

W typowym modelu usługi wysyłają raporty dotyczące ich stanu, a informacje są agregowane w celu zapewnienia ogólnego widoku stanu kondycji aplikacji. Jeśli używasz koordynatora, można podać informacje o kondycji do klastra koordynatora, dzięki czemu klaster może działać odpowiednio. Jeśli zainwestujesz w wysokiej jakości raportowanie kondycji dostosowane do aplikacji, można znacznie łatwiej wykryć i rozwiązać problemy dla uruchomionej aplikacji.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Wdrażanie kontroli kondycji w usługach ASP.NET Core

Podczas tworzenia mikrousługi ASP.NET Core lub aplikacji sieci web można użyć wbudowanej funkcji kontroli kondycji, która została wydana w programie ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Podobnie jak wiele ASP.NET podstawowych funkcji, kontrole kondycji są wyposażone w zestaw usług i oprogramowanie pośredniczące.

Usługi sprawdzania kondycji i oprogramowanie pośredniczące są łatwe w użyciu i zapewniają możliwości, które umożliwiają sprawdzanie poprawności, czy dowolny zasób zewnętrzny potrzebny dla aplikacji (takiej jak baza danych programu SQL Server lub zdalny interfejs API) działa poprawnie. Korzystając z tej funkcji, można również zdecydować, co to znaczy, że zasób jest w dobrej kondycji, jak wyjaśniamy później.

Aby skutecznie korzystać z tej funkcji, należy najpierw skonfigurować usługi w mikrousługach. Po drugie, potrzebujesz aplikacji frontonu, która wysyła zapytania do raportów kondycji. Ta aplikacja frontonu może być niestandardową aplikacją raportowania lub może być sama koordynatorem, który może odpowiednio reagować na stany kondycji.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Korzystanie z funkcji HealthChecks w zapleczu ASP.NET mikrousług

W tej sekcji dowiesz się, jak zaimplementować funkcję HealthChecks w przykładzie ASP.NET aplikacji interfejsu API sieci Web Core 3.1 podczas korzystania z pakietu [Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) Implementacja tej funkcji w mikrousług na dużą skalę, takich jak eShopOnContainers jest wyjaśnione w następnej sekcji.

Aby rozpocząć, należy zdefiniować, co stanowi stan w dobrej kondycji dla każdej mikrousługi. W przykładowej aplikacji definiujemy mikrousługi jest w dobrej kondycji, jeśli jego interfejs API jest dostępny za pośrednictwem protokołu HTTP i jego powiązanej bazy danych programu SQL Server jest również dostępna.

W programie .NET Core 3.1 z wbudowanymi interfejsami API można skonfigurować usługi, dodać sprawdzanie kondycji mikrousługi i zależną bazę danych programu SQL Server w ten sposób:

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

W poprzednim kodzie `services.AddHealthChecks()` metoda konfiguruje podstawowe sprawdzanie HTTP, który zwraca kod stanu **200** z "Zdrowy".  Ponadto metoda `AddCheck()` rozszerzenia konfiguruje `SqlConnectionHealthCheck` niestandardowe, które sprawdza kondycję powiązanej bazy danych SQL.

Metoda `AddCheck()` dodaje nowe sprawdzanie kondycji o określonej nazwie `IHealthCheck`i implementacji typu . Można dodać wiele kontroli kondycji przy użyciu AddCheck metody, więc mikrousługi nie zapewni stan "w dobrej kondycji", dopóki wszystkie jego kontrole są w dobrej kondycji.

`SqlConnectionHealthCheck`jest klasą niestandardową, która implementuje `IHealthCheck`, która przyjmuje parametry połączenia jako parametr konstruktora i wykonuje proste zapytanie, aby sprawdzić, czy połączenie z bazą danych SQL zakończy się pomyślnie. Zwraca, `HealthCheckResult.Healthy()` jeśli kwerenda została `FailureStatus` wykonana pomyślnie i z rzeczywistym wyjątkiem, gdy nie powiedzie się.

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

Należy zauważyć, `Select 1` że w poprzednim kodzie jest kwerenda używana do sprawdzania kondycji bazy danych. Aby monitorować dostępność mikrousług, orchestrators jak Kubernetes okresowo wykonywać kontrole kondycji, wysyłając żądania do testowania mikrousług. Ważne jest, aby zachować efektywne zapytania bazy danych, tak aby te operacje są szybkie i nie powodują większego wykorzystania zasobów.

Na koniec dodaj oprogramowanie pośredniczące, które `/hc`odpowiada na ścieżkę adresu URL:

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

Po wywołaniu `<yourmicroservice>/hc` punktu końcowego uruchamia wszystkie kontrole kondycji, które `AddHealthChecks()` są skonfigurowane w metodzie w klasie Uruchamianie i pokazuje wynik.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementacja HealthChecks w eShopOnContainers

Mikrousługi w eShopOnContainers polegać na wielu usług do wykonywania swoich zadań. Na przykład `Catalog.API` mikrousługi z eShopOnContainers zależy od wielu usług, takich jak Usługi Azure Blob Storage, SQL Server i RabbitMQ. W związku z tym ma kilka `AddCheck()` kontroli kondycji dodane przy użyciu metody. Dla każdej usługi zależnej należy dodać niestandardową `IHealthCheck` implementację definiują jej odpowiedni stan kondycji.

Projekt open-source [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) rozwiązuje ten problem, udostępniając niestandardowe implementacje sprawdzania kondycji dla każdej z tych usług dla przedsiębiorstwa, które są oparte na programie .NET Core 3.1. Każda kontrola kondycji jest dostępna jako pojedynczy pakiet NuGet, który można łatwo dodać do projektu. eShopOnContainers używa ich szeroko we wszystkich swoich mikrousług.

Na przykład w `Catalog.API` mikrousługi dodano następujące pakiety NuGet:

![Zrzut ekranu przedstawiający pakiety AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Rysunek 8-7**. Niestandardowe kontrole kondycji zaimplementowane w pliku Catalog.API przy użyciu aspNetCore.Diagnostics.HealthChecks

W poniższym kodzie implementacje sprawdzania kondycji są dodawane dla każdej usługi zależnej, a następnie oprogramowanie pośredniczące jest skonfigurowane:

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

Na koniec dodaj oprogramowanie pośredniczące HealthCheck, aby słuchać punktu końcowego "/hc":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Zapytanie do mikrousług, aby raportować o ich stanie zdrowia

Po skonfigurowaniu kontroli kondycji zgodnie z opisem w tym artykule i masz mikrousługi uruchomione w docker, można bezpośrednio sprawdzić z przeglądarki, czy jest w dobrej kondycji. Musisz opublikować port kontenera na hoście platformy Docker, dzięki czemu można uzyskać `localhost`dostęp do kontenera za pośrednictwem zewnętrznego adresu IP hosta platformy Docker lub za pośrednictwem , jak pokazano na rysunku 8-8.

![Zrzut ekranu odpowiedzi JSON zwrócony przez sprawdzenie kondycji.](./media/monitor-app-health/health-check-json-response.png)

**Rysunek 8-8**. Sprawdzanie stanu kondycji pojedynczej usługi z przeglądarki

W tym teście widać, `Catalog.API` że mikrousługa (uruchomiona na porcie 5101) jest w dobrej kondycji, zwracając stan HTTP 200 i informacje o stanie w JSON. Usługa sprawdziła również kondycję zależności bazy danych programu SQL Server i rabbitmq, więc sprawdzanie kondycji zgłosiło się jako w dobrej kondycji.

## <a name="use-watchdogs"></a>Korzystanie z watchdogs

Watchdog jest oddzielną usługą, która może obserwować kondycję i obciążenia między usługami `HealthChecks` i raportować kondycję mikrousług, korzystając z zapytań z biblioteki wprowadzonej wcześniej. Może to pomóc w zapobieganiu błędom, które nie zostaną wykryte na podstawie widoku pojedynczej usługi. Watchdogs również są dobrym miejscem do hostowania kodu, który może wykonywać akcje korygujące dla znanych warunków bez interakcji z użytkownikiem.

Przykład eShopOnContainers zawiera stronę sieci web, która wyświetla przykładowe raporty kontroli kondycji, jak pokazano na rysunku 8-9. Jest to najprostszy watchdog można mieć, ponieważ pokazuje tylko stan mikrousług i aplikacji sieci web w eShopOnContainers. Zazwyczaj watchdog również wykonuje działania, gdy wykryje niezdrowe stany.

Na szczęście [aspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) zapewnia również [aspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet pakiet, który może służyć do wyświetlania wyników kontroli kondycji ze skonfigurowanych identyfikatorów URI.

![Zrzut ekranu przedstawiający stan kondycji interfejsu użytkownika interfejsu użytkownika interfejsu użytkownika eShopOnContainers.](./media/monitor-app-health/health-check-status-ui.png)

**Rysunek 8-9**. Przykładowy raport kontroli kondycji w eShopOnContainers

Podsumowując, ta usługa watchdog wysyła zapytanie do punktu końcowego "/hc" każdej mikrousługi. Spowoduje to wykonanie wszystkich kontroli kondycji zdefiniowanych w nim i zwróci ogólny stan kondycji w zależności od wszystkich tych kontroli. HealthChecksUI jest łatwy do użycia z kilku wpisów konfiguracji i dwa wiersze kodu, które muszą zostać dodane do Startup.cs usługi watchdog.

Przykładowy plik konfiguracyjny dla interfejsu użytkownika sprawdzania kondycji:

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
    app.UseHealthChecksUI(config=> config.UIPath = "/hc-ui");
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>Kontrole kondycji podczas korzystania z koordynatorów

Aby monitorować dostępność mikrousług, orchestrators jak Kubernetes i service fabric okresowo wykonywać kontrole kondycji, wysyłając żądania do testowania mikrousług. Gdy koordynator stwierdzi, że usługa/kontener jest w złej kondycji, zatrzymuje routingu żądań do tego wystąpienia. Zwykle tworzy również nowe wystąpienie tego kontenera.

Na przykład większość koordynatorów może używać kontroli kondycji do zarządzania wdrożeniami o zerowym przestoju. Tylko wtedy, gdy stan usługi/kontenera zmieni się w dobrej kondycji, koordynator rozpocznie routing ruchu do wystąpień usługi/kontenera.

Monitorowanie kondycji jest szczególnie ważne, gdy koordynator wykonuje uaktualnienie aplikacji. Niektóre orchestrators (jak azure service fabric) aktualizacji usług w fazach — na przykład mogą zaktualizować jedną piątą powierzchni klastra dla każdego uaktualnienia aplikacji. Zestaw węzłów, które są uaktualniane w tym samym czasie, jest określany jako *domena uaktualnienia*. Po każdej domenie uaktualnienia został uaktualniony i jest dostępny dla użytkowników, że domena uaktualnienia musi przejść kontroli kondycji przed wdrożeniem przenosi się do następnej domeny uaktualnienia.

Innym aspektem kondycji usługi jest raportowanie metryk z usługi. Jest to zaawansowana funkcja modelu kondycji niektórych koordynatorów, takich jak sieci szkieletowej usług. Metryki są ważne podczas korzystania z orchestrator, ponieważ są one używane do równoważenia użycia zasobów. Metryki mogą być również wskaźnikiem kondycji systemu. Na przykład może mieć aplikację, która ma wiele mikrousług, a każde wystąpienie zgłasza żądania na sekundę (RPS) metryki. Jeśli jedna usługa używa więcej zasobów (pamięci, procesora itp.) niż inna usługa, orchestrator może przenieść wystąpienia usługi w klastrze, aby spróbować utrzymać równomierne wykorzystanie zasobów.

Należy zauważyć, że usługa Azure Service Fabric udostępnia własny [model monitorowania kondycji,](/azure/service-fabric/service-fabric-health-introduction)który jest bardziej zaawansowany niż proste kontrole kondycji.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Zaawansowane monitorowanie: wizualizacja, analiza i alerty

Ostatnią częścią monitorowania jest wizualizacja strumienia zdarzeń, raportowanie wydajności usługi i alerty po wykryciu problemu. Można użyć różnych rozwiązań dla tego aspektu monitorowania.

Można użyć prostych aplikacji niestandardowych pokazujących stan usług, takich jak strona niestandardowa wyświetlana podczas wyjaśniania [aspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Możesz też użyć bardziej zaawansowanych narzędzi, takich jak [Usługa Azure Monitor,](https://azure.microsoft.com/services/monitor/) aby zgłaszać alerty na podstawie strumienia zdarzeń.

Na koniec, jeśli przechowujesz wszystkie strumienie zdarzeń, możesz użyć usługi Microsoft Power BI lub innych rozwiązań, takich jak Kibana lub Splunk, aby wizualizować dane.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **HealthChecks i HealthChecks UI dla ASP.NET Core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Wprowadzenie do monitorowania kondycji sieci szkieletowej usług** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitor** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Poprzedni](implement-circuit-breaker-pattern.md)
>[następny](../secure-net-microservices-web-applications/index.md)
