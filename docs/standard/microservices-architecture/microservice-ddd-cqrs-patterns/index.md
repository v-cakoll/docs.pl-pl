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
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Poruszając złożoności firm Mikrousługi DDD i wzorce CQRS

*Projektowanie modelu domeny dla każdego mikrousługi lub kontekstu ograniczone, odzwierciedlający wiedzę na temat domeny biznesowych.*

Ta sekcja dotyczy przede wszystkim bardziej zaawansowanych mikrousług, który implementuje gdy zachodzi potrzeba rozwiązania złożonych podsystemów lub mikrousług pochodzące z wiedzy ekspertów domeny kiedykolwiek zmiana reguł biznesowych. Wzorce architektura używana w tej sekcji są oparte na projektowanie oparte na domenie (DDD) i podejścia poleceń i zapytań podział odpowiedzialności (CQRS), zgodnie z opisami w rysunek 9-1.

![](./media/image1.png)

**Rysunek 9-1**. Architektury mikrousługi zewnętrznego i wewnętrznej architektury wzorce dla każdego mikrousługi

Jednak większość techniki mikrousług, takich jak implementacji usługi interfejsu API platformy ASP.NET Core sieci Web lub uwidaczniać metadane programu Swagger z Swashbuckle, opartych na danych mają również zastosowanie do bardziej zaawansowanych mikrousług, wewnętrznie zaimplementowany przy użyciu DDD wzorce. W tej sekcji jest rozszerzeniem poprzednich sekcjach, ponieważ większość rozwiązań opisem również zastosowanie w tym miejscu lub dla dowolnego rodzaju mikrousługi.

Ta sekcja zawiera szczegółowe najpierw, uproszczone wzorce CQRS używane w aplikacji eShopOnContainers odwołania. Później otrzymasz Omówienie techniki DDD, które umożliwiają znaleźć typowe wzorce, które można wykorzystać w aplikacjach użytkownika.

DDD jest duża tematu z bogaty zestaw zasoby szkoleniowe. Można uruchomić z książek, takich jak [projekt Domain-Driven](https://domainlanguage.com/ddd/) Evans marek i dodatkowe materiały z Vaughn Vernon, Jimmy Nilsson małych Gregowi, Udi Dahan, Jimmy Bogard i wiele innych ekspertów DDD/CQRS. Jednak w większości wszystkie muszą próby Dowiedz się, jak zastosować techniki DDD z konwersacji, whiteboarding i domeny sesji modelowania z ekspertami w domenie konkretnych biznesowych.

#### <a name="additional-resources"></a>Dodatkowe zasoby

##### <a name="ddd-domain-driven-design"></a>DDD (oparte na domenie projekt)

-   **Evans marek. Język domeny**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)

-   **Pole Fowler. Domeny oparte na projekt**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Wzmocnienie domenę: Elementarz**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>DDD książek

-   **Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Evans marek. Odwołania projektu oparte na domenie: Definicje i wzorzec podsumowania**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Implementowanie projektu oparte na domenie**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Domeny oparte na projekt destylowanej**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Projektowanie oparte na domenie i wzorce**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Torre de la Cesarowi. W Przewodniku dotyczącym architektury N-warstwowych zorientowane na domenie z platformą .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Avram abela i Floyd Marinescu. Domeny oparte na projekt szybko**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

Szkolenie DDD

-   **Julie Lerman i Steve Smith. Podstawowe informacje na temat projektowania sterowanych domeny**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Poprzednie] (.. / multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [dalej] (apply-simplified-microservice-cqrs-ddd-patterns.md)
