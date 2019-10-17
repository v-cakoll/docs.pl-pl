---
title: Co to jest Apache Spark?
description: Dowiedz się więcej na temat scenariuszy Apache Spark i danych Big Data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: ccf41f08df3c68a039210320f14219e6b6229a64
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396237"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="0f20b-103">Co to jest Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="0f20b-103">What is Apache Spark?</span></span>

<span data-ttu-id="0f20b-104">[Apache Spark](https://spark.apache.org/) to platforma przetwarzania równoległego typu open source, która obsługuje przetwarzanie w pamięci w celu zwiększenia wydajności aplikacji, które analizują dane Big Data.</span><span class="sxs-lookup"><span data-stu-id="0f20b-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="0f20b-105">Rozwiązania danych Big Data są przeznaczone do obsługi danych, które są zbyt duże lub złożone dla tradycyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="0f20b-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="0f20b-106">Platforma Spark przetwarza duże ilości danych w pamięci, które są znacznie szybsze niż alternatywy oparte na dyskach.</span><span class="sxs-lookup"><span data-stu-id="0f20b-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span> 

## <a name="common-big-data-scenarios"></a><span data-ttu-id="0f20b-107">Typowe scenariusze danych Big Data</span><span class="sxs-lookup"><span data-stu-id="0f20b-107">Common big data scenarios</span></span>

<span data-ttu-id="0f20b-108">Można rozważyć użycie architektury danych Big Data, jeśli trzeba przechowywać i przetwarzać duże ilości danych, przekształcać dane bez struktury lub przetwarzać dane przesyłane strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="0f20b-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="0f20b-109">Spark to aparat przetwarzania rozproszonego ogólnego przeznaczenia, który może być używany dla kilku scenariuszy danych Big Data.</span><span class="sxs-lookup"><span data-stu-id="0f20b-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span> 

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="0f20b-110">Wyodrębnianie, przekształcanie i ładowanie (ETL)</span><span class="sxs-lookup"><span data-stu-id="0f20b-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="0f20b-111">[Wyodrębnianie, przekształcanie i ładowanie (ETL)](/azure/architecture/data-guide/relational-data/etl) to proces zbierania danych z jednego lub wielu źródeł, modyfikowania danych i przechodzenia danych do nowego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="0f20b-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="0f20b-112">Istnieje kilka sposobów przekształcania danych, w tym:</span><span class="sxs-lookup"><span data-stu-id="0f20b-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="0f20b-113">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="0f20b-113">Filtering</span></span>
* <span data-ttu-id="0f20b-114">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="0f20b-114">Sorting</span></span>
* <span data-ttu-id="0f20b-115">Agregowanie</span><span class="sxs-lookup"><span data-stu-id="0f20b-115">Aggregating</span></span>
* <span data-ttu-id="0f20b-116">Łączenie</span><span class="sxs-lookup"><span data-stu-id="0f20b-116">Joining</span></span>
* <span data-ttu-id="0f20b-117">Czyszczenie</span><span class="sxs-lookup"><span data-stu-id="0f20b-117">Cleaning</span></span>
* <span data-ttu-id="0f20b-118">Deduplikacja</span><span class="sxs-lookup"><span data-stu-id="0f20b-118">Deduplicating</span></span>
* <span data-ttu-id="0f20b-119">Ponownego</span><span class="sxs-lookup"><span data-stu-id="0f20b-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="0f20b-120">Przetwarzanie strumienia danych w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="0f20b-120">Real-time data stream processing</span></span>

<span data-ttu-id="0f20b-121">Dane są przesyłane strumieniowo lub w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="0f20b-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="0f20b-122">Dane telemetryczne z urządzeń IoT, Weblogs i strumieni kliknięć to wszystkie przykłady danych przesyłanych strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="0f20b-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="0f20b-123">Dane w czasie rzeczywistym mogą być przetwarzane w celu zapewnienia użytecznych informacji, takich jak analiza geoprzestrzenna, zdalne monitorowanie i wykrywanie anomalii.</span><span class="sxs-lookup"><span data-stu-id="0f20b-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="0f20b-124">Podobnie jak w przypadku danych relacyjnych, można filtrować, agregować i przygotowywać dane przesyłane strumieniowo przed przeniesieniem danych do ujścia danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="0f20b-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="0f20b-125">Apache Spark obsługuje [Przetwarzanie strumieni danych](/azure/architecture/data-guide/big-data/real-time-processing) w czasie rzeczywistym za poorednictwem [przesyłania strumieniowego Spark](https://spark.apache.org/streaming/).</span><span class="sxs-lookup"><span data-stu-id="0f20b-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span> 

### <a name="batch-processing"></a><span data-ttu-id="0f20b-126">Przetwarzanie wsadowe</span><span class="sxs-lookup"><span data-stu-id="0f20b-126">Batch processing</span></span>

<span data-ttu-id="0f20b-127">[Przetwarzanie wsadowe](/azure/architecture/data-guide/big-data/batch-processing) polega na przetwarzaniu danych Big Data.</span><span class="sxs-lookup"><span data-stu-id="0f20b-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="0f20b-128">Można filtrować, agregować i przygotowywać bardzo duże zestawy danych, korzystając ze długotrwałych zadań.</span><span class="sxs-lookup"><span data-stu-id="0f20b-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="0f20b-129">Uczenie maszynowe przez MLlib</span><span class="sxs-lookup"><span data-stu-id="0f20b-129">Machine learning through MLlib</span></span>

<span data-ttu-id="0f20b-130">Uczenie maszynowe jest używane w przypadku zaawansowanych problemów analitycznych.</span><span class="sxs-lookup"><span data-stu-id="0f20b-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="0f20b-131">Komputer może używać istniejących danych do prognozowania lub przewidywania przyszłych zachowań, rezultatów i trendów.</span><span class="sxs-lookup"><span data-stu-id="0f20b-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="0f20b-132">Biblioteka uczenia maszynowego Apache Spark, [MLlib](https://spark.apache.org/mllib/), zawiera kilka algorytmów uczenia maszynowego i narzędzi.</span><span class="sxs-lookup"><span data-stu-id="0f20b-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="0f20b-133">Przetwarzanie grafu za poorednictwem GraphX</span><span class="sxs-lookup"><span data-stu-id="0f20b-133">Graph processing through GraphX</span></span>

<span data-ttu-id="0f20b-134">Wykres jest kolekcją węzłów połączonych przez krawędzie.</span><span class="sxs-lookup"><span data-stu-id="0f20b-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="0f20b-135">Możesz użyć bazy danych grafu, jeśli masz dane lub dane hierarchiczne z połączonymi relacjami.</span><span class="sxs-lookup"><span data-stu-id="0f20b-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="0f20b-136">Te dane można przetwarzać przy użyciu Apache Spark interfejsu API [GraphX](https://spark.apache.org/graphx/) .</span><span class="sxs-lookup"><span data-stu-id="0f20b-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="0f20b-137">Przetwarzanie danych SQL i strukturalnych przy użyciu platformy Spark SQL</span><span class="sxs-lookup"><span data-stu-id="0f20b-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="0f20b-138">Jeśli pracujesz ze strukturą (sformatowaną) danymi, możesz użyć zapytań SQL w aplikacji Spark przy użyciu [platformy Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="0f20b-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="0f20b-139">Architektura Apache Spark</span><span class="sxs-lookup"><span data-stu-id="0f20b-139">Apache Spark architecture</span></span>

<span data-ttu-id="0f20b-140">Apache Spark, która używa architektury Master/Worker, ma trzy główne składniki: Sterownik, wykonawcy i Menedżera klastra.</span><span class="sxs-lookup"><span data-stu-id="0f20b-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="0f20b-142">Sterownik</span><span class="sxs-lookup"><span data-stu-id="0f20b-142">Driver</span></span>

<span data-ttu-id="0f20b-143">Sterownik składa się z programu, takiego jak C# Aplikacja konsolowa i sesja platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="0f20b-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="0f20b-144">Sesja platformy Spark pobiera program i dzieli go na mniejsze zadania, które są obsługiwane przez wykonawcy.</span><span class="sxs-lookup"><span data-stu-id="0f20b-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="0f20b-145">Wykonawców</span><span class="sxs-lookup"><span data-stu-id="0f20b-145">Executors</span></span>

<span data-ttu-id="0f20b-146">Każdy wykonawca lub węzeł procesu roboczego odbiera zadanie ze sterownika i wykonuje to zadanie.</span><span class="sxs-lookup"><span data-stu-id="0f20b-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="0f20b-147">Wykonawcy znajdują się w jednostce znanej jako klaster.</span><span class="sxs-lookup"><span data-stu-id="0f20b-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="0f20b-148">Menedżer klastra</span><span class="sxs-lookup"><span data-stu-id="0f20b-148">Cluster manager</span></span>

<span data-ttu-id="0f20b-149">Menedżer klastra komunikuje się zarówno z sterownikiem, jak i modułami wykonującymi:</span><span class="sxs-lookup"><span data-stu-id="0f20b-149">The cluster manager communicates with both the driver and the executors to:</span></span>

- <span data-ttu-id="0f20b-150">Zarządzanie alokacją zasobów</span><span class="sxs-lookup"><span data-stu-id="0f20b-150">Manage resource allocation</span></span>
- <span data-ttu-id="0f20b-151">Zarządzanie dzieleniem programu</span><span class="sxs-lookup"><span data-stu-id="0f20b-151">Manage program division</span></span>
- <span data-ttu-id="0f20b-152">Zarządzanie wykonywaniem programu</span><span class="sxs-lookup"><span data-stu-id="0f20b-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="0f20b-153">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="0f20b-153">Language support</span></span>

<span data-ttu-id="0f20b-154">Apache Spark obsługuje następujące języki programowania:</span><span class="sxs-lookup"><span data-stu-id="0f20b-154">Apache Spark supports the following programming languages:</span></span>

- <span data-ttu-id="0f20b-155">Scala</span><span class="sxs-lookup"><span data-stu-id="0f20b-155">Scala</span></span>
- <span data-ttu-id="0f20b-156">Python</span><span class="sxs-lookup"><span data-stu-id="0f20b-156">Python</span></span>
- <span data-ttu-id="0f20b-157">Java</span><span class="sxs-lookup"><span data-stu-id="0f20b-157">Java</span></span>
- <span data-ttu-id="0f20b-158">SQL</span><span class="sxs-lookup"><span data-stu-id="0f20b-158">SQL</span></span>
- <span data-ttu-id="0f20b-159">R</span><span class="sxs-lookup"><span data-stu-id="0f20b-159">R</span></span>
- <span data-ttu-id="0f20b-160">.NET</span><span class="sxs-lookup"><span data-stu-id="0f20b-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="0f20b-161">Interfejsy API platformy Spark</span><span class="sxs-lookup"><span data-stu-id="0f20b-161">Spark APIs</span></span>

<span data-ttu-id="0f20b-162">Apache Spark obsługuje następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="0f20b-162">Apache Spark supports the following APIs:</span></span>

- [<span data-ttu-id="0f20b-163">Interfejs API platformy Spark Scala</span><span class="sxs-lookup"><span data-stu-id="0f20b-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
- [<span data-ttu-id="0f20b-164">Interfejs API języka Java platformy Spark</span><span class="sxs-lookup"><span data-stu-id="0f20b-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
- [<span data-ttu-id="0f20b-165">Interfejs API języka Python platformy Spark</span><span class="sxs-lookup"><span data-stu-id="0f20b-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
- [<span data-ttu-id="0f20b-166">Interfejs API platformy Spark języka R</span><span class="sxs-lookup"><span data-stu-id="0f20b-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
- <span data-ttu-id="0f20b-167">[Platforma Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), funkcje wbudowane</span><span class="sxs-lookup"><span data-stu-id="0f20b-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="0f20b-168">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0f20b-168">Next steps</span></span>

<span data-ttu-id="0f20b-169">Dowiedz się, jak za pomocą Apache Spark w aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="0f20b-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="0f20b-170">Przy użyciu platformy .NET dla Apache Spark deweloperzy z interfejsem .NET i logiką biznesową mogą zapisywać C# zapytania F#dotyczące danych Big Data w i.</span><span class="sxs-lookup"><span data-stu-id="0f20b-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0f20b-171">Co to jest platforma .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="0f20b-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
