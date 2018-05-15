---
title: Monitorowanie kondycji
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Monitorowanie kondycji
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 81c4fc7662212bb3c6586a590d87e731220b7b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="health-monitoring"></a><span data-ttu-id="803bc-103">Monitorowanie kondycji</span><span class="sxs-lookup"><span data-stu-id="803bc-103">Health monitoring</span></span>

<span data-ttu-id="803bc-104">Monitorowanie kondycji można zezwolić na niemal czasie rzeczywistym informacje o stanie kontenery i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="803bc-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="803bc-105">Monitorowanie kondycji znaczenie ma wiele aspektów pracy mikrousług i jest szczególnie ważne w przypadku orchestrators przeprowadzania uaktualnień aplikacja częściowa w faz, jak wyjaśniono dalej.</span><span class="sxs-lookup"><span data-stu-id="803bc-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="803bc-106">Aplikacje oparte na Mikrousług często używają pulsów lub testy kondycji, aby włączyć ich monitory wydajności, planiści i orchestrators na zarządzanie wieloma usługami.</span><span class="sxs-lookup"><span data-stu-id="803bc-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="803bc-107">Jeśli usługi nie może wysłać jakiegoś "Jestem aktywności" sygnału na żądanie lub według harmonogramu, aplikacja może stają przed ryzyka podczas wdrażania aktualizacji lub może po prostu za późno wykrywanie błędów i nie można zatrzymać kaskadowych błędów, które może zakończyć w głównych awarii.</span><span class="sxs-lookup"><span data-stu-id="803bc-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="803bc-108">W typowej modelu usług wysyłać raporty o stanie ich, a tych informacji jest agregowana w celu zapewnienia przeglądu ogólny stan kondycji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="803bc-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="803bc-109">Jeśli używasz programu orchestrator, musisz podać informacje o kondycji do klastra programu orchestrator, aby klaster mógł działać w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="803bc-109">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="803bc-110">Jeśli poświęcić raportowania kondycji wysokiej jakości, dostosowany do aplikacji, można wykrywać i znacznie łatwiejsze Rozwiązywanie problemów w uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="803bc-110">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="803bc-111">Implementowanie kondycji sprawdza w usługach platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="803bc-111">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="803bc-112">Podczas tworzenia aplikacji platformy ASP.NET Core mikrousługi lub sieci web, można użyć poza pasmem biblioteki (nie oficjalne jako część ASP.NETCore) o nazwie `HealthChecks` od zespołu programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="803bc-112">When developing an ASP.NET Core microservice or web application, you can use an out-of-band library (not official as part of ASP.NETCore) named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="803bc-113">Jest dostępny w tej [repozytorium GitHub](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="803bc-113">It is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="803bc-114">Ta biblioteka jest łatwy w użyciu i udostępnia funkcje, dzięki którym można zweryfikować określonego zasobu zewnętrznego wymagane dla aplikacji (na przykład baza danych SQL Server lub zdalnego interfejsu API) działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="803bc-114">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="803bc-115">Korzystając z tej biblioteki, można również określić, co oznacza to, czy zasób jest w dobrej kondycji, jak możemy wyjaśnić później.</span><span class="sxs-lookup"><span data-stu-id="803bc-115">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="803bc-116">Aby użyć tej biblioteki, musisz najpierw użyć biblioteki w Twojej mikrousług.</span><span class="sxs-lookup"><span data-stu-id="803bc-116">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="803bc-117">Po drugie należy aplikacji frontonu, który odpytuje raportów kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="803bc-118">Można raportowania aplikacji niestandardowej aplikacji frontonu lub może być orchestrator sam mogły odpowiednio zareagować na stany kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-118">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="803bc-119">Za pomocą biblioteki HealthChecks w sieci wewnętrznej mikrousług ASP.NET</span><span class="sxs-lookup"><span data-stu-id="803bc-119">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="803bc-120">Widać, jak biblioteka HealthChecks jest używana w eShopOnContainers przykładowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="803bc-120">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="803bc-121">Aby rozpocząć, musisz zdefiniować, co stanowi stan kondycji dla każdego mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="803bc-121">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="803bc-122">W przykładowej aplikacji mikrousług są w dobrej kondycji, jeśli mikrousługi interfejsu API jest dostępny za pośrednictwem protokołu HTTP i jeśli jego powiązanych bazy danych programu SQL Server jest również dostępna.</span><span class="sxs-lookup"><span data-stu-id="803bc-122">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="803bc-123">W przyszłości można zainstalować biblioteki HealthChecks jako pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="803bc-123">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="803bc-124">Jednak opracowywania tego tekstu, musisz pobrać i Skompiluj kod jako część rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="803bc-124">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="803bc-125">Klonowanie kodu dostępne pod adresem https://github.com/dotnet-architecture/HealthChecks i skopiuj następujące foldery do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="803bc-125">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="803bc-126">src/wspólne</span><span class="sxs-lookup"><span data-stu-id="803bc-126">src/common</span></span>
  - <span data-ttu-id="803bc-127">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="803bc-127">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="803bc-128">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="803bc-128">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="803bc-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="803bc-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="803bc-130">Można także użyć dodatkowe kontrole, takich jak te dla platformy Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale ponieważ ta wersja eShopOnContainers nie ma żadnych zależności na platformie Azure, nie jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="803bc-130">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="803bc-131">Nie trzeba kontroli kondycji programu ASP.NET, ponieważ eShopOnContainers jest oparta na platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="803bc-131">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="803bc-132">Rysunek 10 – 6 przedstawia biblioteki HealthChecks w programie Visual Studio, gotowy do użycia jako bloku konstrukcyjnego przez dowolnego mikrousług.</span><span class="sxs-lookup"><span data-stu-id="803bc-132">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="803bc-133">**Rysunek 10 – 6**.</span><span class="sxs-lookup"><span data-stu-id="803bc-133">**Figure 10-6**.</span></span> <span data-ttu-id="803bc-134">Kod źródłowy platformy ASP.NET Core HealthChecks biblioteki w rozwiązaniu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="803bc-134">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="803bc-135">Jak wprowadzone wcześniej, najpierw musisz w każdym projekcie mikrousługi jest można dodać odwołania do bibliotek HealthChecks trzy.</span><span class="sxs-lookup"><span data-stu-id="803bc-135">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="803bc-136">Następnie należy dodać akcje sprawdzania kondycji, które należy wykonać w tym mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="803bc-136">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="803bc-137">Te akcje są po prostu zależne od innych baz danych lub mikrousług (HttpUrlCheck) (obecnie SqlCheck\* baz danych programu SQL Server).</span><span class="sxs-lookup"><span data-stu-id="803bc-137">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="803bc-138">Możesz dodać akcji w obrębie klasy uruchamiania każdego mikrousługi ASP.NET lub aplikacji sieci web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="803bc-138">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="803bc-139">Każdej usługi lub aplikacji sieci web należy skonfigurować przez dodanie wszystkich jego zależności HTTP lub bazy danych jako jedną metodę AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="803bc-139">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="803bc-140">Na przykład aplikacja sieci web MVC z eShopOnContainers zależy od wielu usług, w związku z tym ma kilka metod AddCheck dodane do kontroli kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-140">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="803bc-141">Na przykład w poniższym kodzie widać jak mikrousługi katalogu Dodaje zależność w swojej bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="803bc-141">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="803bc-142">Jednak aplikację sieci web MVC eShopOnContainers ma wiele zależności od reszty mikrousług.</span><span class="sxs-lookup"><span data-stu-id="803bc-142">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="803bc-143">W związku z tym wywołuje jedną metodę AddUrlCheck dla każdego mikrousługi, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="803bc-143">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="803bc-144">W związku z tym mikrousługi nie będą umożliwiać stanu "zdrowy", dopóki wszystkie jego testy są w dobrej kondycji oraz.</span><span class="sxs-lookup"><span data-stu-id="803bc-144">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="803bc-145">Jeśli mikrousługi nie ma zależności usługi lub na serwerze SQL, należy po prostu Dodaj wyboru Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="803bc-145">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="803bc-146">Poniższy kod jest mikrousługi basket.api eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="803bc-146">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="803bc-147">(Mikrousługi koszyka korzysta z pamięci podręcznej Redis, ale biblioteki nie ma jeszcze dostawcę Redis kondycji wyboru).</span><span class="sxs-lookup"><span data-stu-id="803bc-147">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="803bc-148">Dla usługi lub aplikacji sieci web do udostępnienia punktu końcowego sprawdzania kondycji, musi włączyć UseHealthChecks (\[*adres url\_dla\_kondycji\_sprawdza*\]) rozszerzenia Metoda.</span><span class="sxs-lookup"><span data-stu-id="803bc-148">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="803bc-149">Ta metoda przechodzi w WebHostBuilder w głównej metody klasy Program ASP.NET Core usługi lub sieci web aplikacji, tuż po UseKestrel, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="803bc-149">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="803bc-150">Proces przebiega następująco: każdego mikrousługi przedstawia HC punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="803bc-150">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="803bc-151">Tego punktu końcowego jest tworzony przez bibliotekę HealthChecks platformy ASP.NET Core oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="803bc-151">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="803bc-152">Po wywołaniu tego punktu końcowego uruchamia wszystkie testy kondycji skonfigurowanych w metodzie AddHealthChecks w klasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="803bc-152">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="803bc-153">Metoda UseHealthChecks oczekuje na port lub ścieżki.</span><span class="sxs-lookup"><span data-stu-id="803bc-153">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="803bc-154">Tego portu lub ścieżka jest punkt końcowy do użycia w celu sprawdzenia kondycji usługi.</span><span class="sxs-lookup"><span data-stu-id="803bc-154">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="803bc-155">Na przykład mikrousługi katalogu używa HC ścieżki.</span><span class="sxs-lookup"><span data-stu-id="803bc-155">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="803bc-156">Buforowanie odpowiedzi na sprawdzenie kondycji</span><span class="sxs-lookup"><span data-stu-id="803bc-156">Caching health check responses</span></span>

