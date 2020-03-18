---
title: Architektura logiczna a architektura fizyczna
description: Zrozumienie różnic między architektury logicznej i fizycznej.
ms.date: 09/20/2018
ms.openlocfilehash: 8d1bfca190eb9b18d46625fa4afdec963eb07054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834402"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Architektura logiczna a architektura fizyczna

Jest to przydatne w tym momencie, aby zatrzymać i omówić rozróżnienie między architektury logicznej i architektury fizycznej i jak to dotyczy projektowania aplikacji opartych na mikrousługach.

Aby rozpocząć tworzenie mikrousług nie wymaga użycia żadnej określonej technologii. Na przykład kontenery platformy Docker nie są obowiązkowe, aby utworzyć architekturę opartą na mikrousługach. Te mikrousługi mogą być również uruchamiane jako zwykłe procesy. Mikrousługi to architektura logiczna.

Ponadto nawet wtedy, gdy mikrousługi mogą być fizycznie zaimplementowane jako pojedynczej usługi, procesu lub kontenera (dla uproszczenia, to podejście podjęte w początkowej wersji [eShopOnContainers),](https://aka.ms/MicroservicesArchitecture)ta parzystość między mikrousług biznesowych i usługi fizycznej lub kontenera nie musi być wymagane we wszystkich przypadkach podczas tworzenia dużych i złożonych aplikacji składa się z wielu dziesiątek lub nawet setek usług.

W tym miejscu istnieje różnica między architekturą logiczną aplikacji a architekturą fizyczną. Architektura logiczna i logiczne granice systemu niekoniecznie mapują jeden do jednego na architekturę fizyczną lub wdrożeniową. Może się zdarzyć, ale często tak nie jest.

Chociaż być może zidentyfikowano niektóre mikrousługi biznesowe lub ograniczone konteksty, nie oznacza to, że najlepszym sposobem ich zaimplementowania jest zawsze utworzenie pojedynczej usługi (na przykład ASP.NET internetowego interfejsu API) lub pojedynczego kontenera platformy Docker dla każdej mikrousługi biznesowej. Posiadanie reguły mówiąc, że każda mikrousługa biznesowa musi zostać zaimplementowana przy użyciu pojedynczej usługi lub kontenera jest zbyt sztywne.

W związku z tym mikrousługi biznesowej lub ograniczony kontekst jest logiczną architekturą, która może pokrywać się (lub nie) z architekturą fizyczną. Ważną kwestią jest to, że mikrousługi biznesowej lub ograniczony kontekst musi być autonomiczny, umożliwiając kod i stan, które mają być niezależnie wersjonowane, wdrożone i skalowane.

Jak pokazano na rysunku 4-8, mikrousługi biznesowe katalogu może składać się z kilku usług lub procesów. Mogą to być wiele ASP.NET usług interfejsu API sieci Web lub innych usług korzystających z protokołu HTTP lub dowolnego innego protokołu. Co ważniejsze, usługi mogą udostępniać te same dane, o ile usługi te są zgodne w odniesieniu do tej samej domeny biznesowej.

![Diagram mikrousługi biznesowej katalogu z serwerami fizycznymi.](./media/logical-versus-physical-architecture/multiple-physical-services.png)

**Rysunek 4-8**. Mikrousługi biznesowe z kilkoma usługami fizycznymi

Usługi w przykładzie współużytkują ten sam model danych, ponieważ usługa interfejsu API sieci Web jest przeznaczona dla tych samych danych co usługa wyszukiwania. W fizycznym implementacji mikrousługi biznesowej dzielisz tę funkcję, dzięki czemu można skalować każdą z tych usług wewnętrznych w górę lub w dół w razie potrzeby. Być może usługa interfejsu API sieci Web zwykle wymaga więcej wystąpień niż usługa wyszukiwania lub odwrotnie.

Krótko mówiąc, logiczna architektura mikrousług nie zawsze musi pokrywać się z architekturą wdrażania fizycznego. W tym przewodniku, gdy wspominamy o mikrousługi, mamy na myśli mikrousługi biznesowe lub logiczne, które można mapować do jednego lub więcej usług (fizycznych). W większości przypadków będzie to pojedyncza usługa, ale może być więcej.

>[!div class="step-by-step"]
>[Poprzedni](data-sovereignty-per-microservice.md)
>[następny](distributed-data-management.md)
