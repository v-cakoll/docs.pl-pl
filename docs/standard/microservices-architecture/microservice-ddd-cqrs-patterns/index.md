---
title: Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 1af53f8f37e516219767fdde49eb7da9927d9e29
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182466"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Co dzień do czynienia złożoności biznesowych w Mikrousługach przy użyciu wzorców CQRS i DDD

*Projektowanie modelu domeny dla poszczególnych mikrousług lub ograniczony kontekst odzwierciedlającą znajomości domeny biznesowej.*

Ta sekcja koncentruje się na bardziej zaawansowanych mikrousług, który implementuje, gdy trzeba czoła złożonych podsystemów lub mikrousług pochodzące z wiedzy i ekspertów z konkretnych dziedzin ciągle zmieniające reguły biznesowe. Wzorce architektury używanych w tej sekcji zależą od projektowania opartego na domenach (DDD) i podejścia polecenia i podział odpowiedzialności zapytania (CQRS), jak pokazano w rysunek 9-1.

![](./media/image1.png)

**Rysunek 9-1**. Opartych na architekturze mikrousług zewnętrznego i wewnętrznej architekturze wzorce dla poszczególnych mikrousług

Jednak większość technik dla danych opartych na mikrousługach, takie jak sposób implementacji usługi internetowego interfejsu API platformy ASP.NET Core lub jak do udostępnienia metadanych struktury Swagger przy użyciu pakietu Swashbuckle, mają również zastosowanie do bardziej zaawansowanych mikrousługi implementowane wewnętrznie z DDD wzorce. Ta sekcja jest rozszerzeniem przedstawione w poprzednich sekcjach, ponieważ większość rozwiązań wcześniej przedstawionych stosuje się także, w tym miejscu lub dla dowolnych mikrousług.

W tej sekcji najpierw zawiera szczegółowe informacje dotyczące uproszczonego wzorców CQRS używanych w ramach aplikacji eShopOnContainers aplikacji odwołanie. Później otrzymasz Przegląd techniki DDD, umożliwiających wyszukiwanie typowych wzorców, które można użyć ponownie w swoich aplikacjach.

DDD to duże temat bogaty zestaw zasoby szkoleniowe. Można uruchomić z książek, takich jak [projektowania driven](https://domainlanguage.com/ddd/) Eric Evans i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard oraz inni eksperci DDD/CQRS. Ale w większości wszystkie próby Dowiedz się, jak zastosować techniki DDD z konwersacji, pracę na tablicach i sesji modelowania z ekspertami w domenie firmy konkretnych domeny.

#### <a name="additional-resources"></a>Dodatkowe zasoby

##### <a name="ddd-domain-driven-design"></a>DDD (projektowania opartego na domenie)

-   **Eric Evans. Język domeny**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)

-   **Martina Fowlera. Projektowania opartego na domenie**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Wzmocnienie domenę: podstawowe informacje**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>Książki DDD

-   **Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Eric Evans. Dotyczące projektowania opartego na domenie: Definicje i wzorzec podsumowania**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Implementowanie projektu opartego na domenach**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Projektowania opartego na domenie, destylowany**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Stosowanie projektowania opartego na domenie i wzorców**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Torre'a de la Cesarowi. Przewodnik N-warstwowe dotycząca architektury zorientowanej na domeny przy użyciu platformy .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Abel Avram i Floyd Marinescu. Domain-Driven projektowania szybko**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

Szkolenie DDD

-   **Julie Lerman i Steve Smith. Podstawowe informacje dotyczące projektowania opartego na domenie**
    [*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Poprzednie](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[dalej](apply-simplified-microservice-cqrs-ddd-patterns.md)