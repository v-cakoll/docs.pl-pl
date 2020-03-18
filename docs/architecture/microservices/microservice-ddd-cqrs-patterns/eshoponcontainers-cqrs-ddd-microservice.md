---
title: Stosowanie zasad CQRS i CQS w mikrousługach DDD w ramach aplikacji eShopOnContainers
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zrozumieć sposób CQRS jest zaimplementowana w mikrousługi zamawiania w eShopOnContainers.
ms.date: 03/03/2020
ms.openlocfilehash: 16fe46189a5b43591adebbb764d4acef2f7efbfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847157"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Stosowanie metod CQRS i CQS w mikrousługach DDD w eShopOnContainers

Projekt mikrousługi zamawiania w aplikacji referencyjnej eShopOnContainers opiera się na zasadach CQRS. Jednak używa najprostszego podejścia, który jest po prostu oddzielenie kwerend y od poleceń i przy użyciu tej samej bazy danych dla obu akcji.

Istotą tych wzorców i ważnym punktem jest to, że zapytania są idempotentne: bez względu na to, ile razy zapytań systemu, stan tego systemu nie zmieni. Innymi słowy zapytania są wolne od efektów ubocznych.

W związku z tym można użyć innego modelu danych "odczyty" niż logiki transakcyjnej "zapisuje" model domeny, mimo że mikrousług porządkowania są przy użyciu tej samej bazy danych. W związku z tym jest to uproszczone podejście CQRS.

Z drugiej strony polecenia, które wyzwalają transakcje i aktualizacje danych, zmieniają stan w systemie. Dzięki poleceń, trzeba być ostrożnym w kontaktach ze złożonością i ciągle zmieniających się reguł biznesowych. To jest, gdy chcesz zastosować techniki DDD mieć lepszy system modelowany.

Wzorce DDD przedstawione w tym przewodniku nie powinny być stosowane uniwersalnie. Wprowadzają ograniczenia w projekcie. Ograniczenia te zapewniają korzyści, takie jak wyższa jakość w czasie, szczególnie w poleceniach i innym kodzie modyfikuje stan systemu. Jednak te ograniczenia dodać złożoność z mniejszą ilością korzyści dla odczytu i wykonywania zapytań danych.

Jednym z takich wzorców jest zagregowany wzorzec, który badamy bardziej w kolejnych sekcjach. Krótko mówiąc, we wzorcu agregacji wiele obiektów domeny traktujesz jako pojedynczą jednostkę w wyniku ich relacji w domenie. Nie zawsze może uzyskać korzyści z tego wzorca w kwerendach; może zwiększyć złożoność logiki zapytania. W przypadku zapytań tylko do odczytu nie można uzyskać zalety traktowania wielu obiektów jako pojedynczej agregacji. Otrzymujesz tylko złożoność.

Jak pokazano na rysunku 7-2 w poprzedniej sekcji, ten przewodnik sugeruje przy użyciu wzorców DDD tylko w obszarze transakcyjnych/aktualizacji mikrousługi (to jest, jak wyzwalane przez polecenia). Kwerendy mogą być zgodne z prostszym podejściem i powinny być oddzielone od poleceń, zgodnie z podejściem CQRS.

W celu zaimplementowania "po stronie zapytań", można wybrać jedną z wielu metod, z pełnowartościowego ORM jak EF Core, Projekcje AutoMapper, procedury przechowywane, widoki, zmaterializowane widoki lub mikro ORM.

W tym przewodniku i eShopOnContainers (w szczególności mikrousługi zamawiania) zdecydowaliśmy się zaimplementować proste zapytania przy użyciu mikro ORM jak [Dapper](https://github.com/StackExchange/dapper-dot-net). Dzięki temu można zaimplementować dowolne zapytanie na podstawie instrukcji SQL, aby uzyskać najlepszą wydajność, dzięki lekkiej struktury z bardzo małym obciążeniem.

Należy zauważyć, że podczas korzystania z tej metody, wszelkie aktualizacje do modelu, które mają wpływ na sposób jednostek są utrwalione do bazy danych SQL również potrzebują oddzielnych aktualizacji do zapytań SQL używanych przez Dapper lub innych oddzielnych (non-EF) podejścia do wykonywania zapytań.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Wzorce CQRS i DDD nie są architekturami najwyższego poziomu

Ważne jest, aby zrozumieć, że CQRS i większość wzorców DDD (takich jak warstwy DDD lub model domeny z agregacjami) nie są style architektury, ale tylko wzorce architektury. Mikrousługi, SOA i architektura sterowana zdarzeniami (EDA) są przykładami stylów architektonicznych. Opisują one system wielu składników, takich jak wiele mikrousług. Wzorce CQRS i DDD opisują coś wewnątrz jednego systemu lub komponentu; w takim przypadku coś wewnątrz mikrousługi.

Różne ograniczone konteksty (BC) będą wykorzystywać różne wzorce. Mają różne obowiązki, a to prowadzi do różnych rozwiązań. Warto podkreślić, że wymuszanie tego samego wzorca wszędzie prowadzi do awarii. Nie używaj wzorców CQRS i DDD wszędzie. Wiele podsystemów, kontrolerów bcs lub mikrousług są prostsze i można je łatwiej zaimplementować przy użyciu prostych usług CRUD lub przy użyciu innego podejścia.

Istnieje tylko jedna architektura aplikacji: architektura systemu lub aplikacji end-to-end, którą projektujesz (na przykład architektura mikrousług). Jednak projekt każdego ograniczonego kontekstu lub mikrousługi w tej aplikacji odzwierciedla własne kompromisy i wewnętrzne decyzje projektowe na poziomie wzorców architektury. Nie próbuj stosować tych samych wzorców architektonicznych, takich jak CQRS lub DDD wszędzie.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. CQRS (CQRS)** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Grzegorz Young. Dokumenty CQRS** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan. Wyjaśnione CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Poprzedni](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[następny](cqrs-microservice-reads.md)
