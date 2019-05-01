---
title: Monitorowanie kondycji
description: Zapoznaj się z jednym ze sposobów wdrażania, monitorowania kondycji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: deebcf6771d24be34050dd7fdfb807a681ebce1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818625"
---
# <a name="health-monitoring"></a><span data-ttu-id="72f09-103">Monitorowanie kondycji</span><span class="sxs-lookup"><span data-stu-id="72f09-103">Health monitoring</span></span>

<span data-ttu-id="72f09-104">Monitorowanie kondycji można zezwolić na niemal w czasie rzeczywistym informacje o stanie mikrousług i kontenerów.</span><span class="sxs-lookup"><span data-stu-id="72f09-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="72f09-105">Monitorowanie kondycji mają kluczowe znaczenie dla wielu aspektów Obsługa mikrousług i jest szczególnie ważne podczas koordynatorów wykonywania uaktualnień aplikacji częściowej w fazach, zgodnie z opisem w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="72f09-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="72f09-106">Aplikacje oparte na Mikrousługach często używają pulsów lub kontroli kondycji, aby umożliwić ich monitory wydajności, harmonogramów i koordynatorów śledzić wiele różnych usług.</span><span class="sxs-lookup"><span data-stu-id="72f09-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="72f09-107">Jeśli usługi nie może wysłać jakiegoś rodzaju sygnału "Jestem aktywności", na żądanie lub zgodnie z harmonogramem, aplikacja może stoją w obliczu ryzyka podczas wdrażania aktualizacji lub może po prostu za późno wykrywanie błędów i nie można zatrzymać występują kaskadowe awarie, które mogą znaleźć się w głównych awarii.</span><span class="sxs-lookup"><span data-stu-id="72f09-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="72f09-108">W typowym modelu usług wysyłać raporty o ich stanie, a te informacje mają charakter do zapewnienia całościowego widoku stanu kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72f09-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="72f09-109">Jeśli używasz programu orchestrator można określić informacje o kondycji klastra usługi orchestrator w co klaster może działać w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="72f09-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="72f09-110">Użytkownik inwestujący w raportowania stanu wysokiej jakości, który jest dostosowany do Twojej aplikacji, można wykryć i znacznie łatwiejsze Rozwiązywanie problemów dla uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72f09-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="72f09-111">Kontroli kondycji implementacji w usługach platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="72f09-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="72f09-112">Podczas tworzenia aplikacji mikrousług lub sieci web platformy ASP.NET Core, można użyć funkcji kontroli kondycji wbudowanych, wydanej w ASP .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="72f09-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="72f09-113">Podobnie jak wiele w ASP.NET Core funkcje, kondycji, które testy mają zestaw usług i oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="72f09-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="72f09-114">Usługi sprawdzania kondycji i oprogramowanie pośredniczące są łatwe w użyciu i oferuje możliwości, dzięki którym możesz Sprawdź, czy dowolny zasób zewnętrzny potrzebne dla aplikacji (np. bazy danych programu SQL Server lub zdalnemu interfejsowi API) działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="72f09-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="72f09-115">Podczas korzystania z tej funkcji można również określić, co oznacza że zasobu jest w dobrej kondycji, jak możemy wyjaśnić później.</span><span class="sxs-lookup"><span data-stu-id="72f09-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="72f09-116">Aby skutecznie korzystać z tej funkcji, musisz najpierw skonfigurować usługi w programie mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="72f09-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="72f09-117">Po drugie potrzebujesz aplikacji frontonu, który odpytuje raportów kondycji.</span><span class="sxs-lookup"><span data-stu-id="72f09-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="72f09-118">Fronton aplikacji może być niestandardowych aplikacji do raportowania lub może być orchestrator sam można odpowiednio reagować na stany kondycji.</span><span class="sxs-lookup"><span data-stu-id="72f09-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="72f09-119">Funkcja HealthChecks w mikrousługi zaplecza programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="72f09-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="72f09-120">W tej sekcji dowiesz się, jak funkcja HealthChecks jest używana w przykładowej aplikacji 2.2 internetowego interfejsu API platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="72f09-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="72f09-121">Implementacja tej funkcji w mikrousługach dużej skali, jak w ramach aplikacji eShopOnContainers zostało wyjaśnione w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="72f09-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="72f09-122">Aby rozpocząć, musisz zdefiniować, co stanowi stan kondycji dla poszczególnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="72f09-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="72f09-123">W przykładowej aplikacji mikrousług są w dobrej kondycji, jeśli dostępna jest również powiązanej bazie danych programu SQL Server i mikrousług interfejsu API jest dostępny za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="72f09-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="72f09-124">.NET Core 2.2, za pomocą wbudowanych interfejsów API można skonfigurować usługi, dodać sprawdzanie kondycji dla mikrousług i jego zależnych bazy danych programu SQL Server w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="72f09-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="72f09-125">W poprzednim kodzie `services.AddHealthChecks()` metoda konfiguruje podstawowe sprawdzenie protokołu HTTP, która zwraca kod stanu **200** za pomocą "Dobra kondycja".</span><span class="sxs-lookup"><span data-stu-id="72f09-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="72f09-126">Dodatkowo `AddCheck()` — metoda rozszerzenia konfiguruje niestandardowy `SqlConnectionHealthCheck` kontrole kondycji SQL Database powiązane.</span><span class="sxs-lookup"><span data-stu-id="72f09-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="72f09-127">`AddCheck()` Metoda dodaje nowe sprawdzenie kondycji o określonej nazwie i implementacji typu `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="72f09-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="72f09-128">Możesz dodać wiele kondycji umożliwia sprawdzenie za pomocą metody AddCheck, więc mikrousługi nie będzie zapewniać "" dobrej kondycji, dopóki wszystkie jego kontrole są w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="72f09-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="72f09-129">`SqlConnectionHealthCheck` Klasa niestandardowa, która implementuje są `IHealthCheck`, która pobiera parametry połączenia jako parametr konstruktora i wykonuje proste zapytanie, aby sprawdzić, czy połączenie z bazą danych SQL jest pomyślne.</span><span class="sxs-lookup"><span data-stu-id="72f09-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="72f09-130">Zwraca `HealthCheckResult.Healthy()` Jeśli kwerenda zostanie wykonana pomyślnie, a jeśli tak, to a `FailureStatus` z faktyczny wyjątek, gdy zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="72f09-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="72f09-131">Należy pamiętać, że w poprzednim kodzie `Select 1` zapytanie użyte do sprawdzenia kondycji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="72f09-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="72f09-132">Aby monitorować dostępność mikrousługi, koordynatorów, takich jak Kubernetes i usługi Service Fabric okresowo sprawdzać kondycję, wysyłając żądania do testowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="72f09-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="72f09-133">Należy zachować wydajność zapytań bazy danych tak, aby te operacje są szybkie i nie powodują lepszego wykorzystania zasobów.</span><span class="sxs-lookup"><span data-stu-id="72f09-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="72f09-134">Na koniec Utwórz oprogramowania pośredniczącego, które odpowiada na ścieżkę adresu url "HC":</span><span class="sxs-lookup"><span data-stu-id="72f09-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

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

