---
title: Stosowanie zasad CQRS i CQS w mikrousługach DDD w ramach aplikacji eShopOnContainers
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zrozumieć sposób CQRS jest implementowany w mikrousługi zamawiania w eShopOnContainers.
ms.date: 03/03/2020
ms.openlocfilehash: eda0ee374b41a81811e92e2829b10dc8515e0ccd
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988495"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Stosowanie metod CQRS i CQS w mikrousługach DDD w eShopOnContainers

Projekt mikrousługi zamawiania w aplikacji referencyjnej eShopOnContainers opiera się na zasadach CQRS. Jednak używa najprostszego podejścia, które jest po prostu oddzielenie kwerend od poleceń i przy użyciu tej samej bazy danych dla obu akcji.

Istotą tych wzorców, a ważnym punktem tutaj jest to, że zapytania są idempotentne: bez względu na to, ile razy kwerendy systemu, stan tego systemu nie ulegnie zmianie. Innymi słowy, zapytania są bez efektów ubocznych.

W związku z tym można użyć innego modelu danych "odczyty" niż logiki transakcyjnej "zapisuje" model domeny, nawet jeśli mikrousługi zamawiania są przy użyciu tej samej bazy danych. W związku z tym jest to uproszczone podejście CQRS.

Z drugiej strony polecenia, które wyzwalają transakcje i aktualizacje danych, zmieniają stan w systemie. Dzięki poleciom musisz zachować ostrożność w radzeniu sobie ze złożonością i ciągle zmieniającymi się regułami biznesowymi. W tym miejscu chcesz zastosować techniki DDD, aby mieć lepiej modelowany system.

Wzory DDD przedstawione w tym przewodniku nie powinny być stosowane powszechnie. Wprowadzają one ograniczenia w projekcie. Ograniczenia te zapewniają korzyści, takie jak wyższa jakość w czasie, zwłaszcza w poleceniach i innych kodów, który modyfikuje stan systemu. Jednak te ograniczenia dodać złożoność z mniejszą liczbą korzyści dla odczytu i wykonywania zapytań danych.

Jednym z takich wzorów jest wzór Agregacji, który analizujemy więcej w kolejnych sekcjach. Krótko mówiąc, we wzorcu Agreguj wiele obiektów domeny traktujesz jako pojedynczą jednostkę w wyniku ich relacji w domenie. Nie zawsze można uzyskać korzyści z tego wzorca w kwerendach; może zwiększyć złożoność logiki zapytań. W przypadku kwerend tylko do odczytu nie można uzyskać korzyści wynikające z traktowania wielu obiektów jako pojedynczego agregacji. Otrzymujesz tylko złożoność.

Jak pokazano na rysunku 7-2 w poprzedniej sekcji, w tym przewodniku sugeruje przy użyciu wzorców DDD tylko w transakcyjnych/aktualizuje obszar mikrousługi (czyli wyzwalane przez polecenia). Zapytania można wykonać prostsze podejście i powinny być oddzielone od poleceń, zgodnie z podejściem CQRS.

Do implementacji "po stronie zapytań", można wybrać między wieloma podejściami, z pełnowymiarowego ORM, takich jak EF Core, projekcje AutoMapper, procedury przechowywane, widoki, zmaterializowane widoki lub mikro ORM.

W tym przewodniku i w eShopOnContainers (w szczególności mikrousługi zamawiania) zdecydowaliśmy się zaimplementować proste zapytania za pomocą micro ORM jak [Dapper](https://github.com/StackExchange/dapper-dot-net). Dzięki temu można zaimplementować wszelkie zapytania oparte na instrukcjach SQL, aby uzyskać najlepszą wydajność, dzięki lekkiej ramach z bardzo małym obciążeniem.

Należy zauważyć, że podczas korzystania z tej metody, wszelkie aktualizacje modelu, które wpływają na sposób jednostek są utrwalone do bazy danych SQL również potrzebują oddzielnych aktualizacji zapytań SQL używanych przez Dapper lub inne oddzielne (non-EF) podejścia do wykonywania zapytań.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Wzorce CQRS i DDD nie są architekturami najwyższego poziomu

Ważne jest, aby zrozumieć, że CQRS i większość wzorców DDD (takich jak warstwy DDD lub model domeny z agregatami) nie są stylami architektury, ale tylko wzorcami architektury. Mikrousługi, SOA i architektury opartej na zdarzeniach (EDA) są przykładami stylów architektonicznych. Opisują system wielu składników, takich jak wiele mikrousług. Wzorce CQRS i DDD opisują coś wewnątrz jednego systemu lub składnika; w tym przypadku coś wewnątrz mikrousługi.

Różne ograniczone konteksty (BC) będą wykorzystywać różne wzorce. Mają różne obowiązki, a to prowadzi do różnych rozwiązań. Warto podkreślić, że wymuszanie tego samego wzorca wszędzie prowadzi do awarii. Nie używaj wzorców CQRS i DDD wszędzie. Wiele podsystemów, kontrolerów domeny lub mikrousług są prostsze i można łatwiej zaimplementować przy użyciu prostych usług CRUD lub przy użyciu innego podejścia.

Istnieje tylko jedna architektura aplikacji: architektura systemu lub aplikacji end-to-end, które projektujesz (na przykład architektura mikrousług). Jednak projekt każdego ograniczonego kontekstu lub mikrousług w ramach tej aplikacji odzwierciedla własne kompromisy i wewnętrzne decyzje projektowe na poziomie wzorców architektury. Nie próbuj stosować tych samych wzorców architektonicznych, takich jak CQRS lub DDD wszędzie.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. CQRS (CQRS)** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young. Dokumenty CQRS** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan. Wyjaśnione CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Poprzedni](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[następny](cqrs-microservice-reads.md)
