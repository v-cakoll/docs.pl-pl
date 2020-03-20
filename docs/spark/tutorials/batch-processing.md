---
title: Przetwarzanie wsadowe za pomocą samouczka .NET for Apache Spark
description: Dowiedz się, jak wykonać przetwarzanie wsadowe przy użyciu platformy .NET for Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187551"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Samouczek: Wykonaj przetwarzanie wsadowe za pomocą platformy .NET dla platformy Apache Spark

W tym samouczku dowiesz się, jak wykonać przetwarzanie wsadowe przy użyciu platformy .NET for Apache Spark. Przetwarzanie wsadowe jest przekształcenie danych w spoczynku, co oznacza, że dane źródłowe zostały już załadowane do magazynu danych.

Przetwarzanie wsadowe jest zazwyczaj wykonywane za generowane za wiele dużych, płaskich zestawów danych, które muszą być przygotowane do dalszej analizy. Przetwarzanie dzienników i magazynowanie danych są typowymi scenariuszami przetwarzania wsadowego. W tym scenariuszu można analizować informacje o projektach GitHub, takie jak liczba czasu różnych projektów zostały rozwidlione lub jak niedawno projekty zostały zaktualizowane.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Tworzenie i uruchamianie aplikacji .NET dla aplikacji Apache Spark
> * Odczytywanie danych w ramce DataFrame i przygotowywanie ich do analizy
> * Przetwarzanie danych przy użyciu programu Spark SQL

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli po raz pierwszy używasz platformy .NET for Apache Spark, zapoznaj się z samouczkiem [Wprowadzenie do platformy .NET for Apache Spark,](../tutorials/get-started.md) aby dowiedzieć się, jak przygotować środowisko i uruchomić pierwszą aplikację .NET dla platformy Spark apache.

## <a name="download-the-sample-data"></a>Pobieranie przykładowych danych

[GHTorrent](http://ghtorrent.org/) monitoruje wszystkie publiczne zdarzenia Usługi GitHub, takie jak informacje o projektach, zatwierdzeniach i obserwatorach, i przechowuje zdarzenia i ich strukturę w bazach danych. Dane zbierane w różnych okresach są dostępne jako archiwa do pobrania. Ponieważ pliki zrzutu są bardzo duże, w tym przewodniku użyto [obciętej wersji pliku zrzutu,](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) który można pobrać z gitHub.

> [!NOTE]
> Zestaw danych GHTorrent jest dystrybuowany w ramach systemu podwójnego licencjonowania[(Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)). Do celów niekomercyjnych (w tym między innymi do celów edukacyjnych, badawczych lub osobistych) zestaw danych jest rozpowszechniany na [licencji CC-BY-SA.](https://creativecommons.org/licenses/by-sa/4.0/)

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

1. W wierszu polecenia uruchom następujące polecenia, aby utworzyć nową aplikację konsoli:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   Polecenie `dotnet` tworzy `new` aplikację typu `console` dla Ciebie. Parametr `-o` tworzy katalog o nazwie *mySparkBatchApp,* w którym aplikacja jest przechowywana i wypełnia go wymaganymi plikami. Polecenie `cd mySparkBatchApp` zmienia katalog na katalog aplikacji, który został właśnie utworzony.

1. Aby użyć platformy .NET for Apache Spark w aplikacji, należy zainstalować pakiet Microsoft.Spark. W konsoli uruchom następujące polecenie:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Tworzenie sparkSession

1. Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs* w *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Dodaj następujący kod do obszaru nazw projektu. *s_referenceData* jest używany w dalszej części programu do filtrowania na podstawie daty.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Dodaj następujący kod wewnątrz main metody, aby ustanowić nowy SparkSession. SparkSession jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API DataFrame. Wywołując `spark` obiekt, można uzyskać dostęp do funkcji Platformy Spark i DataFrame w całym programie.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Przygotowywanie danych

1. Odczyt pliku wejściowego `DataFrame`do pliku , który jest rozproszoną kolekcją danych zorganizowanych w nazwane kolumny. Kolumny danych można ustawić za <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>pomocą pliku . Użyj <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> tej metody, aby wyświetlić dane w dataframe. Pamiętaj, aby zaktualizować ścieżkę pliku CSV do lokalizacji pobranych danych GitHub.

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

1. Użyj <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> metody, aby upuścić wiersze z wartościami NA (null) i metodę usuwania <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> niektórych kolumn z danych. Pomaga to zapobiegać błędom podczas próby analizowania danych lub kolumn null, które nie są istotne dla ostatecznej analizy.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analizowanie danych

Spark SQL umożliwia wykonywanie wywołań SQL na danych. Często łączy się funkcje zdefiniowane przez użytkownika i program Spark SQL w celu zastosowania funkcji zdefiniowanej przez użytkownika do wszystkich wierszy elementu DataFrame.

Można w szczególności `spark.Sql` wywołać naśladować standardowe wywołania SQL widoczne w innych typach aplikacji. Można również wywołać <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> metody, takie jak i w szczególności łączyć, filtrować i wykonywać obliczenia na danych.

Celem tej aplikacji jest uzyskanie pewnych spostrzeżeń na temat danych projektów GitHub. Dodaj do programu następujące fragmenty kodu, aby analizować dane.

1. Dodaj następujący blok kodu znajduje liczbę razy każdy język został rozwidleczony. Po pierwsze dane są pogrupowane według języka. Następnie pobierana jest średnia liczba wideł z każdego języka.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Dodaj następujący blok kodu, aby zamówić średnią liczbę widelców w malejącej kolejności, aby zobaczyć, które języki są najbardziej rozwidli. Oznacza to, że największa liczba wideł pojawi się jako pierwsza.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. Następny blok kodu pokazuje, jak niedawno projekty zostały zaktualizowane. Rejestrujesz nową funkcję zdefiniowaną przez użytkownika o nazwie *MyUDF* i porównujesz ją z *datą, s_referenceDate*, która została zadeklarowana na początku samouczka. Data dla każdego projektu jest porównywana z datą odwołania. Następnie program Spark SQL jest używany do wywoływania UDF w każdym wierszu danych do analizowania każdego projektu w zestawie danych.

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

1. Zadzwoń, `spark.Stop()` aby zakończyć SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Uruchamianie aplikacji za pomocą spark-submit

1. Użyj następującego polecenia, aby utworzyć aplikację .NET:

   ```dotnetcli
   dotnet build
   ```

1. Uruchom aplikację `spark-submit`za pomocą pliku . Pamiętaj, aby zaktualizować następujące polecenie za pomocą rzeczywistych ścieżek do pliku jar platformy Microsoft Spark.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Uzyskiwanie kodu

Możesz zobaczyć [pełne rozwiązanie](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) na GitHub.

## <a name="next-steps"></a>Następne kroki

Przejdź do następnego artykułu, aby dowiedzieć się, jak przetwarzać dane strumieniowe za pomocą platformy .NET for Apache Spark.
> [!div class="nextstepaction"]
> [Samouczek: Zorganizowane przesyłanie strumieniowe z .NET dla platformy Apache Spark](streaming.md)
