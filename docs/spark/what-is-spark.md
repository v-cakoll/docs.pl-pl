---
title: Co to jest platforma Apache Spark?
description: Dowiedz się więcej o apache spark i scenariuszach dużych zbiorów danych.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458176"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="840ec-103">Co to jest platforma Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="840ec-103">What is Apache Spark?</span></span>

<span data-ttu-id="840ec-104">[Apache Spark](https://spark.apache.org/) to platforma przetwarzania równoległego typu open source, która obsługuje przetwarzanie w pamięci w celu zwiększenia wydajności aplikacji analizujących duże zbiory danych.</span><span class="sxs-lookup"><span data-stu-id="840ec-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="840ec-105">Rozwiązania big data są przeznaczone do obsługi danych, które są zbyt duże lub złożone dla tradycyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="840ec-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="840ec-106">Platforma Spark przetwarza duże ilości danych w pamięci, co jest znacznie szybsze niż alternatywy oparte na dysku.</span><span class="sxs-lookup"><span data-stu-id="840ec-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="840ec-107">Typowe scenariusze dużych zbiorów danych</span><span class="sxs-lookup"><span data-stu-id="840ec-107">Common big data scenarios</span></span>

<span data-ttu-id="840ec-108">Można rozważyć architekturę dużych zbiorów danych, jeśli trzeba przechowywać i przetwarzać duże ilości danych, przekształcać dane bez struktury lub przetwarzać dane strumieniowe.</span><span class="sxs-lookup"><span data-stu-id="840ec-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="840ec-109">Spark to aparat przetwarzania rozproszonego ogólnego przeznaczenia, który może być używany w kilku scenariuszach dużych zbiorów danych.</span><span class="sxs-lookup"><span data-stu-id="840ec-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="840ec-110">Wyodrębnianie, przekształcanie i ładowanie (ETL)</span><span class="sxs-lookup"><span data-stu-id="840ec-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="840ec-111">[Wyodrębnianie, przekształcanie i ładowanie (ETL)](/azure/architecture/data-guide/relational-data/etl) to proces zbierania danych z jednego lub wielu źródeł, modyfikowania danych i przenoszenia danych do nowego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="840ec-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="840ec-112">Istnieje kilka sposobów przekształcania danych, w tym:</span><span class="sxs-lookup"><span data-stu-id="840ec-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="840ec-113">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="840ec-113">Filtering</span></span>
* <span data-ttu-id="840ec-114">Sortowanie</span><span class="sxs-lookup"><span data-stu-id="840ec-114">Sorting</span></span>
* <span data-ttu-id="840ec-115">Agregowania</span><span class="sxs-lookup"><span data-stu-id="840ec-115">Aggregating</span></span>
* <span data-ttu-id="840ec-116">Dołączenie</span><span class="sxs-lookup"><span data-stu-id="840ec-116">Joining</span></span>
* <span data-ttu-id="840ec-117">Czyszczenia</span><span class="sxs-lookup"><span data-stu-id="840ec-117">Cleaning</span></span>
* <span data-ttu-id="840ec-118">Deduplikowanie</span><span class="sxs-lookup"><span data-stu-id="840ec-118">Deduplicating</span></span>
* <span data-ttu-id="840ec-119">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="840ec-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="840ec-120">Przetwarzanie strumienia danych w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="840ec-120">Real-time data stream processing</span></span>

<span data-ttu-id="840ec-121">Przesyłanie strumieniowe lub w czasie rzeczywistym dane są danymi w ruchu.</span><span class="sxs-lookup"><span data-stu-id="840ec-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="840ec-122">Telemetria z urządzeń IoT, blogów i strumieni kliknięć są przykładami przesyłania strumieniowego danych.</span><span class="sxs-lookup"><span data-stu-id="840ec-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="840ec-123">Dane w czasie rzeczywistym mogą być przetwarzane w celu dostarczenia przydatnych informacji, takich jak analiza geoprzestrzenna, zdalne monitorowanie i wykrywanie anomalii.</span><span class="sxs-lookup"><span data-stu-id="840ec-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="840ec-124">Podobnie jak dane relacyjne, można filtrować, agregować i przygotowywać dane przesyłania strumieniowego przed przeniesieniem danych do ujścia danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="840ec-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="840ec-125">Apache Spark obsługuje [przetwarzanie strumienia danych w czasie rzeczywistym](/azure/architecture/data-guide/big-data/real-time-processing) za pośrednictwem usługi Spark [Streaming.](https://spark.apache.org/streaming/)</span><span class="sxs-lookup"><span data-stu-id="840ec-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="840ec-126">Przetwarzanie wsadowe</span><span class="sxs-lookup"><span data-stu-id="840ec-126">Batch processing</span></span>

<span data-ttu-id="840ec-127">[Przetwarzanie wsadowe](/azure/architecture/data-guide/big-data/batch-processing) polega na przetwarzaniu dużych zbiorów danych w spoczynku.</span><span class="sxs-lookup"><span data-stu-id="840ec-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="840ec-128">Można filtrować, agregować i przygotowywać bardzo duże zestawy danych przy użyciu długotrwałych zadań równolegle.</span><span class="sxs-lookup"><span data-stu-id="840ec-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="840ec-129">Uczenie maszynowe za pośrednictwem MLlib</span><span class="sxs-lookup"><span data-stu-id="840ec-129">Machine learning through MLlib</span></span>

<span data-ttu-id="840ec-130">Uczenie maszynowe jest używane do zaawansowanych problemów analitycznych.</span><span class="sxs-lookup"><span data-stu-id="840ec-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="840ec-131">Komputer może używać istniejących danych do prognozowania lub przewidywania przyszłych zachowań, wyników i trendów.</span><span class="sxs-lookup"><span data-stu-id="840ec-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="840ec-132">Biblioteka uczenia maszynowego Apache Spark, [MLlib,](https://spark.apache.org/mllib/)zawiera kilka algorytmów uczenia maszynowego i narzędzi.</span><span class="sxs-lookup"><span data-stu-id="840ec-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="840ec-133">Przetwarzanie wykresów za pośrednictwem GraphX</span><span class="sxs-lookup"><span data-stu-id="840ec-133">Graph processing through GraphX</span></span>

<span data-ttu-id="840ec-134">Wykres jest zbiorem węzłów połączonych krawędziami.</span><span class="sxs-lookup"><span data-stu-id="840ec-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="840ec-135">Jeśli masz dane hierarchiczne lub dane z połączonymi relacjami, możesz użyć bazy danych wykresów.</span><span class="sxs-lookup"><span data-stu-id="840ec-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="840ec-136">Można przetwarzać te dane przy użyciu api [GraphX](https://spark.apache.org/graphx/) firmy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="840ec-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="840ec-137">Przetwarzanie danych SQL i strukturalnych za pomocą programu Spark SQL</span><span class="sxs-lookup"><span data-stu-id="840ec-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="840ec-138">Jeśli pracujesz z danymi strukturalnymi (sformatowanymi), możesz użyć zapytań SQL w aplikacji Spark przy użyciu [programu Spark SQL](https://spark.apache.org/sql/).</span><span class="sxs-lookup"><span data-stu-id="840ec-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="840ec-139">Architektura Apache Spark</span><span class="sxs-lookup"><span data-stu-id="840ec-139">Apache Spark architecture</span></span>

<span data-ttu-id="840ec-140">Apache Spark, który używa architektury master/worker, ma trzy główne składniki: sterownik, executors i menedżera klastra.</span><span class="sxs-lookup"><span data-stu-id="840ec-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="840ec-142">Sterownik</span><span class="sxs-lookup"><span data-stu-id="840ec-142">Driver</span></span>

<span data-ttu-id="840ec-143">Sterownik składa się z programu, takich jak aplikacja konsoli Języka C# i sesji Platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="840ec-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="840ec-144">Sesja Spark pobiera program i dzieli go na mniejsze zadania, które są obsługiwane przez wykonawców.</span><span class="sxs-lookup"><span data-stu-id="840ec-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="840ec-145">Executors</span><span class="sxs-lookup"><span data-stu-id="840ec-145">Executors</span></span>

<span data-ttu-id="840ec-146">Każdy wykonawca lub węzeł procesu roboczego odbiera zadanie od sterownika i wykonuje to zadanie.</span><span class="sxs-lookup"><span data-stu-id="840ec-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="840ec-147">Executors znajdują się na jednostce znanej jako klaster.</span><span class="sxs-lookup"><span data-stu-id="840ec-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="840ec-148">Menedżer klastrów</span><span class="sxs-lookup"><span data-stu-id="840ec-148">Cluster manager</span></span>

<span data-ttu-id="840ec-149">Menedżer klastra komunikuje się zarówno ze sterownikiem, jak i wykonawcami w celu:</span><span class="sxs-lookup"><span data-stu-id="840ec-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="840ec-150">Zarządzanie alokacją zasobów</span><span class="sxs-lookup"><span data-stu-id="840ec-150">Manage resource allocation</span></span>
* <span data-ttu-id="840ec-151">Zarządzanie podziałem programu</span><span class="sxs-lookup"><span data-stu-id="840ec-151">Manage program division</span></span>
* <span data-ttu-id="840ec-152">Zarządzanie wykonywaniem programu</span><span class="sxs-lookup"><span data-stu-id="840ec-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="840ec-153">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="840ec-153">Language support</span></span>

<span data-ttu-id="840ec-154">Apache Spark obsługuje następujące języki programowania:</span><span class="sxs-lookup"><span data-stu-id="840ec-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="840ec-155">Scala</span><span class="sxs-lookup"><span data-stu-id="840ec-155">Scala</span></span>
* <span data-ttu-id="840ec-156">Python</span><span class="sxs-lookup"><span data-stu-id="840ec-156">Python</span></span>
* <span data-ttu-id="840ec-157">Java</span><span class="sxs-lookup"><span data-stu-id="840ec-157">Java</span></span>
* <span data-ttu-id="840ec-158">SQL</span><span class="sxs-lookup"><span data-stu-id="840ec-158">SQL</span></span>
* <span data-ttu-id="840ec-159">R</span><span class="sxs-lookup"><span data-stu-id="840ec-159">R</span></span>
* <span data-ttu-id="840ec-160">.NET</span><span class="sxs-lookup"><span data-stu-id="840ec-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="840ec-161">Interfejsy API platformy Spark</span><span class="sxs-lookup"><span data-stu-id="840ec-161">Spark APIs</span></span>

<span data-ttu-id="840ec-162">Apache Spark obsługuje następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="840ec-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="840ec-163">Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="840ec-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="840ec-164">Spark Java API</span><span class="sxs-lookup"><span data-stu-id="840ec-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="840ec-165">Spark Python API</span><span class="sxs-lookup"><span data-stu-id="840ec-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="840ec-166">Spark R API</span><span class="sxs-lookup"><span data-stu-id="840ec-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="840ec-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), wbudowane funkcje</span><span class="sxs-lookup"><span data-stu-id="840ec-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="840ec-168">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="840ec-168">Next steps</span></span>

<span data-ttu-id="840ec-169">Dowiedz się, jak używać aplikacji Apache Spark w aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="840ec-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="840ec-170">Dzięki platformie .NET for Apache Spark deweloperzy z funkcją .NET i logiką biznesową mogą zapisywać zapytania o duże zbiory danych w językach C# i F#.</span><span class="sxs-lookup"><span data-stu-id="840ec-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="840ec-171">Co to jest .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="840ec-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
