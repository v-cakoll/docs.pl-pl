---
title: Rozwiązywanie problemów ze złożonościami biznesowymi w mikrousłudze z wzorcami DDD i CQRS
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Dowiedz się, jak radzić sobie ze złożonymi scenariuszami biznesowymi stosującymi wzorce DDD i CQRS
ms.date: 10/08/2018
ms.openlocfilehash: 88b105b68307c8587f877bb9ddf370e143d8539b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73739830"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="74ed8-103">Zajmij się złożonością biznesową w mikrousługach dzięki wzorcom DDD i CQRS</span><span class="sxs-lookup"><span data-stu-id="74ed8-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="74ed8-104">*Zaprojektuj model domeny dla każdej mikrousługi lub ograniczonego kontekstu, który odzwierciedla zrozumienie domeny biznesowej.*</span><span class="sxs-lookup"><span data-stu-id="74ed8-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="74ed8-105">W tej sekcji koncentruje się na bardziej zaawansowanych mikrousług, które implementują, gdy trzeba rozwiązać złożonych podsystemów lub mikrousług pochodzących z wiedzy ekspertów domeny z reguł biznesowych ciągle zmieniających się.</span><span class="sxs-lookup"><span data-stu-id="74ed8-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="74ed8-106">Wzorce architektury używane w tej sekcji są oparte na projektach opartych na domenie (DDD) i podejściach do segregacji odpowiedzialności za polecenia i zapytania (CQRS), jak pokazano na rysunku 7-1.</span><span class="sxs-lookup"><span data-stu-id="74ed8-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagram porównujący wzorce architektury zewnętrznej i wewnętrznej.":::
<span data-ttu-id="74ed8-108">Różnica między architekturą zewnętrzną: wzorce mikrousług, bramy interfejsu API, odporna komunikacja, pub/sub itp., a architektura wewnętrzna: oparte na danych/CRUD, wzorce DDD, wstrzykiwanie zależności, wiele bibliotek itp.</span><span class="sxs-lookup"><span data-stu-id="74ed8-108">Difference between external architecture: microservice patterns, API gateways, resilient communications, pub/sub, etc., and internal architecture: data driven/CRUD, DDD patterns, dependency injection, multiple libraries, etc.</span></span>
:::image-end:::

