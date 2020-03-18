---
title: Podejścia do architektury — aplikacje bezserwerowe
description: Wprowadzenie do podejścia do architektury do tworzenia aplikacji korporacyjnych opartych na chmurze, od architektur n-warstwowych do bezserwerowych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522899"
---
# <a name="architecture-approaches"></a><span data-ttu-id="11419-103">Podejścia do architektury</span><span class="sxs-lookup"><span data-stu-id="11419-103">Architecture approaches</span></span>

<span data-ttu-id="11419-104">Zrozumienie istniejących podejść do projektowania aplikacji dla przedsiębiorstw pomaga wyjaśnić rolę odgrywanej przez bezserwerowe.</span><span class="sxs-lookup"><span data-stu-id="11419-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="11419-105">Istnieje wiele podejść i wzorców, które ewoluowały przez dziesięciolecia rozwoju oprogramowania, a wszystkie mają swoje wady i zalety.</span><span class="sxs-lookup"><span data-stu-id="11419-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="11419-106">W wielu przypadkach ostateczne rozwiązanie może nie obejmować podjęcia decyzji w sprawie jednego podejścia, ale może integrować kilka podejść.</span><span class="sxs-lookup"><span data-stu-id="11419-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="11419-107">Scenariusze migracji często obejmują przejście z jednego podejścia architektury do innego za pomocą podejścia hybrydowego.</span><span class="sxs-lookup"><span data-stu-id="11419-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="11419-108">Ten rozdział zawiera omówienie wzorców architektury logicznej i fizycznej dla aplikacji korporacyjnych.</span><span class="sxs-lookup"><span data-stu-id="11419-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="11419-109">Wzorce architektury</span><span class="sxs-lookup"><span data-stu-id="11419-109">Architecture patterns</span></span>

<span data-ttu-id="11419-110">Nowoczesne aplikacje biznesowe są zgodne z różnymi wzorcami architektury.</span><span class="sxs-lookup"><span data-stu-id="11419-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="11419-111">Ta sekcja przedstawia przegląd typowych wzorców.</span><span class="sxs-lookup"><span data-stu-id="11419-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="11419-112">Wzorce wymienione w tym miejscu nie koniecznie wszystkie najlepsze rozwiązania, ale ilustrują różne podejścia.</span><span class="sxs-lookup"><span data-stu-id="11419-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="11419-113">Aby uzyskać więcej informacji, zobacz [Przewodnik po architekturze aplikacji platformy Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="11419-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="11419-114">Monoliths</span><span class="sxs-lookup"><span data-stu-id="11419-114">Monoliths</span></span>

<span data-ttu-id="11419-115">Wiele aplikacji biznesowych jest zgodnych ze wzorem monolitu.</span><span class="sxs-lookup"><span data-stu-id="11419-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="11419-116">Starsze aplikacje są często implementowane jako monolity.</span><span class="sxs-lookup"><span data-stu-id="11419-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="11419-117">We wzorcu monolitu wszystkie problemy aplikacji są zawarte w jednym wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="11419-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="11419-118">Wszystko, od interfejsu użytkownika do wywołań bazy danych znajduje się w tej samej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="11419-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Architektura monolitu](./media/monolith-architecture.png)

