---
title: Stosowanie zasad CQRS i CQS w mikrousługach DDD w ramach aplikacji eShopOnContainers
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się ze sposobem, w jaki CQRS jest zaimplementowany w mikrousłudze porządkowania w eShopOnContainers.
ms.date: 03/03/2020
ms.openlocfilehash: 0fd38a93a1056cda4abd2f9f89ee9efc626985c8
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144282"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Zastosuj podejścia CQRS i CQS w mikrousłudze DDD w eShopOnContainers

Projektowanie mikrousługi porządkowania w aplikacji referencyjnej eShopOnContainers opiera się na zasadach CQRS. Jednak używa najprostszym podejściem, które po prostu oddziela zapytania od poleceń i korzysta z tej samej bazy danych dla obu akcji.

Istotą tych wzorców i ważnym punktem jest to, że zapytania są idempotentnee: niezależnie od tego, ile razy wykonujesz zapytania o system, stan tego systemu nie ulegnie zmianie. Innymi słowy, zapytania są bezpłatne.

Z tego względu można użyć innego modelu danych "odczyty" niż model domeny "zapisy" logiki transakcyjnej, nawet jeśli mikrousługi, które korzystają z tej samej bazy danych. W związku z tym jest to uproszczone podejście CQRS.

Z drugiej strony polecenia, które wyzwalają transakcje i aktualizacje danych, zmieniają stan w systemie. Przy użyciu poleceń należy zachować ostrożność podczas pracy z złożonością i kiedykolwiek zmieniającymi się regułami biznesowymi. Jest to miejsce, w którym chcesz zastosować techniki DDD, aby lepiej modelowany system.

Wzorców DDD przedstawionych w tym przewodniku nie należy stosować uniwersalnie. Wprowadzają ograniczenia dotyczące Twojego projektu. Te ograniczenia zapewniają korzyści, takie jak wyższa jakość w miarę upływu czasu, szczególnie w przypadku poleceń i innych kodów modyfikujących stan systemu. Jednak te ograniczenia zwiększają złożoność z mniejszą liczbą korzyści w przypadku odczytywania i wykonywania zapytań dotyczących danych.

Jednym z takich wzorców jest wzorzec agregacji, który analizujemy więcej w dalszych sekcjach. Krótko, we wzorcu agregacji traktujesz wiele obiektów domeny jako pojedynczą jednostkę w wyniku ich relacji w domenie. Nie zawsze można uzyskać korzyści z tego wzorca w zapytaniach. może zwiększyć złożoność logiki zapytań. W przypadku zapytań tylko do odczytu nie są korzyści wynikające z traktowania wielu obiektów jako pojedynczej agregacji. Możesz uzyskać tylko złożoność.

Jak pokazano na rysunku 7-2 w poprzedniej sekcji, ten przewodnik sugeruje użycie wzorców DDD tylko w obszarze transakcyjne/aktualizacje w mikrousłudze (to jest wyzwolone przez polecenia). Zapytania mogą być zgodne z prostszym podejściem i powinny być oddzielone od poleceń, zgodnie z podejściem CQRS.

W celu zaimplementowania "strony zapytania" można wybrać między wieloma podejściami, z rozwiniętą ORM, takich jak EF Core, projekcje automapowania, procedury składowane, widoki, widoki z materiałami lub mikro ORM.

W tym przewodniku i w eShopOnContainers (w odróżnieniu od mikrousługi porządkowania) wprowadziliśmy proste zapytania przy użyciu mikroorm, takiego jak [Dapper](https://github.com/StackExchange/dapper-dot-net). Dzięki temu można zaimplementować dowolne zapytanie w oparciu o instrukcje SQL, aby uzyskać najlepszą wydajność, dzięki czemu środowisko lekkie z bardzo małym obciążeniem.

Należy pamiętać, że w przypadku korzystania z tej metody wszystkie aktualizacje modelu, które mają wpływ na sposób utrwalania jednostek w usłudze SQL Database, wymagają również oddzielnych aktualizacji zapytań SQL używanych przez Dapper lub innych oddzielnych metod (innych niż EF) do wykonywania zapytań.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Wzorce CQRS i DDD nie są architekturami najwyższego poziomu

Ważne jest, aby zrozumieć, że CQRS i większość wzorców (takich jak warstwy DDD lub model domeny z agregacjami) nie są stylami architektury, ale tylko wzorców architektury. Mikrousługi, SOA i architektura sterowana zdarzeniami (EDA) to przykłady stylów architektury. Opisano w nim system wielu składników, na przykład wiele mikrousług. Wzorce CQRS i DDD opisują coś wewnątrz pojedynczego systemu lub składnika; w tym przypadku coś wewnątrz mikrousługi.

Różne konteksty ograniczone (BCs) będą wykorzystywać różne wzorce. Mają różne obowiązki i które prowadzą do różnych rozwiązań. Warto naciskać na to, aby wymuszać ten sam wzorzec wszędzie tam, gdzie prowadzi do błędu. Nie używaj CQRS i DDD wzorców wszędzie. Wiele podsystemów, usług BCs lub mikrousług jest prostsze i można je zaimplementować łatwiej przy użyciu prostych usług CRUD lub innych rozwiązań.

Istnieje tylko jedna architektura aplikacji: architektura projektowania aplikacji systemowej lub kompleksowej (na przykład architektury mikrousług). Jednak projekt każdego ograniczonego kontekstu lub mikrousług w tej aplikacji odzwierciedla własne kompromisy i wewnętrzne decyzje projektowe na poziomie wzorców architektury. Nie należy próbować stosować tych samych wzorców architektonicznych, takich jak CQRS lub DDD wszędzie.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Fowlera Martin. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young. CQRS dokumenty** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **UDI Dahan. Wyjaśniono CQRS** \
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Poprzedni](apply-simplified-microservice-cqrs-ddd-patterns.md) 
> [Dalej](cqrs-microservice-reads.md)