<span data-ttu-id="74ed8-109">**Rysunek 7-1**.</span><span class="sxs-lookup"><span data-stu-id="74ed8-109">**Figure 7-1**.</span></span> <span data-ttu-id="74ed8-110">Zewnętrzna architektura mikrousług a wzorce architektury wewnętrznej dla każdej mikrousługi</span><span class="sxs-lookup"><span data-stu-id="74ed8-110">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="74ed8-111">Jednak większość technik mikrousług opartych na danych, takich jak sposób implementowania usługi ASP.NET Core Web API lub jak udostępnić metadane Swagger z Swashbuckle lub NSwag, mają również zastosowanie do bardziej zaawansowanych mikrousług zaimplementowanych wewnętrznie z wzorce DDD.</span><span class="sxs-lookup"><span data-stu-id="74ed8-111">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="74ed8-112">Ta sekcja jest rozszerzeniem poprzednich sekcji, ponieważ większość praktyk wyjaśnionych wcześniej stosuje się również w tym miejscu lub dla wszelkiego rodzaju mikrousług.</span><span class="sxs-lookup"><span data-stu-id="74ed8-112">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="74ed8-113">Ta sekcja najpierw zawiera szczegółowe informacje na temat uproszczonych wzorców CQRS używanych w aplikacji referencyjnej eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="74ed8-113">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="74ed8-114">Później otrzymasz przegląd technik DDD, które umożliwiają znalezienie typowych wzorców, które można ponownie użyć w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="74ed8-114">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="74ed8-115">DDD to duży temat z bogatym zestawem zasobów do nauki.</span><span class="sxs-lookup"><span data-stu-id="74ed8-115">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="74ed8-116">Możesz zacząć od książek, takich jak [Domain-Driven Design](https://domainlanguage.com/ddd/) Eric A enas Evans i dodatkowych materiałów z Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, i wielu innych ekspertów DDD / CQRS.</span><span class="sxs-lookup"><span data-stu-id="74ed8-116">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="74ed8-117">Ale przede wszystkim musisz spróbować dowiedzieć się, jak stosować techniki DDD z konwersacji, whiteboardingi i sesji modelowania domen z ekspertami w konkretnej domenie biznesowej.</span><span class="sxs-lookup"><span data-stu-id="74ed8-117">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="74ed8-118">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="74ed8-118">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="74ed8-119">DDD (projekt oparty na domenie)</span><span class="sxs-lookup"><span data-stu-id="74ed8-119">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="74ed8-120">**Eric Evans. Język domeny** </span><span class="sxs-lookup"><span data-stu-id="74ed8-120">**Eric Evans. Domain Language** </span></span>\
  <https://domainlanguage.com/>

- <span data-ttu-id="74ed8-121">**Martin Fowler. Projekt oparty na domenie** </span><span class="sxs-lookup"><span data-stu-id="74ed8-121">**Martin Fowler. Domain-Driven Design** </span></span>\
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="74ed8-122">**Jimmy Bogard. Wzmocnienie domeny: podkład** </span><span class="sxs-lookup"><span data-stu-id="74ed8-122">**Jimmy Bogard. Strengthening your domain: a primer** </span></span>\
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="74ed8-123">Książki DDD</span><span class="sxs-lookup"><span data-stu-id="74ed8-123">DDD books</span></span>

- <span data-ttu-id="74ed8-124">**Eric Evans. Projektowanie oparte na domenie: walka ze złożonością w sercu oprogramowania** </span><span class="sxs-lookup"><span data-stu-id="74ed8-124">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="74ed8-125">**Eric Evans. Odwołanie do projektu opartena na domenie: definicje i podsumowania wzorców** </span><span class="sxs-lookup"><span data-stu-id="74ed8-125">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="74ed8-126">**Vaughn Vernon. Wdrażanie projektu opartego na domenie** </span><span class="sxs-lookup"><span data-stu-id="74ed8-126">**Vaughn Vernon. Implementing Domain-Driven Design** </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="74ed8-127">**Vaughn Vernon. Projekt oparty na domenie destylowany** </span><span class="sxs-lookup"><span data-stu-id="74ed8-127">**Vaughn Vernon. Domain-Driven Design Distilled** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="74ed8-128">**Jimmy Nilsson. Stosowanie projektu i wzorców opartych na domenie** </span><span class="sxs-lookup"><span data-stu-id="74ed8-128">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** </span></span>\
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="74ed8-129">**Cesar de la Torre. Wielowarstwowy przewodnik architektury zorientowanej na domenę z platformą .NET** </span><span class="sxs-lookup"><span data-stu-id="74ed8-129">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** </span></span>\
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="74ed8-130">**Abel Avram i Floyd Marinescu. Szybki projekt oparty na domenie** </span><span class="sxs-lookup"><span data-stu-id="74ed8-130">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="74ed8-131">**Scott Millett, Nick Tune - Wzorce, zasady i praktyki projektowania opartego na domenie** </span><span class="sxs-lookup"><span data-stu-id="74ed8-131">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** </span></span>\
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="74ed8-132">Szkolenie DDD</span><span class="sxs-lookup"><span data-stu-id="74ed8-132">DDD training</span></span>

- <span data-ttu-id="74ed8-133">**Julie Lerman i Steve Smith. Podstawy projektu oparte na domenie** </span><span class="sxs-lookup"><span data-stu-id="74ed8-133">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** </span></span>\
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="74ed8-134">[Poprzedni](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[następny](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="74ed8-134">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
