---
title: Podejścia do architektury — aplikacje bezserwerowe
description: Wprowadzenie do architektury podejścia do tworzenia aplikacji korporacyjnych opartych na chmurze, od architektur N-warstwowych do bezserwerowych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522899"
---
# <a name="architecture-approaches"></a><span data-ttu-id="b6c85-103">Podejścia do architektury</span><span class="sxs-lookup"><span data-stu-id="b6c85-103">Architecture approaches</span></span>

<span data-ttu-id="b6c85-104">Zrozumienie istniejących podejścia do tworzenia aplikacji dla przedsiębiorstw pomaga wyjaśnić rolę odgrywaną przez serwer.</span><span class="sxs-lookup"><span data-stu-id="b6c85-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="b6c85-105">Istnieje wiele metod i wzorców, które są rozbudowane w trakcie tworzenia oprogramowania, a wszystkie mają własne zalety i wady.</span><span class="sxs-lookup"><span data-stu-id="b6c85-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="b6c85-106">W wielu przypadkach ostateczne rozwiązanie nie może polegać na wyborze jednego podejścia, ale może zintegrować kilka metod.</span><span class="sxs-lookup"><span data-stu-id="b6c85-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="b6c85-107">Scenariusze migracji często obejmują zmianę z jednej architektury do innej za pośrednictwem podejścia hybrydowego.</span><span class="sxs-lookup"><span data-stu-id="b6c85-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="b6c85-108">Ten rozdział zawiera omówienie wzorców architektury logicznej i fizycznej dla aplikacji dla przedsiębiorstw.</span><span class="sxs-lookup"><span data-stu-id="b6c85-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="b6c85-109">Wzorce architektury</span><span class="sxs-lookup"><span data-stu-id="b6c85-109">Architecture patterns</span></span>

<span data-ttu-id="b6c85-110">Nowoczesne aplikacje biznesowe są zgodne z różnymi wzorcami architektury.</span><span class="sxs-lookup"><span data-stu-id="b6c85-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="b6c85-111">Ta sekcja reprezentuje przegląd wspólnych wzorców.</span><span class="sxs-lookup"><span data-stu-id="b6c85-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="b6c85-112">Wzorce wymienione w tym miejscu nie zawsze są najlepszym rozwiązaniem, ale ilustrują różne podejścia.</span><span class="sxs-lookup"><span data-stu-id="b6c85-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="b6c85-113">Aby uzyskać więcej informacji, zobacz [Przewodnik po architekturze aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="b6c85-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="b6c85-114">Monolitów</span><span class="sxs-lookup"><span data-stu-id="b6c85-114">Monoliths</span></span>

<span data-ttu-id="b6c85-115">Wiele aplikacji firmowych jest zgodnych ze wzorcem monolitu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="b6c85-116">Starsze aplikacje są często implementowane jako monolitów.</span><span class="sxs-lookup"><span data-stu-id="b6c85-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="b6c85-117">We wzorcu monolitu wszystkie problemy dotyczące aplikacji są zawarte w jednym wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="b6c85-118">Wszystkie elementy z interfejsu użytkownika do wywołań bazy danych są zawarte w tej samej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Architektura monolitu](./media/monolith-architecture.png)