<span data-ttu-id="72f09-135">Gdy punkt końcowy `<yourmicroservice>/hc` jest wywołana, uruchamia wszystkie kontrole kondycji, które są skonfigurowane w `AddHealthChecks()` metody w klasie uruchamiania i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="72f09-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="72f09-136">Implementacja HealthChecks w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="72f09-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="72f09-137">Mikrousługi w ramach aplikacji eShopOnContainers zależy od wielu usług w celu wykonania swojego zadania.</span><span class="sxs-lookup"><span data-stu-id="72f09-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="72f09-138">Na przykład `Catalog.API` mikrousługi w ramach aplikacji eShopOnContainers zależy od wielu usług, takich jak Azure Blob Storage, SQL Server i oprogramowania RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="72f09-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="72f09-139">W związku z tym, ma kilka kontroli kondycji dodane przy użyciu `AddCheck()` metody.</span><span class="sxs-lookup"><span data-stu-id="72f09-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="72f09-140">Dla każdej usługi zależne niestandardowego `IHealthCheck` wdrożenia, który definiuje jej stan kondycji odpowiednimi musi zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="72f09-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="72f09-141">Projekt typu open-source [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) rozwiązuje ten problem, dostarczając implementacje sprawdzania kondycji niestandardowe dla każdego z tych usług dla przedsiębiorstw, które są zbudowane na podstawie platformy .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="72f09-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="72f09-142">Każdy sprawdzenie kondycji jest dostępny jako poszczególnych pakietów NuGet, który można łatwo dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="72f09-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="72f09-143">ramach aplikacji eShopOnContainers używane są często w wszystkie jego mikrousług.</span><span class="sxs-lookup"><span data-stu-id="72f09-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="72f09-144">Na przykład w `Catalog.API` mikrousłudze oraz NuGet następujące pakiety zostały dodane:</span><span class="sxs-lookup"><span data-stu-id="72f09-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Widok projektu Catalog.API, gdy pakiety AspNetCore.Diagnostics.HealthChecks NuGet do których istnieją odwołania w Eksploratorze rozwiązań](./media/image6.png)

