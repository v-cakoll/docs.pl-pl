---
title: Przetwarzanie wsadowe za pomocą platformy .NET dla Apache Spark — samouczek
description: Dowiedz się, jak przeprowadzić przetwarzanie wsadowe przy użyciu platformy .NET dla Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: bd91fb401b9beb6ae74c4599b25e43284473f8b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75466414"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Samouczek: wykonywanie przetwarzania wsadowego za pomocą platformy .NET dla Apache Spark

W tym samouczku dowiesz się, jak przeprowadzić przetwarzanie wsadowe przy użyciu platformy .NET dla Apache Spark. Przetwarzanie wsadowe to transformacja danych magazynowanych, co oznacza, że dane źródłowe zostały już załadowane do magazynu danych. 

Przetwarzanie wsadowe jest zwykle wykonywane nad dużymi, płaskimi zestawami danych, które muszą zostać przygotowane do dalszej analizy. Przetwarzanie dzienników i magazynowanie danych to typowe scenariusze przetwarzania wsadowego. W tym scenariuszu analizujesz informacje o projektach GitHub, takich jak liczba różnych projektów przewidzianych do przetworzenia lub czas ich aktualizacji. 

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:

> [!div class="checklist"]
>
> * Utwórz i Uruchom platformę .NET dla aplikacji Apache Spark
> * Odczytywanie danych do ramki Dataframe i przygotowywanie jej do analizy
> * Przetwarzanie danych przy użyciu platformy Spark SQL

## <a name="prerequisites"></a>Wymagania wstępne 

Jeśli korzystasz z platformy .NET dla Apache Spark, zapoznaj się z samouczkiem wprowadzenie do [platformy .NET dla Apache Spark](../tutorials/get-started.md) , aby dowiedzieć się, jak przygotować środowisko i uruchomić pierwszą aplikację .net for Apache Spark.

## <a name="download-the-sample-data"></a>Pobieranie przykładowych danych

[GHTorrent](http://ghtorrent.org/) monitoruje wszystkie publiczne zdarzenia usługi GitHub, takie jak informacje o projektach, zatwierdzeń i Obserwatorach, a także przechowuje zdarzenia i ich strukturę w bazach danych. Dane zbierane przez różne okresy są dostępne jako archiwa do pobrania. Ponieważ pliki zrzutu są bardzo duże, ten przewodnik używa [obciętej wersji pliku zrzutu](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) , który można pobrać z witryny GitHub.

> [!NOTE]
> Zestaw danych GHTorrent jest dystrybuowany w ramach podwójnego planu licencjonowania ([Creative Commons Attribution +](https://wiki.creativecommons.org/wiki/CCPlus)). W przypadku niekomercyjnych celów (w tym, ale nie ograniczonych do, edukacyjnych, badawczych lub prywatnych), zestaw danych jest dystrybuowany w ramach [licencji CC-by-sa](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. W wierszu polecenia Uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   `dotnet` polecenie tworzy `new` aplikacji typu `console`. Parametr `-o` tworzy katalog o nazwie *mySparkBatchApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami. `cd mySparkBatchApp` polecenie zmienia katalog na właśnie utworzony katalog aplikacji.

1. Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark. W konsoli programu uruchom następujące polecenie:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Utwórz SparkSession

1. Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* w *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Dodaj następujący kod do przestrzeni nazw projektu. *s_referenceData* jest używany później w programie do filtrowania na podstawie daty.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Dodaj następujący kod wewnątrz metody Main, aby określić nowy SparkSession. SparkSession jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API Dataframe. Wywołując obiekt `spark`, można uzyskać dostęp do funkcji Spark i Dataframe w całym programie.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Przygotowywanie danych

1. Odczytaj plik wejściowy do `DataFrame`, czyli rozproszonej kolekcji danych zorganizowanych w nazwanych kolumn. Możesz ustawić kolumny dla danych za pomocą <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>. Użyj metody <xref:Microsoft.Spark.Sql.DataFrame.Show%2A>, aby wyświetlić dane w ramce Dataframe. Pamiętaj, aby zaktualizować ścieżkę pliku CSV do lokalizacji pobranych danych usługi GitHub.

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. Użyj metody <xref:Microsoft.Spark.Sql.DataFrame.Na%2A>, aby porzucić wiersze z wartościami NA (null), i metodę <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A>, aby usunąć niektóre kolumny z danych. Pozwala to zapobiec błędom, jeśli próbujesz analizować dane o wartości null lub kolumny, które nie są istotne dla ostatniej analizy.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analizowanie danych

Platforma Spark SQL umożliwia wykonywanie wywołań SQL na danych. Często istnieje możliwość łączenia funkcji zdefiniowanych przez użytkownika i platformy Spark SQL w celu zastosowania funkcji zdefiniowanej przez użytkownika do wszystkich wierszy ramki danych.

Możesz wywoływać `spark.Sql`, aby naśladować standardowe wywołania SQL widoczne w innych typach aplikacji. Możesz również wywołać metody, takie jak <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> i <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A>, aby w sposób umożliwiał łączenie, filtrowanie i wykonywanie obliczeń na danych.

Celem tej aplikacji jest uzyskanie szczegółowych informacji o danych projektów usługi GitHub. Dodaj następujące fragmenty kodu do programu w celu przeanalizowania danych.

1. Dodaj następujący blok kodu Znajdź liczbę przypadków, w których każdy język został przerozwidleni. Najpierw dane są pogrupowane według języka. Następnie jest wykonywana średnia liczba rozwidleniów z każdego języka.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Dodaj następujący blok kodu w celu uporządkowania oredniej liczby rozwidleniów w kolejności malejącej, aby zobaczyć, które języki są najbardziej rozwidlenie. Oznacza to, że największa liczba rozwidleniów zostanie wyświetlona jako pierwsza.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show(); 
   ```

1. Następny blok kodu pokazuje, jak ostatnio projekty zostały zaktualizowane. Należy zarejestrować nową funkcję zdefiniowaną przez użytkownika o nazwie *MyUDF* i porównać ją z datą, *s_referenceDate*, która została zadeklarowana na początku samouczka. Data dla każdego projektu jest porównywana z datą odwołania. Następnie program Spark SQL jest używany do wywołania funkcji UDF w każdym wierszu danych w celu przeanalizowania każdego projektu w zestawie danych.

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);   
   cleanedProjects.CreateOrReplaceTempView("dateView"); 

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. Wywołaj `spark.Stop()`, aby zakończyć SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Korzystanie z platformy Spark — przesyłanie w celu uruchomienia aplikacji

1. Użyj następującego polecenia, aby skompilować aplikację .NET:

   ```dotnetcli
   dotnet build
   ```

1. Uruchom aplikację za pomocą `spark-submit`. Pamiętaj, aby zaktualizować następujące polecenie z rzeczywistymi ścieżkami do pliku JAR Microsoft Spark.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Uzyskaj kod

Możesz zobaczyć [pełne rozwiązanie](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) w witrynie GitHub.

## <a name="next-steps"></a>Następne kroki

Przejdź do następnego artykułu, aby dowiedzieć się, jak przetwarzać dane przesyłane strumieniowo przy użyciu platformy .NET dla Apache Spark.
> [!div class="nextstepaction"]
> [Samouczek: strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark](streaming.md)
