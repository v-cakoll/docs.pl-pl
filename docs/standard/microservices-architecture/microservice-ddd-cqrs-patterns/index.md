---
title: Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: bc8ff6262436af6eb49a4ef8635d502e80b74b5a
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874390"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="d23cd-103">Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD</span><span class="sxs-lookup"><span data-stu-id="d23cd-103">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="d23cd-104">*Projektowanie modelu domeny dla poszczególnych mikrousług lub ograniczony kontekst odzwierciedlającą znajomości domeny biznesowej.*</span><span class="sxs-lookup"><span data-stu-id="d23cd-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="d23cd-105">Ta sekcja koncentruje się na bardziej zaawansowanych mikrousług, który implementuje, gdy trzeba czoła złożonych podsystemów lub mikrousług pochodzące z wiedzy i ekspertów z konkretnych dziedzin ciągle zmieniające reguły biznesowe.</span><span class="sxs-lookup"><span data-stu-id="d23cd-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="d23cd-106">Wzorce architektury używanych w tej sekcji zależą od projektowania opartego na domenach (DDD) i podejścia polecenia i podział odpowiedzialności zapytania (CQRS), jak pokazano w rysunek 9-1.</span><span class="sxs-lookup"><span data-stu-id="d23cd-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="d23cd-107">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="d23cd-107">**Figure 9-1**.</span></span> <span data-ttu-id="d23cd-108">Opartych na architekturze mikrousług zewnętrznego i wewnętrznej architekturze wzorce dla poszczególnych mikrousług</span><span class="sxs-lookup"><span data-stu-id="d23cd-108">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="d23cd-109">Jednak większość technik dla danych opartych na mikrousługach, takie jak sposób implementacji usługi internetowego interfejsu API platformy ASP.NET Core lub jak do udostępnienia metadanych struktury Swagger przy użyciu pakietu Swashbuckle, mają również zastosowanie do bardziej zaawansowanych mikrousługi implementowane wewnętrznie z DDD wzorce.</span><span class="sxs-lookup"><span data-stu-id="d23cd-109">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="d23cd-110">Ta sekcja jest rozszerzeniem przedstawione w poprzednich sekcjach, ponieważ większość rozwiązań wcześniej przedstawionych stosuje się także, w tym miejscu lub dla dowolnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="d23cd-110">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="d23cd-111">W tej sekcji najpierw zawiera szczegółowe informacje dotyczące uproszczonego wzorców CQRS używanych w ramach aplikacji eShopOnContainers aplikacji odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d23cd-111">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="d23cd-112">Później otrzymasz Przegląd techniki DDD, umożliwiających wyszukiwanie typowych wzorców, które można użyć ponownie w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d23cd-112">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="d23cd-113">DDD to duże temat bogaty zestaw zasoby szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="d23cd-113">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="d23cd-114">Można uruchomić z książek, takich jak [projektowania driven](https://domainlanguage.com/ddd/) Eric Evans i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard oraz inni eksperci DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="d23cd-114">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="d23cd-115">Ale w większości wszystkie próby Dowiedz się, jak zastosować techniki DDD z konwersacji, pracę na tablicach i sesji modelowania z ekspertami w domenie firmy konkretnych domeny.</span><span class="sxs-lookup"><span data-stu-id="d23cd-115">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d23cd-116">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="d23cd-116">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="d23cd-117">DDD (projektowania opartego na domenie)</span><span class="sxs-lookup"><span data-stu-id="d23cd-117">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="d23cd-118">**Eric Evans. Język domeny**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-118">**Eric Evans. Domain Language**
[*https://domainlanguage.com/*](https://domainlanguage.com/)</span></span>

-   <span data-ttu-id="d23cd-119">**Martina Fowlera. Projektowania opartego na domenie**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="d23cd-119">**Martin Fowler. Domain-Driven Design**
[*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="d23cd-120">**Jimmy Bogard. Wzmocnienie domenę: podstawowe informacje**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-120">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="d23cd-121">Książki DDD</span><span class="sxs-lookup"><span data-stu-id="d23cd-121">DDD books</span></span>

-   <span data-ttu-id="d23cd-122">**Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-122">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="d23cd-123">**Eric Evans. Dotyczące projektowania opartego na domenie: Definicje i wzorzec podsumowania**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-123">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="d23cd-124">**Vaughn Vernon. Implementowanie projektu opartego na domenach**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-124">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="d23cd-125">**Vaughn Vernon. Projektowania opartego na domenie, destylowany**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-125">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="d23cd-126">**Jimmy Nilsson. Stosowanie projektowania opartego na domenie i wzorców**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-126">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="d23cd-127">**Torre'a de la Cesarowi. Przewodnik N-warstwowe dotycząca architektury zorientowanej na domeny przy użyciu platformy .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-127">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="d23cd-128">**Abel Avram i Floyd Marinescu. Domain-Driven projektowania szybko**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="d23cd-128">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="d23cd-129">Szkolenie DDD</span><span class="sxs-lookup"><span data-stu-id="d23cd-129">DDD training</span></span>

-   <span data-ttu-id="d23cd-130">**Julie Lerman i Steve Smith. Podstawowe informacje dotyczące projektowania opartego na domenie**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="d23cd-130">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d23cd-131">[Poprzednie](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[dalej](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="d23cd-131">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>