<span data-ttu-id="803bc-157">Ponieważ nie chcesz spowodować "odmowa usługi" (DoS) w usługach lub po prostu nie chcesz mieć wpływ na wydajność usługi poprzez sprawdzenie zasobów można zbyt często pamięci podręcznej zwraca i skonfigurować czas trwania pamięci podręcznej dla każdego sprawdzania kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-157">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="803bc-158">Domyślnie czas buforowania wewnętrznie jest ustawiony na 5 minut, ale można zmienić ten czas trwania pamięci podręcznej w każdym sprawdzenie kondycji, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="803bc-158">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="803bc-159">Wykonywanie zapytania z mikrousług raport stanu kondycji</span><span class="sxs-lookup"><span data-stu-id="803bc-159">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="803bc-160">Po skonfigurowaniu kontroli kondycji zgodnie z opisem w tym miejscu po mikrousługi działa w Docker można bezpośrednio sprawdzić z przeglądarki, jeśli jest w dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-160">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="803bc-161">(To wymagają są publikowania port kontenera poza hostów Docker, więc można uzyskać dostęp do kontenera, za pośrednictwem hosta lokalnego lub zewnętrzny adres IP hosta Docker). Rysunek 10-7 przedstawiono żądania w przeglądarce i odpowiadająca mu reakcja.</span><span class="sxs-lookup"><span data-stu-id="803bc-161">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="803bc-162">**Rysunek 10-7**.</span><span class="sxs-lookup"><span data-stu-id="803bc-162">**Figure 10-7**.</span></span> <span data-ttu-id="803bc-163">Sprawdzanie stanu kondycji pojedynczą usługę przy użyciu przeglądarki</span><span class="sxs-lookup"><span data-stu-id="803bc-163">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="803bc-164">W tym teście widać mikrousługi catalog.api (uruchomiony na porcie 5101) jest w dobrej kondycji zwracanie stan HTTP 200 i informacje o stanie w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="803bc-164">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="803bc-165">Oznacza to również, czy wewnętrznie usługi również sprawdzić kondycję jego zależność bazy danych programu SQL Server i że sprawdzenie kondycji został raportuje swój stan jako dobrej kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-165">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="803bc-166">Przy użyciu watchdogs</span><span class="sxs-lookup"><span data-stu-id="803bc-166">Using watchdogs</span></span>