<span data-ttu-id="72f09-146">**Rysunek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="72f09-146">**Figure 8-7**.</span></span> <span data-ttu-id="72f09-147">Zaimplementowane w Catalog.API przy użyciu AspNetCore.Diagnostics.HealthChecks niestandardowe kontrole kondycji</span><span class="sxs-lookup"><span data-stu-id="72f09-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="72f09-148">W poniższym kodzie implementacji kontroli kondycji są dodawane do poszczególnych usług zależnych, a następnie jest skonfigurować oprogramowanie pośredniczące:</span><span class="sxs-lookup"><span data-stu-id="72f09-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="72f09-149">Na koniec Dodaj oprogramowanie pośredniczące test kondycji do nasłuchiwania na punkt końcowy "HC":</span><span class="sxs-lookup"><span data-stu-id="72f09-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="72f09-150">Zapytanie mikrousługi do raportów dotyczących stanu kondycji</span><span class="sxs-lookup"><span data-stu-id="72f09-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="72f09-151">Po skonfigurowaniu kontrole kondycji, zgodnie z opisem w tym artykule i masz mikrousług uruchamiane na platformie Docker, możesz bezpośrednio sprawdzić z przeglądarki, jeśli jest w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="72f09-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="72f09-152">Należy opublikować port kontenera na hoście platformy Docker, dzięki czemu można korzystać z kontenera, za pośrednictwem zewnętrzny adres IP hosta platformy Docker lub za pomocą `localhost`, jak pokazano na rysunku 8-8.</span><span class="sxs-lookup"><span data-stu-id="72f09-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Widok w przeglądarce odpowiedź JSON zwracany przez kontrolę kondycji](./media/image7.png)

<span data-ttu-id="72f09-154">**Rysunek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="72f09-154">**Figure 8-8**.</span></span> <span data-ttu-id="72f09-155">Sprawdzanie stanu kondycji jednej usługi w przeglądarce</span><span class="sxs-lookup"><span data-stu-id="72f09-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="72f09-156">W tym teście możesz zobaczyć, że `Catalog.API` mikrousługi (uruchomiony na porcie 5101) jest w dobrej kondycji, zwracając stanu HTTP 200 i informacje o stanie w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="72f09-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="72f09-157">Usługa również sprawdzane kondycji jej zależności bazy danych programu SQL Server i oprogramowania RabbitMQ, więc sprawdzenie kondycji zgłaszane jako w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="72f09-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="72f09-158">Użyj watchdogs</span><span class="sxs-lookup"><span data-stu-id="72f09-158">Use watchdogs</span></span>

