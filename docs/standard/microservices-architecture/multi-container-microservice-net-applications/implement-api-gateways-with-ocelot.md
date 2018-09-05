---
title: Wdrażanie bramy interfejsu API za pomocą Ocelot
description: Dowiedz się, jak zaimplementować bramy interfejsu API za pomocą Ocelot i sposobu użycia Ocelot w środowiskach opartych na kontenerach.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: dbb3fdb27175a86291d3a942ff168a5aae787c0c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43453078"
---
# <a name="implementing-api-gateways-with-ocelot"></a><span data-ttu-id="86ae5-103">Wdrażanie bramy interfejsu API za pomocą Ocelot</span><span class="sxs-lookup"><span data-stu-id="86ae5-103">Implementing API Gateways with Ocelot</span></span>

<span data-ttu-id="86ae5-104">Aplikacja mikrousług referencyjna [ramach aplikacji eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) używa [Ocelot](https://github.com/ThreeMammals/Ocelot) ponieważ Ocelot jest prosty i lekkie bramy interfejsu API, które można wdrożyć w dowolnym miejscu oraz mikrousługi / kontenery tak jak dowolne spośród następujących środowisk, które są używane w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="86ae5-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot) because Ocelot is a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="86ae5-105">Hosta platformy docker, dev lokalnym komputerze, lokalnie lub w chmurze.</span><span class="sxs-lookup"><span data-stu-id="86ae5-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="86ae5-106">Klaster Kubernetes w środowisku lokalnym lub w chmurze zarządzanych, takich jak Azure Kubernetes Service (AKS).</span><span class="sxs-lookup"><span data-stu-id="86ae5-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="86ae5-107">Klaster usługi Service Fabric w środowisku lokalnym lub w chmurze.</span><span class="sxs-lookup"><span data-stu-id="86ae5-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="86ae5-108">Usługa Service Fabric siatki jako PaaS/aplikacje niewymagające użycia serwera na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="86ae5-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="86ae5-109">Architektury i projektowania usługi bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="86ae5-110">Poniższy diagram architektury pokazuje, jak bramy interfejsu API są implementowane za pomocą Ocelot w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="86ae5-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![diagram architektury ramach aplikacji eShopOnContainers przedstawiający klienta aplikacji, mikrousługi i bramy interfejsu API między](./media/image28.png)

<span data-ttu-id="86ae5-112">**Rysunek 8-27.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-112">**Figure 8-27.**</span></span> <span data-ttu-id="86ae5-113">Architektura ramach aplikacji eShopOnContainers z bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="86ae5-114">Ten diagram przedstawia, jak cała aplikacja jest wdrażana do jednego hosta platformy Docker lub rozwoju PC "Docker for Windows" lub "Docker dla komputerów Mac".</span><span class="sxs-lookup"><span data-stu-id="86ae5-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="86ae5-115">Jednak wdrażanie do dowolnego programu orchestrator mogą być bardzo podobne, ale żaden kontener w diagramie może być skalowanych w poziomie w programie orchestrator.</span><span class="sxs-lookup"><span data-stu-id="86ae5-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span> 

<span data-ttu-id="86ae5-116">Ponadto zasobów infrastruktury, takich jak bazy danych, pamięci podręcznej i brokerami powinna być przenoszona z koordynatora i wdrożone do wysokiej dostępności systemów infrastruktury, takich jak Azure SQL Database, Azure Cosmos DB, Azure redis cache, usługa Azure Service Bus lub dowolnego HA klastrowanie rozwiązanie dla środowisk lokalnych.</span><span class="sxs-lookup"><span data-stu-id="86ae5-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="86ae5-117">Jak można również Zwróć uwagę na diagramie, masz kilka bramy interfejsu API umożliwia wielu zespołów programistycznych jako autonomiczny (sprzedaż w tym przypadku funkcje programu vs. Zakupy funkcji) podczas opracowywania i wdrażania ich mikrousługi oraz ich powiązane bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span> 

<span data-ttu-id="86ae5-118">Jeśli masz pojedynczą monolityczne bramą interfejsu API, która oznacza pojedynczy punkt zostać zaktualizowane przez kilka zespołów deweloperskich, które można połączyć wszystkie mikrousługi przy użyciu jednej części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86ae5-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="86ae5-119">Możesz to zrobić jeszcze więcej możliwości w projekt, czasami szczegółowych bramy interfejsu API można także ograniczona do mikrousług biznesowej, w zależności od wybranej architektury.</span><span class="sxs-lookup"><span data-stu-id="86ae5-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="86ae5-120">O granicach bramy interfejsu API definiowane przez firmę lub domeny pomogą uzyskać lepsze projektu.</span><span class="sxs-lookup"><span data-stu-id="86ae5-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span> 

<span data-ttu-id="86ae5-121">Na przykład zapewniającym dużą szczegółowość w warstwie bramy interfejsu API może być szczególnie przydatne w przypadku bardziej zaawansowanych aplikacji interfejsu użytkownika złożonych, które są oparte na mikrousługach, ponieważ koncepcji szczegółowych bramy interfejsu API jest podobny do usługi kompozycji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="86ae5-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span> 

<span data-ttu-id="86ae5-122">Aby uzyskać więcej informacji na temat usług kompozycji interfejsu użytkownika, zobacz [Tworzenie złożonego interfejsu użytkownika opartego na mikrousługach](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/microservice-based-composite-ui-shape-layout).</span><span class="sxs-lookup"><span data-stu-id="86ae5-122">For more information about UI composition services, see [Creating composite UI based on microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/microservice-based-composite-ui-shape-layout).</span></span>

<span data-ttu-id="86ae5-123">Jako kluczowym wnioskiem w przypadku wielu aplikacji i dużych średniego przy użyciu niestandardowej produktu bramy interfejsu API zazwyczaj to dobra metoda, ale nie jako pojedynczy agregatora monolityczne lub unikatowy centralnej interfejsu API bram o ile nie zezwala na wiele niezależnych od tej bramy interfejsu API Konfiguracja obszarów dla kilku zespołów deweloperskich, Tworzenie autonomicznego mikrousług.</span><span class="sxs-lookup"><span data-stu-id="86ae5-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="86ae5-124">Przykładowe mikrousług/kontenerów, aby przekierować za pośrednictwem bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-124">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="86ae5-125">Na przykład `eShopOnContainers` ma około sześciu mikrousługi — typy wewnętrzne, które mają być opublikowane za pośrednictwem bramy interfejsu API, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="86ae5-125">As an example, `eShopOnContainers` has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>
 
![](./media/image29.png)

<span data-ttu-id="86ae5-126">**Rysunek 8-28.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-126">**Figure 8-28.**</span></span> <span data-ttu-id="86ae5-127">Mikrousługi folderów w ramach aplikacji eShopOnContainers rozwiązania w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86ae5-127">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="86ae5-128">O usłudze tożsamości w projekcie, który pozostanie w poza bramy interfejsu API routingu, ponieważ jest on tylko przekrojowe dotyczą w systemie, ale z Ocelot istnieje również możliwość dołączyć go jako część listy przekierowania.</span><span class="sxs-lookup"><span data-stu-id="86ae5-128">About the Identity service, in the design it is left out of the API Gateway routing because it is the only cross-cutting concern in the system, but with Ocelot it is also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="86ae5-129">Te usługi są implementowane jako usługi internetowego interfejsu API platformy ASP.NET Core, obecnie, jak można stwierdzić, ze względu na kod.</span><span class="sxs-lookup"><span data-stu-id="86ae5-129">All those services are currently implemented as ASP.NET Core Web API services, as you can tell because of the code.</span></span> <span data-ttu-id="86ae5-130">Skupmy się na jednym z mikrousług, podobnie jak kod mikrousług katalogu.</span><span class="sxs-lookup"><span data-stu-id="86ae5-130">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![](./media/image30.png)

<span data-ttu-id="86ae5-131">**Rysunek 8-29.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-131">**Figure 8-29.**</span></span> <span data-ttu-id="86ae5-132">Przykładowy internetowy interfejs API mikrousług (mikrousług katalogu)</span><span class="sxs-lookup"><span data-stu-id="86ae5-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="86ae5-133">Widać, że mikrousługa wykazu jest typowym projekcie internetowego interfejsu API platformy ASP.NET Core za pomocą kilku kontrolerów i metod, takich jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86ae5-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```
<span data-ttu-id="86ae5-134">Żądanie HTTP zostaną uruchomione tego rodzaju kod C#, uzyskiwanie dostępu do bazy danych mikrousług, a także żadnych dodatkowych działań.</span><span class="sxs-lookup"><span data-stu-id="86ae5-134">The HTTP request will end up running that kind of C# code accessing the microservice database plus any additional action.</span></span>

<span data-ttu-id="86ae5-135">W odniesieniu do adresu URL mikrousług, gdy kontenery są wdrażane Tworzenie lokalnego komputera (lokalnego hosta platformy Docker), każda mikrousługa kontener ma zawsze wewnętrzny port, zwykle jest to port 80, określone w pliku dockerfile i tak jak w poniższym pliku dockerfile:</span><span class="sxs-lookup"><span data-stu-id="86ae5-135">In regards to the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port, usually port 80, specified in its dockerfile, as in the following dockerfile:</span></span>

```
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="86ae5-136">Port 80, jak pokazano w kodzie jest wewnętrzny w ramach hosta platformy Docker, więc nie można nawiązać połączenia przez aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="86ae5-136">The port 80 shown in the code is internal within the Docker host, so it cannot be reached by the client apps.</span></span> <span data-ttu-id="86ae5-137">Aplikacje klienckie mogą uzyskać dostęp tylko do portów zewnętrznych (jeśli istnieje), gdy wdrażanie przy użyciu `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="86ae5-137">The client apps can access only to the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="86ae5-138">Nie należy można opublikować tych portów zewnętrznych, w przypadku wdrażania w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="86ae5-138">Those external ports shouldn't be published when deploying into a production environment.</span></span> <span data-ttu-id="86ae5-139">Jest to dokładnie, dlaczego chcesz używać bramy interfejsu API, aby uniknąć bezpośrednia komunikacja między aplikacjami klienta i mikrousług.</span><span class="sxs-lookup"><span data-stu-id="86ae5-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="86ae5-140">Jednak podczas opracowywania, ma bezpośredni dostęp mikrousług/kontenera i uruchom je za pośrednictwem struktury Swagger.</span><span class="sxs-lookup"><span data-stu-id="86ae5-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="86ae5-141">Właśnie w ramach aplikacji eShopOnContainers portów zewnętrznych są nadal zaznaczone nawet wtedy, gdy nie będą używane przez bramę interfejsów API lub aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="86ae5-141">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="86ae5-142">Oto przykład `docker-compose.override.yml` pliku dla mikrousług katalogu:</span><span class="sxs-lookup"><span data-stu-id="86ae5-142">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes. 
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="86ae5-143">Możesz zobaczyć, jak w konfiguracji platformy docker-compose.override.yml wewnętrzny port kontenera wykazu jest port 80, ale numer portu na potrzeby dostępu zewnętrznego to 5101.</span><span class="sxs-lookup"><span data-stu-id="86ae5-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="86ae5-144">Jednak ten port nie powinien używanych przez aplikację, za pomocą bramy interfejsu API tylko debugowanie, uruchamianie i testowanie po prostu mikrousług katalogu.</span><span class="sxs-lookup"><span data-stu-id="86ae5-144">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="86ae5-145">Zwykle nie można wdrożyć za pomocą platformy docker-compose w środowisku produkcyjnym, ponieważ środowisko wdrażania produkcyjnym mikrousług jest koordynatora Kubernetes lub usługi Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="86ae5-145">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="86ae5-146">Podczas wdrażania tych środowisk użyjesz różnymi plikami konfiguracji gdzie nie będzie publikować bezpośrednio dowolnym porcie zewnętrznym mikrousług, ale, będzie zawsze używać zwrotny serwer proxy z bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-146">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="86ae5-147">Uruchamianie mikrousług wykazu w lokalnego hosta platformy Docker, uruchamiając rozwiązania pełnego w ramach aplikacji eShopOnContainers z programu Visual Studio (go uruchomić wszystkie usługi na platformie docker-tworzą pliki) lub po prostu uruchamianie mikrousług katalogu za pomocą następujących platformy docker-compose polecenia w pliku polecenia lub programu PowerShell umieszczony w folderze gdzie `docker-compose.yml` i są umieszczane docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="86ae5-147">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="86ae5-148">To polecenie uruchamia tylko catalog.api usługi kontenera, a także zależności, które są określone w docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="86ae5-148">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="86ae5-149">W takim kontenera programu SQL Server i oprogramowania RabbitMQ kontenera.</span><span class="sxs-lookup"><span data-stu-id="86ae5-149">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="86ae5-150">Następnie można również bezpośrednio dostęp do mikrousług katalogu a jego metod za pośrednictwem interfejsu użytkownika programu Swagger bezpośrednio za pomocą dostęp, czy "external" portu, w tym przypadku `http://localhost:5101`.</span><span class="sxs-lookup"><span data-stu-id="86ae5-150">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101`.</span></span> 

![](./media/image31.png)

<span data-ttu-id="86ae5-151">**Rysunek 8-30.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-151">**Figure 8-30.**</span></span> <span data-ttu-id="86ae5-152">Testowanie mikrousług katalogu za pomocą jego interfejsu użytkownika programu Swagger</span><span class="sxs-lookup"><span data-stu-id="86ae5-152">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="86ae5-153">W tym momencie można ustawić punkt przerwania w kodzie języka C# w programie Visual Studio, testowanie mikrousług za pomocą metod udostępnianych w interfejs użytkownika struktury Swagger i na koniec oczyszczania wszystkiego za pomocą `docker-compose down` polecenia.</span><span class="sxs-lookup"><span data-stu-id="86ae5-153">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="86ae5-154">Jednak ta komunikacja bezpośredniego dostępu do mikrousług, w tym przypadku za pośrednictwem portu zewnętrznego 5101 jest dokładnie chce się uniknąć w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86ae5-154">However, this direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="86ae5-155">I można uniknąć, ustawiając dodatkowy poziom pośredni bramy interfejsu API (w tym przypadku Ocelot).</span><span class="sxs-lookup"><span data-stu-id="86ae5-155">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="86ae5-156">Dzięki temu aplikacja kliencka nie uzyskać bezpośredni dostęp do mikrousług.</span><span class="sxs-lookup"><span data-stu-id="86ae5-156">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="86ae5-157">Wdrażanie usługi bramy interfejsu API za pomocą Ocelot</span><span class="sxs-lookup"><span data-stu-id="86ae5-157">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="86ae5-158">Ocelot jest zasadniczo zbiorem middlewares, które można zastosować w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="86ae5-158">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="86ae5-159">Ocelot jest przeznaczona do pracy z platformą ASP.NET Core tylko.</span><span class="sxs-lookup"><span data-stu-id="86ae5-159">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="86ae5-160">Jest ono przeznaczone dla netstandard2.0, dzięki czemu może służyć wszędzie tam, gdzie .NET Standard 2.0 jest obsługiwane, w tym środowiska uruchomieniowego .NET Core 2.0 i środowiska uruchomieniowego .NET Framework 4.6.1 oraz jego nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="86ae5-160">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="86ae5-161">Zainstaluj Ocelot i jego zależności w projekcie platformy ASP.NET Core za pomocą [pakietu NuGet w Ocelot](https://www.nuget.org/packages/Ocelot/), z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86ae5-161">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```
Install-Package Ocelot
```

<span data-ttu-id="86ae5-162">W ramach aplikacji eShopOnContainers jego implementacja bramy interfejsu API jest prosty projekt hostem sieci Web platformy ASP.NET Core i middlewares firmy Ocelot obsługi wszystkie funkcje bramy interfejsu API, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="86ae5-162">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![](./media/image32.png)

<span data-ttu-id="86ae5-163">**Rysunek 8-31.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-163">**Figure 8-31.**</span></span> <span data-ttu-id="86ae5-164">Podstawowy projekt OcelotApiGw w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="86ae5-164">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="86ae5-165">Ten projekt hostem sieci Web platformy ASP.NET Core jest tworzone przez dwa pliki proste, `Program.cs` i `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="86ae5-165">This ASP.NET Core WebHost project is made by two simple files, the `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="86ae5-166">Plik Program.cs musi jedynie tworzyć i konfigurować typowe BuildWebHost Core ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86ae5-166">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span> 

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))                
                                                          .ConfigureAppConfiguration(
                              ic => ic.AddJsonFile(Path.Combine("configuration",
                                                                "configuration.json")))
                                                                .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="86ae5-167">Należy koniecznie zwrócić uwagę na Ocelot jest `configuration.json` pliku, który należy podać do konstruktora za pośrednictwem `AddJsonFile()` metody.</span><span class="sxs-lookup"><span data-stu-id="86ae5-167">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="86ae5-168">Czy `configuration.json` służy do określania wszystkich interfejsu API bramy ReRoutes, co oznacza, zewnętrzne punkty końcowe o określonych portów i skorelowane wewnętrznych punktów końcowych, zazwyczaj przy użyciu różnych portów.</span><span class="sxs-lookup"><span data-stu-id="86ae5-168">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="86ae5-169">Istnieją dwie sekcje w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86ae5-169">There are two sections to the configuration.</span></span> <span data-ttu-id="86ae5-170">Tablica przekieruje i GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="86ae5-170">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="86ae5-171">Przekieruje to obiekty, które Ocelot stwierdzić, jak ma traktować żądania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="86ae5-171">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="86ae5-172">Jego konfigurację globalną umożliwia zastąpienia przekierowuje określone ustawienia.</span><span class="sxs-lookup"><span data-stu-id="86ae5-172">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="86ae5-173">Jest to przydatne, jeśli nie chcesz zarządzać mnóstwo przekierowuje określone ustawienia.</span><span class="sxs-lookup"><span data-stu-id="86ae5-173">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="86ae5-174">Oto uproszczony przykład [konfiguracji przekierowania](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) plików z jednego z bramy interfejsu API w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="86ae5-174">Here’s a simplified example of [ReRoute configuration](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) file from one of the API Gateways from eShopOnContainers.</span></span>

```
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
    
  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="86ae5-175">Główne funkcje bramy interfejsu API Ocelot jest przychodzących żądań HTTP i przekazują je do podrzędnego usługa, obecnie jako innego protokołu HTTP żądania.</span><span class="sxs-lookup"><span data-stu-id="86ae5-175">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="86ae5-176">Firmy ocelot Opisuje routing jedno żądanie do innego jako ponownie rozesłać.</span><span class="sxs-lookup"><span data-stu-id="86ae5-176">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="86ae5-177">Na przykład Skupmy się na jednym z przekieruje w configuration.json powyższej konfiguracji dla mikrousług koszyka.</span><span class="sxs-lookup"><span data-stu-id="86ae5-177">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="86ae5-178">DownstreamPathTemplate, schemat i DownstreamHostAndPorts należy mikrousług wewnętrzny adres URL, z którego to żądanie, które zostaną przekazane do.</span><span class="sxs-lookup"><span data-stu-id="86ae5-178">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span> 

<span data-ttu-id="86ae5-179">Numer portu to port wewnętrzny używany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="86ae5-179">The port is the internal port used by the service.</span></span> <span data-ttu-id="86ae5-180">Podczas korzystania z kontenerów, port określony w odpowiednim plikiem dockerfile.</span><span class="sxs-lookup"><span data-stu-id="86ae5-180">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="86ae5-181">`Host` Jest nazwą usługi, która jest zależna od usługi rozpoznawania nazw, używasz.</span><span class="sxs-lookup"><span data-stu-id="86ae5-181">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="86ae5-182">Korzystając z platformy docker-compose usług nazwy są dostarczane przez hosta platformy Docker, który używa nazwy usługi udostępniane na platformie docker-tworzą pliki.</span><span class="sxs-lookup"><span data-stu-id="86ae5-182">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="86ae5-183">Jeśli używasz programu orchestrator, takich jak Kubernetes lub usługi Service Fabric, tej nazwy powinny być rozpoznawane przez DNS lub rozpoznawania nazw, dostarczone przez poszczególnych koordynatorów.</span><span class="sxs-lookup"><span data-stu-id="86ae5-183">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="86ae5-184">DownstreamHostAndPorts jest tablica zawierająca hosta i portu usługami podrzędnymi, które chcesz przekazywać żądania do.</span><span class="sxs-lookup"><span data-stu-id="86ae5-184">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="86ae5-185">Zwykle to po prostu zawiera jeden wpis, ale czasami możesz chcieć równoważenia obciążenia żądań kierowanych do usługi transmisji i Ocelot pozwala dodać więcej niż jeden wpis, a następnie wybierz moduł równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="86ae5-185">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="86ae5-186">Ale jeśli za pomocą platformy Azure i wszelkie orchestrator jest prawdopodobnie lepiej zrozumieć równoważenia obciążenia za pomocą infrastruktury chmury i programu orchestrator.</span><span class="sxs-lookup"><span data-stu-id="86ae5-186">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="86ae5-187">UpstreamPathTemplate jest adres URL, który Ocelot będzie używany do identyfikowania które DownstreamPathTemplate do użycia dla danego żądania od klienta.</span><span class="sxs-lookup"><span data-stu-id="86ae5-187">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="86ae5-188">Na koniec UpstreamHttpMethod jest używana, więc Ocelot można odróżnić różne żądania (POST, GET PUT) do tego samego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="86ae5-188">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="86ae5-189">W tym momencie może mieć jednej bramy interfejsu API Ocelot (ASP.NET Core WebHost) przy użyciu jednej lub [wielu scalić pliki configuration.json](http://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) lub można również przechowywać [konfiguracji w magazynie KV Konsul](http://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="86ae5-189">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](http://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](http://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span> 

<span data-ttu-id="86ae5-190">Ale wprowadzoną w sekcjach architektury i projektu, jeśli na pewno chcesz mieć autonomicznego mikrousług, może być lepszym rozwiązaniem podzielić tego jednego monolityczne bramy interfejsu API na wiele bramy interfejsu API i/lub BFF (zaplecze dla frontonu).</span><span class="sxs-lookup"><span data-stu-id="86ae5-190">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="86ae5-191">W tym celu Zobaczmy, jak zaimplementować podejście z kontenerami aparatu Docker.</span><span class="sxs-lookup"><span data-stu-id="86ae5-191">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="86ae5-192">Przy użyciu jednego obrazu kontenera platformy Docker w celu uruchamiania wielu różnych bramy interfejsu API / BFF typy kontenera</span><span class="sxs-lookup"><span data-stu-id="86ae5-192">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span> 

<span data-ttu-id="86ae5-193">Projekt w ramach aplikacji eShopOnContainers implementuje jednego obrazu kontenera platformy Docker przy użyciu bramy interfejsu API Ocelot, ale następnie podczas wdrażania do platformy Docker, tworzy różnych usług/kontenerów dla każdego typu interfejsu API — bramy/BFF, podając inną configuration.json plik dla każdego kontenera.</span><span class="sxs-lookup"><span data-stu-id="86ae5-193">The design in eShopOnContainers implements a single Docker container image with the Ocelot API Gateway but then, when deploying to Docker, it creates different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file for each container.</span></span>

![](./media/image33.png)

<span data-ttu-id="86ae5-194">**Rysunek 8 do 32.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-194">**Figure 8-32.**</span></span> <span data-ttu-id="86ae5-195">Ponowne użycie jednego obrazu platformy Docker Ocelot wielu typów bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-195">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="86ae5-196">W ramach aplikacji eShopOnContainers, "Ogólnego Ocelot interfejsu API bramy obrazu platformy Docker" jest tworzony za pomocą projektu o nazwie "OcelotApiGw" i obrazu nazwę "eshop/ocelotapigw", oznacza to określone w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="86ae5-196">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="86ae5-197">Następnie podczas wdrażania do platformy Docker, nastąpi cztery kontenery bramy interfejsu API utworzonego na podstawie tego samego obrazu Docker, jak pokazano w poniższym wyodrębnione z pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="86ae5-197">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```
PARTIAL DOCKER-COMPOSE.YML

  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
 
  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
 
  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="86ae5-198">Ponadto i jak widać w pliku docker-compose.override.yml, jedyną różnicą między tymi kontenerów bramy interfejsu API jest Ocelot pliku konfiguracji, który jest inny dla każdego kontenera usługi i jest określony w czasie wykonywania za pomocą woluminu platformy Docker, jak pokazano w następującym pliku docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="86ae5-198">Additionally, and as you can see in the docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and is specified at runtime through a Docker volume, as shown in the following docker-compose.override.yml file.</span></span>

```
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5200:80"   
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration
 
mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5201:80"   
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5202:80"   
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api              
  ports:
    - "5203:80"   
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="86ae5-199">W związku z tym poprzedni kod i zgodnie z informacjami w Eksploratorze programu Visual Studio poniżej to jedyny plik niezbędnej do zdefiniowania każdego określonego firm/BFF bramy interfejsu API jest po prostu plikiem configuration.json, ponieważ cztery bramy interfejsu API są oparte na ten sam obraz platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="86ae5-199">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![](./media/image34.png)

<span data-ttu-id="86ae5-200">**Rysunek 8-33.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-200">**Figure 8-33.**</span></span> <span data-ttu-id="86ae5-201">To jedyny plik niezbędnej do zdefiniowania każdej bramy interfejsu API / BFF z Ocelot to plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="86ae5-201">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span> 

<span data-ttu-id="86ae5-202">Dzieląc bramy interfejsu API na wiele bram interfejsu API, zespoły deweloperów różnych, skupiając się na różne podzbiory mikrousług można zarządzać własne bramy interfejsu API za pomocą niezależnych plikach konfiguracji Ocelot.</span><span class="sxs-lookup"><span data-stu-id="86ae5-202">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="86ae5-203">Ponadto w tym samym czasie można wykorzystać ten sam obraz platformy Docker Ocelot.</span><span class="sxs-lookup"><span data-stu-id="86ae5-203">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span> 

<span data-ttu-id="86ae5-204">Teraz po uruchomieniu ramach aplikacji eShopOnContainers przy użyciu bramy interfejsu API (domyślnie włączone w programie VS podczas otwierania rozwiązania w ramach aplikacji eShopOnContainers ServicesAndWebApps.sln, czy działa "docker-compose up"), zostaną wykonane następujące trasy próbki.</span><span class="sxs-lookup"><span data-stu-id="86ae5-204">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span> 

<span data-ttu-id="86ae5-205">Na przykład podczas odwiedzania adresu URL połączenia nadrzędnego http://localhost:5202/api/v1/c/catalog/items/2/ obsługiwanej przez webshoppingapigw bramy interfejsu API, uzyskać wynik z wewnętrznego adresu URL podrzędne http://catalog.api/api/v1/2 w ramach hosta platformy Docker, tak jak w poniższym przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="86ae5-205">For instance, when visiting the upstream URL http://localhost:5202/api/v1/c/catalog/items/2/ served by the webshoppingapigw API Gateway, you get the result from the internal Downstream URL http://catalog.api/api/v1/2 within the Docker host, as in the following browser.</span></span>

![](./media/image35.png)

<span data-ttu-id="86ae5-206">**Rysunek 8-34.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-206">**Figure 8-34.**</span></span> <span data-ttu-id="86ae5-207">Uzyskiwanie dostępu do mikrousług przy użyciu adresu URL podany przez bramę interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-207">Accessing a microservice through a URL provided by the API Gateway</span></span> 

<span data-ttu-id="86ae5-208">Ze względu na testowania i debugowania ze względu na, jeśli chce się uzyskać bezpośredni dostęp do kontenera Docker katalogu (tylko w środowisku programistycznym), bez przekazywania przez bramę interfejsu API, ponieważ "catalog.api" jest wewnętrznym hosta platformy Docker (usługa rozpoznawania nazw DNS Odnajdywanie obsługiwane przez docker-compose nazw usług), jedynym sposobem uzyskiwania bezpośredniego dostępu do kontenera jest za pośrednictwem portu zewnętrznego, opublikowane w docker-compose.override.yml, która jest dostępna tylko w przypadku tworzenia testów, takich jak http://localhost:5101/api/v1/Catalog/items/1 poniżej Przeglądarka.</span><span class="sxs-lookup"><span data-stu-id="86ae5-208">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as http://localhost:5101/api/v1/Catalog/items/1 in the following browser.</span></span>

![](./media/image36.png)

<span data-ttu-id="86ae5-209">**Rysunek 8 – 35.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-209">**Figure 8-35.**</span></span> <span data-ttu-id="86ae5-210">Bezpośredni dostęp do mikrousług do celów testowych</span><span class="sxs-lookup"><span data-stu-id="86ae5-210">Direct access to a microservice for testing purposes</span></span> 

<span data-ttu-id="86ae5-211">Ale gdy aplikacja jest skonfigurowana, dzięki czemu uzyskuje dostęp wszystkie mikrousługi za pośrednictwem bramy interfejsu API nie jest jednak przeniesiony bezpośrednio "skróty".</span><span class="sxs-lookup"><span data-stu-id="86ae5-211">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span> 

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="86ae5-212">Wzorzec agregacji za pomocą bramy w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="86ae5-212">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="86ae5-213">Jak wprowadzone wcześniej, elastyczny sposób implementacji agregacji żądania jest za pomocą niestandardowych usług przez kod.</span><span class="sxs-lookup"><span data-stu-id="86ae5-213">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="86ae5-214">Można również wdrożyć agregacji żądania z funkcją agregacji żądania w Ocelot, ale może nie być tak elastyczne, ilu potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="86ae5-214">You could also implement request aggregation with the Request Aggregation feature in Ocelot, but it might not be as flexible as you need.</span></span> <span data-ttu-id="86ae5-215">Dlatego wybrane sposobem realizowania agregacji w ramach aplikacji eShopOnContainers jest jawne usługi internetowego interfejsu API platformy ASP.NET Core dla każdego agregatora.</span><span class="sxs-lookup"><span data-stu-id="86ae5-215">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span> 

<span data-ttu-id="86ae5-216">Zgodnie z tego podejścia diagram składu bramę interfejsu API jest w rzeczywistości nieco bardziej rozszerzony, biorąc pod uwagę usług agregatora, które nie są wyświetlane na diagramie uproszczona architektura globalnego przedstawionego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="86ae5-216">According to that approach, the API Gateway composition diagram is in reality a bit more extended when taking into account the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span> 

<span data-ttu-id="86ae5-217">Na poniższym diagramie widać również jak usług agregatora odnoszą się do ich powiązane bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-217">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![](./media/image37.png)

<span data-ttu-id="86ae5-218">**Rysunek 8-36.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-218">**Figure 8-36.**</span></span> <span data-ttu-id="86ae5-219">Architektura ramach aplikacji eShopOnContainers z usługami agregatora</span><span class="sxs-lookup"><span data-stu-id="86ae5-219">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="86ae5-220">Poniższa ilustracja jest powiększania sprawy, dzięki czemu można zauważyć, jak dla obszaru "Zakupy" biznesowe aplikacje klienckie można poprawić, zmniejszając liczbę operacji przy użyciu mikrousług, korzystając z tych usług agregator w ramach obszaru bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-220">The following image is zooming in further, so you can notice how for the “Shopping” business area, the client apps could be improved by reducing chattiness with microservices when using those aggregator services under the realm of the API Gateways.</span></span> 

 ![](./media/image38.png)

<span data-ttu-id="86ae5-221">**Rysunek 8-37.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-221">**Figure 8-37.**</span></span> <span data-ttu-id="86ae5-222">Powiększ wizji usług agregatora</span><span class="sxs-lookup"><span data-stu-id="86ae5-222">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="86ae5-223">Można zauważyć, jak podczas na diagramie przedstawiono możliwe żądania pochodzące z bramy interfejsu API go uzyskać dość złożony.</span><span class="sxs-lookup"><span data-stu-id="86ae5-223">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="86ae5-224">Mimo że można zobaczyć, jak strzałki w kolorze niebieskim będzie można uprościć, z punktu widzenia aplikacji klienta podczas używania wzorca agregatora, zmniejszając liczbę operacji i opóźnień w komunikacji, ostatecznie znacznego poprawienia użytkownika środowisko (aplikacje zdalne aplikacje mobilne i SPA), szczególnie.</span><span class="sxs-lookup"><span data-stu-id="86ae5-224">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span> 

<span data-ttu-id="86ae5-225">W przypadku "Marketing" obszar działalności i mikrousług jest bardzo prosty przypadek użycia, więc nie istniała potrzeba, aby użyć agregatora, ale może być również możliwe, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="86ae5-225">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="86ae5-226">Uwierzytelnianie i autoryzacja w Ocelot bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-226">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="86ae5-227">W przypadku bramy interfejsu API Ocelot może się znajdować usługi uwierzytelniania, na przykład usługi internetowego interfejsu API platformy ASP.NET Core przy użyciu [IdentityServer](http://identityserver.io/) dostarczanie token uwierzytelniania, w poziomie lub w ramach bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-227">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](http://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="86ae5-228">Ponieważ jest w ramach aplikacji eShopOnContainers przy użyciu wielu bramy interfejsu API z granicami oparte na BFF i obszarów działalności, usługa tożsamości/Auth pozostanie poza bramy interfejsu API, jak podkreślono na żółto na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="86ae5-228">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

 ![](./media/image39.png)

<span data-ttu-id="86ae5-229">**Rysunek 8-38.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-229">**Figure 8-38.**</span></span> <span data-ttu-id="86ae5-230">Pozycja Usługa zarządzania tożsamościami w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="86ae5-230">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="86ae5-231">Jednak Ocelot obsługuje również siedzieć mikrousług tożsamości/uwierzytelnianie w ramach bramy interfejsu API, tak jak ten inny diagram.</span><span class="sxs-lookup"><span data-stu-id="86ae5-231">However, Ocelot also supports to sit the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

 ![](./media/image40.png)

<span data-ttu-id="86ae5-232">**Rysunek 8-39.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-232">**Figure 8-39.**</span></span> <span data-ttu-id="86ae5-233">Uwierzytelnianie w Ocelot bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="86ae5-233">Authentication in Ocelot API Gateway</span></span>

<span data-ttu-id="86ae5-234">Ponieważ aplikacji w ramach aplikacji eShopOnContainers została podzielona bramy interfejsu API na wiele BFF (zaplecze dla serwera sieci Web) i obszarów działalności bramy interfejsu API i inną opcją będzie była do utworzenia dodatkowych bramy interfejsu API dla odciąż przekrojowe zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="86ae5-234">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="86ae5-235">Wybór będzie podejście w bardziej złożonych mikrousług na podstawie architektury z wielu mikrousług odciąż przekrojowe zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="86ae5-235">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="86ae5-236">Ponieważ istnieje tylko jeden kwestią przekrojowe w ramach aplikacji eShopOnContainers, zdecydowano tylko obsługi usługi zabezpieczeń z obszaru bramy interfejsu API dla uproszczenia firmy sake.</span><span class="sxs-lookup"><span data-stu-id="86ae5-236">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="86ae5-237">W każdym przypadku jeśli aplikacja jest zabezpieczona na poziomie bramy interfejsu API, moduł uwierzytelniania bramy interfejsu API Ocelot odwiedzeniu na początku podczas próby użycia wszystkie mikrousługi zabezpieczone.</span><span class="sxs-lookup"><span data-stu-id="86ae5-237">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="86ae5-238">Który ponownie kieruje żądania HTTP do odwiedzenia mikrousługi tożsamości lub uwierzytelniania, tak więc, możesz odwiedzić stronę usług chronionych za pomocą access_token uzyskiwanie tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="86ae5-238">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="86ae5-239">Metodą zabezpieczanie przy użyciu uwierzytelniania dowolnej usługi na poziomie bramy interfejsu API jest ustawienie AuthenticationProviderKey w powiązanych ustawieniami configuration.json.</span><span class="sxs-lookup"><span data-stu-id="86ae5-239">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="86ae5-240">Po uruchomieniu Ocelot go odczyta AuthenticationOptions.AuthenticationProviderKey przekieruje i sprawdź, czy dostawcę uwierzytelniania, zarejestrowanych z danym kluczem.</span><span class="sxs-lookup"><span data-stu-id="86ae5-240">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="86ae5-241">Jeśli nie istnieje, następnie Ocelot nie zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="86ae5-241">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="86ae5-242">Jeśli, następnie przekierowanie użyje tego dostawcy, podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86ae5-242">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="86ae5-243">Ponieważ skonfigurowano Ocelot WebHost `authenticationProviderKey = "IdentityApiKey"`, mogą one wymagać uwierzytelniania zawsze wtedy, gdy tej usługi zawiera wszystkich żądań bez żadnych tokenu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="86ae5-243">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span> 

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };                   
                });
            //...
