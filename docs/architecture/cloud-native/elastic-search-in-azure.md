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
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="2974d-103">Elasticsearch w aplikacji natywnej dla chmury</span><span class="sxs-lookup"><span data-stu-id="2974d-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2974d-104">Elasticsearch to rozproszony system wyszukiwania i analizy, który umożliwia złożone możliwości wyszukiwania w różnych typach danych.</span><span class="sxs-lookup"><span data-stu-id="2974d-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="2974d-105">Jest open source i bardzo popularne.</span><span class="sxs-lookup"><span data-stu-id="2974d-105">It's open source and widely popular.</span></span> <span data-ttu-id="2974d-106">Zastanów się, w jaki sposób następujące firmy integrują Elasticsearch ze swoim zastosowaniem:</span><span class="sxs-lookup"><span data-stu-id="2974d-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="2974d-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) dla pełnego tekstu i przyrostowe (szukaj podczas pisania) wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="2974d-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="2974d-108">[GitHub](https://www.elastic.co/customers/github) do indeksowania i uwidaczniania ponad 8 milionów repozytoriów kodu.</span><span class="sxs-lookup"><span data-stu-id="2974d-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="2974d-109">[Docker](https://www.elastic.co/customers/docker) do tworzenia biblioteki kontenerów wykrywalne.</span><span class="sxs-lookup"><span data-stu-id="2974d-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="2974d-110">Elasticsearch jest zbudowany na górze [Apache Lucene](https://lucene.apache.org/core/) pełnotekstowej wyszukiwarki.</span><span class="sxs-lookup"><span data-stu-id="2974d-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="2974d-111">Lucene zapewnia indeksowanie dokumentów o wysokiej wydajności i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="2974d-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="2974d-112">Indeksuje dane za pomocą odwróconego schematu indeksowania – zamiast mapować strony na słowa kluczowe, mapuje słowa kluczowe na strony, podobnie jak słowniczek na końcu książki.</span><span class="sxs-lookup"><span data-stu-id="2974d-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="2974d-113">Lucene ma zaawansowane możliwości składni kwerendy i może wysyłać zapytania do danych przez:</span><span class="sxs-lookup"><span data-stu-id="2974d-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="2974d-114">Termin (pełne słowo)</span><span class="sxs-lookup"><span data-stu-id="2974d-114">Term (a full word)</span></span>
- <span data-ttu-id="2974d-115">Prefiks (rozpoczyna się od wyrazu)</span><span class="sxs-lookup"><span data-stu-id="2974d-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="2974d-116">Symbol wieloznaczny\*(za pomocą filtrów " " lub "?"</span><span class="sxs-lookup"><span data-stu-id="2974d-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="2974d-117">Fraza (sekwencja tekstu w dokumencie)</span><span class="sxs-lookup"><span data-stu-id="2974d-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="2974d-118">Wartość logiczna (wyszukiwanie złożone łączące kwerendy)</span><span class="sxs-lookup"><span data-stu-id="2974d-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="2974d-119">Podczas gdy Lucene zapewnia niski poziom instalacji wodno-kanalizacyjnej do wyszukiwania, Elasticsearch zapewnia serwer, który znajduje się na szczycie Lucene.</span><span class="sxs-lookup"><span data-stu-id="2974d-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="2974d-120">Elasticsearch dodaje funkcje wyższego poziomu, aby uprościć pracę Lucene, w tym RESTful API, aby uzyskać dostęp do funkcji indeksowania i wyszukiwania Lucene.</span><span class="sxs-lookup"><span data-stu-id="2974d-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="2974d-121">Zapewnia również rozproszoną infrastrukturę zdolną do masowej skalowalności, odporności na uszkodzenia i wysokiej dostępności.</span><span class="sxs-lookup"><span data-stu-id="2974d-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="2974d-122">W przypadku większych aplikacji natywnych dla chmury ze złożonymi wymaganiami dotyczącymi wyszukiwania elasticsearch jest dostępny jako usługa zarządzana na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="2974d-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="2974d-123">Witryna Microsoft Azure Marketplace zawiera wstępnie skonfigurowane szablony, za pomocą których deweloperzy mogą wdrażać klaster Elasticsearch na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="2974d-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="2974d-124">W portalu Microsoft Azure Marketplace deweloperzy mogą używać wstępnie skonfigurowanych szablonów utworzonych w celu szybkiego wdrożenia klastra Elasticsearch na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="2974d-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="2974d-125">Korzystając z oferty zarządzanej przez platformę Azure, można wdrożyć do 50 węzłów danych, 20 węzłów koordynujących i trzy dedykowane węzły główne.</span><span class="sxs-lookup"><span data-stu-id="2974d-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="2974d-126">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="2974d-126">Summary</span></span>

<span data-ttu-id="2974d-127">W tym rozdziale przedstawiono szczegółowe spojrzenie na dane w systemach natywnych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="2974d-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="2974d-128">Zaczęliśmy od kontrastowania przechowywania danych w aplikacjach monolitycznych z wzorcami przechowywania danych w systemach natywnych dla chmury.</span><span class="sxs-lookup"><span data-stu-id="2974d-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="2974d-129">Przyjrzeliśmy się wzorcom danych zaimplementowanym w systemach natywnych dla chmury, w tym zapytaniom międzyusługowym, transakcjami rozproszonymi i wzorcom w celu obsługi systemów o dużej objętości.</span><span class="sxs-lookup"><span data-stu-id="2974d-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="2974d-130">Porównaliśmy SQL z danymi NoSQL.</span><span class="sxs-lookup"><span data-stu-id="2974d-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="2974d-131">Przyjrzeliśmy się opcji przechowywania danych dostępnych na platformie Azure, które obejmują opcje zorientowane na microsoft i open source.</span><span class="sxs-lookup"><span data-stu-id="2974d-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="2974d-132">Na koniec omówiliśmy buforowanie i elasticsearch w aplikacji natywnej dla chmury.</span><span class="sxs-lookup"><span data-stu-id="2974d-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="2974d-133">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="2974d-133">References</span></span>

- [<span data-ttu-id="2974d-134">Wzorzec podziału odpowiedzialności polecenia i zapytania (CQRS)</span><span class="sxs-lookup"><span data-stu-id="2974d-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="2974d-135">Wzorzec pozyskiwania zdarzeń</span><span class="sxs-lookup"><span data-stu-id="2974d-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="2974d-136">Dlaczego partycja RDBMS nie jest tolerancyjna w pozorach CAP i dlaczego jest dostępna?</span><span class="sxs-lookup"><span data-stu-id="2974d-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="2974d-137">Zmaterializowany widok</span><span class="sxs-lookup"><span data-stu-id="2974d-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="2974d-138">Wszystko, co naprawdę musisz wiedzieć o bazach danych open source</span><span class="sxs-lookup"><span data-stu-id="2974d-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="2974d-139">Wzorzec transakcji kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="2974d-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="2974d-140">Wzór sagi</span><span class="sxs-lookup"><span data-stu-id="2974d-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="2974d-141">Wzory sagi | Jak zaimplementować transakcje biznesowe przy użyciu mikrousług</span><span class="sxs-lookup"><span data-stu-id="2974d-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="2974d-142">Wzorzec transakcji kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="2974d-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="2974d-143">Pierwsze za 9-Ball: Cosmos DB Poziom spójności Wyjaśniono</span><span class="sxs-lookup"><span data-stu-id="2974d-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="2974d-144">Eksplorowanie różnych typów baz danych NoSQL część II</span><span class="sxs-lookup"><span data-stu-id="2974d-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="2974d-145">W bazach danych RDBMS, NoSQL i NewSQL. Wywiad z Johnem Ryanem</span><span class="sxs-lookup"><span data-stu-id="2974d-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="2974d-146">SQL vs NoSQL vs NewSQL: Pełne porównanie</span><span class="sxs-lookup"><span data-stu-id="2974d-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="2974d-147">DASH: Cztery właściwości natywnych baz danych Kubernetes</span><span class="sxs-lookup"><span data-stu-id="2974d-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="2974d-148">KaraluchDB</span><span class="sxs-lookup"><span data-stu-id="2974d-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="2974d-149">TiDB (TiDB)</span><span class="sxs-lookup"><span data-stu-id="2974d-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="2974d-150">YugabyteDB (YugabyteDB)</span><span class="sxs-lookup"><span data-stu-id="2974d-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="2974d-151">Witesa</span><span class="sxs-lookup"><span data-stu-id="2974d-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="2974d-152">Elasticsearch: Ostateczny przewodnik</span><span class="sxs-lookup"><span data-stu-id="2974d-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="2974d-153">Wprowadzenie do Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="2974d-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="2974d-154">[Poprzedni](azure-caching.md)
>[następny](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="2974d-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
