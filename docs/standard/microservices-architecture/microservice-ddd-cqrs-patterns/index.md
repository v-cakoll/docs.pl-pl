---
title: Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: af67f94b2c56f6a1ec794abbf7d3dad0d78033ec
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105761"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="341af-103">Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS</span><span class="sxs-lookup"><span data-stu-id="341af-103">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="341af-104">*Projektowanie modelu domeny dla każdego mikrousługi lub kontekstu ograniczone, odzwierciedlający wiedzę na temat domeny biznesowych.*</span><span class="sxs-lookup"><span data-stu-id="341af-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="341af-105">Ta sekcja dotyczy przede wszystkim bardziej zaawansowanych mikrousług, który implementuje gdy zachodzi potrzeba rozwiązania złożonych podsystemów lub mikrousług pochodzące z wiedzy ekspertów domeny kiedykolwiek zmiana reguł biznesowych.</span><span class="sxs-lookup"><span data-stu-id="341af-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="341af-106">Wzorce architektura używana w tej sekcji są oparte na projektowanie oparte na domenie (DDD) i podejścia poleceń i zapytań podział odpowiedzialności (CQRS), zgodnie z opisami w rysunek 9-1.</span><span class="sxs-lookup"><span data-stu-id="341af-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="341af-107">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="341af-107">**Figure 9-1**.</span></span> <span data-ttu-id="341af-108">Architektury mikrousługi zewnętrznego i wewnętrznej architektury wzorce dla każdego mikrousługi</span><span class="sxs-lookup"><span data-stu-id="341af-108">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="341af-109">Jednak większość techniki mikrousług, takich jak implementacji usługi interfejsu API platformy ASP.NET Core sieci Web lub uwidaczniać metadane programu Swagger z Swashbuckle, opartych na danych mają również zastosowanie do bardziej zaawansowanych mikrousług, wewnętrznie zaimplementowany przy użyciu DDD wzorce.</span><span class="sxs-lookup"><span data-stu-id="341af-109">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="341af-110">W tej sekcji jest rozszerzeniem poprzednich sekcjach, ponieważ większość rozwiązań opisem również zastosowanie w tym miejscu lub dla dowolnego rodzaju mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="341af-110">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="341af-111">Ta sekcja zawiera szczegółowe najpierw, uproszczone wzorce CQRS używane w aplikacji eShopOnContainers odwołania.</span><span class="sxs-lookup"><span data-stu-id="341af-111">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="341af-112">Później otrzymasz Omówienie techniki DDD, które umożliwiają znaleźć typowe wzorce, które można wykorzystać w aplikacjach użytkownika.</span><span class="sxs-lookup"><span data-stu-id="341af-112">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="341af-113">DDD jest duża tematu z bogaty zestaw zasoby szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="341af-113">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="341af-114">Można uruchomić z książek, takich jak [projekt Domain-Driven](https://domainlanguage.com/ddd/) Evans marek i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson małych Gregowi, Udi Dahan, Jimmy Bogard i wiele innych ekspertów DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="341af-114">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="341af-115">Jednak w większości wszystkie muszą próby Dowiedz się, jak zastosować techniki DDD z konwersacji, whiteboarding i domeny sesji modelowania z ekspertami w domenie konkretnych biznesowych.</span><span class="sxs-lookup"><span data-stu-id="341af-115">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="341af-116">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="341af-116">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="341af-117">DDD (oparte na domenie projekt)</span><span class="sxs-lookup"><span data-stu-id="341af-117">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="341af-118">**Evans marek. Język domeny**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="341af-118">**Eric Evans. Domain Language**
[*https://domainlanguage.com/*](https://domainlanguage.com/)</span></span>

-   <span data-ttu-id="341af-119">**Pole Fowler. Projektowanie oparte na domenie**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="341af-119">**Martin Fowler. Domain-Driven Design**
[*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="341af-120">**Jimmy Bogard. Wzmocnienie domenę: Elementarz**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="341af-120">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="341af-121">DDD książek</span><span class="sxs-lookup"><span data-stu-id="341af-121">DDD books</span></span>

-   <span data-ttu-id="341af-122">**Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="341af-122">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="341af-123">**Evans marek. Odwołania projektu oparte na domenie: Definicje i wzorzec podsumowania**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="341af-123">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="341af-124">**Vaughn Vernon. Implementowanie projektu oparte na domenie**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="341af-124">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="341af-125">**Vaughn Vernon. Projektowanie oparte na domenie destylowany**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="341af-125">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="341af-126">**Jimmy Nilsson. Projektowanie oparte na domenie i wzorce**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="341af-126">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="341af-127">**Torre de la Cesarowi. W Przewodniku dotyczącym architektury N-warstwowych zorientowane na domenie z platformą .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="341af-127">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="341af-128">**Avram abela i Floyd Marinescu. Domeny oparte na projekt szybko**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="341af-128">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="341af-129">Szkolenie DDD</span><span class="sxs-lookup"><span data-stu-id="341af-129">DDD training</span></span>

-   <span data-ttu-id="341af-130">**Julie Lerman i Steve Smith. Podstawowe informacje na temat projektowania oparte na domenie**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="341af-130">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="341af-131">[Poprzednie](../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)
[dalej](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="341af-131">[Previous](../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
