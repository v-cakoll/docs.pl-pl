---
title: Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD
description: 'Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, jak analizować złożone scenariusze zastosowania wzorców CQRS i DDD'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="d9419-103">Złożoność firm czoła w Mikrousługach przy użyciu wzorców CQRS i DDD</span><span class="sxs-lookup"><span data-stu-id="d9419-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="d9419-104">*Projektowanie modelu domeny dla poszczególnych mikrousług lub ograniczony kontekst odzwierciedlającą znajomości domeny biznesowej.*</span><span class="sxs-lookup"><span data-stu-id="d9419-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="d9419-105">Ta sekcja koncentruje się na bardziej zaawansowanych mikrousług, który implementuje, gdy trzeba czoła złożonych podsystemów lub mikrousług pochodzące z wiedzy i ekspertów z konkretnych dziedzin ciągle zmieniające reguły biznesowe.</span><span class="sxs-lookup"><span data-stu-id="d9419-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="d9419-106">Wzorce architektury używanych w tej sekcji zależą od projektowania opartego na domenach (DDD) i podejścia polecenia i podział odpowiedzialności zapytania (CQRS), jak pokazano w rysunek 7-1.</span><span class="sxs-lookup"><span data-stu-id="d9419-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![Różnica między architektury zewnętrznych: mikrousług wzorców bramy interfejsu API, odporne na błędy komunikacji, publikowania/subskrybowania, itp. i architekturę wewnętrzną: opartych na danych/CRUD wzorców DDD, wstrzykiwanie zależności, wiele bibliotek, itp.](./media/image1.png)

<span data-ttu-id="d9419-108">**Rysunek 7-1**.</span><span class="sxs-lookup"><span data-stu-id="d9419-108">**Figure 7-1**.</span></span> <span data-ttu-id="d9419-109">Opartych na architekturze mikrousług zewnętrznego i wewnętrznej architekturze wzorce dla poszczególnych mikrousług</span><span class="sxs-lookup"><span data-stu-id="d9419-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="d9419-110">Jednak większość technik dla danych opartych na mikrousługach, takie jak sposób implementacji usługi internetowego interfejsu API platformy ASP.NET Core lub jak do udostępnienia metadanych struktury Swagger przy użyciu pakietu Swashbuckle lub NSwag, mają również zastosowanie do bardziej zaawansowanych mikrousługi implementowane wewnętrznie z Wzorców DDD.</span><span class="sxs-lookup"><span data-stu-id="d9419-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="d9419-111">Ta sekcja jest rozszerzeniem przedstawione w poprzednich sekcjach, ponieważ większość rozwiązań wcześniej przedstawionych stosuje się także, w tym miejscu lub dla dowolnych mikrousług.</span><span class="sxs-lookup"><span data-stu-id="d9419-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="d9419-112">W tej sekcji najpierw zawiera szczegółowe informacje dotyczące uproszczonego wzorców CQRS używanych w ramach aplikacji eShopOnContainers aplikacji odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d9419-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="d9419-113">Później otrzymasz Przegląd techniki DDD, umożliwiających wyszukiwanie typowych wzorców, które można użyć ponownie w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d9419-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="d9419-114">DDD to duże temat bogaty zestaw zasoby szkoleniowe.</span><span class="sxs-lookup"><span data-stu-id="d9419-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="d9419-115">Można uruchomić z książek, takich jak [projektowania driven](https://domainlanguage.com/ddd/) Eric Evans i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard oraz inni eksperci DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="d9419-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="d9419-116">Ale w większości wszystkie próby Dowiedz się, jak zastosować techniki DDD z konwersacji, pracę na tablicach i sesji modelowania z ekspertami w domenie firmy konkretnych domeny.</span><span class="sxs-lookup"><span data-stu-id="d9419-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="d9419-117">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="d9419-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="d9419-118">DDD (projektowania opartego na domenie)</span><span class="sxs-lookup"><span data-stu-id="d9419-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="d9419-119">**Eric Evans. Język domeny** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-119">**Eric Evans. Domain Language** \\</span></span>
  [https://domainlanguage.com/](https://domainlanguage.com/)

- <span data-ttu-id="d9419-120">**Martin Fowler. Projektowania opartego na domenie** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-120">**Martin Fowler. Domain-Driven Design** \\</span></span>
  [https://martinfowler.com/tags/domain%20driven%20design.html](https://martinfowler.com/tags/domain%20driven%20design.html)

- <span data-ttu-id="d9419-121">**Jimmy Bogard. Wzmocnienie domenę: podstawowe informacje** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-121">**Jimmy Bogard. Strengthening your domain: a primer** \\</span></span>
  [https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a><span data-ttu-id="d9419-122">Książki DDD</span><span class="sxs-lookup"><span data-stu-id="d9419-122">DDD books</span></span>

- <span data-ttu-id="d9419-123">**Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

- <span data-ttu-id="d9419-124">**Eric Evans. Informacje dotyczące projektowania opartego na domenie: Definicje i wzorzec podsumowania** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

- <span data-ttu-id="d9419-125">**Vaughn Vernon. Implementowanie projektu opartego na domenach** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-125">**Vaughn Vernon. Implementing Domain-Driven Design** \\</span></span>
  [https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

- <span data-ttu-id="d9419-126">**Vaughn Vernon. Projektowania opartego na domenie, destylowany** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-126">**Vaughn Vernon. Domain-Driven Design Distilled** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

- <span data-ttu-id="d9419-127">**Jimmy Nilsson. Stosowanie projektowania opartego na domenie i wzorców** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** \\</span></span>
  [https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

- <span data-ttu-id="d9419-128">**Torre'a de la Cesarowi. Przewodnik N-warstwowe dotycząca architektury zorientowanej na domeny przy użyciu platformy .NET** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** \\</span></span>
  [https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

- <span data-ttu-id="d9419-129">**Abel Avram i Floyd Marinescu. Domain-Driven projektowania szybko** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** \\</span></span>
  [https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

- <span data-ttu-id="d9419-130">**Scott Millett, Dostosuj Nick — wzorce, zasady i praktyki projektowania opartego na domenie** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \\</span></span>
  [http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html](http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html)

##### <a name="ddd-training"></a><span data-ttu-id="d9419-131">Szkolenie DDD</span><span class="sxs-lookup"><span data-stu-id="d9419-131">DDD training</span></span>

- <span data-ttu-id="d9419-132">**Julie Lerman i Steve Smith. Podstawowe informacje dotyczące projektowania opartego na domenie** \\</span><span class="sxs-lookup"><span data-stu-id="d9419-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** \\</span></span>
  [https://bit.ly/PS-DDD](https://bit.ly/PS-DDD)

>[!div class="step-by-step"]
><span data-ttu-id="d9419-133">[Poprzednie](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[dalej](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="d9419-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>