---
title: Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 87b48624fde8c7cdab097289f1cf56ab56e1173f
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="64cac-104">Projektowanie mikrousługi warstwy aplikacji i interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="64cac-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="64cac-105">Za pomocą stałych zasad i iniekcja zależności</span><span class="sxs-lookup"><span data-stu-id="64cac-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="64cac-106">STAŁE zasady są krytyczne technik w celu można użyć w dowolnej aplikacji modern i strategicznych, takich jak tworzenie mikrousługi wzorami DDD.</span><span class="sxs-lookup"><span data-stu-id="64cac-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="64cac-107">STAŁE jest skrótem tej grupy pięć podstawowych zasad:</span><span class="sxs-lookup"><span data-stu-id="64cac-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="64cac-108">Pojedynczy zasady odpowiedzialności</span><span class="sxs-lookup"><span data-stu-id="64cac-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="64cac-109">Zasada otwarty/zamknięty</span><span class="sxs-lookup"><span data-stu-id="64cac-109">Open/closed principle</span></span>

-   <span data-ttu-id="64cac-110">Zasada podstawienia Liskov</span><span class="sxs-lookup"><span data-stu-id="64cac-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="64cac-111">Zasada podział — interfejs</span><span class="sxs-lookup"><span data-stu-id="64cac-111">Interface Segregation principle</span></span>

-   <span data-ttu-id="64cac-112">Zasada odwracanie zależności</span><span class="sxs-lookup"><span data-stu-id="64cac-112">Dependency Inversion principle</span></span>

<span data-ttu-id="64cac-113">STAŁE są dotyczące sposobu projektowania aplikacji lub mikrousługi wewnętrzny warstwy i oddzielenie zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="64cac-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="64cac-114">Nie jest powiązany z domeną, ale do projektu technicznego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64cac-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="64cac-115">Końcowe zasady zasady odwracanie zależności (Podpisane) umożliwia oddzielana od pozostałej części warstwy, dzięki czemu lepiej implementacji rozdzielonymi warstw DDD warstwę infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="64cac-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="64cac-116">Podpisane jest jednym ze sposobów realizacji zasady odwracanie zależności.</span><span class="sxs-lookup"><span data-stu-id="64cac-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="64cac-117">To technika osiągnięcia luźne powiązanie między obiektów i ich zależności.</span><span class="sxs-lookup"><span data-stu-id="64cac-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="64cac-118">Zamiast bezpośrednio uruchamianiu współpracownicy lub przy użyciu statycznych odwołań, obiekty, które klasy wymaga, aby jego akcje są dostarczony do (lub "wstrzykuje") klasy.</span><span class="sxs-lookup"><span data-stu-id="64cac-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="64cac-119">W większości przypadków klasy będzie zadeklarować ich zależności za pomocą ich konstruktora, dzięki czemu mogą być zgodna z zasadą jawne zależności.</span><span class="sxs-lookup"><span data-stu-id="64cac-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="64cac-120">Podpisane zazwyczaj opiera się na określonym kontenery Inwersja kontroli (Inwersja kontroli).</span><span class="sxs-lookup"><span data-stu-id="64cac-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="64cac-121">Platformy ASP.NET Core udostępnia prosty wbudowanych kontenera IoC, ale można również użyć kontenera IoC Ulubione, takich jak Autofac lub Ninject.</span><span class="sxs-lookup"><span data-stu-id="64cac-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="64cac-122">Wykonując stałych zasad klas będzie zazwyczaj naturalnie za mały, dobrze factored i łatwo przetestowane.</span><span class="sxs-lookup"><span data-stu-id="64cac-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="64cac-123">Ale jak należy znać, jeśli zbyt wiele zależności są są wstrzykiwane do klas?</span><span class="sxs-lookup"><span data-stu-id="64cac-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="64cac-124">Jeśli używasz Podpisane za pomocą konstruktora będzie łatwo wykryć który analizując tylko z liczbą parametrów dla Twojego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="64cac-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="64cac-125">Jeśli istnieją zbyt wiele zależności, zwykle jest to znak ( [kodu zapachu](http://deviq.com/code-smells/)) próbuje zrobić zbyt dużo klasy i prawdopodobnie narusza zasady pojedynczego odpowiedzialności.</span><span class="sxs-lookup"><span data-stu-id="64cac-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="64cac-126">Może upłynąć innego przewodnik szczegółowo stałe.</span><span class="sxs-lookup"><span data-stu-id="64cac-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="64cac-127">W związku z tym w tym przewodniku wymaga minimalnej znajomości tych tematów.</span><span class="sxs-lookup"><span data-stu-id="64cac-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="64cac-128">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="64cac-128">Additional resources</span></span>

-   <span data-ttu-id="64cac-129">**STAŁE: Zasady podstawowych Obiektowo**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="64cac-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="64cac-130">**Inwersja kontroli kontenerów i wzorzec iniekcji zależności**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="64cac-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="64cac-131">**Steve Smith. Nowe jest sklejki**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="64cac-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="64cac-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="64cac-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