<span data-ttu-id="803bc-167">Programu alarmowego jest oddzielny usługa można obejrzeć kondycji i obciążenie usługi i kondycji raport o mikrousług badając z biblioteką HealthChecks wprowadzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="803bc-167">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="803bc-168">Może to pomóc zapobiec wystąpieniu błędów, które nie można wykryć na podstawie widoku jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="803bc-168">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="803bc-169">Watchdogs są również dobrym miejscem do kodu hosta, który może wykonywać akcje naprawcze wykonane dla znanych warunki bez interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="803bc-169">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="803bc-170">Przykład eShopOnContainers zawiera strony sieci web, która wyświetla przykładowe raporty sprawdzania kondycji, jak pokazano na rysunku nr 10-8.</span><span class="sxs-lookup"><span data-stu-id="803bc-170">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="803bc-171">Jest to najprostsza programu alarmowego może wystąpić, ponieważ wszystkie robi są pokazuje stan aplikacji sieci web i mikrousług w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="803bc-171">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="803bc-172">Zazwyczaj programu alarmowego również wykonuje akcje, po wykryciu stanów złej kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-172">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="803bc-173">**Rysunek 10-8**.</span><span class="sxs-lookup"><span data-stu-id="803bc-173">**Figure 10-8**.</span></span> <span data-ttu-id="803bc-174">Przykładowy raport ze sprawdzania kondycji w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="803bc-174">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="803bc-175">Podsumowując oprogramowanie pośredniczące ASP.NET biblioteki ASP.NET Core HealthChecks zawiera punkt końcowy wyboru jednego kondycji dla każdego mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="803bc-175">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="803bc-176">Spowoduje to wykonania sprawdzenia kondycji zdefiniowane w nim i zwracany ogólny stan kondycji, w zależności od tych kontroli.</span><span class="sxs-lookup"><span data-stu-id="803bc-176">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="803bc-177">Biblioteka HealthChecks jest otwarty przez nowe funkcje sprawdzania kondycji przyszłych zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="803bc-177">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="803bc-178">Na przykład oczekuje się, że w przyszłości biblioteki będzie miało kontroli kondycji dla pamięci podręcznej Redis i innych baz danych.</span><span class="sxs-lookup"><span data-stu-id="803bc-178">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="803bc-179">Biblioteki umożliwia raportowania przez wiele zależności aplikacji lub usługi kondycji, a następnie można wykonać akcji w oparciu o te testy kondycji.</span><span class="sxs-lookup"><span data-stu-id="803bc-179">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="803bc-180">Sprawdzanie kondycji, używając orchestrators</span><span class="sxs-lookup"><span data-stu-id="803bc-180">Health checks when using orchestrators</span></span>

