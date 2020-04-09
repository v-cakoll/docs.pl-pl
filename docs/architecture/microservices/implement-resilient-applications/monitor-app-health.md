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
# <a name="health-monitoring"></a><span data-ttu-id="753e0-103">Monitorowanie kondycji</span><span class="sxs-lookup"><span data-stu-id="753e0-103">Health monitoring</span></span>

<span data-ttu-id="753e0-104">Monitorowanie kondycji może zezwolić w czasie zbliżonym do rzeczywistego informacji o stanie kontenerów i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="753e0-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="753e0-105">Monitorowanie kondycji ma kluczowe znaczenie dla wielu aspektów mikrousług operacyjnych i jest szczególnie ważne, gdy koordynatorzy wykonują częściowe uaktualnienia aplikacji w fazach, jak wyjaśniono później.</span><span class="sxs-lookup"><span data-stu-id="753e0-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="753e0-106">Aplikacje oparte na mikrousługach często używają pulsu lub kontroli kondycji, aby umożliwić ich monitory wydajności, harmonogramy i koordynatorów, aby śledzić wiele usług.</span><span class="sxs-lookup"><span data-stu-id="753e0-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="753e0-107">Jeśli usługi nie mogą wysłać jakiegoś sygnału "Żyję", na żądanie lub zgodnie z harmonogramem, aplikacja może napotkać ryzyko podczas wdrażania aktualizacji lub może po prostu wykryć awarie zbyt późno i nie być w stanie zatrzymać kaskadowych awarii, które mogą skończyć się poważnymi awariami.</span><span class="sxs-lookup"><span data-stu-id="753e0-107">If services cannot send some sort of "I'm alive" signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="753e0-108">W typowym modelu usługi wysyłają raporty dotyczące ich stanu, a informacje są agregowane w celu zapewnienia ogólnego widoku stanu kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="753e0-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="753e0-109">Jeśli używasz koordynatora, można podać informacje o kondycji do klastra koordynatora, dzięki czemu klaster może działać odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="753e0-109">If you're using an orchestrator, you can provide health information to your orchestrator's cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="753e0-110">Jeśli zainwestujesz w wysokiej jakości raportowanie kondycji dostosowane do aplikacji, można znacznie łatwiej wykryć i rozwiązać problemy dla uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="753e0-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="753e0-111">Wdrażanie kontroli kondycji w usługach ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="753e0-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="753e0-112">Podczas tworzenia mikrousługi ASP.NET Core lub aplikacji sieci web można użyć wbudowanej funkcji kontroli kondycji, która została wydana w programie ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span><span class="sxs-lookup"><span data-stu-id="753e0-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="753e0-113">Podobnie jak wiele ASP.NET podstawowych funkcji, kontrole kondycji są wyposażone w zestaw usług i oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="753e0-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="753e0-114">Usługi sprawdzania kondycji i oprogramowanie pośredniczące są łatwe w użyciu i zapewniają możliwości, które umożliwiają sprawdzanie poprawności, czy dowolny zasób zewnętrzny potrzebny dla aplikacji (takiej jak baza danych programu SQL Server lub zdalny interfejs API) działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="753e0-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="753e0-115">Korzystając z tej funkcji, można również zdecydować, co to znaczy, że zasób jest w dobrej kondycji, jak wyjaśniamy później.</span><span class="sxs-lookup"><span data-stu-id="753e0-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="753e0-116">Aby skutecznie korzystać z tej funkcji, należy najpierw skonfigurować usługi w mikrousługach.</span><span class="sxs-lookup"><span data-stu-id="753e0-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="753e0-117">Po drugie, potrzebujesz aplikacji frontonu, która wysyła zapytania do raportów kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="753e0-118">Ta aplikacja frontonu może być niestandardową aplikacją raportowania lub może być sama koordynatorem, który może odpowiednio reagować na stany kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="753e0-119">Korzystanie z funkcji HealthChecks w zapleczu ASP.NET mikrousług</span><span class="sxs-lookup"><span data-stu-id="753e0-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="753e0-120">W tej sekcji dowiesz się, jak zaimplementować funkcję HealthChecks w przykładzie ASP.NET aplikacji interfejsu API sieci Web Core 3.1 podczas korzystania z pakietu [Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)</span><span class="sxs-lookup"><span data-stu-id="753e0-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="753e0-121">Implementacja tej funkcji w mikrousług na dużą skalę, takich jak eShopOnContainers jest wyjaśnione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="753e0-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="753e0-122">Aby rozpocząć, należy zdefiniować, co stanowi stan w dobrej kondycji dla każdej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="753e0-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="753e0-123">W przykładowej aplikacji definiujemy mikrousługi jest w dobrej kondycji, jeśli jego interfejs API jest dostępny za pośrednictwem protokołu HTTP i jego powiązanej bazy danych programu SQL Server jest również dostępna.</span><span class="sxs-lookup"><span data-stu-id="753e0-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="753e0-124">W programie .NET Core 3.1 z wbudowanymi interfejsami API można skonfigurować usługi, dodać sprawdzanie kondycji mikrousługi i zależną bazę danych programu SQL Server w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="753e0-124">In .NET Core 3.1, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="753e0-125">W poprzednim kodzie `services.AddHealthChecks()` metoda konfiguruje podstawowe sprawdzanie HTTP, który zwraca kod stanu **200** z "Zdrowy".</span><span class="sxs-lookup"><span data-stu-id="753e0-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with "Healthy".</span></span>  <span data-ttu-id="753e0-126">Ponadto metoda `AddCheck()` rozszerzenia konfiguruje `SqlConnectionHealthCheck` niestandardowe, które sprawdza kondycję powiązanej bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="753e0-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database's health.</span></span>

