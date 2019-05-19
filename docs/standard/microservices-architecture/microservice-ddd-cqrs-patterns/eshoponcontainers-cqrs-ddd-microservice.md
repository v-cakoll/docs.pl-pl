---
title: Stosowanie zasad CQRS i CQS w mikrousługach DDD w ramach aplikacji eShopOnContainers
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Poznaj sposób, w jaki sposób jest implementowany CQRS szeregowania mikrousługi w ramach aplikacji eShopOnContainers.
ms.date: 10/08/2018
ms.openlocfilehash: 0380e759595e8a159e89f858a5ced4dacfa4e9b4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875909"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Stosowanie podejścia CQRS i CQS w mikrousługach DDD w ramach aplikacji eShopOnContainers

Projekt szeregowania mikrousługi w ramach aplikacji eShopOnContainers aplikacja referencyjna jest oparta na zasadach podejścia CQRS. Jednak używa najprostszą metodą, co jest po prostu oddzielenie zapytania w poleceniach i przy użyciu tej samej bazy danych dla obu akcji.

Kluczową cechą tych wzorców i należy koniecznie zwrócić uwagę, jest, że zapytania są idempotentne: niezależnie od tego, ile razy zapytań systemu, nie zmienią się stan tego systemu. Innymi słowy zapytania są efekt uboczny bezpłatnie.

W związku z tym można użyć różnych "Odczyt" model danych niż logiki transakcyjnej "zapisuje" model domeny, mimo że szeregowania mikrousług korzystają z tej samej bazy danych. Dlatego jest to uproszczone podejście CQRS.

Z drugiej strony poleceń, które wyzwalają transakcji i aktualizacji danych, zmiany stanu w systemie. Za pomocą poleceń, musisz należy zachować ostrożność podczas dotyczących złożoności i ciągle zmieniające reguł biznesowych. Jest to, gdzie chcesz zastosować technik DDD, aby lepiej modelowanych systemu.

Nie można zastosować powszechnie wzorców DDD, w tym przewodniku. Wprowadzają ograniczenia dotyczące projektu. Te ograniczenia zapewniają korzyści, takich jak wyższej jakości, wraz z upływem czasu, szczególnie w przypadku polecenia i innego kodu, który modyfikuje stan systemu. Jednak te ograniczenia zwiększenia złożoności, z mniejszą liczbą korzyści, Odczyt i wykonywanie zapytań o dane.

Jeden taki wzorzec jest wzorca agregacji omówiony bardziej w kolejnych sekcjach. Krótko mówiąc we wzorcu agregacji traktować wiele obiektów domeny jako pojedyncza jednostka wyniku ich relacje w domenie. Nie mogą zawsze uzyskać korzyści wynikające z tego wzorca w zapytaniach; to może zwiększyć złożoność logiki zapytania. Dla zapytań tylko do odczytu nie uzyskać korzyści wynikające z traktowanie wielu obiektów jako jednej wartości zagregowanej. Uzyskujesz tylko złożoności.

Jak pokazano w rysunek 7-2, ten przewodnik sugeruje, przy użyciu wzorców DDD tylko w obszarze transakcyjnej/aktualizacji usługi mikrousługi (jak wyzwalane za pomocą poleceń). Zapytania można wykonać prostszej metody i powinna być oddzielona od po podejście CQRS poleceń.

Wykonania na stronie"zapytania", można wybrać wiele metod z Twojej pełnej ORM, takie jak EF Core, AutoMapper projekcji, procedury składowane, widoki, zmaterializowanych widoków lub wczesnych ORM.

W tym przewodniku, jak i w ramach aplikacji eShopOnContainers (w szczególności szeregowania mikrousług) Wybraliśmy Implementowanie prostych zapytań przy użyciu micro ORM, takie jak [programem Dapper](https://github.com/StackExchange/dapper-dot-net). Dzięki temu można zaimplementować dowolnego zapytania oparte na instrukcji SQL, aby uzyskać najlepszą wydajność, dzięki światła framework z niewielkim zapasem.

Należy zauważyć, że gdy użycie tej metody aktualizacji do modelu, wpływających na to, jak jednostki są zachowywane w usługą SQL database również oddzielne aktualizacje do zapytania SQL, które korzystają z programem Dapper lub wszelkie inne oddzielne metody (bez EF) do wykonywania zapytań.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Wzorców CQRS i DDD nie są architektur najwyższego poziomu

Jest ważne dowiedzieć się, że CQRS i większość wzorców DDD (np. warstwy DDD lub modelu domeny przy użyciu wartości zagregowane) nie są stylami architektury, ale tylko wzorce architektury. Mikrousługi, SOA i architektura sterowana zdarzeniami (EDA) są przykładami stylami architektury. Opisują one systemu z wielu składników, takich jak wiele mikrousług. Wzorców CQRS i DDD opisanie czegoś co wewnątrz pojedynczego systemu lub component; w tym przypadku coś wewnątrz mikrousługi.

Ograniczonych kontekstów (usług łączności biznesowej) będzie używać różnych wzorców. Mają różne obowiązki i która prowadzi do różnych rozwiązaniach. Warto podkreślając, że wymuszania tego samego wzorca, który wszędzie prowadzi do awarii. Nie używaj wzorców CQRS i DDD wszędzie. Wiele podsystemów, usług łączności biznesowej lub mikrousług są prostsze i można ją wdrożyć łatwiej za pomocą usługi simple CRUD lub przy użyciu innej metody.

Istnieje tylko jedna aplikacja architektury: Architektura aplikacji system lub end-to-end projektowania (na przykład w architekturze mikrousług). Jednak projekt każdego ograniczonego kontekstu lub mikrousług tej aplikacji odzwierciedla własne wady i zalety i decyzje dotyczące projektu wewnętrznego na poziomie wzorców architektury. Nie należy próbować użyć tego samego architektury wzorców takich jak CQRS i DDD wszędzie.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Martin Fowler. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Grega Younga. Podejście CQRS dokumentów** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan. Sklarowanego CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Poprzednie](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[dalej](cqrs-microservice-reads.md)