<span data-ttu-id="72f09-159">Strażnika jest oddzielną usługą, którą można obejrzeć kondycji i obciążenia usług i kondycji raport na temat mikrousług, badając z `HealthChecks` biblioteki wprowadzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="72f09-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="72f09-160">Może to pomóc uniknąć błędów, które nie są wykrywane na podstawie widoku jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="72f09-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="72f09-161">Watchdogs również są dobrym miejscem do śledzenia hostowanie kodu, które może wykonywać działania korygujące znane warunki bez interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="72f09-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="72f09-162">Próbki w ramach aplikacji eShopOnContainers zawiera strona internetowa, która wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano w rysunek 8 do 9.</span><span class="sxs-lookup"><span data-stu-id="72f09-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="72f09-163">Jest to najprostsza strażnika, który może mieć, ponieważ tylko pokazuje stan mikrousług i aplikacji sieci web w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="72f09-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="72f09-164">Strażnika również potrzebuje zazwyczaj akcje w przypadku wykrycia złej kondycji stanów.</span><span class="sxs-lookup"><span data-stu-id="72f09-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="72f09-165">Na szczęście [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) udostępnia również [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) pakietu NuGet, który może służyć do wyświetlania sprawdzenie kondycji powstały na skutek skonfigurowanego identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="72f09-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Widok przeglądarki aplikacji WebStatus, przedstawiający stan kondycji wszystkich mikrousługi w ramach aplikacji eShopOnContainers](./media/image8.png)