<span data-ttu-id="753e0-127">Metoda `AddCheck()` dodaje nowe sprawdzanie kondycji o określonej nazwie `IHealthCheck`i implementacji typu .</span><span class="sxs-lookup"><span data-stu-id="753e0-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="753e0-128">Można dodać wiele kontroli kondycji przy użyciu AddCheck metody, więc mikrousługi nie zapewni stan "w dobrej kondycji", dopóki wszystkie jego kontrole są w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a "healthy" status until all its checks are healthy.</span></span>

<span data-ttu-id="753e0-129">`SqlConnectionHealthCheck`jest klasą niestandardową, która implementuje `IHealthCheck`, która przyjmuje parametry połączenia jako parametr konstruktora i wykonuje proste zapytanie, aby sprawdzić, czy połączenie z bazą danych SQL zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="753e0-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="753e0-130">Zwraca, `HealthCheckResult.Healthy()` jeśli kwerenda została `FailureStatus` wykonana pomyślnie i z rzeczywistym wyjątkiem, gdy nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="753e0-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="753e0-131">Należy zauważyć, `Select 1` że w poprzednim kodzie jest kwerenda używana do sprawdzania kondycji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="753e0-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="753e0-132">Aby monitorować dostępność mikrousług, orchestrators jak Kubernetes okresowo wykonywać kontrole kondycji, wysyłając żądania do testowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="753e0-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="753e0-133">Ważne jest, aby zachować efektywne zapytania bazy danych, tak aby te operacje są szybkie i nie powodują większego wykorzystania zasobów.</span><span class="sxs-lookup"><span data-stu-id="753e0-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="753e0-134">Na koniec dodaj oprogramowanie pośredniczące, które `/hc`odpowiada na ścieżkę adresu URL:</span><span class="sxs-lookup"><span data-stu-id="753e0-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

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