<span data-ttu-id="11419-120">Podejście monolitu ma kilka zalet.</span><span class="sxs-lookup"><span data-stu-id="11419-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="11419-121">Często łatwo jest ściągnąć jedną bazę kodu i rozpocząć pracę.</span><span class="sxs-lookup"><span data-stu-id="11419-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="11419-122">Czas zwiększania czasu może być krótszy, a tworzenie środowisk testowych jest tak proste, jak dostarczenie nowej kopii.</span><span class="sxs-lookup"><span data-stu-id="11419-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="11419-123">Monolit może być zaprojektowany tak, aby zawierał wiele komponentów i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11419-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="11419-124">Niestety, wzór monolitu ma tendencję do rozkładu na dużą skalę.</span><span class="sxs-lookup"><span data-stu-id="11419-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="11419-125">Główne wady podejścia monolitu obejmują:</span><span class="sxs-lookup"><span data-stu-id="11419-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="11419-126">Trudne do pracy równolegle w tej samej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="11419-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="11419-127">Wszelkie zmiany, bez względu na to, jak trywialne, wymaga wdrożenia nowej wersji całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11419-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="11419-128">Refaktoryzacja potencjalnie wpływa na całą aplikację.</span><span class="sxs-lookup"><span data-stu-id="11419-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="11419-129">Często jedynym rozwiązaniem do skalowania jest tworzenie wielu, intensywnie zaopatrzony kopii monolitu.</span><span class="sxs-lookup"><span data-stu-id="11419-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="11419-130">Wraz z rozwojem systemów lub innymi systemami integracja może być trudna.</span><span class="sxs-lookup"><span data-stu-id="11419-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="11419-131">Może być trudne do przetestowania ze względu na konieczność skonfigurowania całego monolitu.</span><span class="sxs-lookup"><span data-stu-id="11419-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="11419-132">Ponowne użycie kodu jest trudne i często inne aplikacje kończą się własnymi kopiami kodu.</span><span class="sxs-lookup"><span data-stu-id="11419-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="11419-133">Wiele firm patrzy na chmurę jako okazję do migracji aplikacji monolitu, a jednocześnie refaktoryzacji ich do bardziej użytecznych wzorców.</span><span class="sxs-lookup"><span data-stu-id="11419-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="11419-134">Często można wyrwać poszczególne aplikacje i składniki, aby umożliwić ich utrzymanie, wdrożenie i skalowanie oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="11419-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="11419-135">Aplikacje wielowarstwowe</span><span class="sxs-lookup"><span data-stu-id="11419-135">N-Layer applications</span></span>

<span data-ttu-id="11419-136">Logika aplikacji n-warstwowej partycji do określonych warstw.</span><span class="sxs-lookup"><span data-stu-id="11419-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="11419-137">Najczęstsze warstwy to:</span><span class="sxs-lookup"><span data-stu-id="11419-137">The most common layers include:</span></span>

- <span data-ttu-id="11419-138">Interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="11419-138">User interface</span></span>
- <span data-ttu-id="11419-139">Logika biznesowa</span><span class="sxs-lookup"><span data-stu-id="11419-139">Business logic</span></span>
- <span data-ttu-id="11419-140">Dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="11419-140">Data access</span></span>

<span data-ttu-id="11419-141">Inne warstwy mogą obejmować pośredniczenie, przetwarzanie wsadowe i interfejs API.</span><span class="sxs-lookup"><span data-stu-id="11419-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="11419-142">Ważne jest, aby pamiętać, że warstwy są logiczne.</span><span class="sxs-lookup"><span data-stu-id="11419-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="11419-143">Mimo że są one opracowane w izolacji, wszystkie mogą być wdrażane na tej samej platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="11419-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Architektura n-warstwowa](./media/n-layer-architecture.png)

<span data-ttu-id="11419-145">Podejście N-Layer ma kilka zalet, w tym:</span><span class="sxs-lookup"><span data-stu-id="11419-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="11419-146">Refaktoryzacja jest izolowana do warstwy.</span><span class="sxs-lookup"><span data-stu-id="11419-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="11419-147">Zespoły mogą niezależnie tworzyć, testować, wdrażać i obsługiwać oddzielne warstwy.</span><span class="sxs-lookup"><span data-stu-id="11419-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="11419-148">Warstwy można wymieniać, na przykład warstwa danych może uzyskać dostęp do wielu baz danych bez konieczności wprowadzania zmian w warstwie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11419-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="11419-149">Bezserwerowy może służyć do zaimplementowania jednej lub więcej warstw.</span><span class="sxs-lookup"><span data-stu-id="11419-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="11419-150">Mikrousługi</span><span class="sxs-lookup"><span data-stu-id="11419-150">Microservices</span></span>