<span data-ttu-id="72f09-167">**Rysunek 8 – 9**.</span><span class="sxs-lookup"><span data-stu-id="72f09-167">**Figure 8-9**.</span></span> <span data-ttu-id="72f09-168">Przykładowy raport ze sprawdzania kondycji w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="72f09-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="72f09-169">W podsumowaniu ta usługa strażnika wysyła zapytanie do endpoint "HC" poszczególne mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="72f09-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="72f09-170">Spowoduje to wykonania sprawdzenia kondycji wykona zdefiniowaną i zwracać o ogólnej kondycji, w zależności od tych sprawdzeń.</span><span class="sxs-lookup"><span data-stu-id="72f09-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="72f09-171">HealthChecksUI jest bardzo łatwe mogą korzystać z kilku pozycji konfiguracji i dwa wiersze kodu, który musi zostać dodane do pliku Startup.cs usługi strażnika.</span><span class="sxs-lookup"><span data-stu-id="72f09-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="72f09-172">Przykładowy plik konfiguracji dla kondycji Sprawdź interfejsu użytkownika:</span><span class="sxs-lookup"><span data-stu-id="72f09-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="72f09-173">Plik Startup.CS, który dodaje HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="72f09-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="72f09-174">Kontrole kondycji w przypadku korzystania z koordynatorami</span><span class="sxs-lookup"><span data-stu-id="72f09-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="72f09-175">Aby monitorować dostępność mikrousługi, koordynatorów, takich jak Kubernetes i usługi Service Fabric okresowo sprawdzać kondycję, wysyłając żądania do testowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="72f09-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="72f09-176">Gdy koordynatora ustali, że kontenerze/usługi jest zła, przestanie kierowania żądań do tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="72f09-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="72f09-177">Również zazwyczaj tworzy nowe wystąpienie tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="72f09-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="72f09-178">Na przykład większość koordynatorów można użyć kontroli kondycji Zarządzanie wdrożeniami bez jakichkolwiek przestojów.</span><span class="sxs-lookup"><span data-stu-id="72f09-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="72f09-179">Tylko wtedy, gdy stan zmiany/z kontenera usługi w dobrej kondycji będzie koordynatora start routingu ruchu do/z kontenera usługi wystąpień.</span><span class="sxs-lookup"><span data-stu-id="72f09-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="72f09-180">Monitorowanie kondycji jest szczególnie ważne w przypadku, gdy koordynatora wykonuje uaktualnienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72f09-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="72f09-181">Niektórych koordynatorów (np. usługi Azure Service Fabric) aktualizacji usługi w fazach — na przykład może zaktualizować co piątej powierzchni klastra dla uaktualnienie każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72f09-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="72f09-182">Zestaw węzłów, który jest uaktualniony, w tym samym czasie jest określany jako *domeny uaktualnień*.</span><span class="sxs-lookup"><span data-stu-id="72f09-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="72f09-183">Po każdej z domen został uaktualniony i jest dostępna dla użytkowników, że domena uaktualnienia musi upłynąć kontrole kondycji wdrożenia przechodzi do następnej domeny uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="72f09-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="72f09-184">Innym aspektem kondycja usługi zgłasza metryki z usługi.</span><span class="sxs-lookup"><span data-stu-id="72f09-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="72f09-185">Jest to zaawansowana funkcja model kondycji niektórych koordynatorów, takich jak usługi Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="72f09-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="72f09-186">Metryki są ważne w przypadku, gdy za pomocą programu orchestrator, ponieważ są one używane do równoważyć obciążenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="72f09-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="72f09-187">Metryki można także wskaźnik określający kondycji systemu.</span><span class="sxs-lookup"><span data-stu-id="72f09-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="72f09-188">Na przykład Niewykluczone, że aplikacja, która ma wiele mikrousług i każde wystąpienie raporty Metryka żądania na sekundę (RPS).</span><span class="sxs-lookup"><span data-stu-id="72f09-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="72f09-189">Jeśli jedna usługa używa więcej zasobów (pamięci, procesora, itp.), od innej usługi, koordynatora można poruszanie wystąpień usługi w klastrze w celu utrzymania nawet wykorzystanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="72f09-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="72f09-190">Należy pamiętać, że usługi Azure Service Fabric udostępnia swoje własne [monitorowanie kondycji modelu](/azure/service-fabric/service-fabric-health-introduction), co jest bardziej zaawansowane niż kontrole kondycji proste.</span><span class="sxs-lookup"><span data-stu-id="72f09-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="72f09-191">Zaawansowane monitorowanie: wizualizacja, analizy i alerty</span><span class="sxs-lookup"><span data-stu-id="72f09-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="72f09-192">Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raporty dotyczące wydajności i alerty po wykryciu problemu.</span><span class="sxs-lookup"><span data-stu-id="72f09-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="72f09-193">Można użyć różnych rozwiązań dla systemów monitorowania.</span><span class="sxs-lookup"><span data-stu-id="72f09-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="72f09-194">Można użyć prostej aplikacji niestandardowych, przedstawiający stan usług, takich jak niestandardowa strona wyświetlana podczas wyjaśniających [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="72f09-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="72f09-195">Można także użyć bardziej zaawansowanych narzędzi, takich jak [usługi Azure Monitor](https://azure.microsoft.com/services/monitor/) można zgłaszać alerty w oparciu o strumień zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="72f09-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="72f09-196">Na koniec jeśli są przechowywane wszystkie strumienie zdarzeń, służy Microsoft Power BI ani innych rozwiązań, takich jak Kibana lub Splunk umożliwiają wizualizację danych.</span><span class="sxs-lookup"><span data-stu-id="72f09-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="72f09-197">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="72f09-197">Additional resources</span></span>

- <span data-ttu-id="72f09-198">**HealthChecks i HealthChecks UI dla platformy ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="72f09-198">**HealthChecks and HealthChecks UI for ASP.NET Core** \\</span></span>
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="72f09-199">**Wprowadzenie do monitorowania kondycji usługi Service Fabric** \\</span><span class="sxs-lookup"><span data-stu-id="72f09-199">**Introduction to Service Fabric health monitoring** \\</span></span>
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="72f09-200">**Azure Monitor**
  <https://azure.microsoft.com/services/monitor/></span><span class="sxs-lookup"><span data-stu-id="72f09-200">**Azure Monitor**
<https://azure.microsoft.com/services/monitor/></span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72f09-201">[Poprzednie](implement-circuit-breaker-pattern.md)
>[dalej](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="72f09-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
