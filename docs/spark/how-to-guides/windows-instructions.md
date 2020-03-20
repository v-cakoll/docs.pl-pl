---
title: Tworzenie aplikacji platformy .NET dla platformy Spark w systemie Windows
description: Dowiedz się, jak utworzyć aplikację platformy .NET dla platformy Spark w systemie Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185759"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Dowiedz się, jak utworzyć aplikację .NET dla platformy Spark w systemie Windows

W tym artykule dowiesz się, jak utworzyć aplikacje platformy .NET dla platformy Apache Spark w systemie Windows.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli masz już wszystkie poniższe wymagania wstępne, przejdź do kroków [kompilacji.](#build)

  1. Pobierz i zainstaluj **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - zainstalowanie `dotnet` zestawu SDK doda pasek narzędzi do ścieżki. Obsługiwane są platformy .NET Core 2.1, 2.2 i 3.1.
  2. Zainstaluj **[program Visual Studio 2019](https://www.visualstudio.com/downloads/)** (wersja 16.3 lub nowsza). Wersja wspólnotowa jest całkowicie darmowa. Podczas konfigurowania instalacji należy uwzględnić następujące składniki co najmniej:
     * Programowa firma .NET
       * Wszystkie wymagane składniki
         * Narzędzia programistyczne .NET Framework 4.6.1
     * Tworzenie aplikacji dla wielu platform w środowisku .NET Core
       * Wszystkie wymagane składniki
  3. Zainstaluj **[javę Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.
     - Wybierz odpowiednią wersję dla danego systemu operacyjnego. Na przykład *jdk-8u201-windows-x64.exe* dla komputera z systemem Windows x64.
     - Zainstaluj za pomocą instalatora i sprawdź, czy możesz uruchomić `java` z wiersza polecenia.
  4. Zainstaluj **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.
     - Pobierz [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Wyodrębnij do katalogu lokalnego. Na przykład *C:\bin\apache-maven-3.6.0\*.
     - Dodaj Apache Maven do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml). Na przykład *C:\bin\apache-maven-3.6.0\bin*.
     - Sprawdź, czy można `mvn` uruchomić z wiersza polecenia.
  5. Zainstaluj **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.
     - Pobierz [apache Spark 2.3+](https://spark.apache.org/downloads.html) i wyodrębnij go do folderu lokalnego (na przykład *C:\bin\spark-2.3.2-bin-hadoop2.7)\*za pomocą [7-zip](https://www.7-zip.org/). (Obsługiwane wersje iskry to 2.3.*, 2.4.0, 2.4.1, 2.4.3 i 2.4.4)
     - Dodaj [nową zmienną](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`środowiskową . Na przykład *C:\bin\spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - Dodaj apache spark do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml). Na przykład *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Sprawdź, czy można `spark-shell` uruchomić z wiersza polecenia.
        Przykładowe wyjście konsoli:

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. Zainstaluj **[WinUtils](https://github.com/steveloughran/winutils)**.
     - Pobierz `winutils.exe` plik binarny z [repozytorium WinUtils](https://github.com/steveloughran/winutils). Należy wybrać wersję programu Hadoop, z którą skompilowano dystrybucję platformy Spark. Dla exammple, użyj hadoop-2.7.1 dla Spark 2.3.2.
     - Zapisz `winutils.exe` plik binarny w wybranym katalogu. Na przykład *C:\hadoop\bin*.
     - Ustaw, `HADOOP_HOME` aby odzwierciedlić katalog z winutils.exe (bez kosza). Na przykład za pomocą wiersza polecenia:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Ustaw zmienną środowiskową PATH, aby uwzględnić `%HADOOP_HOME%\bin`. Na przykład za pomocą wiersza polecenia:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Przed przejściem do `dotnet`następnej sekcji upewnij się, że można uruchomić program , `java`, `mvn` `spark-shell` z wiersza polecenia. Czujesz, że jest lepszy sposób? [Otwórz problem](https://github.com/dotnet/spark/issues) i nie krępuj się wnieść swój wkład.

> [!NOTE]
> Nowe wystąpienie wiersza polecenia może być wymagane, jeśli zaktualizowano wszystkie zmienne środowiskowe.

## <a name="build"></a>Kompilacja

W pozostałej części tego przewodnika należy sklonować repozytorium platformy .NET for Apache Spark do komputera. Można wybrać dowolną lokalizację sklonowanego repozytorium. Na przykład *C:\github\dotnet-spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Tworzenie warstwy rozszerzeń Platformy .NET dla apache Spark Scala

Podczas przesyłania aplikacji .NET, .NET for Apache Spark ma niezbędną logikę zapisaną w Scali, która informuje Apache Spark, jak obsługiwać żądania (na przykład żądanie utworzenia nowej sesji platformy Spark, żądanie przeniesienia danych ze strony .NET do strony JVM itp.). Tę logikę można znaleźć w [.NET dla kodu źródłowego Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).

Niezależnie od tego, czy używasz programu .NET Framework, czy .NET Core, należy utworzyć warstwę rozszerzenia .NET for Apache Spark Scala:

```powershell
cd src\scala
mvn clean package
```

Powinny być widoczne jars utworzone dla obsługiwanych wersji platformy Spark:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Tworzenie przykładowych aplikacji platformy .NET dla platformy Spark

W tej sekcji wyjaśniono, jak utworzyć [przykładowe aplikacje](https://github.com/dotnet/spark/tree/master/examples) dla platformy .NET for Apache Spark. Te kroki pomogą w zrozumieniu ogólnego procesu tworzenia dla dowolnej aplikacji platformy .NET for Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Korzystanie z programu Visual Studio dla programu .NET Framework

  1. Otwórz `src\csharp\Microsoft.Spark.sln` w programie Visual `Microsoft.Spark.CSharp.Examples` Studio `examples` i skompiluj projekt w folderze (spowoduje to również kompilację projektu powiązań .NET). Jeśli chcesz, możesz napisać własny kod `Microsoft.Spark.Examples` w projekcie ("input_file.json" w tym przykładzie jest plikiem json z danymi, z których chcesz utworzyć ramkę danych):
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     Po pomyślnym zakończeniu kompilacji zostaną wyświetlone odpowiednie pliki binarne wyprodukowane w katalogu wyjściowym.
     Przykładowe wyjście konsoli:

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a>Korzystanie z interfejsu wiersza polecenia .NET Core dla rdzenia .NET

> [!NOTE]
> Obecnie pracujemy nad automatyzacją kompilacji .NET Core dla platformy Spark .NET. Do tego czasu doceniamy twoją cierpliwość w wykonywaniu niektórych kroków ręcznie.

  1. Zbuduj pracownika:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Przykładowe wyjście konsoli:

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. Tworzenie próbek:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Przykładowe wyjście konsoli:

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a>Uruchamianie przykładowych aplikacji platformy .NET for Spark

Po utworzeniu przykłady, uruchamianie `spark-submit` ich będzie za pośrednictwem niezależnie od tego, czy są przeznaczone dla platformy .NET Framework lub .NET Core. Upewnij się, że masz następujące [wymagania wstępne](#prerequisites) sekcji i zainstalowane Apache Spark.

  1. Ustaw `DOTNET_WORKER_DIR` zmienną lub `PATH` środowiskową tak, aby zawierała ścieżkę, w `Microsoft.Spark.Worker` której został wygenerowany plik binarny (na przykład *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x6\publish* for .NET Core):

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Otwórz program Powershell i przejdź do katalogu, w którym został wygenerowany plik binarny aplikacji (np. *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. Uruchamianie aplikacji jest zgodne z podstawową strukturą:

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Oto kilka przykładów, które można uruchomić:

     - **[Program Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven dostępne)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (słoiki dostarczone)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
