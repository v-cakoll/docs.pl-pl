---
title: Monitorowanie kondycji
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Monitorowanie kondycji
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 35f6d773d714878f56a5e9151320072ebcd51e06
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145978"
---
# <a name="health-monitoring"></a><span data-ttu-id="c1e63-103">Monitorowanie kondycji</span><span class="sxs-lookup"><span data-stu-id="c1e63-103">Health monitoring</span></span>

<span data-ttu-id="c1e63-104">Monitorowanie kondycji można zezwolić na niemal w czasie rzeczywistym informacje o stanie mikrousług i kontenerów.</span><span class="sxs-lookup"><span data-stu-id="c1e63-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="c1e63-105">Monitorowanie kondycji mają kluczowe znaczenie dla wielu aspektów Obsługa mikrousług i jest szczególnie ważne podczas koordynatorów wykonywania uaktualnień aplikacji częściowej w fazach, zgodnie z opisem w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="c1e63-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="c1e63-106">Aplikacje oparte na Mikrousługach często używają pulsów lub kontroli kondycji, aby umożliwić ich monitory wydajności, harmonogramów i koordynatorów śledzić wiele różnych usług.</span><span class="sxs-lookup"><span data-stu-id="c1e63-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="c1e63-107">Jeśli usługi nie może wysłać jakiegoś rodzaju sygnału "Jestem aktywności", na żądanie lub zgodnie z harmonogramem, aplikacja może stoją w obliczu ryzyka podczas wdrażania aktualizacji lub może po prostu za późno wykrywanie błędów i nie można zatrzymać występują kaskadowe awarie, które mogą znaleźć się w głównych awarii.</span><span class="sxs-lookup"><span data-stu-id="c1e63-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="c1e63-108">W typowym modelu usług wysyłać raporty o ich stanie, a te informacje mają charakter do zapewnienia całościowego widoku stanu kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="c1e63-109">Jeśli używasz programu orchestrator można określić informacje o kondycji klastra usługi orchestrator w co klaster może działać w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="c1e63-109">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="c1e63-110">Użytkownik inwestujący w raportowania stanu wysokiej jakości, który jest dostosowany do Twojej aplikacji, można wykryć i znacznie łatwiejsze Rozwiązywanie problemów dla uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-110">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="c1e63-111">Implementowanie kondycji sprawdza w usługach platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c1e63-111">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="c1e63-112">Podczas tworzenia aplikacji mikrousług lub sieci web platformy ASP.NET Core, można użyć biblioteki out-of-band (nie official będzie przydatna jako część ASP.NETCore) o nazwie `HealthChecks` przez zespół programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c1e63-112">When developing an ASP.NET Core microservice or web application, you can use an out-of-band library (not official as part of ASP.NETCore) named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="c1e63-113">Jest on dostępny w tym [repozytorium GitHub](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="c1e63-113">It is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="c1e63-114">Ta biblioteka jest łatwa w użyciu i udostępnia funkcje, dzięki którym Sprawdź poprawność określonego zasobu zewnętrznego potrzebne dla aplikacji (np. bazy danych programu SQL Server lub zdalnemu interfejsowi API) działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c1e63-114">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="c1e63-115">Korzystając z tej biblioteki, można również określić, co oznacza że zasobu jest w dobrej kondycji, jak możemy wyjaśnić później.</span><span class="sxs-lookup"><span data-stu-id="c1e63-115">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="c1e63-116">Aby można było używać tej biblioteki, należy najpierw użyć biblioteki w mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="c1e63-116">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="c1e63-117">Po drugie potrzebujesz aplikacji frontonu, który odpytuje raportów kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="c1e63-118">Fronton aplikacji może być niestandardowych aplikacji do raportowania lub może być orchestrator sam można odpowiednio reagować na stany kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-118">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="c1e63-119">Za pomocą biblioteki HealthChecks w zaplecza mikrousług platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c1e63-119">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="c1e63-120">Aby zobaczyć, jak biblioteka HealthChecks jest używana w ramach aplikacji eShopOnContainers przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-120">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="c1e63-121">Aby rozpocząć, musisz zdefiniować, co stanowi stan kondycji dla poszczególnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c1e63-121">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="c1e63-122">W przykładowej aplikacji mikrousług są w dobrej kondycji, jeśli mikrousług interfejsu API jest dostępny za pośrednictwem protokołu HTTP i jeśli jego powiązanej bazy danych programu SQL Server jest również dostępna.</span><span class="sxs-lookup"><span data-stu-id="c1e63-122">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="c1e63-123">W przyszłości można zainstalować bibliotekę HealthChecks jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="c1e63-123">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="c1e63-124">Jednak na chwilę obecną, musisz pobrać i skompilować kod jako część rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c1e63-124">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="c1e63-125">Klonowanie kodu dostępne pod adresem https://github.com/dotnet-architecture/HealthChecks i skopiuj następujące foldery do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="c1e63-125">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="c1e63-126">src/common</span><span class="sxs-lookup"><span data-stu-id="c1e63-126">src/common</span></span>
  - <span data-ttu-id="c1e63-127">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="c1e63-127">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="c1e63-128">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="c1e63-128">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="c1e63-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="c1e63-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="c1e63-130">Można także użyć dodatkowe czynności kontrolne, takie jak te dla platformy Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale ponieważ w tej wersji w ramach aplikacji eShopOnContainers nie ma żadnych zależności na platformie Azure, nie jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="c1e63-130">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="c1e63-131">Nie potrzebujesz kontrole kondycji programu ASP.NET, ponieważ w ramach aplikacji eShopOnContainers zależy od platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1e63-131">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="c1e63-132">Rysunek 10-6 przedstawia biblioteki HealthChecks w programie Visual Studio, gotowe do użycia jako blok konstrukcyjny przez wszystkie mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="c1e63-132">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="c1e63-133">**Rysunek 10-6**.</span><span class="sxs-lookup"><span data-stu-id="c1e63-133">**Figure 10-6**.</span></span> <span data-ttu-id="c1e63-134">Kod źródłowy biblioteki ASP.NET Core HealthChecks w rozwiązaniu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1e63-134">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="c1e63-135">Jak wprowadzone wcześniej, najpierw należy w każdym projekcie mikrousług jest można dodać odwołania do bibliotek HealthChecks trzy.</span><span class="sxs-lookup"><span data-stu-id="c1e63-135">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="c1e63-136">Później możesz dodać akcje sprawdzania kondycji, które mają być wykonywane w tym mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c1e63-136">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="c1e63-137">Te akcje są po prostu zależności dla innych baz danych lub mikrousługi (HttpUrlCheck) (obecnie SqlCheck\* baz danych programu SQL Server).</span><span class="sxs-lookup"><span data-stu-id="c1e63-137">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="c1e63-138">Możesz dodać akcję w obrębie klasy uruchamiania poszczególnych mikrousług platformy ASP.NET lub aplikacji sieci web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c1e63-138">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="c1e63-139">Każdej usługi lub aplikacji sieci web, należy skonfigurować przez dodanie wszystkich jego zależności HTTP lub baza danych jako jedna metoda AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="c1e63-139">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="c1e63-140">Na przykład aplikacji sieci web MVC, w ramach aplikacji eShopOnContainers zależy od wielu usług, dlatego ma kilka metod AddCheck dodane do kontroli kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-140">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="c1e63-141">Na przykład w poniższym kodzie widać jak mikrousługi katalogu została dodana zależność dotycząca swojej bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c1e63-141">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

