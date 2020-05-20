---
title: Elasticsearch w aplikacjach natywnych w chmurze
description: Dowiedz się więcej na temat dodawania funkcji wyszukiwania elastycznego do aplikacji natywnych w chmurze.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: e956f28877d88ce5279944964a877efc324918b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614087"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="f6473-103">Elasticsearch w aplikacji natywnej w chmurze</span><span class="sxs-lookup"><span data-stu-id="f6473-103">Elasticsearch in a cloud-native app</span></span>

<span data-ttu-id="f6473-104">Elasticsearch to rozproszony system wyszukiwania i analizy, który umożliwia złożone funkcje wyszukiwania w różnych typach danych.</span><span class="sxs-lookup"><span data-stu-id="f6473-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="f6473-105">Jest to "open source" i szeroko popularne.</span><span class="sxs-lookup"><span data-stu-id="f6473-105">It's open source and widely popular.</span></span> <span data-ttu-id="f6473-106">Rozważ, jak następujące firmy integrują Elasticsearch z aplikacjami:</span><span class="sxs-lookup"><span data-stu-id="f6473-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="f6473-107">[Witrynę Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) do wyszukiwania pełnotekstowego i przyrostowego (wyszukiwanie w trakcie pisania).</span><span class="sxs-lookup"><span data-stu-id="f6473-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="f6473-108">W witrynie [GitHub](https://www.elastic.co/customers/github) można indeksować i uwidaczniać ponad 8 000 000 repozytoriów kodu.</span><span class="sxs-lookup"><span data-stu-id="f6473-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="f6473-109">Platforma [Docker](https://www.elastic.co/customers/docker) umożliwiająca odnajdywanie biblioteki kontenerów.</span><span class="sxs-lookup"><span data-stu-id="f6473-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="f6473-110">Elasticsearch jest oparta na aparacie wyszukiwania pełnotekstowego [Apache Lucene](https://lucene.apache.org/core/) .</span><span class="sxs-lookup"><span data-stu-id="f6473-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="f6473-111">Lucene umożliwiają indeksowanie dokumentów o wysokiej wydajności i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="f6473-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="f6473-112">Indeksuje dane z odwróconym schematem indeksowania — zamiast mapowania stron do słów kluczowych, mapuje słowa kluczowe na strony w taki sam sposób jak słownik na końcu książki.</span><span class="sxs-lookup"><span data-stu-id="f6473-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="f6473-113">Lucene mają zaawansowane możliwości składni zapytań i mogą wykonywać zapytania dotyczące danych, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f6473-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="f6473-114">Term (pełny wyraz)</span><span class="sxs-lookup"><span data-stu-id="f6473-114">Term (a full word)</span></span>
- <span data-ttu-id="f6473-115">Prefiks (zaczyna się od Word)</span><span class="sxs-lookup"><span data-stu-id="f6473-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="f6473-116">Symbol wieloznaczny (przy użyciu \* filtrów "" lub "?")</span><span class="sxs-lookup"><span data-stu-id="f6473-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="f6473-117">Phrase (sekwencja tekstu w dokumencie)</span><span class="sxs-lookup"><span data-stu-id="f6473-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="f6473-118">Wartość logiczna (złożone wyszukiwania łączące zapytania)</span><span class="sxs-lookup"><span data-stu-id="f6473-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="f6473-119">Podczas gdy Lucene, udostępniają instalację niskiego poziomu na potrzeby wyszukiwania, Elasticsearch udostępnia serwer, który znajduje się na podstawie Lucene.</span><span class="sxs-lookup"><span data-stu-id="f6473-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="f6473-120">Elasticsearch dodaje funkcje wyższego poziomu, aby uprościć pracę Lucene, łącznie z interfejsem API RESTful w celu uzyskania dostępu do funkcji indeksowania i wyszukiwania Lucene.</span><span class="sxs-lookup"><span data-stu-id="f6473-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="f6473-121">Zapewnia również infrastrukturę rozproszoną, która umożliwia ogromne skalowanie, odporność na uszkodzenia i wysoką dostępność.</span><span class="sxs-lookup"><span data-stu-id="f6473-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="f6473-122">W przypadku większych aplikacji natywnych w chmurze, które mają złożone wymagania dotyczące wyszukiwania, Elasticsearch jest dostępny jako usługa zarządzana na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f6473-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="f6473-123">Wstępnie skonfigurowane szablony funkcji Microsoft Azure Marketplace, których deweloperzy mogą używać do wdrażania klastra Elasticsearch na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f6473-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="f6473-124">W Microsoft Azure Marketplace deweloperzy mogą korzystać ze wstępnie skonfigurowanych szablonów utworzonych w celu szybkiego wdrożenia klastra Elasticsearch na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f6473-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="f6473-125">Korzystając z oferty zarządzanej przez platformę Azure, można wdrożyć maksymalnie 50 węzłów danych, 20 koordynujące węzły i trzy dedykowane węzły główne.</span><span class="sxs-lookup"><span data-stu-id="f6473-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="f6473-126">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f6473-126">Summary</span></span>

<span data-ttu-id="f6473-127">W tym rozdziale przedstawiono szczegółowe dane w systemach natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="f6473-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="f6473-128">Rozpoczęto od różnicowania magazynu danych w aplikacjach monolitycznych ze wzorcami magazynu danych w systemach natywnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="f6473-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="f6473-129">Oglądamy wzorce danych zaimplementowane w systemach natywnych w chmurze, w tym zapytania międzyusługowe, transakcje rozproszone i wzorce, aby zająć się systemami o dużej pojemności.</span><span class="sxs-lookup"><span data-stu-id="f6473-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="f6473-130">Korzystamy z kodu SQL z danymi NoSQL.</span><span class="sxs-lookup"><span data-stu-id="f6473-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="f6473-131">Znaleźliśmy dostępne opcje przechowywania danych na platformie Azure, które obejmują opcje skoncentrowane na firmie Microsoft i w trybie Open Source.</span><span class="sxs-lookup"><span data-stu-id="f6473-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="f6473-132">Wreszcie omawiamy buforowanie i Elasticsearch w aplikacji natywnej w chmurze.</span><span class="sxs-lookup"><span data-stu-id="f6473-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="f6473-133">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="f6473-133">References</span></span>

- [<span data-ttu-id="f6473-134">Wzorzec podziału odpowiedzialności polecenia i zapytania (CQRS)</span><span class="sxs-lookup"><span data-stu-id="f6473-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="f6473-135">Wzorzec określania źródła zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f6473-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="f6473-136">Dlaczego RDBMS jest odporna na partycje w CAP theorem i dlaczego jest dostępna?</span><span class="sxs-lookup"><span data-stu-id="f6473-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="f6473-137">Zmaterializowany widok</span><span class="sxs-lookup"><span data-stu-id="f6473-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="f6473-138">Wszystko, co naprawdę trzeba wiedzieć na temat baz danych open source</span><span class="sxs-lookup"><span data-stu-id="f6473-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="f6473-139">Wzorzec transakcji kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="f6473-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="f6473-140">Wzorzec Saga</span><span class="sxs-lookup"><span data-stu-id="f6473-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="f6473-141">Wzorce Saga | Jak zaimplementować transakcje biznesowe przy użyciu mikrousług</span><span class="sxs-lookup"><span data-stu-id="f6473-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="f6473-142">Wzorzec transakcji kompensacyjnych</span><span class="sxs-lookup"><span data-stu-id="f6473-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="f6473-143">Po 9-piłkę: Cosmos DB poziomów spójności wyjaśniono</span><span class="sxs-lookup"><span data-stu-id="f6473-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="f6473-144">Eksplorowanie różnych typów baz danych NoSQL część II</span><span class="sxs-lookup"><span data-stu-id="f6473-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="f6473-145">W bazach danych RDBMS, NoSQL i NewSQL. Wywiad z John Ryan</span><span class="sxs-lookup"><span data-stu-id="f6473-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="f6473-146">SQL vs NoSQL vs NewSQL: pełne porównanie</span><span class="sxs-lookup"><span data-stu-id="f6473-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="f6473-147">KRESKa: cztery właściwości natywnych baz danych Kubernetes</span><span class="sxs-lookup"><span data-stu-id="f6473-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="f6473-148">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="f6473-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="f6473-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="f6473-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="f6473-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="f6473-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="f6473-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="f6473-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="f6473-152">Elasticsearch: Ostateczny Przewodnik</span><span class="sxs-lookup"><span data-stu-id="f6473-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="f6473-153">Wprowadzenie do oprogramowania Apache Lucene</span><span class="sxs-lookup"><span data-stu-id="f6473-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="f6473-154">[Poprzedni](azure-caching.md) 
> [Dalej](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="f6473-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
