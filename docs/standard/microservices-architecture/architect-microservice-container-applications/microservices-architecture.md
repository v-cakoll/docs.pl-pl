---
title: "Architektura Mikrousług"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Architektura Mikrousług"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a><span data-ttu-id="8de37-104">Architektura Mikrousług</span><span class="sxs-lookup"><span data-stu-id="8de37-104">Microservices architecture</span></span>

<span data-ttu-id="8de37-105">Jak wskazuje nazwę, architektura mikrousług jest podejście do tworzenia aplikacji serwera jako zestaw usług mała.</span><span class="sxs-lookup"><span data-stu-id="8de37-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="8de37-106">Każda usługa jest uruchamiana we własnym procesie i komunikuje się z innymi procesami przy użyciu protokołów, takich jak HTTP/HTTPS, Websocket, lub [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span><span class="sxs-lookup"><span data-stu-id="8de37-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="8de37-107">Każdy mikrousługi implementuje określonej domeny end-to-end lub możliwości biznesowe w obrębie granicy kontekstu oraz poszczególnych musi być opracowana autonomicznie i możliwych do wdrożenia niezależnie.</span><span class="sxs-lookup"><span data-stu-id="8de37-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="8de37-108">Na koniec każdego mikrousługi powinien być właścicielem jego modelu danych powiązanych domeny i logika domeny (suwerenności i zarządzanie zdecentralizowane danych) na podstawie technologii magazynowania danych (SQL, NoSQL) i różnych języków programowania.</span><span class="sxs-lookup"><span data-stu-id="8de37-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="8de37-109">Jaki rozmiar powinna być mikrousługi?</span><span class="sxs-lookup"><span data-stu-id="8de37-109">What size should a microservice be?</span></span> <span data-ttu-id="8de37-110">Podczas tworzenia mikrousługi, rozmiar nie może być istotne.</span><span class="sxs-lookup"><span data-stu-id="8de37-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="8de37-111">Zamiast tego istotne należy utworzyć słabo sprzężona usług, więc autonomię tworzenia, wdrażania i skalowania dla każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="8de37-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="8de37-112">Oczywiście podczas identyfikacji i mikrousług projektowania, należy spróbować były możliwie najmniejsze tak długo, jak nie ma zbyt wiele zależności bezpośrednich z innych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="8de37-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="8de37-113">Większe znaczenie niż rozmiar mikrousługi spójności wewnętrznego, który musi mieć i jego niezależność od innych usług.</span><span class="sxs-lookup"><span data-stu-id="8de37-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="8de37-114">Dlaczego architektura mikrousług?</span><span class="sxs-lookup"><span data-stu-id="8de37-114">Why a microservices architecture?</span></span> <span data-ttu-id="8de37-115">Krótko mówiąc zapewnia elastyczność długoterminowej.</span><span class="sxs-lookup"><span data-stu-id="8de37-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="8de37-116">Mikrousług włączyć lepsze utrzymanie w systemach złożonych, duże i wysoko skalowane przez umożliwienie tworzenia aplikacji z wielu usług niezależnie do wdrożenia że mieć cykle szczegółowego i autonomicznego.</span><span class="sxs-lookup"><span data-stu-id="8de37-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="8de37-117">Dodatkowa korzyść mikrousług można skalować w poziomie niezależnie.</span><span class="sxs-lookup"><span data-stu-id="8de37-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="8de37-118">Zamiast aplikacją wbudowanymi pojedynczego musi skalowanie w poziomie jako jednostki, możesz zamiast tego skalować w poziomie określonych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="8de37-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="8de37-119">W ten sposób można skalować tylko funkcjonalności wymaga więcej przetwarzania zasilania lub sieci przepustowość do obsługi żądanie, a nie skalowania innych obszarach aplikacji, które nie muszą być skalowane obszaru.</span><span class="sxs-lookup"><span data-stu-id="8de37-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="8de37-120">Oznacza to, że oszczędności, ponieważ potrzebna mniej sprzętu.</span><span class="sxs-lookup"><span data-stu-id="8de37-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="8de37-121">**Rysunek 4 – 6**.</span><span class="sxs-lookup"><span data-stu-id="8de37-121">**Figure 4-6**.</span></span> <span data-ttu-id="8de37-122">Wbudowanymi wdrożenia i podejście mikrousług</span><span class="sxs-lookup"><span data-stu-id="8de37-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="8de37-123">Jak pokazano na rysunku 4 – 6, podejście mikrousług umożliwia elastyczne zmiany i szybkie iteracji każdego mikrousługi nie można zmienić określone, mała obszary aplikacji złożonych, duże i skalowalne.</span><span class="sxs-lookup"><span data-stu-id="8de37-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="8de37-124">Zaprojektowanie szczegółowych aplikacji opartych na mikrousług umożliwia ciągłej integracji i rozwiązań ciągłego dostarczania.</span><span class="sxs-lookup"><span data-stu-id="8de37-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="8de37-125">Przyspiesza również dostarczania nowych funkcji, do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8de37-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="8de37-126">Szczegółowe kompozycji aplikacji umożliwia również uruchamianie i testowanie mikrousług w izolacji i rozwijać je samodzielnie, przy zachowaniu wyczyść kontraktów między nimi.</span><span class="sxs-lookup"><span data-stu-id="8de37-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="8de37-127">Tak długo, jak nie zmienisz interfejsów lub umowy, można zmienić wewnętrzny wykonania dowolnego mikrousługi lub dodawanie nowych funkcji bez przerywania innych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="8de37-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="8de37-128">Poniżej przedstawiono istotne aspekty umożliwiające Powodzenie w przejściu w środowisku produkcyjnym z użyciem systemu mikrousług:</span><span class="sxs-lookup"><span data-stu-id="8de37-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="8de37-129">Monitorowanie i kondycji kontroli usług i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="8de37-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="8de37-130">Skalowalnej infrastruktury usług (czyli chmury i orchestrators).</span><span class="sxs-lookup"><span data-stu-id="8de37-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="8de37-131">Zabezpieczenia projektowania i wdrażania na wielu poziomach: uwierzytelniania, autoryzacji, zarządzanie klucze tajne, bezpiecznej komunikacji, itp.</span><span class="sxs-lookup"><span data-stu-id="8de37-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="8de37-132">Dostarczanie szybkie aplikacji, zwykle za pomocą różnych zespołów koncentrujących się na różnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="8de37-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="8de37-133">DevOps i CI/CD rozwiązań i infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="8de37-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="8de37-134">Z nich tylko pierwsze trzy są objęte lub wprowadzone w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="8de37-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="8de37-135">Ostatnie dwa punkty, które są związane z cyklem życia aplikacji, znajdują się w dodatkowych [konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami](https://aka.ms/dockerlifecycleebook) Książka elektroniczna.</span><span class="sxs-lookup"><span data-stu-id="8de37-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8de37-136">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="8de37-136">Additional resources</span></span>

-   <span data-ttu-id="8de37-137">**Russinovichem znaku. Mikrousług: Ma obrotów aplikacji obsługiwane przez usługę w chmurze**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="8de37-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="8de37-138">**Pole Fowler. Mikrousług**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="8de37-138">**Martin Fowler. Microservices**
[*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="8de37-139">**Pole Fowler. Wymagania wstępne Mikrousługi**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="8de37-139">**Martin Fowler. Microservice Prerequisites**
[*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="8de37-140">**Jimmy Nilsson. Bryłkach chmury obliczeniowej**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="8de37-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="8de37-141">**Torre de la Cesarowi. Konteneryzowanych cyklem życia aplikacji Docker z platformy firmy Microsoft i narzędziami** (do pobrania Książka elektroniczna) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="8de37-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="8de37-142">[Poprzednie] (usługa ukierunkowane architecture.md) [dalej] (danych suwerenności na microservice.md)</span><span class="sxs-lookup"><span data-stu-id="8de37-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