<span data-ttu-id="c1e63-142">Jednak aplikację sieci web MVC w ramach aplikacji eShopOnContainers ma wiele zależności na pozostałą część mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c1e63-142">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="c1e63-143">W związku z tym wywołuje jedną metodę AddUrlCheck dla poszczególnych mikrousług, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c1e63-143">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

<span data-ttu-id="c1e63-144">W związku z tym mikrousługi nie będą umożliwiać "" dobrej kondycji, dopóki wszystkie jego kontrole są w dobrej kondycji również.</span><span class="sxs-lookup"><span data-stu-id="c1e63-144">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="c1e63-145">Jeśli mikrousług ma zależność w usłudze lub w programie SQL Server, należy po prostu dodać wyboru Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="c1e63-145">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="c1e63-146">Poniższy kod jest w ramach aplikacji eShopOnContainers mikrousług basket.api.</span><span class="sxs-lookup"><span data-stu-id="c1e63-146">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="c1e63-147">(Mikrousług koszyka korzysta z pamięci podręcznej redis cache, ale biblioteki nie ma jeszcze dostawcę sprawdzanie kondycji pamięci podręcznej Redis).</span><span class="sxs-lookup"><span data-stu-id="c1e63-147">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="c1e63-148">Dla usługi lub aplikacji sieci web można uwidocznić punkt końcowy kontroli kondycji, musi włączyć UseHealthChecks (\[*adresu url\_dla\_kondycji\_sprawdza*\]) rozszerzenia Metoda.</span><span class="sxs-lookup"><span data-stu-id="c1e63-148">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="c1e63-149">Ta metoda jest przesyłany w WebHostBuilder poziomu w metodzie głównej klasy programu ASP.NET Core service lub sieci web aplikacji, tuż po UseKestrel, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1e63-149">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

