---
title: Architektura logiczna a architektura fizyczna
description: Zapoznaj się z różnicami między architekturami logicznymi a fizycznymi.
ms.date: 09/20/2018
ms.openlocfilehash: c269369e9b5391e8d25ece46e6b08e34a82fbbba
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295494"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Architektura logiczna a architektura fizyczna

Jest to przydatne w tym momencie, aby zatrzymywać i omawiać rozróżnienie między architekturą logiczną i architekturą fizyczną oraz jak ma to zastosowanie do projektowania aplikacji opartych na mikrousługach.

Aby rozpocząć, tworzenie mikrousług nie wymaga zastosowania żadnej konkretnej technologii. Na przykład kontenery platformy Docker nie są wymagane do utworzenia architektury opartej na mikrousługach. Te mikrousługi mogą być również uruchamiane jako zwykłe procesy. Mikrousługi są architekturą logiczną.

Ponadto nawet w przypadku, gdy mikrousługa może być fizycznie zaimplementowana jako jedna usługa, proces lub kontener (w przypadku uproszczenia jest to podejście wykonywane w początkowej wersji [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), ta różnica między mikrousługą biznesową w przypadku tworzenia dużej i złożonej aplikacji składającej się z wielu dziesiątek lub nawet setek usług usługa fizyczna lub kontener nie musi być wymagana we wszystkich przypadkach.

Jest to sytuacja, w której istnieje różnica między architekturą logiczną aplikacji a architekturą fizyczną. Architektura logiczna i granice logiczne systemu nie zawsze mapują jeden do jednego na architekturę fizyczną lub rozmieszczenia. Może się tak zdarzyć, ale często nie.

Chociaż można zidentyfikować pewne mikrousługi biznesowe lub ograniczone konteksty, nie oznacza to, że najlepszym sposobem wdrożenia jest zawsze utworzenie pojedynczej usługi (takiej jak ASP.NET Web API) lub jednego kontenera Docker dla każdej mikrousługi biznesowej. Zasada mówiąca, że każda mikrousługa biznesowa musi być implementowana przy użyciu jednej usługi lub kontenera jest zbyt sztywna.

W związku z tym, mikrousługa biznesowa lub ograniczone kontekst jest architekturą logiczną, która może być zbieżna (lub nie) z architekturą fizyczną. Ważną kwestią jest to, że mikrousługa biznesowa lub ograniczone kontekst muszą być autonomiczne, umożliwiając, aby kod i stan były niezależnie w wersji, wdrożone i skalowane.

Jak pokazano na rysunku 4-8, usługa biznesowa katalogu może składać się z kilku usług lub procesów. Mogą to być wiele usług internetowego interfejsu API ASP.NET lub dowolnego innego rodzaju usług korzystających z protokołu HTTP lub dowolnego innego protokołu. Co ważniejsze, usługi mogą współużytkować te same dane, o ile te usługi są spójne w odniesieniu do tej samej domeny biznesowej.

![Diagram mikrousługi biznesowej katalogu, który zawiera usługę interfejsu API usługi wyszukiwania i bazę danych SQL Server.](./media/image8.png)

**Rysunek 4-8**. Mikrousługa biznesowa z kilkoma usługami fizycznymi

Usługi w tym przykładzie korzystają z tego samego modelu danych, ponieważ usługa interfejsu API sieci Web jest przeznaczona dla tych samych danych co usługa wyszukiwania. W związku z tym w fizycznej implementacji mikrousługi biznesowej należy podzielić tę funkcję, aby można było skalować każdą z tych wewnętrznych usług w zależności od potrzeb. Być może usługa interfejsu API sieci Web zwykle potrzebuje większej liczby wystąpień niż usługa wyszukiwania lub odwrotnie.

W skrócie logicznej architekturze mikrousług nie zawsze jest konieczna zbieżność z fizyczną architekturą wdrażania. W tym przewodniku, gdy wspominamy mikrousługi, oznacza to, że firma lub logiczna mikrousługa, która może mapować do jednej lub kilku (fizycznych) usług. W większości przypadków jest to jedna usługa, ale może być większa.

>[!div class="step-by-step"]
>[Poprzedni](data-sovereignty-per-microservice.md)Następny
>[](distributed-data-management.md)
