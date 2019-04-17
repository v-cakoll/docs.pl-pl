---
title: Rozwiązywanie problemów ze złożonościami biznesowymi w mikrousłudze z wzorcami DDD i CQRS
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Dowiedz się, jak analizować złożone scenariusze zastosowania wzorców CQRS i DDD
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: f17acd6765de96bf8cec28c4e212733822fa0b73
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611110"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Złożoność firm czoła w Mikrousługach przy użyciu wzorców CQRS i DDD

*Projektowanie modelu domeny dla poszczególnych mikrousług lub ograniczony kontekst odzwierciedlającą znajomości domeny biznesowej.*

Ta sekcja koncentruje się na bardziej zaawansowanych mikrousług, który implementuje, gdy trzeba czoła złożonych podsystemów lub mikrousług pochodzące z wiedzy i ekspertów z konkretnych dziedzin ciągle zmieniające reguły biznesowe. Wzorce architektury używanych w tej sekcji zależą od projektowania opartego na domenach (DDD) i podejścia polecenia i podział odpowiedzialności zapytania (CQRS), jak pokazano w rysunek 7-1.

![Różnica między architektury zewnętrznych: mikrousług wzorców bramy interfejsu API, odporne na błędy komunikacji, publikowania/subskrybowania, itp. i architekturę wewnętrzną: opartych na danych/CRUD wzorców DDD, wstrzykiwanie zależności, wiele bibliotek, itp.](./media/image1.png)

**Rysunek 7-1**. Opartych na architekturze mikrousług zewnętrznego i wewnętrznej architekturze wzorce dla poszczególnych mikrousług

Jednak większość technik dla danych opartych na mikrousługach, takie jak sposób implementacji usługi internetowego interfejsu API platformy ASP.NET Core lub jak do udostępnienia metadanych struktury Swagger przy użyciu pakietu Swashbuckle lub NSwag, mają również zastosowanie do bardziej zaawansowanych mikrousługi implementowane wewnętrznie z Wzorców DDD. Ta sekcja jest rozszerzeniem przedstawione w poprzednich sekcjach, ponieważ większość rozwiązań wcześniej przedstawionych stosuje się także, w tym miejscu lub dla dowolnych mikrousług.

W tej sekcji najpierw zawiera szczegółowe informacje dotyczące uproszczonego wzorców CQRS używanych w ramach aplikacji eShopOnContainers aplikacji odwołanie. Później otrzymasz Przegląd techniki DDD, umożliwiających wyszukiwanie typowych wzorców, które można użyć ponownie w swoich aplikacjach.

DDD to duże temat bogaty zestaw zasoby szkoleniowe. Można uruchomić z książek, takich jak [projektowania driven](https://domainlanguage.com/ddd/) Eric Evans i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard oraz inni eksperci DDD/CQRS. Ale w większości wszystkie próby Dowiedz się, jak zastosować techniki DDD z konwersacji, pracę na tablicach i sesji modelowania z ekspertami w domenie firmy konkretnych domeny.

#### <a name="additional-resources"></a>Dodatkowe zasoby

##### <a name="ddd-domain-driven-design"></a>DDD (projektowania opartego na domenie)

- **Eric Evans. Język domeny** \
  <https://domainlanguage.com/>

- **Martin Fowler. Projektowania opartego na domenie** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Wzmocnienie domenę: podstawowe informacje** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>Książki DDD

- **Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Informacje dotyczące projektowania opartego na domenie: Definicje i wzorzec podsumowania** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Implementowanie projektu opartego na domenach** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Projektowania opartego na domenie, destylowany** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Stosowanie projektowania opartego na domenie i wzorców** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Torre'a de la Cesarowi. Przewodnik N-warstwowe dotycząca architektury zorientowanej na domeny przy użyciu platformy .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram i Floyd Marinescu. Domain-Driven projektowania szybko** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Dostosuj Nick — wzorce, zasady i praktyki projektowania opartego na domenie** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>Szkolenie DDD

- **Julie Lerman i Steve Smith. Podstawowe informacje dotyczące projektowania opartego na domenie** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Poprzednie](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[dalej](apply-simplified-microservice-cqrs-ddd-patterns.md)