<span data-ttu-id="c1e63-150">Ten proces przebiega następująco: każda mikrousługa udostępnia HC punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c1e63-150">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="c1e63-151">Punkt końcowy jest tworzony przez bibliotekę HealthChecks oprogramowania pośredniczącego platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1e63-151">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="c1e63-152">Po wywołaniu tego punktu końcowego, uruchamia wszystkie kontrole kondycji, które są skonfigurowane w metodzie AddHealthChecks w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="c1e63-152">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="c1e63-153">Metoda UseHealthChecks oczekuje portu lub ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c1e63-153">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="c1e63-154">Tego portu lub ścieżki jest punkt końcowy, aby użyć, aby sprawdzić kondycję usługi.</span><span class="sxs-lookup"><span data-stu-id="c1e63-154">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="c1e63-155">Na przykład mikrousług katalogu używa HC ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c1e63-155">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="c1e63-156">Buforowanie odpowiedzi sprawdzania kondycji</span><span class="sxs-lookup"><span data-stu-id="c1e63-156">Caching health check responses</span></span>

<span data-ttu-id="c1e63-157">Ponieważ nie chcesz spowodować odmowę usługi (DoS) w usługach lub po prostu nie chcesz mieć wpływ na wydajność usługi, sprawdzając zasobów można zbyt często, zwraca wartość w pamięci podręcznej i skonfigurować czas trwania pamięci podręcznej, przy każdym sprawdzaniu kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-157">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="c1e63-158">Domyślnie czas trwania pamięci podręcznej wewnętrznie jest ustawiony na 5 minut, ale możesz zmienić ten czas trwania pamięci podręcznej w każdym sprawdzenie kondycji, tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c1e63-158">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="c1e63-159">Wykonywanie zapytań mikrousługi do raportów dotyczących stanu kondycji</span><span class="sxs-lookup"><span data-stu-id="c1e63-159">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="c1e63-160">Po skonfigurowaniu kontrole kondycji, zgodnie z opisem w tym miejscu po mikrousług na platformie Docker, możesz bezpośrednio sprawdzić z przeglądarki, jeśli jest w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-160">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="c1e63-161">(To wymagają jest publikowany port kontenera hosta platformy Docker, dzięki czemu można korzystać z kontenera, za pośrednictwem hosta lokalnego lub zewnętrzny adres IP hosta platformy Docker). Rysunek 10-7 przedstawiono żądanie, w przeglądarce i odpowiednich odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c1e63-161">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="c1e63-162">**Rysunek 10-7**.</span><span class="sxs-lookup"><span data-stu-id="c1e63-162">**Figure 10-7**.</span></span> <span data-ttu-id="c1e63-163">Sprawdzanie stanu kondycji jednej usługi w przeglądarce</span><span class="sxs-lookup"><span data-stu-id="c1e63-163">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="c1e63-164">W tym teście widać, mikrousługi catalog.api (uruchomiony na porcie 5101) jest w dobrej kondycji i zwracanie stanu HTTP 200 i informacje o stanie w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="c1e63-164">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="c1e63-165">Oznacza to również, że wewnętrznie usługa również sprawdzane kondycję jego zależność bazy danych programu SQL Server i że sprawdzenie kondycji zgłoszono sama jako w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-165">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="c1e63-166">Za pomocą watchdogs</span><span class="sxs-lookup"><span data-stu-id="c1e63-166">Using watchdogs</span></span>