<span data-ttu-id="b6c85-120">Istnieje kilka zalet podejścia do monolitu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="b6c85-121">Często można łatwo ściągnąć pojedynczy kod podstawowy i rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="b6c85-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="b6c85-122">Czas zwiększania obciążenia może być mniejszy i tworzenie środowisk testowych jest proste, co zapewnia nową kopię.</span><span class="sxs-lookup"><span data-stu-id="b6c85-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="b6c85-123">Monolitu może być zaprojektowana tak, aby obejmowała wiele składników i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6c85-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="b6c85-124">Niestety, wzorzec monolituu może być podzielony na dużą skalę.</span><span class="sxs-lookup"><span data-stu-id="b6c85-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="b6c85-125">Główne wady podejścia monolitu obejmują:</span><span class="sxs-lookup"><span data-stu-id="b6c85-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="b6c85-126">Trudne równoległe działanie w tej samej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="b6c85-127">Wszelkie zmiany, niezależnie od tego, jak uproszczony, wymagają wdrożenia nowej wersji całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6c85-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="b6c85-128">Refaktoryzacja może mieć wpływ na całą aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6c85-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="b6c85-129">Często jedyne rozwiązanie do skalowania polega na utworzeniu wielu kopii monolituych intensywnie korzystających z zasobów.</span><span class="sxs-lookup"><span data-stu-id="b6c85-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="b6c85-130">Po rozwinięciu systemu lub uzyskaniu innych systemów integracja może być trudna.</span><span class="sxs-lookup"><span data-stu-id="b6c85-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="b6c85-131">Może być trudne do przetestowania ze względu na konieczność skonfigurowania całego monolitu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="b6c85-132">Ponowne użycie kodu jest wyzwaniem i często inne aplikacje kończą swoje własne kopie kodu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="b6c85-133">Wiele firm przeszukuje chmurę jako okazję do migracji aplikacji monolitu i w tym samym czasie refaktoryzacji ich do bardziej użytecznych wzorców.</span><span class="sxs-lookup"><span data-stu-id="b6c85-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="b6c85-134">Często należy rozdzielić poszczególne aplikacje i składniki, aby umożliwić ich utrzymanie, wdrożenie i skalowanie osobno.</span><span class="sxs-lookup"><span data-stu-id="b6c85-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="b6c85-135">Aplikacje N-warstwowe</span><span class="sxs-lookup"><span data-stu-id="b6c85-135">N-Layer applications</span></span>

<span data-ttu-id="b6c85-136">Warstwa aplikacji N-warstwowa partycji aplikacji w określonych warstwach.</span><span class="sxs-lookup"><span data-stu-id="b6c85-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="b6c85-137">Najbardziej typowe warstwy obejmują:</span><span class="sxs-lookup"><span data-stu-id="b6c85-137">The most common layers include:</span></span>

- <span data-ttu-id="b6c85-138">Interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="b6c85-138">User interface</span></span>
- <span data-ttu-id="b6c85-139">Logika biznesowa</span><span class="sxs-lookup"><span data-stu-id="b6c85-139">Business logic</span></span>
- <span data-ttu-id="b6c85-140">Dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="b6c85-140">Data access</span></span>

<span data-ttu-id="b6c85-141">Inne warstwy mogą obejmować oprogramowanie pośredniczące, przetwarzanie wsadowe i interfejs API.</span><span class="sxs-lookup"><span data-stu-id="b6c85-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="b6c85-142">Ważne jest, aby zauważyć, że warstwy są logiczne.</span><span class="sxs-lookup"><span data-stu-id="b6c85-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="b6c85-143">Mimo że są one opracowywane jako izolacja, mogą zostać wdrożone na tej samej platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="b6c85-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Architektura N-warstwowa](./media/n-layer-architecture.png)

<span data-ttu-id="b6c85-145">Istnieje kilka zalet podejścia do warstwy N, w tym:</span><span class="sxs-lookup"><span data-stu-id="b6c85-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="b6c85-146">Refaktoryzacja jest izolowana dla warstwy.</span><span class="sxs-lookup"><span data-stu-id="b6c85-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="b6c85-147">Zespoły mogą niezależnie kompilować, testować, wdrażać i konserwować oddzielne warstwy.</span><span class="sxs-lookup"><span data-stu-id="b6c85-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="b6c85-148">Warstwy mogą być wymieniane, na przykład warstwa danych może uzyskać dostęp do wielu baz danych bez konieczności wprowadzania zmian w warstwie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b6c85-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="b6c85-149">W celu zaimplementowania jednej lub kilku warstw może być używana bezserwerowa.</span><span class="sxs-lookup"><span data-stu-id="b6c85-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="b6c85-150">Mikrousług</span><span class="sxs-lookup"><span data-stu-id="b6c85-150">Microservices</span></span>