<span data-ttu-id="803bc-181">Monitorowanie dostępności sieci mikrousług, orchestrators jak Docker Swarm, Kubernetes i sieci szkieletowej usług okresowo sprawdzania kondycji, wysyłając żądania do testowania mikrousług.</span><span class="sxs-lookup"><span data-stu-id="803bc-181">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="803bc-182">Gdy orchestrator Określa, że kontenerze/usługi jest zła, przestaje routingu żądań do tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="803bc-182">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="803bc-183">Również zazwyczaj tworzy nowe wystąpienie tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="803bc-183">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="803bc-184">Na przykład większość orchestrators służy kontroli kondycji Zarządzanie wdrożeniami przestoju zero.</span><span class="sxs-lookup"><span data-stu-id="803bc-184">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="803bc-185">Tylko wtedy, gdy stan zmienia kontener/usługi, do dobrej kondycji będzie orchestrator start routingu ruchu do wystąpień kontenera/usług.</span><span class="sxs-lookup"><span data-stu-id="803bc-185">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="803bc-186">Monitorowanie kondycji jest szczególnie ważne w przypadku, gdy orchestrator przeprowadza uaktualnienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="803bc-186">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="803bc-187">Usługi w aktualizacji niektórych orchestrators (takich jak sieć szkieletowa usług Azure), fazy — na przykład może zaktualizować co piątej powierzchni klastra dla każdego uaktualnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="803bc-187">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="803bc-188">Zestaw określonych węzłów, który jest uaktualniony, w tym samym czasie jest określany jako *domeny uaktualnienia*.</span><span class="sxs-lookup"><span data-stu-id="803bc-188">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="803bc-189">Po każdej z domen został uaktualniony i jest dostępny dla użytkowników, że domena uaktualnienia musi upłynąć kontroli kondycji wdrożenia przechodzi do następnej domeny uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="803bc-189">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="803bc-190">Innym aspektem usługi kondycji jest raportowania metryki z usługi.</span><span class="sxs-lookup"><span data-stu-id="803bc-190">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="803bc-191">Jest to zaawansowane możliwości model kondycji niektóre orchestrators, takich jak sieć szkieletowa usług.</span><span class="sxs-lookup"><span data-stu-id="803bc-191">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="803bc-192">Metryki są ważne, gdy za pomocą programu orchestrator, ponieważ są one używane do równoważyć obciążenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="803bc-192">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="803bc-193">Metryki można również wskaźnik kondycji systemu.</span><span class="sxs-lookup"><span data-stu-id="803bc-193">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="803bc-194">Na przykład może być aplikacja, która ma wiele mikrousług i każde wystąpienie raporty Metryka żądania na sekundę (RPS).</span><span class="sxs-lookup"><span data-stu-id="803bc-194">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="803bc-195">Jeśli jedna usługa używa więcej zasobów (pamięci, procesora, itp.) od innej usługi, orchestrator można poruszanie wystąpień usługi w klastrze, aby spróbować Obsługa nawet wykorzystania zasobów.</span><span class="sxs-lookup"><span data-stu-id="803bc-195">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="803bc-196">Należy pamiętać, że jeśli używasz usługi Azure Service Fabric zawiera własną [monitorowanie kondycji modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), który jest bardziej zaawansowane niż kontroli kondycji proste.</span><span class="sxs-lookup"><span data-stu-id="803bc-196">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="803bc-197">Zaawansowane monitorowanie: wizualizacji, analizy i alerty</span><span class="sxs-lookup"><span data-stu-id="803bc-197">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="803bc-198">Ostatnia część monitorowania jest wizualizacja strumienia zdarzeń, raporty dotyczące wydajności usługi i alerty, gdy zostanie wykryty problem.</span><span class="sxs-lookup"><span data-stu-id="803bc-198">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="803bc-199">Można użyć różnych rozwiązań dla ten aspekt monitorowania.</span><span class="sxs-lookup"><span data-stu-id="803bc-199">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="803bc-200">Można użyć prostego niestandardowych aplikacji przedstawiający stan usług, takich jak niestandardowe strony firma Microsoft wykazały, gdy firma Microsoft wyjaśniono [platformy ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="803bc-200">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="803bc-201">Lub można zgłaszać alerty w oparciu o strumień zdarzeń za pomocą bardziej zaawansowanych narzędzi, takich jak Azure Application Insights and Operations Management Suite.</span><span class="sxs-lookup"><span data-stu-id="803bc-201">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="803bc-202">Ponadto jeśli były przechowywane wszystkich strumieni zdarzeń, służy Microsoft Power BI lub rozwiązanie innej firmy, takich jak Kibana lub Splunk do wizualizacji danych.</span><span class="sxs-lookup"><span data-stu-id="803bc-202">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="803bc-203">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="803bc-203">Additional resources</span></span>

-   <span data-ttu-id="803bc-204">**Program ASP.NET Core HealthChecks** (wczesnego wydawania) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="803bc-204">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="803bc-205">**Wprowadzenie do monitorowania kondycji sieci szkieletowej usług**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="803bc-205">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="803bc-206">**Usługa Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="803bc-206">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="803bc-207">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="803bc-207">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="803bc-208">[Poprzednie] (wdrożenie obwodu-dzielącego wyrazy pattern.md) [dalej] (.. /Secure-NET-microservices-Web-Applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="803bc-208">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>