<span data-ttu-id="c1e63-167">Strażnika jest oddzielną usługą, którą można obejrzeć kondycji i obciążenia usług i kondycji raport na temat mikrousług, badając za pomocą biblioteki HealthChecks wprowadzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="c1e63-167">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="c1e63-168">Może to pomóc uniknąć błędów, które nie są wykrywane na podstawie widoku jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="c1e63-168">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="c1e63-169">Watchdogs również są dobrym miejscem do śledzenia hostowanie kodu, które może wykonywać działania korygujące znane warunki bez interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="c1e63-169">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="c1e63-170">Próbki w ramach aplikacji eShopOnContainers zawiera strony sieci web, który wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano w rysunek 10-8.</span><span class="sxs-lookup"><span data-stu-id="c1e63-170">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="c1e63-171">Jest to najprostsza strażnika, może istnieć, ponieważ on za zadanie jest pokazuje stan mikrousług i aplikacji sieci web w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c1e63-171">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="c1e63-172">Strażnika również potrzebuje zazwyczaj akcje w przypadku wykrycia złej kondycji stanów.</span><span class="sxs-lookup"><span data-stu-id="c1e63-172">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="c1e63-173">**Rysunek 10-8**.</span><span class="sxs-lookup"><span data-stu-id="c1e63-173">**Figure 10-8**.</span></span> <span data-ttu-id="c1e63-174">Przykładowy raport ze sprawdzania kondycji w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="c1e63-174">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="c1e63-175">W podsumowaniu oprogramowanie pośredniczące ASP.NET, ASP.NET Core HealthChecks biblioteki udostępnia punkt końcowy kontroli kondycji jednego dla poszczególnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c1e63-175">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="c1e63-176">Spowoduje to wykonania sprawdzenia kondycji wykona zdefiniowaną i zwracać o ogólnej kondycji, w zależności od tych sprawdzeń.</span><span class="sxs-lookup"><span data-stu-id="c1e63-176">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="c1e63-177">Biblioteka HealthChecks jest rozszerzalny poprzez nowe funkcje sprawdzania kondycji przyszłych zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="c1e63-177">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="c1e63-178">Na przykład oczekujemy, że w przyszłości biblioteki będzie miał kontrole kondycji dla pamięci podręcznej redis Cache i innych baz danych.</span><span class="sxs-lookup"><span data-stu-id="c1e63-178">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="c1e63-179">Biblioteka umożliwia raportowania przez wiele zależności aplikacji lub usługi kondycji, i może następnie podjąć działania w oparciu kontrole kondycji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-179">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="c1e63-180">Kontrole kondycji w przypadku korzystania z koordynatorami</span><span class="sxs-lookup"><span data-stu-id="c1e63-180">Health checks when using orchestrators</span></span>

