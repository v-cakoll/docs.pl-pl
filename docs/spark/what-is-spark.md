---
title: Co to jest Apache Spark?
description: Dowiedz się więcej na temat scenariuszy Apache Spark i danych Big Data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458176"
---
# <a name="what-is-apache-spark"></a>Co to jest Apache Spark?

[Apache Spark](https://spark.apache.org/) to platforma przetwarzania równoległego typu open source, która obsługuje przetwarzanie w pamięci w celu zwiększenia wydajności aplikacji, które analizują dane Big Data. Rozwiązania danych Big Data są przeznaczone do obsługi danych, które są zbyt duże lub złożone dla tradycyjnych baz danych. Platforma Spark przetwarza duże ilości danych w pamięci, które są znacznie szybsze niż alternatywy oparte na dyskach.

## <a name="common-big-data-scenarios"></a>Typowe scenariusze danych Big Data

Można rozważyć użycie architektury danych Big Data, jeśli trzeba przechowywać i przetwarzać duże ilości danych, przekształcać dane bez struktury lub przetwarzać dane przesyłane strumieniowo. Spark to aparat przetwarzania rozproszonego ogólnego przeznaczenia, który może być używany dla kilku scenariuszy danych Big Data.

### <a name="extract-transform-and-load-etl"></a>Wyodrębnianie, przekształcanie i ładowanie (ETL)

[Wyodrębnianie, przekształcanie i ładowanie (ETL)](/azure/architecture/data-guide/relational-data/etl) to proces zbierania danych z jednego lub wielu źródeł, modyfikowania danych i przechodzenia danych do nowego magazynu danych. Istnieje kilka sposobów przekształcania danych, w tym:

* Filtrowanie
* Sortowanie
* Agregowanie
* Łączenie
* Czyszczenie
* Deduplikacja
* Ponownego

### <a name="real-time-data-stream-processing"></a>Przetwarzanie strumienia danych w czasie rzeczywistym

Dane są przesyłane strumieniowo lub w czasie rzeczywistym. Dane telemetryczne z urządzeń IoT, Weblogs i strumieni kliknięć to wszystkie przykłady danych przesyłanych strumieniowo. Dane w czasie rzeczywistym mogą być przetwarzane w celu zapewnienia użytecznych informacji, takich jak analiza geoprzestrzenna, zdalne monitorowanie i wykrywanie anomalii. Podobnie jak w przypadku danych relacyjnych, można filtrować, agregować i przygotowywać dane przesyłane strumieniowo przed przeniesieniem danych do ujścia danych wyjściowych. Apache Spark obsługuje [Przetwarzanie strumieni danych](/azure/architecture/data-guide/big-data/real-time-processing) w czasie rzeczywistym za poorednictwem [przesyłania strumieniowego Spark](https://spark.apache.org/streaming/).

### <a name="batch-processing"></a>Przetwarzanie wsadowe

[Przetwarzanie wsadowe](/azure/architecture/data-guide/big-data/batch-processing) polega na przetwarzaniu danych Big Data. Można filtrować, agregować i przygotowywać bardzo duże zestawy danych, korzystając ze długotrwałych zadań.

### <a name="machine-learning-through-mllib"></a>Uczenie maszynowe przez MLlib

Uczenie maszynowe jest używane w przypadku zaawansowanych problemów analitycznych. Komputer może używać istniejących danych do prognozowania lub przewidywania przyszłych zachowań, rezultatów i trendów. Biblioteka uczenia maszynowego Apache Spark, [MLlib](https://spark.apache.org/mllib/), zawiera kilka algorytmów uczenia maszynowego i narzędzi.

### <a name="graph-processing-through-graphx"></a>Przetwarzanie grafu za poorednictwem GraphX

Wykres jest kolekcją węzłów połączonych przez krawędzie. Możesz użyć bazy danych grafu, jeśli masz dane lub dane hierarchiczne z połączonymi relacjami. Te dane można przetwarzać przy użyciu Apache Spark interfejsu API [GraphX](https://spark.apache.org/graphx/) .

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>Przetwarzanie danych SQL i strukturalnych przy użyciu platformy Spark SQL

Jeśli pracujesz ze strukturą (sformatowaną) danymi, możesz użyć zapytań SQL w aplikacji Spark przy użyciu [platformy Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Architektura Apache Spark

Apache Spark, która używa architektury Master/Worker, ma trzy główne składniki: Sterownik, wykonawcy i Menedżera klastra.

![Architektura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Sterownik

Sterownik składa się z programu, takiego jak C# Aplikacja konsolowa i sesja platformy Spark. Sesja platformy Spark pobiera program i dzieli go na mniejsze zadania, które są obsługiwane przez wykonawcy.

### <a name="executors"></a>Wykonawców

Każdy wykonawca lub węzeł procesu roboczego odbiera zadanie ze sterownika i wykonuje to zadanie. Wykonawcy znajdują się w jednostce znanej jako klaster.

### <a name="cluster-manager"></a>Menedżer klastra

Menedżer klastra komunikuje się zarówno z sterownikiem, jak i modułami wykonującymi:

* Zarządzanie alokacją zasobów
* Zarządzanie dzieleniem programu
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

* [Interfejs API platformy Spark Scala](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Interfejs API języka Java platformy Spark](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Interfejs API języka Python platformy Spark](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Interfejs API platformy Spark języka R](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Platforma Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), funkcje wbudowane

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak za pomocą Apache Spark w aplikacji .NET. Przy użyciu platformy .NET dla Apache Spark deweloperzy z interfejsem .NET i logiką biznesową mogą zapisywać C# zapytania F#dotyczące danych Big Data w i.
> [!div class="nextstepaction"]
> [Co to jest platforma .NET dla Apache Spark](what-is-apache-spark-dotnet.md)
