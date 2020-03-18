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
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Zajmij się złożonością biznesową w mikrousługach dzięki wzorcom DDD i CQRS

*Zaprojektuj model domeny dla każdej mikrousługi lub ograniczonego kontekstu, który odzwierciedla zrozumienie domeny biznesowej.*

W tej sekcji koncentruje się na bardziej zaawansowanych mikrousług, które implementują, gdy trzeba rozwiązać złożonych podsystemów lub mikrousług pochodzących z wiedzy ekspertów domeny z reguł biznesowych ciągle zmieniających się. Wzorce architektury używane w tej sekcji są oparte na projektach opartych na domenie (DDD) i podejściach do segregacji odpowiedzialności za polecenia i zapytania (CQRS), jak pokazano na rysunku 7-1.

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagram porównujący wzorce architektury zewnętrznej i wewnętrznej.":::
Różnica między architekturą zewnętrzną: wzorce mikrousług, bramy interfejsu API, odporna komunikacja, pub/sub itp., a architektura wewnętrzna: oparte na danych/CRUD, wzorce DDD, wstrzykiwanie zależności, wiele bibliotek itp.
:::image-end:::

**Rysunek 7-1**. Zewnętrzna architektura mikrousług a wzorce architektury wewnętrznej dla każdej mikrousługi

Jednak większość technik mikrousług opartych na danych, takich jak sposób implementowania usługi ASP.NET Core Web API lub jak udostępnić metadane Swagger z Swashbuckle lub NSwag, mają również zastosowanie do bardziej zaawansowanych mikrousług zaimplementowanych wewnętrznie z wzorce DDD. Ta sekcja jest rozszerzeniem poprzednich sekcji, ponieważ większość praktyk wyjaśnionych wcześniej stosuje się również w tym miejscu lub dla wszelkiego rodzaju mikrousług.

Ta sekcja najpierw zawiera szczegółowe informacje na temat uproszczonych wzorców CQRS używanych w aplikacji referencyjnej eShopOnContainers. Później otrzymasz przegląd technik DDD, które umożliwiają znalezienie typowych wzorców, które można ponownie użyć w aplikacjach.

DDD to duży temat z bogatym zestawem zasobów do nauki. Możesz zacząć od książek, takich jak [Domain-Driven Design](https://domainlanguage.com/ddd/) Eric A enas Evans i dodatkowych materiałów z Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, i wielu innych ekspertów DDD / CQRS. Ale przede wszystkim musisz spróbować dowiedzieć się, jak stosować techniki DDD z konwersacji, whiteboardingi i sesji modelowania domen z ekspertami w konkretnej domenie biznesowej.

#### <a name="additional-resources"></a>Zasoby dodatkowe

##### <a name="ddd-domain-driven-design"></a>DDD (projekt oparty na domenie)

- **Eric Evans. Język domeny** \
  <https://domainlanguage.com/>

- **Martin Fowler. Projekt oparty na domenie** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Wzmocnienie domeny: podkład** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>Książki DDD

- **Eric Evans. Projektowanie oparte na domenie: walka ze złożonością w sercu oprogramowania** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Odwołanie do projektu opartena na domenie: definicje i podsumowania wzorców** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Wdrażanie projektu opartego na domenie** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Projekt oparty na domenie destylowany** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Stosowanie projektu i wzorców opartych na domenie** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. Wielowarstwowy przewodnik architektury zorientowanej na domenę z platformą .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram i Floyd Marinescu. Szybki projekt oparty na domenie** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick Tune - Wzorce, zasady i praktyki projektowania opartego na domenie** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>Szkolenie DDD

- **Julie Lerman i Steve Smith. Podstawy projektu oparte na domenie** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Poprzedni](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[następny](apply-simplified-microservice-cqrs-ddd-patterns.md)
