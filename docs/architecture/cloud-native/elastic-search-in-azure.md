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
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="dde18-103">Elastyczne wyszukiwanie w aplikacji natywnej dla chmury</span><span class="sxs-lookup"><span data-stu-id="dde18-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="dde18-104">Elasticsearch to rozproszony system wyszukiwania i analizy, który umożliwia złożone funkcje wyszukiwania w różnych typach danych.</span><span class="sxs-lookup"><span data-stu-id="dde18-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="dde18-105">Jest open source i bardzo popularny.</span><span class="sxs-lookup"><span data-stu-id="dde18-105">It's open source and widely popular.</span></span> <span data-ttu-id="dde18-106">Zastanów się, w jaki sposób następujące firmy integrują Elasticsearch ze swoim zastosowaniem:</span><span class="sxs-lookup"><span data-stu-id="dde18-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="dde18-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) do wyszukiwania pełnotekstowego i przyrostowego (wyszukiwanie podczas pisania).</span><span class="sxs-lookup"><span data-stu-id="dde18-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="dde18-108">[GitHub](https://www.elastic.co/customers/github) do indeksowania i uwidaczniania ponad 8 milionów repozytoriów kodu.</span><span class="sxs-lookup"><span data-stu-id="dde18-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="dde18-109">[Docker](https://www.elastic.co/customers/docker) do tworzenia biblioteki kontenerów wykrywalne.</span><span class="sxs-lookup"><span data-stu-id="dde18-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="dde18-110">Elasticsearch jest zbudowany na górze [Apache Lucene](https://lucene.apache.org/core/) pełnotekstowej wyszukiwarki.</span><span class="sxs-lookup"><span data-stu-id="dde18-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="dde18-111">Lucene zapewnia wysokiej wydajności indeksowania dokumentów i zapytań.</span><span class="sxs-lookup"><span data-stu-id="dde18-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="dde18-112">Indeksuje dane za pomocą odwróconego schematu indeksowania - zamiast mapowania stron na słowa kluczowe, mapuje słowa kluczowe na strony, podobnie jak słowniczek na końcu książki.</span><span class="sxs-lookup"><span data-stu-id="dde18-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="dde18-113">Lucene ma zaawansowane możliwości składni zapytań i może wysyłać zapytania do danych, korzystając z:</span><span class="sxs-lookup"><span data-stu-id="dde18-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="dde18-114">Termin (pełne słowo)</span><span class="sxs-lookup"><span data-stu-id="dde18-114">Term (a full word)</span></span>
- <span data-ttu-id="dde18-115">Prefiks (zaczyna się od słowa)</span><span class="sxs-lookup"><span data-stu-id="dde18-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="dde18-116">Symbol wieloznaczny\*(przy użyciu filtrów " " lub "?")</span><span class="sxs-lookup"><span data-stu-id="dde18-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="dde18-117">Fraza (sekwencja tekstu w dokumencie)</span><span class="sxs-lookup"><span data-stu-id="dde18-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="dde18-118">Wartość logiczna (złożone wyszukiwania łączące zapytania)</span><span class="sxs-lookup"><span data-stu-id="dde18-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="dde18-119">Podczas gdy Lucene zapewnia niski poziom instalacji wodno-kanalizacyjnych do wyszukiwania, Elasticsearch zapewnia serwer, który znajduje się na szczycie Lucene.</span><span class="sxs-lookup"><span data-stu-id="dde18-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="dde18-120">Elasticsearch dodaje funkcje wyższego poziomu, aby uprościć pracę Lucene, w tym RESTful API, aby uzyskać dostęp do funkcji indeksowania i wyszukiwania Lucene.Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span><span class="sxs-lookup"><span data-stu-id="dde18-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene’s indexing and searching functionality.</span></span> <span data-ttu-id="dde18-121">Zapewnia również rozproszoną infrastrukturę zdolną do ogromnej skalowalności, odporności na uszkodzenia i wysokiej dostępności.</span><span class="sxs-lookup"><span data-stu-id="dde18-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="dde18-122">W przypadku większych aplikacji natywnych dla chmury ze złożonymi wymaganiami wyszukiwania usługa Elasticsearch jest dostępna jako usługa zarządzana na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="dde18-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="dde18-123">Microsoft Azure Marketplace oferuje wstępnie skonfigurowane szablony, których deweloperzy mogą używać do wdrażania klastra Elasticsearch na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="dde18-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="dde18-124">W witrynie Microsoft Azure Marketplace deweloperzy mogą używać wstępnie skonfigurowanych szablonów utworzonych w celu szybkiego wdrożenia klastra elasticsearch na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="dde18-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="dde18-125">Korzystając z oferty zarządzanej przez platformę Azure, można wdrożyć maksymalnie 50 węzłów danych, 20 węzłów koordynujących i trzy dedykowane węzły główne.</span><span class="sxs-lookup"><span data-stu-id="dde18-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="dde18-126">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="dde18-126">Summary</span></span>