```

<span data-ttu-id="86ae5-244">Następnie również należy ustawić autoryzacji za pomocą atrybutu [Authorize] na żaden zasób były dostępne takich jak mikrousługi, takie jak w następującym kontrolerem mikrousług koszyka.</span><span class="sxs-lookup"><span data-stu-id="86ae5-244">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {   
      //...
    }
}
```

<span data-ttu-id="86ae5-245">ValidAudiences, takie jak "koszyka" są powiązane z odbiorcami zdefiniowane w poszczególne mikrousługi przy użyciu `AddJwtBearer()` na ConfigureServices() klasy uruchamiania, taki jak poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="86ae5-245">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl"); 
                
services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="86ae5-246">Jako następny krok, jeśli zostanie podjęta próba dostępu do żadnych zabezpieczonej mikrousług, takie jak mikrousługi koszyka za pomocą adresu URL przekierowuje oparte na bramy interfejsu API, takich jak http://localhost:5202/api/v1/b/basket/1 , a następnie otrzymasz 401 Brak autoryzacji, chyba że należy podać prawidłowy token.</span><span class="sxs-lookup"><span data-stu-id="86ae5-246">As next step, if you try to access any secured microservice like the Basket microservice with a Re-Route URL based on the API Gateway like http://localhost:5202/api/v1/b/basket/1 then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="86ae5-247">Z drugiej strony Jeśli adres URL przekierowuje jest uwierzytelniony, Ocelot wywoła, niezależnie od transmisji schemat jest skojarzony z nim (adres URL wewnętrznej mikrousług).</span><span class="sxs-lookup"><span data-stu-id="86ae5-247">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="86ae5-248">**Autoryzacja w warstwie przekieruje Ocelot firmy.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-248">**Authorization at Ocelot’s Re-Routes tier.**</span></span>  <span data-ttu-id="86ae5-249">Ocelot obsługuje autoryzacji opartej na oświadczeniach, ocenione po uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="86ae5-249">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="86ae5-250">Autoryzacja jest ustawiona na poziomie trasy, dodając następujący kod do konfiguracji ponownie rozesłać.</span><span class="sxs-lookup"><span data-stu-id="86ae5-250">You set the authorization at a route level by adding the following code to the re-route configuration.</span></span> 

