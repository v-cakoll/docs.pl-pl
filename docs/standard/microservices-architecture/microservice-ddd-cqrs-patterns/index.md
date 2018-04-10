---
title: Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS
keywords: Docker, Mikrousług, ASP.NET, kontenera
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 45f29a8d19e49685f864b7ca83e466ceb1f73a62
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="56493-104">Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS</span><span class="sxs-lookup"><span data-stu-id="56493-104">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="56493-105">*Projektowanie modelu domeny dla każdego mikrousługi lub kontekstu ograniczone, odzwierciedlający wiedzę na temat domeny biznesowych.*</span><span class="sxs-lookup"><span data-stu-id="56493-105">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="56493-106">Ta sekcja dotyczy przede wszystkim bardziej zaawansowanych mikrousług, który implementuje gdy zachodzi potrzeba rozwiązania złożonych podsystemów lub mikrousług pochodzące z wiedzy ekspertów domeny kiedykolwiek zmiana reguł biznesowych.</span><span class="sxs-lookup"><span data-stu-id="56493-106">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="56493-107">Wzorce architektura używana w tej sekcji są oparte na projektowanie oparte na domenie (DDD) i podejścia poleceń i zapytań podział odpowiedzialności (CQRS), zgodnie z opisami w rysunek 9-1.</span><span class="sxs-lookup"><span data-stu-id="56493-107">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="56493-108">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="56493-108">**Figure 9-1**.</span></span> <span data-ttu-id="56493-109">Architektury mikrousługi zewnętrznego i wewnętrznej architektury wzorce dla każdego mikrousługi</span><span class="sxs-lookup"><span data-stu-id="56493-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="56493-110">Jednak większość techniki mikrousług, takich jak implementacji usługi interfejsu API platformy ASP.NET Core sieci Web lub uwidaczniać metadane programu Swagger z Swashbuckle, opartych na danych mają również zastosowanie do bardziej zaawansowanych mikrousług, wewnętrznie zaimplementowany przy użyciu DDD wzorce.</span><span class="sxs-lookup"><span data-stu-id="56493-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="56493-111">W tej sekcji jest rozszerzeniem poprzednich sekcjach, ponieważ większość rozwiązań opisem również zastosowanie w tym miejscu lub dla dowolnego rodzaju mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="56493-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="56493-112">Ta sekcja zawiera szczegółowe najpierw, uproszczone wzorce CQRS używane w aplikacji eShopOnContainers odwołania.</span><span class="sxs-lookup"><span data-stu-id="56493-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="56493-113">Później otrzymasz Omówienie techniki DDD, które umożliwiają znaleźć typowe wzorce, które można wykorzystać w aplikacjach użytkownika.</span><span class="sxs-lookup"><span data-stu-id="56493-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="56493-114">DDD jest duża tematu z bogaty zestaw zasoby szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="56493-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="56493-115">Można uruchomić z książek, takich jak [projekt Domain-Driven](https://domainlanguage.com/ddd/) Evans marek i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson małych Gregowi, Udi Dahan, Jimmy Bogard i wiele innych ekspertów DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="56493-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="56493-116">Jednak w większości wszystkie muszą próby Dowiedz się, jak zastosować techniki DDD z konwersacji, whiteboarding i domeny sesji modelowania z ekspertami w domenie konkretnych biznesowych.</span><span class="sxs-lookup"><span data-stu-id="56493-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="56493-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="56493-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="56493-118">DDD (oparte na domenie projekt)</span><span class="sxs-lookup"><span data-stu-id="56493-118">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="56493-119">**Evans marek. Język domeny**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="56493-119">**Eric Evans. Domain Language**
[*http://domainlanguage.com/*](http://domainlanguage.com/)</span></span>

-   <span data-ttu-id="56493-120">**Pole Fowler. Domeny oparte na projekt**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="56493-120">**Martin Fowler. Domain-Driven Design**
[*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="56493-121">**Jimmy Bogard. Wzmocnienie domenę: Elementarz**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="56493-121">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="56493-122">DDD książek</span><span class="sxs-lookup"><span data-stu-id="56493-122">DDD books</span></span>

-   <span data-ttu-id="56493-123">**Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="56493-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="56493-124">**Evans marek. Odwołania projektu oparte na domenie: Definicje i wzorzec podsumowania**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="56493-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="56493-125">**Vaughn Vernon. Implementowanie projektu oparte na domenie**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="56493-125">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="56493-126">**Vaughn Vernon. Domeny oparte na projekt destylowanej**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="56493-126">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="56493-127">**Jimmy Nilsson. Projektowanie oparte na domenie i wzorce**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="56493-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="56493-128">**Torre de la Cesarowi. W Przewodniku dotyczącym architektury N-warstwowych zorientowane na domenie z platformą .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="56493-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="56493-129">**Avram abela i Floyd Marinescu. Domeny oparte na projekt szybko**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="56493-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="56493-130">Szkolenie DDD</span><span class="sxs-lookup"><span data-stu-id="56493-130">DDD training</span></span>

-   <span data-ttu-id="56493-131">**Julie Lerman i Steve Smith. Podstawowe informacje na temat projektowania sterowanych domeny**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="56493-131">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="56493-132">[Poprzednie] (.. / multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [dalej] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="56493-132">[Previous] (../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
