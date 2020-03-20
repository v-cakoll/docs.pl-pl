---
title: Co to jest platforma .NET dla platformy Apache Spark?
description: Dowiedz się więcej o platformie .NET for Apache Spark, bezpłatnej, otwartej i wieloplatformowej platformie analizy dużych zbiorów danych, która zabiera platformę Spark do dowolnego miejsca, w której piszesz kod .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458202"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="8f5ae-103">Co to jest platforma .NET dla platformy Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="8f5ae-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="8f5ae-104">[Apache Spark](what-is-spark.md) to aparat przetwarzania rozproszonego ogólnego przeznaczenia do analizy dużych zestawów danych — zazwyczaj terabajtów lub petabajtów danych.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="8f5ae-105">Dzięki platformie .NET for Apache Spark, bezpłatnej, open-source i wieloplatformowej obsłudze platformy .NET dla popularnej platformy analizy dużych zbiorów danych typu open source, możesz teraz dodać moc platformy Apache Spark do aplikacji big data, używając już języków, które znasz.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="8f5ae-106">Dlaczego warto wybrać .NET dla Apache Spark?</span><span class="sxs-lookup"><span data-stu-id="8f5ae-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="8f5ae-107">Platforma .NET for Apache Spark umożliwia deweloperom dostęp do środowiska platformy .NET lub bazy kodu do udziału w świecie analizy dużych zbiorów danych.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="8f5ae-108">.NET for Apache Spark zapewnia wysokiej wydajności interfejsów API do korzystania z spark z języka C# i F#.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="8f5ae-109">Dzięki c# i F#, można uzyskać dostęp:</span><span class="sxs-lookup"><span data-stu-id="8f5ae-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="8f5ae-110">DataFrame i SparkSQL do pracy z danymi strukturalnymi.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="8f5ae-111">Spark Structured Streaming do pracy z danymi przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="8f5ae-112">Spark SQL do pisania zapytań ze składnią SQL.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="8f5ae-113">Integracja uczenia maszynowego dla szybszego szkolenia i przewidywania (czyli użyj .NET dla Apache Spark wraz [ML.NET](https://dot.net/ml)).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="8f5ae-114">Platforma .NET for Apache Spark jest zgodna ze standardem .NET Standard, formalną specyfikacją interfejsów API platformy .NET, które są wspólne dla implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="8f5ae-115">Oznacza to, że można użyć .NET dla Apache Spark w dowolnym miejscu piszesz .NET kod pozwala na ponowne wykorzystanie całej wiedzy, umiejętności, kodu i bibliotek, które już masz jako deweloper .NET.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="8f5ae-116">Program .NET for Apache Spark działa w systemach Windows, Linux i macOS przy użyciu programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="8f5ae-117">Działa również w systemie Windows przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="8f5ae-118">Aplikacje można wdrożyć we wszystkich głównych dostawcach usług w chmurze, w tym usługi Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks i Databricks w usłudze AWS.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="8f5ae-119">.NET dla architektury Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8f5ae-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="8f5ae-120">Powiązanie języka C#/ F# z programem Spark jest zapisywane na nowej warstwie interop platformy Spark, która oferuje łatwiejszą rozszerzalność.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="8f5ae-121">Ta nowa warstwa interop platformy Spark została napisana przy użyciu najlepszych rozwiązań dotyczących rozszerzenia języka i optymalizuje interop i wydajność.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="8f5ae-122">Długoterminowe, ta rozszerzalność może służyć do dodawania obsługi innych języków w spark.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="8f5ae-123">![.NET dla architektury Apache Spark](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="8f5ae-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="8f5ae-124">Możesz dowiedzieć się o obsłudze interop dla rozszerzeń języka Spark z [propozycji](https://issues.apache.org/jira/browse/SPARK-26257).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="8f5ae-125">.NET dla wydajności Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8f5ae-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="8f5ae-126">W porównaniu z Python i Scala przy użyciu [testu porównawczego TPC-H](http://www.tpc.org/tpch/), .NET dla Apache Spark działa dobrze w większości przypadków i jest 2x szybciej niż Python, gdy wydajność funkcji zdefiniowana przez użytkownika jest krytyczna.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="8f5ae-127">Trwają działania na rzecz poprawy i wyników odniesienia.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="8f5ae-128">Aby wykonać własne testy porównawcze, zapoznaj się z punktami odniesienia dostępnymi w [programie .NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="8f5ae-129">.NET dla Apache Spark mapa drogowa</span><span class="sxs-lookup"><span data-stu-id="8f5ae-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="8f5ae-130">Dowiedz się więcej o planach krótkoterminowych i długoterminowych z oficjalnego [planu .NET for Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="8f5ae-131">Fundacja .NET</span><span class="sxs-lookup"><span data-stu-id="8f5ae-131">.NET Foundation</span></span>

<span data-ttu-id="8f5ae-132">Projekt .NET for Apache Spark jest częścią [programu .NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="8f5ae-133">Contributions (Zmiany zawartości)</span><span class="sxs-lookup"><span data-stu-id="8f5ae-133">Contributions</span></span>

<span data-ttu-id="8f5ae-134">Zespół platformy .NET for Apache Spark zachęca do udziału w programach, zarówno problemów z githubem, jak i żądań ściągania.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="8f5ae-135">Najpierw poszukaj [istniejącego problemu](https://github.com/dotnet/spark/issues).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="8f5ae-136">Jeśli nie możesz znaleźć istniejącego problemu, [otwórz nowy problem](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="8f5ae-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8f5ae-137">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8f5ae-137">Next steps</span></span>

<span data-ttu-id="8f5ae-138">Wypróbuj .NET dla Platformy Spark apache.</span><span class="sxs-lookup"><span data-stu-id="8f5ae-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8f5ae-139">Samouczek: Wprowadzenie do platformy .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8f5ae-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
