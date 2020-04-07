---
title: Elastyczne wyszukiwanie w aplikacjach natywnych dla chmury
description: Dowiedz się więcej o dodawaniu funkcji wyszukiwania elastycznego do aplikacji natywnych dla chmury.
author: robvet
ms.date: 03/02/2020
ms.openlocfilehash: da6b9402cf266f5a298b05cf837805b2377bc75a
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805561"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elasticsearch w aplikacji natywnej dla chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch to rozproszony system wyszukiwania i analizy, który umożliwia złożone możliwości wyszukiwania w różnych typach danych. Jest open source i bardzo popularne. Zastanów się, w jaki sposób następujące firmy integrują Elasticsearch ze swoim zastosowaniem:

- [Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) dla pełnego tekstu i przyrostowe (szukaj podczas pisania) wyszukiwanie.
- [GitHub](https://www.elastic.co/customers/github) do indeksowania i uwidaczniania ponad 8 milionów repozytoriów kodu.  
- [Docker](https://www.elastic.co/customers/docker) do tworzenia biblioteki kontenerów wykrywalne.

Elasticsearch jest zbudowany na górze [Apache Lucene](https://lucene.apache.org/core/) pełnotekstowej wyszukiwarki. Lucene zapewnia indeksowanie dokumentów o wysokiej wydajności i wykonywanie zapytań. Indeksuje dane za pomocą odwróconego schematu indeksowania – zamiast mapować strony na słowa kluczowe, mapuje słowa kluczowe na strony, podobnie jak słowniczek na końcu książki. Lucene ma zaawansowane możliwości składni kwerendy i może wysyłać zapytania do danych przez:

- Termin (pełne słowo)
- Prefiks (rozpoczyna się od wyrazu)
- Symbol wieloznaczny\*(za pomocą filtrów " " lub "?"
- Fraza (sekwencja tekstu w dokumencie)
- Wartość logiczna (wyszukiwanie złożone łączące kwerendy)

Podczas gdy Lucene zapewnia niski poziom instalacji wodno-kanalizacyjnej do wyszukiwania, Elasticsearch zapewnia serwer, który znajduje się na szczycie Lucene. Elasticsearch dodaje funkcje wyższego poziomu, aby uprościć pracę Lucene, w tym RESTful API, aby uzyskać dostęp do funkcji indeksowania i wyszukiwania Lucene. Zapewnia również rozproszoną infrastrukturę zdolną do masowej skalowalności, odporności na uszkodzenia i wysokiej dostępności.

W przypadku większych aplikacji natywnych dla chmury ze złożonymi wymaganiami dotyczącymi wyszukiwania elasticsearch jest dostępny jako usługa zarządzana na platformie Azure. Witryna Microsoft Azure Marketplace zawiera wstępnie skonfigurowane szablony, za pomocą których deweloperzy mogą wdrażać klaster Elasticsearch na platformie Azure.

W portalu Microsoft Azure Marketplace deweloperzy mogą używać wstępnie skonfigurowanych szablonów utworzonych w celu szybkiego wdrożenia klastra Elasticsearch na platformie Azure. Korzystając z oferty zarządzanej przez platformę Azure, można wdrożyć do 50 węzłów danych, 20 węzłów koordynujących i trzy dedykowane węzły główne.

## <a name="summary"></a>Podsumowanie

W tym rozdziale przedstawiono szczegółowe spojrzenie na dane w systemach natywnych dla chmury. Zaczęliśmy od kontrastowania przechowywania danych w aplikacjach monolitycznych z wzorcami przechowywania danych w systemach natywnych dla chmury. Przyjrzeliśmy się wzorcom danych zaimplementowanym w systemach natywnych dla chmury, w tym zapytaniom międzyusługowym, transakcjami rozproszonymi i wzorcom w celu obsługi systemów o dużej objętości. Porównaliśmy SQL z danymi NoSQL. Przyjrzeliśmy się opcji przechowywania danych dostępnych na platformie Azure, które obejmują opcje zorientowane na microsoft i open source. Na koniec omówiliśmy buforowanie i elasticsearch w aplikacji natywnej dla chmury.

### <a name="references"></a>Dokumentacja

- [Wzorzec podziału odpowiedzialności polecenia i zapytania (CQRS)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Wzorzec pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [Dlaczego partycja RDBMS nie jest tolerancyjna w pozorach CAP i dlaczego jest dostępna?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Zmaterializowany widok](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Wszystko, co naprawdę musisz wiedzieć o bazach danych open source](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Wzorzec transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Wzór sagi](https://microservices.io/patterns/data/saga.html)

- [Wzory sagi | Jak zaimplementować transakcje biznesowe przy użyciu mikrousług](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Wzorzec transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Pierwsze za 9-Ball: Cosmos DB Poziom spójności Wyjaśniono](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Eksplorowanie różnych typów baz danych NoSQL część II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [W bazach danych RDBMS, NoSQL i NewSQL. Wywiad z Johnem Ryanem](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: Pełne porównanie](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH: Cztery właściwości natywnych baz danych Kubernetes](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [KaraluchDB](https://www.cockroachlabs.com/)

- [TiDB (TiDB)](https://pingcap.com/en/)

- [YugabyteDB (YugabyteDB)](https://www.yugabyte.com/)

- [Witesa](https://vitess.io/)

- [Elasticsearch: Ostateczny przewodnik](http://shop.oreilly.com/product/0636920028505.do)
  
- [Wprowadzenie do Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Poprzedni](azure-caching.md)
>[następny](resiliency.md) <!-- Next Chapter -->
