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
# <a name="what-is-net-for-apache-spark"></a>Co to jest platforma .NET dla platformy Apache Spark?

[Apache Spark](what-is-spark.md) to aparat przetwarzania rozproszonego ogólnego przeznaczenia do analizy dużych zestawów danych — zazwyczaj terabajtów lub petabajtów danych. Dzięki platformie .NET for Apache Spark, bezpłatnej, open-source i wieloplatformowej obsłudze platformy .NET dla popularnej platformy analizy dużych zbiorów danych typu open source, możesz teraz dodać moc platformy Apache Spark do aplikacji big data, używając już języków, które znasz.

## <a name="why-choose-net-for-apache-spark"></a>Dlaczego warto wybrać .NET dla Apache Spark?

Platforma .NET for Apache Spark umożliwia deweloperom dostęp do środowiska platformy .NET lub bazy kodu do udziału w świecie analizy dużych zbiorów danych. .NET for Apache Spark zapewnia wysokiej wydajności interfejsów API do korzystania z spark z języka C# i F#. Dzięki c# i F#, można uzyskać dostęp:

* DataFrame i SparkSQL do pracy z danymi strukturalnymi.
* Spark Structured Streaming do pracy z danymi przesyłania strumieniowego.
* Spark SQL do pisania zapytań ze składnią SQL.
* Integracja uczenia maszynowego dla szybszego szkolenia i przewidywania (czyli użyj .NET dla Apache Spark wraz [ML.NET](https://dot.net/ml)).

Platforma .NET for Apache Spark jest zgodna ze standardem .NET Standard, formalną specyfikacją interfejsów API platformy .NET, które są wspólne dla implementacji platformy .NET. Oznacza to, że można użyć .NET dla Apache Spark w dowolnym miejscu piszesz .NET kod pozwala na ponowne wykorzystanie całej wiedzy, umiejętności, kodu i bibliotek, które już masz jako deweloper .NET.

Program .NET for Apache Spark działa w systemach Windows, Linux i macOS przy użyciu programu .NET Core. Działa również w systemie Windows przy użyciu programu .NET Framework. Aplikacje można wdrożyć we wszystkich głównych dostawcach usług w chmurze, w tym usługi Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks i Databricks w usłudze AWS.

## <a name="net-for-apache-spark-architecture"></a>.NET dla architektury Apache Spark

Powiązanie języka C#/ F# z programem Spark jest zapisywane na nowej warstwie interop platformy Spark, która oferuje łatwiejszą rozszerzalność. Ta nowa warstwa interop platformy Spark została napisana przy użyciu najlepszych rozwiązań dotyczących rozszerzenia języka i optymalizuje interop i wydajność. Długoterminowe, ta rozszerzalność może służyć do dodawania obsługi innych języków w spark.

> [!div class="mx-imgBorder"]
> ![.NET dla architektury Apache Spark](media/dotnet-spark-architecture.png)

Możesz dowiedzieć się o obsłudze interop dla rozszerzeń języka Spark z [propozycji](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>.NET dla wydajności Apache Spark

W porównaniu z Python i Scala przy użyciu [testu porównawczego TPC-H](http://www.tpc.org/tpch/), .NET dla Apache Spark działa dobrze w większości przypadków i jest 2x szybciej niż Python, gdy wydajność funkcji zdefiniowana przez użytkownika jest krytyczna. Trwają działania na rzecz poprawy i wyników odniesienia.

Aby wykonać własne testy porównawcze, zapoznaj się z punktami odniesienia dostępnymi w [programie .NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>.NET dla Apache Spark mapa drogowa

Dowiedz się więcej o planach krótkoterminowych i długoterminowych z oficjalnego [planu .NET for Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).

## <a name="net-foundation"></a>Fundacja .NET

Projekt .NET for Apache Spark jest częścią [programu .NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Contributions (Zmiany zawartości)

Zespół platformy .NET for Apache Spark zachęca do udziału w programach, zarówno problemów z githubem, jak i żądań ściągania. Najpierw poszukaj [istniejącego problemu](https://github.com/dotnet/spark/issues). Jeśli nie możesz znaleźć istniejącego problemu, [otwórz nowy problem](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Następne kroki

Wypróbuj .NET dla Platformy Spark apache.
> [!div class="nextstepaction"]
> [Samouczek: Wprowadzenie do platformy .NET for Apache Spark](./tutorials/get-started.md)
