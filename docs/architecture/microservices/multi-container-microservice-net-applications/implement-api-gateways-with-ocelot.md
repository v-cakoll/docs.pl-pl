---
title: Wdrażanie bram interfejsu API za pomocą rozwiązania Ocelot
description: Dowiedz się, jak implementować bramy interfejsu API za pomocą ocelota i jak używać Ocelota w środowisku opartym na kontenerach.
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846949"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="056e8-103">Implementowanie bram interfejsu API za pomocą ocelota</span><span class="sxs-lookup"><span data-stu-id="056e8-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="056e8-104">Aplikacja mikrousług referencyjnych [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) używa obecnie funkcji dostarczonych przez [wysłannika](https://www.envoyproxy.io/) do zaimplementowania bramy interfejsu API zamiast wcześniejszego odwołania [Ocelot](https://github.com/ThreeMammals/Ocelot).</span><span class="sxs-lookup"><span data-stu-id="056e8-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="056e8-105">Dokonaliśmy tego wyboru projektu ze względu na wbudowaną obsługę protokołu WebSocket firmy Envoy, wymaganą przez nową komunikację międzyserwisową gRPC zaimplementowane w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="056e8-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="056e8-106">Jednak zachowaliśmy tę sekcję w przewodniku, dzięki czemu można rozważyć Ocelot jako prostą, zdolną i lekką bramę interfejsu API odpowiednią dla scenariuszy klasy produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="056e8-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="056e8-107">Projektowanie i projektowanie bram interfejsu API</span><span class="sxs-lookup"><span data-stu-id="056e8-107">Architect and design your API Gateways</span></span>

<span data-ttu-id="056e8-108">Na poniższym diagramie architektury pokazano, jak bramy interfejsu API zostały zaimplementowane za pomocą Ocelot w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="056e8-108">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![Diagram przedstawiający architekturę eShopOnContainers.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="056e8-110">**Rysunek 6-28**.</span><span class="sxs-lookup"><span data-stu-id="056e8-110">**Figure 6-28**.</span></span> <span data-ttu-id="056e8-111">Architektura eShopOnContainers z bramami interfejsu API</span><span class="sxs-lookup"><span data-stu-id="056e8-111">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="056e8-112">Ten diagram pokazuje, jak cała aplikacja jest wdrażana w jednym hoście platformy Docker lub komputerze deweloperscym z "Docker for Windows" lub "Docker for Mac".</span><span class="sxs-lookup"><span data-stu-id="056e8-112">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="056e8-113">Jednak wdrażanie w dowolnym koordynatorem będzie podobny, ale każdy kontener na diagramie może być skalowany w sposób skalowany w koordynatorze.</span><span class="sxs-lookup"><span data-stu-id="056e8-113">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="056e8-114">Ponadto zasoby infrastruktury, takie jak bazy danych, pamięć podręczna i brokerzy komunikatów, powinny zostać odciążone od koordynatora i wdrożone w wysoko dostępnych systemach infrastruktury, takich jak baza danych SQL Azure, usługa Azure Cosmos DB, usługa Azure Redis, usługa Azure Service Bus, lub dowolnego rozwiązania klastrowania ha w środowisku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="056e8-114">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="056e8-115">Jak można również zauważyć na diagramie, mając kilka bram interfejsu API umożliwia wiele zespołów programistycznych być autonomiczne (w tym przypadku funkcje marketingu vs. funkcje zakupów) podczas opracowywania i wdrażania ich mikrousług oraz własnych powiązanych bram interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-115">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="056e8-116">Jeśli masz jedną monolityczną bramę interfejsu API, co oznaczałoby jeden punkt do aktualizacji przez kilka zespołów programistycznych, które mogą łączyć wszystkie mikrousługi z jednej części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="056e8-116">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="056e8-117">Idąc znacznie dalej w projekcie, czasami szczegółowe bramy interfejsu API może być również ograniczona do mikrousługi pojedynczej firmy w zależności od wybranej architektury.</span><span class="sxs-lookup"><span data-stu-id="056e8-117">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="056e8-118">Posiadanie granic bramy interfejsu API podyktowanych przez firmę lub domenę pomoże Ci uzyskać lepszy projekt.</span><span class="sxs-lookup"><span data-stu-id="056e8-118">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="056e8-119">Na przykład szczegółowość w warstwie bramy interfejsu API może być szczególnie przydatne w przypadku bardziej zaawansowanych złożonych aplikacji interfejsu i zestawienia, które są oparte na mikrousługach, ponieważ pojęcie szczegółowej bramy interfejsu API jest podobny do usługi kompozycji interfejsu interfejsu i informacji.</span><span class="sxs-lookup"><span data-stu-id="056e8-119">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="056e8-120">Zagłębiamy się w więcej szczegółów w poprzedniej sekcji [Tworzenie złożonego interfejsu opartego na mikrousługach](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span><span class="sxs-lookup"><span data-stu-id="056e8-120">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="056e8-121">Jako klucz na wynos, dla wielu średnich i dużych aplikacji, przy użyciu niestandardowego produktu Bramy interfejsu API jest zwykle dobrym podejściem, ale nie jako jeden monolityczny agregator lub unikatowa centralna niestandardowa brama interfejsu API, chyba że brama interfejsu API umożliwia wiele niezależnych obszary konfiguracji dla kilku zespołów programistycznych tworzących autonomiczne mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="056e8-121">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="056e8-122">Przykładowe mikrousługi/kontenery do przekierowania za pośrednictwem bram interfejsu API</span><span class="sxs-lookup"><span data-stu-id="056e8-122">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="056e8-123">Na przykład eShopOnContainers ma około sześciu wewnętrznych typów mikrousług, które muszą zostać opublikowane za pośrednictwem bram interfejsu API, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="056e8-123">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Zrzut ekranu przedstawiający folder Usługi z jego podfolderami.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="056e8-125">**Rysunek 6-29**.</span><span class="sxs-lookup"><span data-stu-id="056e8-125">**Figure 6-29**.</span></span> <span data-ttu-id="056e8-126">Foldery mikrousług w rozwiązaniu eShopOnContainers w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="056e8-126">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="056e8-127">Jeśli chodzi o usługę Identity, w projekcie jest ona pozostawiona z routingu bramy interfejsu API, ponieważ jest to jedyny problem przekrojowy w systemie, chociaż w ocelot jest również możliwe dołączenie go jako część list przekierowowania.</span><span class="sxs-lookup"><span data-stu-id="056e8-127">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="056e8-128">Wszystkie te usługi są obecnie implementowane jako ASP.NET podstawowych usług interfejsu API sieci Web, jak można powiedzieć z kodu.</span><span class="sxs-lookup"><span data-stu-id="056e8-128">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="056e8-129">Skupmy się na jednej z mikrousług, takich jak kod mikrousługi katalogu.</span><span class="sxs-lookup"><span data-stu-id="056e8-129">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![Zrzut ekranu przedstawiający Eksploratora rozwiązań z zawartością projektu Catalog.API.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="056e8-131">**Rysunek 6-30**.</span><span class="sxs-lookup"><span data-stu-id="056e8-131">**Figure 6-30**.</span></span> <span data-ttu-id="056e8-132">Przykładowa mikrousługa interfejsu API sieci Web (mikrousługa katalogu)</span><span class="sxs-lookup"><span data-stu-id="056e8-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="056e8-133">Widać, że mikrousługi katalogu jest typowym ASP.NET core web api projektu z kilku kontrolerów i metod, takich jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="056e8-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="056e8-134">Żądanie HTTP zakończy się uruchomienietego tego rodzaju kodu C# dostępu do bazy danych mikrousług i wszelkie dodatkowe wymagane działania.</span><span class="sxs-lookup"><span data-stu-id="056e8-134">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="056e8-135">Jeśli chodzi o adres URL mikrousługi, gdy kontenery są wdrażane na komputerze deweloperskim lokalnego (lokalny host platformy Docker), każdy kontener mikrousługi ma zawsze port wewnętrzny (zwykle port 80) określony w pliku dockerfile, jak w następującym pliku dockerfile:</span><span class="sxs-lookup"><span data-stu-id="056e8-135">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="056e8-136">Port 80 wyświetlany w kodzie jest wewnętrzny w hoście platformy Docker, więc nie można do niego dotrzeć przez aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="056e8-136">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="056e8-137">Aplikacje klienckie mogą uzyskiwać dostęp tylko do `docker-compose`portów zewnętrznych (jeśli istnieją) opublikowanych podczas wdrażania z .</span><span class="sxs-lookup"><span data-stu-id="056e8-137">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="056e8-138">Te porty zewnętrzne nie powinny być publikowane podczas wdrażania w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="056e8-138">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="056e8-139">Właśnie dlatego chcesz użyć bramy interfejsu API, aby uniknąć bezpośredniej komunikacji między aplikacjami klienckimi a mikrousługami.</span><span class="sxs-lookup"><span data-stu-id="056e8-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="056e8-140">Jednak podczas opracowywania chcesz uzyskać dostęp do mikrousługi/kontenera bezpośrednio i uruchomić go za pośrednictwem Swagger.</span><span class="sxs-lookup"><span data-stu-id="056e8-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="056e8-141">Dlatego w eShopOnContainers porty zewnętrzne są nadal określone, nawet jeśli nie będą używane przez bramę interfejsu API lub aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="056e8-141">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="056e8-142">Oto przykład `docker-compose.override.yml` pliku mikrousługi katalogu:</span><span class="sxs-lookup"><span data-stu-id="056e8-142">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="056e8-143">W konfiguracji pliku docker-compose.yml można zobaczyć, jak w konfiguracji docker-compose.override.yml port wewnętrzny kontenera wykazu to port 80, ale port dostępu zewnętrznego to 5101.</span><span class="sxs-lookup"><span data-stu-id="056e8-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="056e8-144">Ale ten port nie powinien być używany przez aplikację podczas korzystania z bramy interfejsu API, tylko do debugowania, uruchamiania i testowania tylko mikrousługi katalogu.</span><span class="sxs-lookup"><span data-stu-id="056e8-144">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="056e8-145">Zwykle nie będzie wdrażać z docker-compose w środowisku produkcyjnym, ponieważ odpowiednie środowisko wdrażania produkcyjnego dla mikrousług jest koordynatorem, takich jak Kubernetes lub sieci szkieletowej usług.</span><span class="sxs-lookup"><span data-stu-id="056e8-145">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="056e8-146">Podczas wdrażania w tych środowiskach używasz różnych plików konfiguracyjnych, gdzie nie będzie publikować bezpośrednio żadnego portu zewnętrznego dla mikrousług, ale zawsze będziesz używać zwrotnego serwera proxy z bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-146">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="056e8-147">Uruchom mikrousługę katalogu w lokalnym hoście platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="056e8-147">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="056e8-148">Uruchom pełne rozwiązanie eShopOnContainers z programu Visual Studio (uruchamia wszystkie usługi w plikach docker-compose) lub uruchom mikrousługę catalogu za pomocą następującego `docker-compose.yml` polecenia `docker-compose.override.yml` docker-compose w cmd lub powershell umieszczonyw folderze, w którym są umieszczone i są umieszczone.</span><span class="sxs-lookup"><span data-stu-id="056e8-148">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="056e8-149">To polecenie uruchamia tylko kontener usługi catalog-api plus zależności, które są określone w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="056e8-149">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="056e8-150">W takim przypadku kontener programu SQL Server i kontener RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="056e8-150">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="056e8-151">Następnie można bezpośrednio uzyskać dostęp do mikrousługi katalogu i zobaczyć jego metody za pośrednictwem interfejsu użytkownika Swagger dostęp bezpośrednio za pośrednictwem tego portu "zewnętrzne", w tym przypadku: `http://localhost:5101/swagger`</span><span class="sxs-lookup"><span data-stu-id="056e8-151">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Zrzut ekranu przedstawiający interfejs firmy Swagger przedstawiający interfejs API REST catalog.api.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="056e8-153">**Rysunek 6-31**.</span><span class="sxs-lookup"><span data-stu-id="056e8-153">**Figure 6-31**.</span></span> <span data-ttu-id="056e8-154">Testowanie mikrousługi katalogu za pomocą interfejsu interfejsu swagger</span><span class="sxs-lookup"><span data-stu-id="056e8-154">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="056e8-155">W tym momencie można ustawić punkt przerwania w kodzie Języka C# w programie Visual Studio, przetestować mikrousługi z `docker-compose down` metodami uwidocznionym w swagger interfejsu i wreszcie oczyścić wszystko za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="056e8-155">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="056e8-156">Jednak bezpośredni dostęp do mikrousługi, w tym przypadku za pośrednictwem portu zewnętrznego 5101, jest dokładnie to, czego chcesz uniknąć w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="056e8-156">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="056e8-157">I można tego uniknąć, ustawiając dodatkowy poziom pośredni bramy interfejsu API (Ocelot, w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="056e8-157">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="056e8-158">W ten sposób aplikacja klienckinie nie będzie bezpośrednio uzyskać dostępu do mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="056e8-158">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="056e8-159">Implementowanie bram interfejsu API za pomocą ocelota</span><span class="sxs-lookup"><span data-stu-id="056e8-159">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="056e8-160">Ocelot to w zasadzie zestaw pośrednień, które można zastosować w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="056e8-160">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="056e8-161">Ocelot jest przeznaczony do pracy tylko z ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="056e8-161">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="056e8-162">Najnowsza wersja pakietu `.NETCoreApp 3.1` dotyczy, a tym samym nie jest odpowiedni dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="056e8-162">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="056e8-163">Instalujesz Ocelot i jego zależności w projekcie ASP.NET Core z [pakietem NuGet Ocelota](https://www.nuget.org/packages/Ocelot/)z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="056e8-163">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="056e8-164">W eShopOnContainers jego implementacja bramy interfejsu API jest prostym ASP.NET core webhost projektu i pośredniczenie Ocelot obsługuje wszystkie funkcje bramy interfejsu API, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="056e8-164">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![Zrzut ekranu przedstawiający Eksploratora rozwiązań z projektem bramy interfejsu API Ocelot.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="056e8-166">**Rysunek 6-32**.</span><span class="sxs-lookup"><span data-stu-id="056e8-166">**Figure 6-32**.</span></span> <span data-ttu-id="056e8-167">Projekt podstawowy OcelotApiGw w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="056e8-167">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="056e8-168">Ten ASP.NET Core WebHost projekt jest w `Program.cs` zasadzie `Startup.cs`zbudowany z dwóch prostych plików: i .</span><span class="sxs-lookup"><span data-stu-id="056e8-168">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="056e8-169">Program.cs po prostu musi utworzyć i skonfigurować typowy ASP.NET Core BuildWebHost.</span><span class="sxs-lookup"><span data-stu-id="056e8-169">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="056e8-170">Ważnym punktem tutaj dla Ocelot jest `configuration.json` plik, który należy `AddJsonFile()` podać do konstruktora za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="056e8-170">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="056e8-171">W `configuration.json` tym miejscu można określić wszystkie retrasy bramy interfejsu API, co oznacza zewnętrzne punkty końcowe z określonymi portami i skorelowanymi wewnętrznymi punktami końcowymi, zwykle przy użyciu różnych portów.</span><span class="sxs-lookup"><span data-stu-id="056e8-171">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="056e8-172">Istnieją dwie sekcje do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="056e8-172">There are two sections to the configuration.</span></span> <span data-ttu-id="056e8-173">Tablica reroutes i GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="056e8-173">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="056e8-174">ReRoutes są obiekty, które mówią Ocelot jak traktować żądanie nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="056e8-174">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="056e8-175">Konfiguracja globalna umożliwia zastępowanie określonych ustawień reroute.</span><span class="sxs-lookup"><span data-stu-id="056e8-175">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="056e8-176">Jest to przydatne, jeśli nie chcesz zarządzać wieloma ustawieniami określonymi w reroute.</span><span class="sxs-lookup"><span data-stu-id="056e8-176">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="056e8-177">Oto uproszczony przykład [pliku konfiguracyjnego ReRoute](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jednej z bram interfejsu API z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="056e8-177">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
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
          "Host": "basket-api",
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

<span data-ttu-id="056e8-178">Główną funkcjonalnością bramy interfejsu API Ocelot jest podjęcie przychodzących żądań HTTP i przekazywanie ich do usługi podrzędnej, obecnie jako inne żądanie HTTP.</span><span class="sxs-lookup"><span data-stu-id="056e8-178">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="056e8-179">Ocelot opisuje routing jednego żądania do drugiego jako ReRoute.</span><span class="sxs-lookup"><span data-stu-id="056e8-179">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="056e8-180">Na przykład skupmy się na jednym z ReRoutes w configuration.json z góry, konfiguracji mikrousługi koszyka.</span><span class="sxs-lookup"><span data-stu-id="056e8-180">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

<span data-ttu-id="056e8-181">DownstreamPathTemplate, Scheme i DownstreamHostAndPorts tworzą wewnętrzny adres URL mikrousługi, do których zostanie przekazane to żądanie.</span><span class="sxs-lookup"><span data-stu-id="056e8-181">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="056e8-182">Port jest portem wewnętrznym używanym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="056e8-182">The port is the internal port used by the service.</span></span> <span data-ttu-id="056e8-183">Podczas korzystania z kontenerów, port określony w jego dockerfile.</span><span class="sxs-lookup"><span data-stu-id="056e8-183">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="056e8-184">Jest `Host` to nazwa usługi, która zależy od rozpoznawania nazw usługi, których używasz.</span><span class="sxs-lookup"><span data-stu-id="056e8-184">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="056e8-185">Podczas korzystania z docker-compose, nazwy usług są dostarczane przez Host platformy Docker, który używa nazw usług podanych w plikach docker-compose.</span><span class="sxs-lookup"><span data-stu-id="056e8-185">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="056e8-186">Jeśli używasz koordynatora, takiego jak Kubernetes lub Sieć szkieletowa usług, ta nazwa powinna być rozpoznawana przez dns lub rozpoznawanie nazw dostarczone przez każdego koordynatora.</span><span class="sxs-lookup"><span data-stu-id="056e8-186">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="056e8-187">DownstreamHostAndPorts to tablica, która zawiera hosta i port wszelkich usług podrzędnych, do których chcesz przesyłać dalej żądania.</span><span class="sxs-lookup"><span data-stu-id="056e8-187">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="056e8-188">Zazwyczaj będzie to tylko zawierać jeden wpis, ale czasami można załadować żądania równoważenia do usług niższego rzędu i Ocelot pozwala dodać więcej niż jeden wpis, a następnie wybrać moduł równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="056e8-188">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="056e8-189">Ale jeśli za pomocą platformy Azure i dowolnego koordynatora jest prawdopodobnie lepszym pomysłem, aby zrównoważyć obciążenia z chmury i infrastruktury koordynatora.</span><span class="sxs-lookup"><span data-stu-id="056e8-189">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="056e8-190">UpstreamPathTemplate jest adres URL, który Ocelot będzie używany do identyfikowania, które DownstreamPathTemplate do użycia dla danego żądania od klienta.</span><span class="sxs-lookup"><span data-stu-id="056e8-190">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="056e8-191">Na koniec UpstreamHttpMetoda jest używana, więc Ocelot można odróżnić różne żądania (GET, POST, PUT) do tego samego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="056e8-191">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="056e8-192">W tym momencie możesz mieć jedną bramę interfejsu API Ocelot (ASP.NET Core WebHost) przy użyciu jednego lub [wielu scalonych plików configuration.json](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) lub możesz również przechowywać [konfigurację w sklepie KV konsula](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="056e8-192">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="056e8-193">Ale jak wprowadzono w architekturze i sekcji projektowania, jeśli naprawdę chcesz mieć autonomiczne mikrousług, może być lepiej podzielić tej pojedynczej bramy interfejsu API monolityczne do wielu bram interfejsu API i/lub BFF (backend dla frontonu).</span><span class="sxs-lookup"><span data-stu-id="056e8-193">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="056e8-194">W tym celu zobaczmy, jak zaimplementować to podejście za pomocą kontenerów platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="056e8-194">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="056e8-195">Używanie pojedynczego obrazu kontenera platformy Docker do uruchamiania wielu różnych typów kontenerów bramy interfejsu API / BFF</span><span class="sxs-lookup"><span data-stu-id="056e8-195">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="056e8-196">W eShopOnContainers używamy pojedynczego obrazu kontenera platformy Docker z bramą interfejsu API Ocelot, ale następnie w czasie wykonywania tworzymy różne usługi/kontenery dla każdego typu bramy interfejsu API/BFF, udostępniając inny plik configuration.json, używając woluminu docker, aby uzyskać dostęp do innego folderu komputera dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="056e8-196">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Diagram pojedynczego obrazu platformy Docker bramy Ocelot dla wszystkich bram interfejsu API.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="056e8-198">**Rysunek 6-33**.</span><span class="sxs-lookup"><span data-stu-id="056e8-198">**Figure 6-33**.</span></span> <span data-ttu-id="056e8-199">Ponowne użycie pojedynczego obrazu platformy Docker ocelot dla wielu typów bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="056e8-199">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="056e8-200">W eShopOnContainers "Generic Ocelot API Gateway Docker Image" jest tworzony z projektem o nazwie "OcelotApiGw" i nazwą obrazu "eshop/ocelotapigw", która jest określona w pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="056e8-200">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="056e8-201">Następnie podczas wdrażania do platformy Docker, będą cztery kontenery bramy interfejsu API utworzone z tego samego obrazu platformy Docker, jak pokazano w poniższym wyjściu z pliku docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="056e8-201">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
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

<span data-ttu-id="056e8-202">Ponadto, jak widać w następującym pliku docker-compose.override.yml, jedyną różnicą między tymi kontenerami bramy interfejsu API jest plik konfiguracyjny Ocelot, który jest inny dla każdego kontenera usługi i jest określony w czasie wykonywania za pośrednictwem Wolumin platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="056e8-202">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="056e8-203">Ze względu na ten poprzedni kod i jak pokazano w Eksploratorze Visual Studio poniżej, jedynym plikiem potrzebnym do zdefiniowania każdej określonej bramy interfejsu API biznesowej/BFF jest tylko plik configuration.json, ponieważ cztery bramy interfejsu API są oparte na tym samym obrazie platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="056e8-203">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Zrzut ekranu przedstawiający wszystkie bramy interfejsu API z plikami configuration.json.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="056e8-205">**Rysunek 6-34**.</span><span class="sxs-lookup"><span data-stu-id="056e8-205">**Figure 6-34**.</span></span> <span data-ttu-id="056e8-206">Jedynym plikiem potrzebnym do zdefiniowania każdej bramy API / BFF za pomocą Ocelota jest plik konfiguracyjny</span><span class="sxs-lookup"><span data-stu-id="056e8-206">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="056e8-207">Dzieląc bramę interfejsu API na wiele bram interfejsu API, różne zespoły programistyczne koncentrujące się na różnych podzbiorach mikrousług mogą zarządzać własnymi bramami interfejsu API przy użyciu niezależnych plików konfiguracyjnych Ocelot.</span><span class="sxs-lookup"><span data-stu-id="056e8-207">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="056e8-208">Ponadto w tym samym czasie mogą ponownie użyć tego samego obrazu docker Ocelot.</span><span class="sxs-lookup"><span data-stu-id="056e8-208">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="056e8-209">Teraz, jeśli uruchomisz eShopOnContainers z bramami interfejsu API (zawarte domyślnie w VS podczas otwierania eShopOnContainers-ServicesAndWebApps.sln rozwiązanie lub jeśli używasz "docker-compose up"), następujące przykładowe trasy zostaną wykonane.</span><span class="sxs-lookup"><span data-stu-id="056e8-209">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="056e8-210">Na przykład podczas odwiedzania `http://localhost:5202/api/v1/c/catalog/items/2/` nadrzędnego adresu URL obsługiwanego przez webshoppingapigw API Gateway, `http://catalog-api/api/v1/2` otrzymasz ten sam wynik z wewnętrznego adresu URL downstream w hoście platformy Docker, jak w następującej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="056e8-210">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Zrzut ekranu przedstawiający przeglądarkę pokazującą odpowiedź przechodzącą przez bramę interfejsu API.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="056e8-212">**Rysunek 6-35**.</span><span class="sxs-lookup"><span data-stu-id="056e8-212">**Figure 6-35**.</span></span> <span data-ttu-id="056e8-213">Uzyskiwanie dostępu do mikrousługi za pośrednictwem adresu URL dostarczonego przez bramę interfejsu API</span><span class="sxs-lookup"><span data-stu-id="056e8-213">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="056e8-214">Ze względu na testowanie lub debugowanie jeśli chcesz uzyskać bezpośredni dostęp do kontenera docker wykazu (tylko w środowisku programistycznym) bez przechodzenia przez bramę interfejsu API, ponieważ "catalog-api" jest rozpoznawaniem DNS wewnętrznym hostem platformy Docker (odnajdywanie usług obsługiwane przez nazwy usług docker-compose), jedynym sposobem bezpośredniego dostępu do kontenera jest port zewnętrzny opublikowany w pliku docker-compose.override.yml, który jest dostępny tylko dla testów programistycznych, takich jak `http://localhost:5101/api/v1/Catalog/items/1` w następującej przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="056e8-214">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Zrzut ekranu przedstawiający przeglądarkę z bezpośrednią odpowiedzią na interfejs Catalog.api.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="056e8-216">**Rysunek 6-36**.</span><span class="sxs-lookup"><span data-stu-id="056e8-216">**Figure 6-36**.</span></span> <span data-ttu-id="056e8-217">Bezpośredni dostęp do mikrousługi do celów testowych</span><span class="sxs-lookup"><span data-stu-id="056e8-217">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="056e8-218">Ale aplikacja jest skonfigurowana tak, aby uzyskać dostęp do wszystkich mikrousług za pośrednictwem bram interfejsu API, a nie przez port bezpośredni "skróty".</span><span class="sxs-lookup"><span data-stu-id="056e8-218">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="056e8-219">Wzorzec agregacji bramy w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="056e8-219">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="056e8-220">Jak wprowadzono wcześniej elastyczny sposób implementowania agregacji żądań jest z usług niestandardowych, według kodu.</span><span class="sxs-lookup"><span data-stu-id="056e8-220">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="056e8-221">Można również zaimplementować agregację żądań za pomocą [funkcji Agregacji żądań w Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale może nie być tak elastyczna, jak potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="056e8-221">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="056e8-222">W związku z tym wybrany sposób implementacji agregacji w eShopOnContainers jest z jawną ASP.NET podstawową usługą interfejsu API sieci Web dla każdego agregatora.</span><span class="sxs-lookup"><span data-stu-id="056e8-222">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="056e8-223">Zgodnie z tym podejściem diagram kompozycji bramy interfejsu API jest w rzeczywistości nieco bardziej rozszerzony, gdy rozważa się usługi agregatora, które nie są wyświetlane na diagramie uproszczonej architektury globalnej pokazanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="056e8-223">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="056e8-224">Na poniższym diagramie można również zobaczyć, jak usługi agregatora działają z powiązanymi bramami interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-224">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Diagram architektury eShopOnContainers przedstawiający usługi agregatora.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="056e8-226">**Rysunek 6-37**.</span><span class="sxs-lookup"><span data-stu-id="056e8-226">**Figure 6-37**.</span></span> <span data-ttu-id="056e8-227">Architektura eShopOnContainers z usługami agregatora</span><span class="sxs-lookup"><span data-stu-id="056e8-227">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="056e8-228">Powiększanie dalej w obszarze działalności "Zakupy" na poniższej ilustracji, można zobaczyć, że chattiness między aplikacjami klienckimi i mikrousług jest zmniejszona podczas korzystania z usług agregatora w bramach interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-228">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![Diagram przedstawiający architekturę eShopOnContainers powiększanie.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="056e8-230">**Rysunek 6-38**.</span><span class="sxs-lookup"><span data-stu-id="056e8-230">**Figure 6-38**.</span></span> <span data-ttu-id="056e8-231">Powiększanie wizji usług agregatora</span><span class="sxs-lookup"><span data-stu-id="056e8-231">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="056e8-232">Można zauważyć, jak, gdy diagram pokazuje możliwe żądania pochodzące z bram interfejsu API może uzyskać złożone.</span><span class="sxs-lookup"><span data-stu-id="056e8-232">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="056e8-233">Chociaż można zobaczyć, jak strzałki na niebiesko zostaną uproszczone, z punktu widzenia aplikacji klienckich, podczas korzystania z wzorca agregatora poprzez zmniejszenie chattiness i opóźnienia w komunikacji, ostatecznie znacznie poprawiając środowisko użytkownika dla aplikacji zdalnych ( aplikacje mobilne i SPA), zwłaszcza.</span><span class="sxs-lookup"><span data-stu-id="056e8-233">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="056e8-234">W przypadku "Marketing" obszar działalności i mikrousług jest to prosty przypadek użycia, więc nie było potrzeby używania agregatorów, ale może być również możliwe, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="056e8-234">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="056e8-235">Uwierzytelnianie i autoryzacja w bramkach interfejsu API Ocelot</span><span class="sxs-lookup"><span data-stu-id="056e8-235">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="056e8-236">W bramie interfejsu API Ocelot można siedzieć usługi uwierzytelniania, takich jak ASP.NET core usługi interfejsu API sieci Web przy użyciu [IdentityServer](https://identityserver.io/) dostarczanie tokenu uwierzytelniania, na zewnątrz lub wewnątrz bramy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-236">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="056e8-237">Ponieważ eShopOnContainers używa wielu bram interfejsu API z granicami opartymi na BFF i obszarach biznesowych, usługa Identity/Auth jest pomijana w bramkach interfejsu API, jak podkreślono na żółto na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="056e8-237">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![Diagram przedstawiający mikrousługi tożsamości pod bramą interfejsu API.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="056e8-239">**Rysunek 6-39**.</span><span class="sxs-lookup"><span data-stu-id="056e8-239">**Figure 6-39**.</span></span> <span data-ttu-id="056e8-240">Stanowisko usługi Tożsamości w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="056e8-240">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="056e8-241">Jednak Ocelot obsługuje również siedzi identity/Auth mikrousługi w granicach bramy interfejsu API, jak w tym innym diagramie.</span><span class="sxs-lookup"><span data-stu-id="056e8-241">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Diagram przedstawiający uwierzytelnianie w bramie interfejsu API Ocelot.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="056e8-243">**Rysunek 6-40**.</span><span class="sxs-lookup"><span data-stu-id="056e8-243">**Figure 6-40**.</span></span> <span data-ttu-id="056e8-244">Uwierzytelnianie w Ocelot</span><span class="sxs-lookup"><span data-stu-id="056e8-244">Authentication in Ocelot</span></span>

<span data-ttu-id="056e8-245">Jak pokazano na poprzednim diagramie, gdy mikrousługi tożsamości znajduje się pod bramą interfejsu API (AG): 1) AG żąda tokenu auth z mikrousługi tożsamości, 2) Mikrousługi tożsamości zwraca token ag, 3-4) żądania AG z mikrousług przy użyciu tokenu auth.</span><span class="sxs-lookup"><span data-stu-id="056e8-245">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="056e8-246">Ponieważ aplikacja eShopOnContainers podzieliła bramę interfejsu API na wiele bff (backend for Frontend) i bramy interfejsu API obszarów biznesowych, inną opcją byłoby utworzenie dodatkowej bramy interfejsu API dla problemów przekrojowych.</span><span class="sxs-lookup"><span data-stu-id="056e8-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="056e8-247">Ten wybór będzie sprawiedliwy w bardziej złożonej architekturze opartej na mikrousługach z wieloma przecięciami dotyczy mikrousług.</span><span class="sxs-lookup"><span data-stu-id="056e8-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="056e8-248">Ponieważ istnieje tylko jeden problem przekrojowy w eShopOnContainers, zdecydowano się po prostu obsługiwać usługę zabezpieczeń z królestwa bramy interfejsu API, dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="056e8-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="056e8-249">W każdym przypadku, jeśli aplikacja jest zabezpieczona na poziomie bramy interfejsu API, moduł uwierzytelniania bramy interfejsu API Ocelot jest odwiedzany na początku podczas próby użycia dowolnej zabezpieczonej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="056e8-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="056e8-250">To przekierowuje żądanie HTTP do odwiedzenia tożsamości lub mikrousługi auth, aby uzyskać token dostępu, dzięki czemu można odwiedzić chronione usługi z access_token.</span><span class="sxs-lookup"><span data-stu-id="056e8-250">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="056e8-251">Sposób, w jaki można zabezpieczyć za pomocą uwierzytelniania dowolnej usługi na poziomie bramy interfejsu API jest ustawienie AuthenticationProviderKey w powiązanych ustawień w configuration.json.</span><span class="sxs-lookup"><span data-stu-id="056e8-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

<span data-ttu-id="056e8-252">Po uruchomieniu ocelot, będzie patrzeć na ReRoutes AuthenticationOptions.AuthenticationProviderKey i sprawdzić, czy istnieje dostawca uwierzytelniania zarejestrowany przy dany klucz.</span><span class="sxs-lookup"><span data-stu-id="056e8-252">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="056e8-253">Jeśli nie, to Ocelot nie uruchomi się.</span><span class="sxs-lookup"><span data-stu-id="056e8-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="056e8-254">Jeśli istnieje, a następnie ReRoute użyje tego dostawcy podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="056e8-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="056e8-255">Ponieważ Ocelot WebHost jest skonfigurowany z `authenticationProviderKey = "IdentityApiKey"`, który będzie wymagał uwierzytelniania, gdy ta usługa ma żadnych żądań bez tokenu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="056e8-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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
        }
    }
}
```

<span data-ttu-id="056e8-256">Następnie należy również ustawić autoryzację z [Authorize] atrybut dla dowolnego zasobu, który ma być dostępny, takich jak mikrousług, takich jak w następującym kontrolerze mikrousługi koszyka.</span><span class="sxs-lookup"><span data-stu-id="056e8-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="056e8-257">ValidAudiences takich jak "koszyk" są skorelowane z odbiorców `AddJwtBearer()` zdefiniowanych w każdej mikrousługi z w ConfigureServices() startup klasy, takich jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="056e8-257">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="056e8-258">Jeśli spróbujesz uzyskać dostęp do dowolnej zabezpieczonej mikrousługi, takiej jak mikrousługa Koszyka z adresem URL reroute opartym na bramie interfejsu API, takiej jak `http://localhost:5202/api/v1/b/basket/1`, otrzymasz 401 Unauthorized, chyba że podasz prawidłowy token.</span><span class="sxs-lookup"><span data-stu-id="056e8-258">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="056e8-259">Z drugiej strony, jeśli adres URL ReRoute jest uwierzytelniony, Ocelot wywoła niezależnie od schematu podrzędnego jest skojarzony z nim (wewnętrzny adres URL mikrousługi).</span><span class="sxs-lookup"><span data-stu-id="056e8-259">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="056e8-260">**Autoryzacja w warstwie ReRoutes ocelota.**</span><span class="sxs-lookup"><span data-stu-id="056e8-260">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="056e8-261">Ocelot obsługuje autoryzację opartą na oświadczeniach ocenianą po uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="056e8-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="056e8-262">Autoryzację można ustawić na poziomie trasy, dodając następujące wiersze do konfiguracji ReRoute.</span><span class="sxs-lookup"><span data-stu-id="056e8-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="056e8-263">W tym przykładzie, gdy przywołuje się zagęszanie autoryzacji, Ocelot znajdzie, czy użytkownik ma typ oświadczenia "UserType" w tokenie i czy wartość tego oświadczenia jest "pracownik".</span><span class="sxs-lookup"><span data-stu-id="056e8-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="056e8-264">Jeśli tak nie jest, użytkownik nie będzie autoryzowany, a odpowiedź będzie zabroniona 403.</span><span class="sxs-lookup"><span data-stu-id="056e8-264">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="056e8-265">Korzystanie z bram interfejsu API Kubernetes a także ocelot</span><span class="sxs-lookup"><span data-stu-id="056e8-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="056e8-266">Korzystając z programu Kubernetes (na przykład w klastrze usługi Azure Kubernetes), zwykle unieruchomić wszystkie żądania HTTP za pośrednictwem [warstwy Usługi Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) opartej na *nginx*.</span><span class="sxs-lookup"><span data-stu-id="056e8-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="056e8-267">W kubernetes, jeśli nie używasz żadnego podejścia przychodzących, a następnie usług i zasobników mają adresów IP tylko routingu przez sieć klastra.</span><span class="sxs-lookup"><span data-stu-id="056e8-267">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="056e8-268">Jeśli jednak używasz metody danych ruchomych, będziesz mieć warstwę środkową między Internetem a usługami (w tym bramami interfejsu API), działając jako zwrotny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="056e8-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="056e8-269">Jako definicja ingress jest zbiorem reguł, które umożliwiają połączenia przychodzące, aby dotrzeć do usług klastrowania.</span><span class="sxs-lookup"><span data-stu-id="056e8-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="056e8-270">Ruch ingress jest zwykle skonfigurowany do świadczenia usług adresów URL dostępnych zewnętrznie, ruchu równoważenia obciążenia, zakończenia SSL i innych.</span><span class="sxs-lookup"><span data-stu-id="056e8-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="056e8-271">Użytkownicy żądają wciągania przez posting zasobu usługi Ingress do serwera interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="056e8-272">W eShopOnContainers podczas tworzenia lokalnie i przy użyciu tylko maszyny deweloperskiej jako hosta platformy Docker, nie używasz żadnych przychodzących, ale tylko wiele bram interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="056e8-273">Jednak podczas określania wartości docelowej środowiska "produkcyjnego" opartego na programach Kubernetes eShopOnContainers używa usługi ingress przed bramami interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-273">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="056e8-274">W ten sposób klienci nadal wywołać ten sam podstawowy adres URL, ale żądania są kierowane do wielu bram interfejsu API lub BFF.</span><span class="sxs-lookup"><span data-stu-id="056e8-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="056e8-275">Bramy interfejsu API są frontonami lub fasadami, które napawają się tylko usługami, ale nie aplikacjami sieci web, które zwykle znajdują się poza ich zakresem.</span><span class="sxs-lookup"><span data-stu-id="056e8-275">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="056e8-276">Ponadto bramy interfejsu API może ukryć niektórych mikrousług wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="056e8-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="056e8-277">Ruch wchodzący, jednak jest po prostu przekierowanie żądań HTTP, ale nie próbuje ukryć żadnych mikrousług lub aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="056e8-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="056e8-278">Posiadanie warstwy Nginx w kubernetes przed aplikacjami sieci web oraz kilka bram interfejsu API Ocelot / BFF jest idealną architekturą, jak pokazano na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="056e8-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Diagram przedstawiający, jak warstwa ruchu wingres pasuje do środowiska AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="056e8-280">**Rysunek 6-41**.</span><span class="sxs-lookup"><span data-stu-id="056e8-280">**Figure 6-41**.</span></span> <span data-ttu-id="056e8-281">Warstwa ingress w eShopOnContainers po wdrożeniu w Kubernetes</span><span class="sxs-lookup"><span data-stu-id="056e8-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="056e8-282">A Kubernetes Ingress działa jako zwrotny serwer proxy dla całego ruchu do aplikacji, w tym aplikacji sieci web, które są zwykle poza zakresem bramy interfejsu Api.</span><span class="sxs-lookup"><span data-stu-id="056e8-282">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="056e8-283">Podczas wdrażania eShopOnContainers w Kubernetes, udostępnia tylko kilka usług lub punktów końcowych za pośrednictwem _ingress_, w zasadzie poniższą listę postfixów na adresy URL:</span><span class="sxs-lookup"><span data-stu-id="056e8-283">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="056e8-284">`/`dla aplikacji internetowej spa klienta</span><span class="sxs-lookup"><span data-stu-id="056e8-284">`/` for the client SPA web application</span></span>
- <span data-ttu-id="056e8-285">`/webmvc`dla aplikacji internetowej klienta MVC</span><span class="sxs-lookup"><span data-stu-id="056e8-285">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="056e8-286">`/webstatus`dla aplikacji sieci web klienta z wyświetlonymi kontrolami stanu/kondycji</span><span class="sxs-lookup"><span data-stu-id="056e8-286">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="056e8-287">`/webshoppingapigw`dla internetowych BFF i procesów biznesowych na zakupy</span><span class="sxs-lookup"><span data-stu-id="056e8-287">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="056e8-288">`/webmarketingapigw`dla internetowych BFF i marketingowych procesów biznesowych</span><span class="sxs-lookup"><span data-stu-id="056e8-288">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="056e8-289">`/mobileshoppingapigw`dla mobilnych BFF i procesów biznesowych na zakupy</span><span class="sxs-lookup"><span data-stu-id="056e8-289">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="056e8-290">`/mobilemarketingapigw`dla mobilnych BFF i procesów marketingowych</span><span class="sxs-lookup"><span data-stu-id="056e8-290">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="056e8-291">Podczas wdrażania w programie Kubernetes każda brama interfejsu API Ocelot używa innego pliku "configuration.json" dla każdego _zasobnika_ z uruchomionymi bramami interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="056e8-291">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="056e8-292">Te pliki "configuration.json" są dostarczane przez zamontowanie (pierwotnie ze skryptem deploy.ps1) woluminu utworzonego na podstawie _mapy konfiguracji_ Kubernetes o nazwie "ocelot".</span><span class="sxs-lookup"><span data-stu-id="056e8-292">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="056e8-293">Każdy kontener montuje powiązany plik konfiguracyjny `/app/configuration`w folderze kontenera o nazwie .</span><span class="sxs-lookup"><span data-stu-id="056e8-293">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="056e8-294">W plikach kodu źródłowego eShopOnContainers oryginalne pliki "configuration.json" `k8s/ocelot/` można znaleźć w folderze.</span><span class="sxs-lookup"><span data-stu-id="056e8-294">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="056e8-295">Dla każdego pliku BFF/APIGateway jest jeden plik.</span><span class="sxs-lookup"><span data-stu-id="056e8-295">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="056e8-296">Dodatkowe funkcje przekrojowe w bramie Interfejsu API Ocelot</span><span class="sxs-lookup"><span data-stu-id="056e8-296">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="056e8-297">Istnieją inne ważne funkcje do badania i używania, podczas korzystania z bramy interfejsu API Ocelot, opisane w poniższych łączach.</span><span class="sxs-lookup"><span data-stu-id="056e8-297">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="056e8-298">**Odkrycie usługi po stronie klienta integrujące Ocelot z konsulem lub Eureką** </span><span class="sxs-lookup"><span data-stu-id="056e8-298">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="056e8-299">**Buforowanie w warstwie bramy interfejsu API** </span><span class="sxs-lookup"><span data-stu-id="056e8-299">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="056e8-300">**Rejestrowanie w warstwie Bramy interfejsu API** </span><span class="sxs-lookup"><span data-stu-id="056e8-300">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="056e8-301">**Jakość usługi (ponownych prób i wyłączników) w warstwie Bramy interfejsu API** </span><span class="sxs-lookup"><span data-stu-id="056e8-301">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="056e8-302">**Ograniczanie szybkości** </span><span class="sxs-lookup"><span data-stu-id="056e8-302">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="056e8-303">[Poprzedni](background-tasks-with-ihostedservice.md)
> [następny](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="056e8-303">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