<span data-ttu-id="c1e63-181">Aby monitorować dostępność mikrousługi, koordynatorów, takich jak Docker Swarm, Kubernetes i usługi Service Fabric okresowo sprawdzać kondycję, wysyłając żądania do testowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="c1e63-181">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="c1e63-182">Gdy koordynatora ustali, że kontenerze/usługi jest zła, przestanie kierowania żądań do tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c1e63-182">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="c1e63-183">Również zazwyczaj tworzy nowe wystąpienie tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="c1e63-183">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="c1e63-184">Na przykład większość koordynatorów można użyć kontroli kondycji Zarządzanie wdrożeniami bez jakichkolwiek przestojów.</span><span class="sxs-lookup"><span data-stu-id="c1e63-184">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="c1e63-185">Tylko wtedy, gdy stan zmiany/z kontenera usługi w dobrej kondycji będzie koordynatora start routingu ruchu do/z kontenera usługi wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c1e63-185">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="c1e63-186">Monitorowanie kondycji jest szczególnie ważne w przypadku, gdy koordynatora wykonuje uaktualnienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-186">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="c1e63-187">Niektórych koordynatorów (np. usługi Azure Service Fabric) aktualizacji usługi w fazach — na przykład może zaktualizować co piątej powierzchni klastra dla uaktualnienie każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1e63-187">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="c1e63-188">Zestaw węzłów, który jest uaktualniony, w tym samym czasie jest określany jako *domeny uaktualnień*.</span><span class="sxs-lookup"><span data-stu-id="c1e63-188">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="c1e63-189">Po każdej z domen został uaktualniony i jest dostępna dla użytkowników, że domena uaktualnienia musi upłynąć kontrole kondycji wdrożenia przechodzi do następnej domeny uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="c1e63-189">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="c1e63-190">Innym aspektem kondycja usługi zgłasza metryki z usługi.</span><span class="sxs-lookup"><span data-stu-id="c1e63-190">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="c1e63-191">Jest to zaawansowana funkcja model kondycji niektórych koordynatorów, takich jak usługi Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="c1e63-191">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="c1e63-192">Metryki są ważne w przypadku, gdy za pomocą programu orchestrator, ponieważ są one używane do równoważyć obciążenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="c1e63-192">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="c1e63-193">Metryki można także wskaźnik określający kondycji systemu.</span><span class="sxs-lookup"><span data-stu-id="c1e63-193">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="c1e63-194">Na przykład Niewykluczone, że aplikacja, która ma wiele mikrousług i każde wystąpienie raporty Metryka żądania na sekundę (RPS).</span><span class="sxs-lookup"><span data-stu-id="c1e63-194">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="c1e63-195">Jeśli jedna usługa używa więcej zasobów (pamięci, procesora, itp.), od innej usługi, koordynatora można poruszanie wystąpień usługi w klastrze w celu utrzymania nawet wykorzystanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="c1e63-195">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="c1e63-196">Należy pamiętać, że jeśli używasz usługi Azure Service Fabric zapewnia własną [monitorowanie kondycji modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), co jest bardziej zaawansowane niż kontrole kondycji proste.</span><span class="sxs-lookup"><span data-stu-id="c1e63-196">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="c1e63-197">Zaawansowane monitorowanie: wizualizacja, analizy i alerty</span><span class="sxs-lookup"><span data-stu-id="c1e63-197">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="c1e63-198">Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raporty dotyczące wydajności i alerty po wykryciu problemu.</span><span class="sxs-lookup"><span data-stu-id="c1e63-198">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="c1e63-199">Można użyć różnych rozwiązań dla systemów monitorowania.</span><span class="sxs-lookup"><span data-stu-id="c1e63-199">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="c1e63-200">Można użyć prostej aplikacji niestandardowych, przedstawiający stan usług, takich jak niestandardowa strona pokazaliśmy, kiedy możemy wyjaśnić [platformy ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="c1e63-200">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="c1e63-201">Lub za pomocą bardziej zaawansowanych narzędzi, takich jak Azure Application Insights i pakietu Operations Management Suite można zgłaszać alerty w oparciu o strumień zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c1e63-201">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="c1e63-202">Ponadto jeśli były przechowywane wszystkie strumienie zdarzeń, służy Microsoft Power BI lub rozwiązań innych firm, takich jak Kibana lub Splunk umożliwiają wizualizację danych.</span><span class="sxs-lookup"><span data-stu-id="c1e63-202">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c1e63-203">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="c1e63-203">Additional resources</span></span>

-   <span data-ttu-id="c1e63-204">**ASP.NET Core HealthChecks** (wczesnego wydawania) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="c1e63-204">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="c1e63-205">**Wprowadzenie do monitorowania kondycji usługi Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="c1e63-205">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="c1e63-206">**Usługi Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="c1e63-206">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="c1e63-207">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="c1e63-207">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c1e63-208">[Poprzednie](implement-circuit-breaker-pattern.md)
>[dalej](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="c1e63-208">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>