<span data-ttu-id="11419-151">**[Architektury mikrousług](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** zawierają typowe cechy, które obejmują:</span><span class="sxs-lookup"><span data-stu-id="11419-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="11419-152">Aplikacje składają się z kilku małych usług.</span><span class="sxs-lookup"><span data-stu-id="11419-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="11419-153">Każda usługa jest uruchamiana w swoim własnym procesie.</span><span class="sxs-lookup"><span data-stu-id="11419-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="11419-154">Usługi są wyrównane wokół domen biznesowych.</span><span class="sxs-lookup"><span data-stu-id="11419-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="11419-155">Usługi komunikują się za pośrednictwem lekkich interfejsów API, zazwyczaj przy użyciu protokołu HTTP jako transportu.</span><span class="sxs-lookup"><span data-stu-id="11419-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="11419-156">Usługi można wdrażać i uaktualniać niezależnie.</span><span class="sxs-lookup"><span data-stu-id="11419-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="11419-157">Usługi nie są zależne od pojedynczego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="11419-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="11419-158">System został zaprojektowany z myślą o awarii, a aplikacja może nadal działać nawet wtedy, gdy niektóre usługi zawiodą.</span><span class="sxs-lookup"><span data-stu-id="11419-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="11419-159">Mikrousługi nie muszą wzajemnie się wykluczać z innymi metodami architektury.</span><span class="sxs-lookup"><span data-stu-id="11419-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="11419-160">Na przykład architektura N-Tier może używać mikrousług dla warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="11419-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="11419-161">Istnieje również możliwość implementowania mikrousług na różne sposoby, od katalogów wirtualnych na hostach usług IIS do kontenerów.</span><span class="sxs-lookup"><span data-stu-id="11419-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="11419-162">Właściwości mikrousług sprawiają, że są one szczególnie idealne dla implementacji bezużycia serwera.</span><span class="sxs-lookup"><span data-stu-id="11419-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architektura mikrousług](./media/microservices-architecture.png)

<span data-ttu-id="11419-164">Zalety architektury mikrousług obejmują:</span><span class="sxs-lookup"><span data-stu-id="11419-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="11419-165">Refaktoryzacja jest często izolowana do pojedynczej usługi.</span><span class="sxs-lookup"><span data-stu-id="11419-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="11419-166">Usługi mogą być uaktualniane niezależnie od siebie.</span><span class="sxs-lookup"><span data-stu-id="11419-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="11419-167">Odporność i elastyczność można dostosować do wymagań poszczególnych usług.</span><span class="sxs-lookup"><span data-stu-id="11419-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="11419-168">Programistyka może odbywać się równolegle między różnymi zespołami i platformami.</span><span class="sxs-lookup"><span data-stu-id="11419-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="11419-169">Łatwiej jest napisać kompleksowe testy dla izolowanych usług.</span><span class="sxs-lookup"><span data-stu-id="11419-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="11419-170">Mikrousługi pochodzą z własnych wyzwań, w tym:</span><span class="sxs-lookup"><span data-stu-id="11419-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="11419-171">Określanie, jakie usługi są dostępne i jak do nich zadzwonić.</span><span class="sxs-lookup"><span data-stu-id="11419-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="11419-172">Zarządzanie cyklem życia usług.</span><span class="sxs-lookup"><span data-stu-id="11419-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="11419-173">Zrozumienie, jak usługi pasują do siebie w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11419-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="11419-174">Pełne testowanie systemu połączeń wykonanych w różnych usługach.</span><span class="sxs-lookup"><span data-stu-id="11419-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="11419-175">Ostatecznie istnieją rozwiązania, aby sprostać wszystkim tym wyzwaniom, w tym wykorzystanie zalet bezserwerowych, które zostały omówione później.</span><span class="sxs-lookup"><span data-stu-id="11419-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="11419-176">[Poprzedni](index.md)
>[następny](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="11419-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