<span data-ttu-id="b6c85-151">Architektury **[mikrousług](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** zawierają wspólne cechy, które obejmują:</span><span class="sxs-lookup"><span data-stu-id="b6c85-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="b6c85-152">Aplikacje składają się z kilku małych usług.</span><span class="sxs-lookup"><span data-stu-id="b6c85-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="b6c85-153">Każda usługa jest uruchamiana we własnym procesie.</span><span class="sxs-lookup"><span data-stu-id="b6c85-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="b6c85-154">Usługi są wyrównane do domeny biznesowej.</span><span class="sxs-lookup"><span data-stu-id="b6c85-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="b6c85-155">Usługi komunikują się za pośrednictwem lekkich interfejsów API, zazwyczaj przy użyciu protokołu HTTP jako transportu.</span><span class="sxs-lookup"><span data-stu-id="b6c85-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="b6c85-156">Usługi mogą być wdrażane i uaktualniane niezależnie.</span><span class="sxs-lookup"><span data-stu-id="b6c85-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="b6c85-157">Usługi nie zależą od pojedynczego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="b6c85-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="b6c85-158">System został zaprojektowany z myślą o awarii, a aplikacja może być uruchomiona nawet w przypadku awarii niektórych usług.</span><span class="sxs-lookup"><span data-stu-id="b6c85-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="b6c85-159">Mikrousługi nie muszą się wzajemnie wykluczać z innych metod architektury.</span><span class="sxs-lookup"><span data-stu-id="b6c85-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="b6c85-160">Na przykład architektura N-warstwowa może korzystać z mikrousług dla warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="b6c85-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="b6c85-161">Istnieje również możliwość zaimplementowania mikrousług na różne sposoby, od katalogów wirtualnych na hostach IIS do kontenerów.</span><span class="sxs-lookup"><span data-stu-id="b6c85-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="b6c85-162">Charakterystyki mikrousług sprawiają, że są one szczególnie idealne dla implementacji bezserwerowych.</span><span class="sxs-lookup"><span data-stu-id="b6c85-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architektura mikrousług](./media/microservices-architecture.png)

<span data-ttu-id="b6c85-164">W architekturze mikrousług są dostępne:</span><span class="sxs-lookup"><span data-stu-id="b6c85-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="b6c85-165">Refaktoryzacja jest często izolowana dla jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="b6c85-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="b6c85-166">Usługi można uaktualnić niezależnie od siebie.</span><span class="sxs-lookup"><span data-stu-id="b6c85-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="b6c85-167">Odporność i elastyczność można dostrajać do wymagań poszczególnych usług.</span><span class="sxs-lookup"><span data-stu-id="b6c85-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="b6c85-168">Programowanie może wystąpić równolegle między różnymi zespołami i platformami.</span><span class="sxs-lookup"><span data-stu-id="b6c85-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="b6c85-169">Łatwiej jest pisać kompleksowe testy dla usług izolowanych.</span><span class="sxs-lookup"><span data-stu-id="b6c85-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="b6c85-170">Mikrousługi są związane z własnymi wyzwaniami, w tym:</span><span class="sxs-lookup"><span data-stu-id="b6c85-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="b6c85-171">Określanie, które usługi są dostępne i jak je wywoływać.</span><span class="sxs-lookup"><span data-stu-id="b6c85-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="b6c85-172">Zarządzanie cyklem życia usług.</span><span class="sxs-lookup"><span data-stu-id="b6c85-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="b6c85-173">Zrozumienie, w jaki sposób usługi mieszczą się w ogólnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6c85-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="b6c85-174">Pełne testowanie systemu wywołań wykonanych między różnymi usługami.</span><span class="sxs-lookup"><span data-stu-id="b6c85-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="b6c85-175">Ostatecznie istnieją rozwiązania, które należy spełnić przed wszystkimi tymi wyzwaniami, w tym w przypadku korzystania z zalet bezserwerowych, które zostały omówione w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="b6c85-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b6c85-176">[Poprzedni](index.md)
>[Następny](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="b6c85-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
