---
title: Elastyczne wyszukiwanie w aplikacjach natywnych dla chmury
description: Dowiedz się więcej o dodawaniu funkcji elastycznego wyszukiwania do aplikacji natywnych dla chmury.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 1bce255b6315006b11e0b6ac77040300f67ed984
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141292"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elastyczne wyszukiwanie w aplikacji natywnej dla chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch to rozproszony system wyszukiwania i analizy, który umożliwia złożone funkcje wyszukiwania w różnych typach danych. Jest open source i bardzo popularny. Zastanów się, w jaki sposób następujące firmy integrują Elasticsearch ze swoim zastosowaniem:

- [Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) do wyszukiwania pełnotekstowego i przyrostowego (wyszukiwanie podczas pisania).
- [GitHub](https://www.elastic.co/customers/github) do indeksowania i uwidaczniania ponad 8 milionów repozytoriów kodu.  
- [Docker](https://www.elastic.co/customers/docker) do tworzenia biblioteki kontenerów wykrywalne.

Elasticsearch jest zbudowany na górze [Apache Lucene](https://lucene.apache.org/core/) pełnotekstowej wyszukiwarki. Lucene zapewnia wysokiej wydajności indeksowania dokumentów i zapytań. Indeksuje dane za pomocą odwróconego schematu indeksowania - zamiast mapowania stron na słowa kluczowe, mapuje słowa kluczowe na strony, podobnie jak słowniczek na końcu książki. Lucene ma zaawansowane możliwości składni zapytań i może wysyłać zapytania do danych, korzystając z:

- Termin (pełne słowo)
- Prefiks (zaczyna się od słowa)
- Symbol wieloznaczny\*(przy użyciu filtrów " " lub "?")
- Fraza (sekwencja tekstu w dokumencie)
- Wartość logiczna (złożone wyszukiwania łączące zapytania)

Podczas gdy Lucene zapewnia niski poziom instalacji wodno-kanalizacyjnych do wyszukiwania, Elasticsearch zapewnia serwer, który znajduje się na szczycie Lucene. Elasticsearch dodaje funkcje wyższego poziomu, aby uprościć pracę Lucene, w tym RESTful API, aby uzyskać dostęp do funkcji indeksowania i wyszukiwania Lucene.Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality. Zapewnia również rozproszoną infrastrukturę zdolną do ogromnej skalowalności, odporności na uszkodzenia i wysokiej dostępności.

W przypadku większych aplikacji natywnych dla chmury ze złożonymi wymaganiami wyszukiwania usługa Elasticsearch jest dostępna jako usługa zarządzana na platformie Azure. Microsoft Azure Marketplace oferuje wstępnie skonfigurowane szablony, których deweloperzy mogą używać do wdrażania klastra Elasticsearch na platformie Azure.

W witrynie Microsoft Azure Marketplace deweloperzy mogą używać wstępnie skonfigurowanych szablonów utworzonych w celu szybkiego wdrożenia klastra elasticsearch na platformie Azure. Korzystając z oferty zarządzanej przez platformę Azure, można wdrożyć maksymalnie 50 węzłów danych, 20 węzłów koordynujących i trzy dedykowane węzły główne.

## <a name="summary"></a>Podsumowanie

W tym rozdziale przedstawiono szczegółowe spojrzenie na dane w systemach natywnych dla chmury. Zaczęliśmy od kontrastowania przechowywania danych w aplikacjach monolitycznych z wzorcami przechowywania danych w systemach natywnych dla chmury. Przyjrzeliśmy się wzorcom danych zaimplementowanym w systemach natywnych dla chmury, w tym zapytań między usługami, transakcjami rozproszonymi i wzorcami do obsługi systemów o dużej objętości. Skontrastowaliśmy SQL z danymi NoSQL. Przyjrzeliśmy się opcjom przechowywania danych dostępnym na platformie Azure, które zawierają opcje skoncentrowane zarówno na platformie Microsoft, jak i open source. Na koniec omówiliśmy buforowanie i elastycznewyszukiwanie w aplikacji natywnej dla chmury.

### <a name="references"></a>Dokumentacja

- [Wzorzec podziału odpowiedzialności polecenia i zapytania (CQRS)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Wzorzec pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [Bazy danych RDBMS vs. NoSQL: Przegląd](https://maxivak.com/rdbms-vs-nosql-databases/)

- [Dlaczego partycja RDBMS nie jest tolerancyjna w owemu orędzie i dlaczego jest dostępna?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Zmaterializowany widok](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Wszystko, co naprawdę musisz wiedzieć o bazach danych open source](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Wzorzec transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Wzór Sagi](https://microservices.io/patterns/data/saga.html)

- [Wzory Sagi | Jak implementować transakcje biznesowe przy użyciu mikrousług](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Wzorzec transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Pierwsze za 9-Ball: Cosmos DB Poziomy spójności Wyjaśnione](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Eksplorowanie różnych typów baz danych NoSQL część II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [W bazach danych RDBMS, NoSQL i NewSQL. Wywiad z Johnem Ryanem](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: Pełne porównanie](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH: Cztery właściwości kubernetes-native baz danych](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [KaraluchDB](https://www.cockroachlabs.com/)

- [Baza danych TiDB](https://pingcap.com/en/)

- [YugabyteDB (yugabyteDB)](https://www.yugabyte.com/)

- [Okręg wyborczy Vitess](https://vitess.io/)

- [Elastyczne wyszukiwanie: Ostateczny przewodnik](http://shop.oreilly.com/product/0636920028505.do)
  
- [Wprowadzenie do Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Poprzedni](azure-caching.md)
>[następny](resiliency.md) <!-- Next Chapter -->