<span data-ttu-id="dde18-127">W tym rozdziale przedstawiono szczegółowe spojrzenie na dane w systemach natywnych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="dde18-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="dde18-128">Zaczęliśmy od kontrastowania przechowywania danych w aplikacjach monolitycznych z wzorcami przechowywania danych w systemach natywnych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="dde18-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="dde18-129">Przyjrzeliśmy się wzorcom danych zaimplementowanym w systemach natywnych dla chmury, w tym zapytań między usługami, transakcjami rozproszonymi i wzorcami do obsługi systemów o dużej objętości.</span><span class="sxs-lookup"><span data-stu-id="dde18-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="dde18-130">Skontrastowaliśmy SQL z danymi NoSQL.</span><span class="sxs-lookup"><span data-stu-id="dde18-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="dde18-131">Przyjrzeliśmy się opcjom przechowywania danych dostępnym na platformie Azure, które zawierają opcje skoncentrowane zarówno na platformie Microsoft, jak i open source.</span><span class="sxs-lookup"><span data-stu-id="dde18-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="dde18-132">Na koniec omówiliśmy buforowanie i elastycznewyszukiwanie w aplikacji natywnej dla chmury.</span><span class="sxs-lookup"><span data-stu-id="dde18-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="dde18-133">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="dde18-133">References</span></span>

- [<span data-ttu-id="dde18-134">Wzorzec podziału odpowiedzialności polecenia i zapytania (CQRS)</span><span class="sxs-lookup"><span data-stu-id="dde18-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="dde18-135">Wzorzec pozyskiwania zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dde18-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="dde18-136">Bazy danych RDBMS vs. NoSQL: Przegląd</span><span class="sxs-lookup"><span data-stu-id="dde18-136">RDBMSs vs. NoSQL Databases: Overview</span></span>](https://maxivak.com/rdbms-vs-nosql-databases/)

- [<span data-ttu-id="dde18-137">Dlaczego partycja RDBMS nie jest tolerancyjna w owemu orędzie i dlaczego jest dostępna?</span><span class="sxs-lookup"><span data-stu-id="dde18-137">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="dde18-138">Zmaterializowany widok</span><span class="sxs-lookup"><span data-stu-id="dde18-138">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="dde18-139">Wszystko, co naprawdę musisz wiedzieć o bazach danych open source</span><span class="sxs-lookup"><span data-stu-id="dde18-139">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="dde18-140">Wzorzec transakcji kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="dde18-140">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="dde18-141">Wzór Sagi</span><span class="sxs-lookup"><span data-stu-id="dde18-141">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="dde18-142">Wzory Sagi | Jak implementować transakcje biznesowe przy użyciu mikrousług</span><span class="sxs-lookup"><span data-stu-id="dde18-142">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="dde18-143">Wzorzec transakcji kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="dde18-143">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="dde18-144">Pierwsze za 9-Ball: Cosmos DB Poziomy spójności Wyjaśnione</span><span class="sxs-lookup"><span data-stu-id="dde18-144">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="dde18-145">Eksplorowanie różnych typów baz danych NoSQL część II</span><span class="sxs-lookup"><span data-stu-id="dde18-145">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="dde18-146">W bazach danych RDBMS, NoSQL i NewSQL. Wywiad z Johnem Ryanem</span><span class="sxs-lookup"><span data-stu-id="dde18-146">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="dde18-147">SQL vs NoSQL vs NewSQL: Pełne porównanie</span><span class="sxs-lookup"><span data-stu-id="dde18-147">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="dde18-148">DASH: Cztery właściwości kubernetes-native baz danych</span><span class="sxs-lookup"><span data-stu-id="dde18-148">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="dde18-149">KaraluchDB</span><span class="sxs-lookup"><span data-stu-id="dde18-149">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="dde18-150">Baza danych TiDB</span><span class="sxs-lookup"><span data-stu-id="dde18-150">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="dde18-151">YugabyteDB (yugabyteDB)</span><span class="sxs-lookup"><span data-stu-id="dde18-151">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="dde18-152">Okręg wyborczy Vitess</span><span class="sxs-lookup"><span data-stu-id="dde18-152">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="dde18-153">Elastyczne wyszukiwanie: Ostateczny przewodnik</span><span class="sxs-lookup"><span data-stu-id="dde18-153">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="dde18-154">Wprowadzenie do Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="dde18-154">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="dde18-155">[Poprzedni](azure-caching.md)
>[następny](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="dde18-155">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
