---
title: Elasticsearch w aplikacjach natywnych w chmurze
description: Dowiedz się więcej na temat dodawania funkcji wyszukiwania elastycznego do aplikacji natywnych w chmurze.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 6ea237eddc89a8c6843d6b34b05b1b71515a99b6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794878"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elasticsearch w aplikacji natywnej w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch to rozproszony system wyszukiwania i analizy, który umożliwia złożone funkcje wyszukiwania w różnych typach danych. Jest to "open source" i szeroko popularne. Rozważ, jak następujące firmy integrują Elasticsearch z aplikacjami:

- [Witrynę Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) do wyszukiwania pełnotekstowego i przyrostowego (wyszukiwanie w trakcie pisania).
- W witrynie [GitHub](https://www.elastic.co/customers/github) można indeksować i uwidaczniać ponad 8 000 000 repozytoriów kodu.  
- Platforma [Docker](https://www.elastic.co/customers/docker) umożliwiająca odnajdywanie biblioteki kontenerów.

Elasticsearch jest oparta na aparacie wyszukiwania pełnotekstowego [Apache Lucene](https://lucene.apache.org/core/) . Lucene umożliwiają indeksowanie dokumentów o wysokiej wydajności i wykonywanie zapytań. Indeksuje dane z odwróconym schematem indeksowania — zamiast mapowania stron do słów kluczowych, mapuje słowa kluczowe na strony w taki sam sposób jak słownik na końcu książki. Lucene mają zaawansowane możliwości składni zapytań i mogą wykonywać zapytania dotyczące danych, wykonując następujące czynności:

- Term (pełny wyraz) 
- Prefiks (zaczyna się od Word)
- Symbol wieloznaczny (przy użyciu filtrów "\*" lub "?")
- Phrase (sekwencja tekstu w dokumencie)
- Wartość logiczna (złożone wyszukiwania łączące zapytania)

Podczas gdy Lucene, udostępniają instalację niskiego poziomu na potrzeby wyszukiwania, Elasticsearch udostępnia serwer, który znajduje się na podstawie Lucene. Elasticsearch dodaje funkcje wyższego poziomu, aby uprościć pracę Lucene, łącznie z interfejsem API RESTful w celu uzyskania dostępu do funkcji indeksowania i wyszukiwania Lucene. Zapewnia również infrastrukturę rozproszoną, która umożliwia ogromne skalowanie, odporność na uszkodzenia i wysoką dostępność.

W przypadku większych aplikacji natywnych w chmurze, które mają złożone wymagania dotyczące wyszukiwania, Elasticsearch jest dostępny jako usługa zarządzana na platformie Azure. Wstępnie skonfigurowane szablony funkcji Microsoft Azure Marketplace, których deweloperzy mogą używać do wdrażania klastra Elasticsearch na platformie Azure.

W Microsoft Azure Marketplace deweloperzy mogą korzystać ze wstępnie skonfigurowanych szablonów utworzonych w celu szybkiego wdrożenia klastra Elasticsearch na platformie Azure. Korzystając z oferty zarządzanej przez platformę Azure, można wdrożyć maksymalnie 50 węzłów danych, 20 koordynujące węzły i trzy dedykowane węzły główne.

## <a name="summary"></a>Podsumowanie

W tym rozdziale przedstawiono szczegółowe dane w systemach natywnych w chmurze. Rozpoczęto od różnicowania magazynu danych w aplikacjach monolitycznych ze wzorcami magazynu danych w systemach natywnych w chmurze. Oglądamy wzorce danych zaimplementowane w systemach natywnych w chmurze, w tym zapytania międzyusługowe, transakcje rozproszone i wzorce, aby zająć się systemami o dużej pojemności. Korzystamy z kodu SQL z danymi NoSQL. Znaleźliśmy dostępne opcje przechowywania danych na platformie Azure, które obejmują opcje skoncentrowane na firmie Microsoft i w trybie Open Source. Wreszcie omawiamy buforowanie i Elasticsearch w aplikacji natywnej w chmurze.

### <a name="references"></a>Odwołania

- [Wzorzec Command and Query Responsibility Segregation (CQRS)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Wzorzec określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [Bazy danych RDBMSs a NoSQL: przegląd](https://maxivak.com/rdbms-vs-nosql-databases/)

- [Dlaczego RDBMS jest odporna na partycje w CAP theorem i dlaczego jest dostępna?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Widok z materiałami](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Wszystko, co naprawdę trzeba wiedzieć na temat baz danych open source](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Wzorzec transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Wzorzec Saga](https://microservices.io/patterns/data/saga.html)

- [Wzorce Saga | Jak zaimplementować transakcje biznesowe przy użyciu mikrousług](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Wzorzec transakcji kompensacyjnych](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Po 9-piłkę: Cosmos DB poziomów spójności wyjaśniono](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Eksplorowanie różnych typów baz danych NoSQL część II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [W bazach danych RDBMS, NoSQL i NewSQL. Wywiad z John Ryan](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: pełne porównanie](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [KRESKa: cztery właściwości natywnych baz danych Kubernetes](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CockroachDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch: Ostateczny Przewodnik](http://shop.oreilly.com/product/0636920028505.do)
  
- [Wprowadzenie do oprogramowania Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Poprzedni](azure-caching.md)
>[Następny](resiliency.md) <!-- Next Chapter -->
