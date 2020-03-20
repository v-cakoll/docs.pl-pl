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
# <a name="what-is-apache-spark"></a>Co to jest platforma Apache Spark?

[Apache Spark](https://spark.apache.org/) to platforma przetwarzania równoległego typu open source, która obsługuje przetwarzanie w pamięci w celu zwiększenia wydajności aplikacji analizujących duże zbiory danych. Rozwiązania big data są przeznaczone do obsługi danych, które są zbyt duże lub złożone dla tradycyjnych baz danych. Platforma Spark przetwarza duże ilości danych w pamięci, co jest znacznie szybsze niż alternatywy oparte na dysku.

## <a name="common-big-data-scenarios"></a>Typowe scenariusze dużych zbiorów danych

Można rozważyć architekturę dużych zbiorów danych, jeśli trzeba przechowywać i przetwarzać duże ilości danych, przekształcać dane bez struktury lub przetwarzać dane strumieniowe. Spark to aparat przetwarzania rozproszonego ogólnego przeznaczenia, który może być używany w kilku scenariuszach dużych zbiorów danych.

### <a name="extract-transform-and-load-etl"></a>Wyodrębnianie, przekształcanie i ładowanie (ETL)

[Wyodrębnianie, przekształcanie i ładowanie (ETL)](/azure/architecture/data-guide/relational-data/etl) to proces zbierania danych z jednego lub wielu źródeł, modyfikowania danych i przenoszenia danych do nowego magazynu danych. Istnieje kilka sposobów przekształcania danych, w tym:

* Filtrowanie
* Sortowanie
* Agregowania
* Dołączenie
* Czyszczenia
* Deduplikowanie
* Sprawdzanie poprawności

### <a name="real-time-data-stream-processing"></a>Przetwarzanie strumienia danych w czasie rzeczywistym

Przesyłanie strumieniowe lub w czasie rzeczywistym dane są danymi w ruchu. Telemetria z urządzeń IoT, blogów i strumieni kliknięć są przykładami przesyłania strumieniowego danych. Dane w czasie rzeczywistym mogą być przetwarzane w celu dostarczenia przydatnych informacji, takich jak analiza geoprzestrzenna, zdalne monitorowanie i wykrywanie anomalii. Podobnie jak dane relacyjne, można filtrować, agregować i przygotowywać dane przesyłania strumieniowego przed przeniesieniem danych do ujścia danych wyjściowych. Apache Spark obsługuje [przetwarzanie strumienia danych w czasie rzeczywistym](/azure/architecture/data-guide/big-data/real-time-processing) za pośrednictwem usługi Spark [Streaming.](https://spark.apache.org/streaming/)

### <a name="batch-processing"></a>Przetwarzanie wsadowe

[Przetwarzanie wsadowe](/azure/architecture/data-guide/big-data/batch-processing) polega na przetwarzaniu dużych zbiorów danych w spoczynku. Można filtrować, agregować i przygotowywać bardzo duże zestawy danych przy użyciu długotrwałych zadań równolegle.

### <a name="machine-learning-through-mllib"></a>Uczenie maszynowe za pośrednictwem MLlib

Uczenie maszynowe jest używane do zaawansowanych problemów analitycznych. Komputer może używać istniejących danych do prognozowania lub przewidywania przyszłych zachowań, wyników i trendów. Biblioteka uczenia maszynowego Apache Spark, [MLlib,](https://spark.apache.org/mllib/)zawiera kilka algorytmów uczenia maszynowego i narzędzi.

### <a name="graph-processing-through-graphx"></a>Przetwarzanie wykresów za pośrednictwem GraphX

Wykres jest zbiorem węzłów połączonych krawędziami. Jeśli masz dane hierarchiczne lub dane z połączonymi relacjami, możesz użyć bazy danych wykresów. Można przetwarzać te dane przy użyciu api [GraphX](https://spark.apache.org/graphx/) firmy Apache Spark.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>Przetwarzanie danych SQL i strukturalnych za pomocą programu Spark SQL

Jeśli pracujesz z danymi strukturalnymi (sformatowanymi), możesz użyć zapytań SQL w aplikacji Spark przy użyciu [programu Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Architektura Apache Spark

Apache Spark, który używa architektury master/worker, ma trzy główne składniki: sterownik, executors i menedżera klastra.

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Sterownik

Sterownik składa się z programu, takich jak aplikacja konsoli Języka C# i sesji Platformy Spark. Sesja Spark pobiera program i dzieli go na mniejsze zadania, które są obsługiwane przez wykonawców.

### <a name="executors"></a>Executors

Każdy wykonawca lub węzeł procesu roboczego odbiera zadanie od sterownika i wykonuje to zadanie. Executors znajdują się na jednostce znanej jako klaster.

### <a name="cluster-manager"></a>Menedżer klastrów

Menedżer klastra komunikuje się zarówno ze sterownikiem, jak i wykonawcami w celu:

* Zarządzanie alokacją zasobów
* Zarządzanie podziałem programu
* Zarządzanie wykonywaniem programu

## <a name="language-support"></a>Obsługa języków

Apache Spark obsługuje następujące języki programowania:

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>Interfejsy API platformy Spark

Apache Spark obsługuje następujące interfejsy API:

* [Spark Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Spark Java API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Spark Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Spark R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), wbudowane funkcje

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak używać aplikacji Apache Spark w aplikacji .NET. Dzięki platformie .NET for Apache Spark deweloperzy z funkcją .NET i logiką biznesową mogą zapisywać zapytania o duże zbiory danych w językach C# i F#.
> [!div class="nextstepaction"]
> [Co to jest .NET dla Apache Spark](what-is-apache-spark-dotnet.md)
