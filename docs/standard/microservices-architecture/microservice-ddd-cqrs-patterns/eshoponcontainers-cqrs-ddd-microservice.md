---
title: Stosowanie CQRS i CQS podejścia w mikrousługi DDD, w eShopOnContainers
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Stosowanie CQRS i CQS podejścia w mikrousługi DDD, w eShopOnContainers
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: fdca8d38157d5c5b62bd077e5d715ca22ac9780f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106752"
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Stosowanie CQRS i CQS podejścia w mikrousługi DDD, w eShopOnContainers

Projekt porządkowania mikrousługi na eShopOnContainers aplikacja referencyjna jest oparta na zasadach CQRS. Jednak używa najprostsza metoda po prostu oddzielanie zapytania z poleceniami i dla obu czynności przy użyciu tej samej bazy danych.

Jest użycia tych wzorców i należy koniecznie zwrócić uwagę, że zapytania są idempotentności: niezależnie od tego, ile razy kwerendy systemu, nie spowoduje zmiany stanu tego systemu. Nawet można użyć modelu danych różnych "odczytów" niż model domeny logiki transakcyjnej "zapisuje", mimo że porządkowania mikrousług używa tej samej bazy danych. Dlatego jest uproszczone podejście CQRS.

Z drugiej strony polecenia, które wyzwolić transakcji i aktualizacji danych, Zmień stan w systemie. Za pomocą polecenia, musisz należy zachować ostrożność podczas dotyczących złożoności i kiedykolwiek zmiana reguł biznesowych. Jest to, gdy chcesz zastosować DDD technik w celu lepszego modelowanego systemu.

Nie można zastosować powszechnie wzorce DDD przedstawionych w tym przewodniku. Oni wprowadzić ograniczenia dotyczące projektu. Ograniczenia te zapewniają korzyści, takich jak wyższej jakości wraz z upływem czasu, szczególnie w przypadku poleceń i innego kodu, który modyfikuje stan systemu. Jednak te ograniczenia zwiększenia złożoności z mniej korzyści za odczytywanie i wykonywanie zapytania na danych.

Jeden taki wzorzec jest wzorcu agregacji więcej omówione w kolejnych sekcjach. Krótko mówiąc we wzorcu agregacji, są traktowane wiele obiektów domeny jako pojedyncza jednostka wyniku ich relacje w domenie. Nie może być zawsze uzyskać korzyści z tego wzorca w zapytaniach; może zwiększyć złożoność logiki kwerendy. Dla zapytań tylko do odczytu nie otrzymasz zalet traktowanie wielu obiektów jako pojedynczy agregacji. Tylko Pobierz złożoności.

Jak pokazano na rysunku 9-2, w tym przewodniku sugeruje przy użyciu wzorców DDD tylko w obszarze transakcyjnej/aktualizacji z mikrousługi (jak wyzwalane przez polecenia). Zapytania można wykonać prostsze i musi być oddzielona od po podejście CQRS poleceń.

Do wykonania na stronie"zapytania", można wybrać wiele metod z Twojej pełnej wersji ORM, takich jak EF Core, AutoMapper projekcje, procedur składowanych, widoków, zmaterializowanych widoków lub micro ORM.

W tym przewodniku, jak i w eShopOnContainers (w szczególności porządkowania mikrousługi) wybraliśmy do zaimplementowania prostych zapytań przy użyciu micro ORM, takie jak [Dapper](https://github.com/StackExchange/dapper-dot-net). Dzięki temu można zaimplementować wszelkie zapytania oparte na instrukcji SQL, aby uzyskać najlepszą wydajność dzięki użyciu światła framework bez nadmiernego obciążenia.

Należy zauważyć, że gdy posłuż się tą metodą, aktualizacje do modelu, które mają wpływ na sposób utrwalone jednostki bazy danych SQL również osobne aktualizacje kwerendy SQL używane przez Dapper lub wszelkie inne oddzielne podejścia (z systemem innym niż EF) do wykonywania zapytania.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Wzorce CQRS i DDD nie są architektury najwyższego poziomu

Pamiętać, że CQRS i większość wzorców DDD (na przykład warstwy DDD lub model domeny z wartości zagregowanych) czy nie architektury style, ale tylko architektura wzorce. Mikrousług, SOA i architektura sterowane zdarzeniami (EDA) to przykłady architektury stylów. Opisują one systemu z wielu składników, takich jak wiele mikrousług. Wzorce CQRS i DDD opisano coś w jednym systemie lub składnik; w tym przypadku coś wewnątrz mikrousługi.

Ograniczone kontekstów (usług łączności biznesowej) będzie stosować różnych wzorców. Mają one różne obowiązki i która prowadzi do różnych rozwiązań. Warto akcentowania który wymuszania tego samego wzorca, który wszędzie prowadzi do awarii. Nie używaj wzorce CQRS i DDD wszędzie. Wiele podsystemów, usług łączności biznesowej lub mikrousług są prostsze i można ją wdrożyć łatwiej przy użyciu usługi simple CRUD lub w inny sposób.

Istnieje tylko jedna aplikacja — architektura: Architektura aplikacji systemu lub na trasie projektowania (na przykład architektura mikrousług). Jednak projekt każdego ograniczone kontekstu lub mikrousługi tej aplikacji odzwierciedla własne wady i zalety i decyzje dotyczące projektu wewnętrznej na poziomie wzorce architektury. Nie należy zastosować te same architektury wzory CQRS lub DDD wszędzie.

####  <a name="additional-resources"></a>Dodatkowe zasoby

-   **Pole Fowler. CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Małych Gregowi. CQS vs. CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Małych Gregowi. CQRS dokumentów**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Małych Gregowi. CQRS, zadanie na podstawie UI i źródłem zdarzenia**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **Udi Dahan. Sklarowanego CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Zdarzenie Sourcing (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[Poprzednie](apply-simplified-microservice-cqrs-ddd-patterns.md)
[dalej](cqrs-microservice-reads.md)