<span data-ttu-id="753e0-135">Po wywołaniu `<yourmicroservice>/hc` punktu końcowego uruchamia wszystkie kontrole kondycji, które `AddHealthChecks()` są skonfigurowane w metodzie w klasie Uruchamianie i pokazuje wynik.</span><span class="sxs-lookup"><span data-stu-id="753e0-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="753e0-136">Implementacja HealthChecks w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="753e0-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="753e0-137">Mikrousługi w eShopOnContainers polegać na wielu usług do wykonywania swoich zadań.</span><span class="sxs-lookup"><span data-stu-id="753e0-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="753e0-138">Na przykład `Catalog.API` mikrousługi z eShopOnContainers zależy od wielu usług, takich jak Usługi Azure Blob Storage, SQL Server i RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="753e0-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="753e0-139">W związku z tym ma kilka `AddCheck()` kontroli kondycji dodane przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="753e0-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="753e0-140">Dla każdej usługi zależnej należy dodać niestandardową `IHealthCheck` implementację definiują jej odpowiedni stan kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="753e0-141">Projekt open-source [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) rozwiązuje ten problem, udostępniając niestandardowe implementacje sprawdzania kondycji dla każdej z tych usług dla przedsiębiorstwa, które są oparte na programie .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="753e0-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET Core 3.1.</span></span> <span data-ttu-id="753e0-142">Każda kontrola kondycji jest dostępna jako pojedynczy pakiet NuGet, który można łatwo dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="753e0-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="753e0-143">eShopOnContainers używa ich szeroko we wszystkich swoich mikrousług.</span><span class="sxs-lookup"><span data-stu-id="753e0-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="753e0-144">Na przykład w `Catalog.API` mikrousługi dodano następujące pakiety NuGet:</span><span class="sxs-lookup"><span data-stu-id="753e0-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Zrzut ekranu przedstawiający pakiety AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="753e0-146">**Rysunek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="753e0-146">**Figure 8-7**.</span></span> <span data-ttu-id="753e0-147">Niestandardowe kontrole kondycji zaimplementowane w pliku Catalog.API przy użyciu aspNetCore.Diagnostics.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="753e0-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="753e0-148">W poniższym kodzie implementacje sprawdzania kondycji są dodawane dla każdej usługi zależnej, a następnie oprogramowanie pośredniczące jest skonfigurowane:</span><span class="sxs-lookup"><span data-stu-id="753e0-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="753e0-149">Na koniec dodaj oprogramowanie pośredniczące HealthCheck, aby słuchać punktu końcowego "/hc":</span><span class="sxs-lookup"><span data-stu-id="753e0-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="753e0-150">Zapytanie do mikrousług, aby raportować o ich stanie zdrowia</span><span class="sxs-lookup"><span data-stu-id="753e0-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="753e0-151">Po skonfigurowaniu kontroli kondycji zgodnie z opisem w tym artykule i masz mikrousługi uruchomione w docker, można bezpośrednio sprawdzić z przeglądarki, czy jest w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="753e0-152">Musisz opublikować port kontenera na hoście platformy Docker, dzięki czemu można uzyskać `localhost`dostęp do kontenera za pośrednictwem zewnętrznego adresu IP hosta platformy Docker lub za pośrednictwem , jak pokazano na rysunku 8-8.</span><span class="sxs-lookup"><span data-stu-id="753e0-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Zrzut ekranu odpowiedzi JSON zwrócony przez sprawdzenie kondycji.](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="753e0-154">**Rysunek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="753e0-154">**Figure 8-8**.</span></span> <span data-ttu-id="753e0-155">Sprawdzanie stanu kondycji pojedynczej usługi z przeglądarki</span><span class="sxs-lookup"><span data-stu-id="753e0-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="753e0-156">W tym teście widać, `Catalog.API` że mikrousługa (uruchomiona na porcie 5101) jest w dobrej kondycji, zwracając stan HTTP 200 i informacje o stanie w JSON.</span><span class="sxs-lookup"><span data-stu-id="753e0-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="753e0-157">Usługa sprawdziła również kondycję zależności bazy danych programu SQL Server i rabbitmq, więc sprawdzanie kondycji zgłosiło się jako w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="753e0-158">Korzystanie z watchdogs</span><span class="sxs-lookup"><span data-stu-id="753e0-158">Use watchdogs</span></span>

<span data-ttu-id="753e0-159">Watchdog jest oddzielną usługą, która może obserwować kondycję i obciążenia między usługami `HealthChecks` i raportować kondycję mikrousług, korzystając z zapytań z biblioteki wprowadzonej wcześniej.</span><span class="sxs-lookup"><span data-stu-id="753e0-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="753e0-160">Może to pomóc w zapobieganiu błędom, które nie zostaną wykryte na podstawie widoku pojedynczej usługi.</span><span class="sxs-lookup"><span data-stu-id="753e0-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="753e0-161">Watchdogs również są dobrym miejscem do hostowania kodu, który może wykonywać akcje korygujące dla znanych warunków bez interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="753e0-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="753e0-162">Przykład eShopOnContainers zawiera stronę sieci web, która wyświetla przykładowe raporty kontroli kondycji, jak pokazano na rysunku 8-9.</span><span class="sxs-lookup"><span data-stu-id="753e0-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="753e0-163">Jest to najprostszy watchdog można mieć, ponieważ pokazuje tylko stan mikrousług i aplikacji sieci web w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="753e0-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="753e0-164">Zazwyczaj watchdog również wykonuje działania, gdy wykryje niezdrowe stany.</span><span class="sxs-lookup"><span data-stu-id="753e0-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="753e0-165">Na szczęście [aspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) zapewnia również [aspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet pakiet, który może służyć do wyświetlania wyników kontroli kondycji ze skonfigurowanych identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="753e0-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Zrzut ekranu przedstawiający stan kondycji interfejsu użytkownika interfejsu użytkownika interfejsu użytkownika eShopOnContainers.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="753e0-167">**Rysunek 8-9**.</span><span class="sxs-lookup"><span data-stu-id="753e0-167">**Figure 8-9**.</span></span> <span data-ttu-id="753e0-168">Przykładowy raport kontroli kondycji w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="753e0-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="753e0-169">Podsumowując, ta usługa watchdog wysyła zapytanie do punktu końcowego "/hc" każdej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="753e0-169">In summary, this watchdog service queries each microservice's "/hc" endpoint.</span></span> <span data-ttu-id="753e0-170">Spowoduje to wykonanie wszystkich kontroli kondycji zdefiniowanych w nim i zwróci ogólny stan kondycji w zależności od wszystkich tych kontroli.</span><span class="sxs-lookup"><span data-stu-id="753e0-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="753e0-171">HealthChecksUI jest łatwy do użycia z kilku wpisów konfiguracji i dwa wiersze kodu, które muszą zostać dodane do Startup.cs usługi watchdog.</span><span class="sxs-lookup"><span data-stu-id="753e0-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="753e0-172">Przykładowy plik konfiguracyjny dla interfejsu użytkownika sprawdzania kondycji:</span><span class="sxs-lookup"><span data-stu-id="753e0-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="753e0-173">Startup.cs plik, który dodaje HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="753e0-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="753e0-174">Kontrole kondycji podczas korzystania z koordynatorów</span><span class="sxs-lookup"><span data-stu-id="753e0-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="753e0-175">Aby monitorować dostępność mikrousług, orchestrators jak Kubernetes i service fabric okresowo wykonywać kontrole kondycji, wysyłając żądania do testowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="753e0-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="753e0-176">Gdy koordynator stwierdzi, że usługa/kontener jest w złej kondycji, zatrzymuje routingu żądań do tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="753e0-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="753e0-177">Zwykle tworzy również nowe wystąpienie tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="753e0-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="753e0-178">Na przykład większość koordynatorów może używać kontroli kondycji do zarządzania wdrożeniami o zerowym przestoju.</span><span class="sxs-lookup"><span data-stu-id="753e0-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="753e0-179">Tylko wtedy, gdy stan usługi/kontenera zmieni się w dobrej kondycji, koordynator rozpocznie routing ruchu do wystąpień usługi/kontenera.</span><span class="sxs-lookup"><span data-stu-id="753e0-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="753e0-180">Monitorowanie kondycji jest szczególnie ważne, gdy koordynator wykonuje uaktualnienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="753e0-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="753e0-181">Niektóre orchestrators (jak azure service fabric) aktualizacji usług w fazach — na przykład mogą zaktualizować jedną piątą powierzchni klastra dla każdego uaktualnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="753e0-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="753e0-182">Zestaw węzłów, które są uaktualniane w tym samym czasie, jest określany jako *domena uaktualnienia*.</span><span class="sxs-lookup"><span data-stu-id="753e0-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="753e0-183">Po każdej domenie uaktualnienia został uaktualniony i jest dostępny dla użytkowników, że domena uaktualnienia musi przejść kontroli kondycji przed wdrożeniem przenosi się do następnej domeny uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="753e0-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="753e0-184">Innym aspektem kondycji usługi jest raportowanie metryk z usługi.</span><span class="sxs-lookup"><span data-stu-id="753e0-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="753e0-185">Jest to zaawansowana funkcja modelu kondycji niektórych koordynatorów, takich jak sieci szkieletowej usług.</span><span class="sxs-lookup"><span data-stu-id="753e0-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="753e0-186">Metryki są ważne podczas korzystania z orchestrator, ponieważ są one używane do równoważenia użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="753e0-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="753e0-187">Metryki mogą być również wskaźnikiem kondycji systemu.</span><span class="sxs-lookup"><span data-stu-id="753e0-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="753e0-188">Na przykład może mieć aplikację, która ma wiele mikrousług, a każde wystąpienie zgłasza żądania na sekundę (RPS) metryki.</span><span class="sxs-lookup"><span data-stu-id="753e0-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="753e0-189">Jeśli jedna usługa używa więcej zasobów (pamięci, procesora itp.) niż inna usługa, orchestrator może przenieść wystąpienia usługi w klastrze, aby spróbować utrzymać równomierne wykorzystanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="753e0-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="753e0-190">Należy zauważyć, że usługa Azure Service Fabric udostępnia własny [model monitorowania kondycji,](/azure/service-fabric/service-fabric-health-introduction)który jest bardziej zaawansowany niż proste kontrole kondycji.</span><span class="sxs-lookup"><span data-stu-id="753e0-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="753e0-191">Zaawansowane monitorowanie: wizualizacja, analiza i alerty</span><span class="sxs-lookup"><span data-stu-id="753e0-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="753e0-192">Ostatnią częścią monitorowania jest wizualizacja strumienia zdarzeń, raportowanie wydajności usługi i alerty po wykryciu problemu.</span><span class="sxs-lookup"><span data-stu-id="753e0-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="753e0-193">Można użyć różnych rozwiązań dla tego aspektu monitorowania.</span><span class="sxs-lookup"><span data-stu-id="753e0-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="753e0-194">Można użyć prostych aplikacji niestandardowych pokazujących stan usług, takich jak strona niestandardowa wyświetlana podczas wyjaśniania [aspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="753e0-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="753e0-195">Możesz też użyć bardziej zaawansowanych narzędzi, takich jak [Usługa Azure Monitor,](https://azure.microsoft.com/services/monitor/) aby zgłaszać alerty na podstawie strumienia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="753e0-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="753e0-196">Na koniec, jeśli przechowujesz wszystkie strumienie zdarzeń, możesz użyć usługi Microsoft Power BI lub innych rozwiązań, takich jak Kibana lub Splunk, aby wizualizować dane.</span><span class="sxs-lookup"><span data-stu-id="753e0-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="753e0-197">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="753e0-197">Additional resources</span></span>

- <span data-ttu-id="753e0-198">**HealthChecks i HealthChecks UI dla ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="753e0-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="753e0-199">**Wprowadzenie do monitorowania kondycji sieci szkieletowej usług** </span><span class="sxs-lookup"><span data-stu-id="753e0-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="753e0-200">**Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="753e0-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="753e0-201">[Poprzedni](implement-circuit-breaker-pattern.md)
>[następny](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="753e0-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