```
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="86ae5-251">W tym przykładzie wywołanego oprogramowania pośredniczącego autoryzacji Ocelot znajdzie Jeśli użytkownik ma typ oświadczenia "UserType" w tokenie, a wartość to roszczenie "pracownik".</span><span class="sxs-lookup"><span data-stu-id="86ae5-251">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="86ae5-252">Jeśli nie, użytkownik nie będzie autoryzowany, a odpowiedź będzie miała 403 — Dostęp zabroniony.</span><span class="sxs-lookup"><span data-stu-id="86ae5-252">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span> 

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="86ae5-253">Przy użyciu transferu danych przychodzących rozwiązania Kubernetes, a także Ocelot interfejsu API bramy</span><span class="sxs-lookup"><span data-stu-id="86ae5-253">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="86ae5-254">Korzystając z rozwiązania Kubernetes (na przykład w klastrze usługi Azure Kubernetes Service), zwykle ujednolicenie żądań HTTP za pośrednictwem [Kuberentes ruch przychodzący warstwy](https://kubernetes.io/docs/concepts/services-networking/ingress/) na podstawie *Nginx*.</span><span class="sxs-lookup"><span data-stu-id="86ae5-254">When using Kubernetes (like in an Azure Kubernetes Service cluster),, you usually unify all the HTTP requests through the [Kuberentes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span> 

<span data-ttu-id="86ae5-255">Kuberentes Jeśli nie używasz jakiejkolwiek metody transferu danych przychodzących, wówczas usług i zasobników miała tylko rutowalne adresy IP przez sieć klastra.</span><span class="sxs-lookup"><span data-stu-id="86ae5-255">In Kuberentes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span> 

<span data-ttu-id="86ae5-256">Jednak jeśli używasz metody transferu danych przychodzących, będziesz mieć warstwy środkowej między Internetem a usługi (łącznie z bram Twojego interfejsu API), działający jako zwrotny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="86ae5-256">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="86ae5-257">Definicja ruchu przychodzącego to zbiór reguł zezwalających na połączenia przychodzące do uzyskania dostępu do usług klastrowania.</span><span class="sxs-lookup"><span data-stu-id="86ae5-257">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="86ae5-258">Ruch przychodzący jest skonfigurowany do Podaj dostępny zewnętrznie adresów URL usług, obciążenia równoważenia ruchu, kończenie żądań SSL i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="86ae5-258">An ingress is configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="86ae5-259">Użytkownicy żądanie transferu danych przychodzących, publikując zasobów transferu danych przychodzących do serwera interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-259">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="86ae5-260">W ramach aplikacji eShopOnContainers, podczas opracowywania lokalnie i za pomocą tylko maszynie deweloperskiej jako hosta platformy Docker nie używasz dowolnego ruchu przychodzącego, ale tylko wielu bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-260">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span> 

<span data-ttu-id="86ae5-261">Jednak gdy przeznaczonych dla środowiska "produkcyjne", w oparciu o Kuberentes, ramach aplikacji eShopOnCOntainers korzysta z transferu danych przychodzących przed bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-261">However, when targeting a “production” environment based on Kuberentes, eShopOnCOntainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="86ae5-262">Dzięki temu klienci wciąż wywołać tego samego podstawowego adresu URL, ale żądania są kierowane do wielu bram API lub BFF.</span><span class="sxs-lookup"><span data-stu-id="86ae5-262">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span> 

<span data-ttu-id="86ae5-263">Należy pamiętać, że bramy interfejsu API są Frontony lub fasad, dzięki czemu są ujawniane tylko usług, ale nie aplikacje sieci web, które są zazwyczaj poza ich zakresem.</span><span class="sxs-lookup"><span data-stu-id="86ae5-263">Note that API Gateways are front-ends or facades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="86ae5-264">Ponadto bramy interfejsu API może ukryć niektórych wewnętrznych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="86ae5-264">In addition, the API Gateways might hide certain internal microservices.</span></span> 

<span data-ttu-id="86ae5-265">Ruch przychodzący, jednak jest po prostu Przekierowywanie żądań HTTP, ale nie próbuje ukryć wszystkie mikrousługi lub aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="86ae5-265">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="86ae5-266">Umieszczenie warstwą Nginx ruch przychodzący w Kuberentes przed aplikacji sieci web, a także kilka bramy interfejsu API Ocelot / BFF jest idealnym rozwiązaniem architektury, jak pokazano na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="86ae5-266">Having an ingress Nginx tier in Kuberentes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

 ![](./media/image41.png)

<span data-ttu-id="86ae5-267">**Rysunek 8-40.**</span><span class="sxs-lookup"><span data-stu-id="86ae5-267">**Figure 8-40.**</span></span> <span data-ttu-id="86ae5-268">Warstwa danych przychodzących w ramach aplikacji eShopOnContainers podczas wdrażania do rozwiązania Kubernetes</span><span class="sxs-lookup"><span data-stu-id="86ae5-268">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="86ae5-269">Gdy wdrażasz ramach aplikacji eShopOnContainers do Kuberentes udostępnia kilka usług lub punktów końcowych za pośrednictwem _ruch przychodzący_, po prostu poniżej postfixes na adresy URL:</span><span class="sxs-lookup"><span data-stu-id="86ae5-269">When you deploy eShopOnContainers into Kuberentes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

-   <span data-ttu-id="86ae5-270">`/` SPA klienta aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="86ae5-270">`/` for the client SPA web application</span></span>
-   <span data-ttu-id="86ae5-271">`/webmvc` dla klienta aplikacji sieci web MVC</span><span class="sxs-lookup"><span data-stu-id="86ae5-271">`/webmvc` for the client MVC web application</span></span>
-   <span data-ttu-id="86ae5-272">`/webstatus` Wyświetlanie stanu/healthchecks aplikacji sieci web klienta</span><span class="sxs-lookup"><span data-stu-id="86ae5-272">`/webstatus` for the client web app showing the status/healthchecks</span></span>
-   <span data-ttu-id="86ae5-273">`/webshoppingapigw` dla sieci web BFF i zakupów procesów biznesowych</span><span class="sxs-lookup"><span data-stu-id="86ae5-273">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
-   <span data-ttu-id="86ae5-274">`/webmarketingapigw` dla sieci web BFF i marketingu procesów biznesowych</span><span class="sxs-lookup"><span data-stu-id="86ae5-274">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
-   <span data-ttu-id="86ae5-275">`/mobileshoppingapigw` dla mobilnych BFF i zakupów procesów biznesowych</span><span class="sxs-lookup"><span data-stu-id="86ae5-275">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
-   <span data-ttu-id="86ae5-276">`/mobilemarketingapigw` przenośne BFF i marketingowych procesów biznesowych</span><span class="sxs-lookup"><span data-stu-id="86ae5-276">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="86ae5-277">Podczas wdrażania usługi Kubernetes, każdej bramy interfejsu API Ocelot jest używany plik różnych "configuration.json" dla każdego _zasobnika_ uruchamianie bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="86ae5-277">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="86ae5-278">Te pliki "configuration.json" są dostarczane przez zainstalowanie (pierwotnie ze skryptem deploy.ps1) woluminu, który został utworzony w oparciu o Kuberentes _mapy config_ o nazwie "ocelot".</span><span class="sxs-lookup"><span data-stu-id="86ae5-278">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kuberentes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="86ae5-279">Każdy kontener instaluje jego pliku konfiguracji powiązane w folderze kontenera o nazwie `/app/configuration`.</span><span class="sxs-lookup"><span data-stu-id="86ae5-279">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="86ae5-280">W ramach aplikacji eShopOnContainers plików kodu źródłowego oryginalnych plików "configuration.json" znajdują się w obrębie `k8s/ocelot/` folderu.</span><span class="sxs-lookup"><span data-stu-id="86ae5-280">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="86ae5-281">Istnieje jeden plik dla każdego BFF/APIGateway.</span><span class="sxs-lookup"><span data-stu-id="86ae5-281">There’s one file for each BFF/APIGateway.</span></span>


## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="86ae5-282">Dodatkowe funkcje przekrojowe bramy interfejsu API Ocelot</span><span class="sxs-lookup"><span data-stu-id="86ae5-282">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="86ae5-283">Istnieją inne ważne funkcje zbadaniu i użyć w przypadku użycia Ocelot bramy interfejsu API, opisane w poniższych łączy.</span><span class="sxs-lookup"><span data-stu-id="86ae5-283">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

-   <span data-ttu-id="86ae5-284">**Odnajdowanie usługi integracji Ocelot z Konsul lub Eureka po stronie klienta** 
    [*http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)</span><span class="sxs-lookup"><span data-stu-id="86ae5-284">**Service discovery in the client side integrating Ocelot with Consul or Eureka** 
[*http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html*](http://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)</span></span>

-   <span data-ttu-id="86ae5-285">**Pamięć podręczna w warstwie bramy interfejsu API** 
    [*http://ocelot.readthedocs.io/en/latest/features/caching.html*](http://ocelot.readthedocs.io/en/latest/features/caching.html)</span><span class="sxs-lookup"><span data-stu-id="86ae5-285">**Caching at the API Gateway tier** 
[*http://ocelot.readthedocs.io/en/latest/features/caching.html*](http://ocelot.readthedocs.io/en/latest/features/caching.html)</span></span>

-   <span data-ttu-id="86ae5-286">**Rejestrowanie na poziomie warstwy bramy interfejsu API** 
    [*http://ocelot.readthedocs.io/en/latest/features/logging.html*](http://ocelot.readthedocs.io/en/latest/features/logging.html)</span><span class="sxs-lookup"><span data-stu-id="86ae5-286">**Logging at the API Gateway tier** 
[*http://ocelot.readthedocs.io/en/latest/features/logging.html*](http://ocelot.readthedocs.io/en/latest/features/logging.html)</span></span>

-   <span data-ttu-id="86ae5-287">**Jakość usług (ponownych prób i wyłączniki) w warstwie bramy interfejsu API** 
    [*http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)</span><span class="sxs-lookup"><span data-stu-id="86ae5-287">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** 
[*http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html*](http://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)</span></span>

-   <span data-ttu-id="86ae5-288">**Ograniczanie szybkości** 
    [*http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )</span><span class="sxs-lookup"><span data-stu-id="86ae5-288">**Rate limiting** 
[*http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html*](http://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="86ae5-289">[Poprzedniego](background-tasks-with-ihostedservice.md) [dalej] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="86ae5-289">[Previous] (background-tasks-with-ihostedservice.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
