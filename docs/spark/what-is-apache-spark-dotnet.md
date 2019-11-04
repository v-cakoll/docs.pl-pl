---
title: Co to jest platforma .NET dla platformy Apache Spark?
description: Dowiedz się więcej na temat platformy .NET dla Apache Spark, bezpłatnej, typu open source i międzyplatformowej platformy do analizy danych Big Data, która wymaga platformy Spark w dowolnym miejscu pisania kodu platformy .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458202"
---
# <a name="what-is-net-for-apache-spark"></a>Co to jest platforma .NET dla platformy Apache Spark?

[Apache Spark](what-is-spark.md) to aparat przetwarzania rozproszonego ogólnego przeznaczenia na potrzeby analiz przez duże zbiory danych — zazwyczaj terabajty lub petabajtów danych. Za pomocą platformy .NET dla Apache Spark, bezpłatna, typu open source i międzyplatformowego wsparcia platformy .NET dla popularnej struktury analizy danych Big Data dla typu open source, możesz teraz dodawać możliwości Apache Spark do aplikacji do obsługi danych Big Data przy użyciu języków, które już znasz.

## <a name="why-choose-net-for-apache-spark"></a>Dlaczego warto wybrać platformę .NET dla Apache Spark?

Program .NET dla Apache Spark umożliwia deweloperom korzystanie z platformy .NET lub baz kodu do wzięcia udziału w świecie analizy danych Big Data. Platforma .NET dla Apache Spark oferuje interfejsy API o wysokiej wydajności służące do korzystania z platformy Spark z C# systemów i F#. Za C# pomocą F#i można uzyskać dostęp do:

* Dataframe i SparkSQL do pracy z danymi strukturalnymi.
* Przesyłanie strumieniowe platformy Spark do pracy z danymi przesyłanymi strumieniowo.
* Program Spark SQL do pisania zapytań ze składnią SQL.
* Integracja z uczeniem maszynowym zapewniająca szybsze szkolenia i prognozowanie (czyli korzystanie z platformy .NET dla Apache Spark obok [ml.NET](https://dot.net/ml)).

Platforma .NET dla Apache Spark jest zgodna z .NET Standard, formalną specyfikacją interfejsów API platformy .NET, które są wspólne dla implementacji platformy .NET. Oznacza to, że można używać platformy .NET do Apache Spark dowolnego miejsca, w którym piszesz kod platformy .NET, aby można było ponownie wykorzystać wszystkie wiedzę, umiejętności, kod i biblioteki, które już masz jako deweloper platformy .NET.

Środowisko .NET dla Apache Spark działa w systemach Windows, Linux i macOS przy użyciu platformy .NET Core. Jest on również uruchamiany w systemie Windows przy użyciu .NET Framework. Aplikacje można wdrażać dla wszystkich głównych dostawców chmury, takich jak Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks i datakosteks w AWS.

## <a name="net-for-apache-spark-architecture"></a>Architektura .NET dla Apache Spark

C#Powiązanie F# języka z platformą Spark jest zapisywane w nowej warstwie międzyoperacyjności platformy Spark, która oferuje łatwiejsze rozszerzanie. Ta nowa warstwa międzyoperacyjności platformy Spark została opracowana przy użyciu najlepszych rozwiązań dotyczących rozszerzenia języka i zoptymalizowanych pod kątem współdziałania i wydajności. Długoterminowe, takie rozszerzalność może służyć do dodawania obsługi innych języków w usłudze Spark.

> [!div class="mx-imgBorder"]
> ![.NET dla architektury Apache Spark](media/dotnet-spark-architecture.png)

Aby uzyskać informacje o obsłudze międzyoperacyjności dla rozszerzeń języka Spark, zapoznaj się z [propozycją](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>Platforma .NET dla Apache Spark wydajności

W porównaniu do języka Python i scala przy użyciu [testu TPC-H](http://www.tpc.org/tpch/)środowisko .net dla Apache Spark jest dobrze w większości przypadków i jest szybsze niż w języku Python, gdy wydajność funkcji zdefiniowanej przez użytkownika jest krytyczna. Istnieje ciągły nakład pracy w celu poprawy i oceny wydajności.

Aby przeprowadzić własne testy porównawcze, zobacz wyniki testów dostępnych w [programie .NET dla Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>Program .NET dla Apache Spark plan

Dowiedz się więcej o krótkoterminowych i długoterminowych planach od oficjalnego [planu .NET na potrzeby Apache Spark](https://github.com/dotnet/spark/blob/master/ROADMAP.md).

## <a name="net-foundation"></a>Platforma .NET Foundation

Projekt .NET for Apache Spark jest częścią programu [.NET Foundation](https://www.dotnetfoundation.org/).

## <a name="contributions"></a>Wysokość

Platforma .NET dla Apache Spark Team zachęca do uczestnictwa, zarówno problemów z usługą GitHub, jak i żądań ściągnięcia. Najpierw poszukaj [istniejącego problemu](https://github.com/dotnet/spark/issues). Jeśli nie możesz znaleźć istniejącego problemu, [Otwórz nowy problem](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Następne kroki

Wypróbuj platformę .NET dla Apache Spark.
> [!div class="nextstepaction"]
> [Samouczek: Rozpoczynanie pracy z platformą .NET dla Apache Spark](./tutorials/get-started.md)
