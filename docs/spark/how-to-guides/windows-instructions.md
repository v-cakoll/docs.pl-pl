---
title: Tworzenie aplikacji platformy .NET dla Apache Spark w systemie Windows
description: Dowiedz się, jak utworzyć platformę .NET dla aplikacji Apache Spark w systemie Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e6dec09f7d3e8d478cdcccf9df1c3e72d5f884eb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928037"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Dowiedz się, jak skompilować aplikację platformy .NET dla Apache Spark w systemie Windows

W tym artykule przedstawiono sposób kompilowania aplikacji platformy .NET dla Apache Spark w systemie Windows.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli masz już wszystkie poniższe wymagania wstępne, przejdź do kroków [kompilacji](#build) .

  1. Pobierz i zainstaluj **[zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** — Instalacja zestawu SDK spowoduje dodanie do ścieżki `dotnet` łańcucha narzędzi. Obsługiwane są programy .NET Core 2,1, 2,2 i 3,1.
  2. Zainstaluj **[program Visual Studio 2019](https://www.visualstudio.com/downloads/)** (wersja 16,3 lub nowsza). Wersja społeczności jest całkowicie bezpłatna. Podczas konfigurowania instalacji należy uwzględnić następujące składniki:
     * Programowanie aplikacji klasycznych dla platformy .NET
       * Wszystkie wymagane składniki
         * Narzędzia programistyczne .NET Framework 4.6.1
     * Programowanie dla wielu platform w środowisku .NET Core
       * Wszystkie wymagane składniki
  3. Zainstaluj **[środowisko Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** . 
     - Wybierz odpowiednią wersję systemu operacyjnego, np. JDK-8u201-Windows-x64. exe dla komputera z systemem win x64.
     - Zainstaluj program przy użyciu Instalatora i sprawdź, czy można uruchamiać `java` z poziomu wiersza polecenia.
  4. Zainstaluj program **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .
     - Pobierz [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
     - Wyodrębnij do katalogu lokalnego, np., `C:\bin\apache-maven-3.6.0\`.
     - Dodaj Maven Apache do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml) , np., `C:\bin\apache-maven-3.6.0\bin`.
     - Sprawdź, czy możesz uruchamiać `mvn` z poziomu wiersza polecenia.
  5. Zainstaluj **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .
     - Pobierz [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) i wyodrębnij go do folderu lokalnego (np. `C:\bin\spark-2.3.2-bin-hadoop2.7\`) przy użyciu [7-zip](https://www.7-zip.org/). (Obsługiwane wersje platformy Spark to 2,3. *, 2.4.0, 2.4.1, 2.4.3 i 2.4.4)
     - Dodaj [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` np., `C:\bin\spark-2.3.2-bin-hadoop2.7\`.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - Dodaj Apache Spark do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml) , np., `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - Sprawdź, czy możesz uruchamiać `spark-shell` z poziomu wiersza polecenia.        
        Przykładowe dane wyjściowe konsoli:

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

  6. Zainstaluj **[WinUtils](https://github.com/steveloughran/winutils)** .
     - Pobierz plik binarny `winutils.exe` z [repozytorium WinUtils](https://github.com/steveloughran/winutils). Należy wybrać wersję usługi Hadoop, z którą została skompilowana dystrybucja platformy Spark, np. przy użyciu usługi Hadoop-2.7.1 dla platformy Spark 2.3.2.
     - Zapisz `winutils.exe` dane binarne w wybranym katalogu, np., `C:\hadoop\bin`.
     - Ustaw `HADOOP_HOME` tak, aby odzwierciedlał katalog z winutils. exe (bez bin). Na przykład za pomocą wiersza polecenia:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Ustaw zmienną środowiskową PATH do uwzględnienia `%HADOOP_HOME%\bin`. Na przykład za pomocą wiersza polecenia:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Przed przejściem do następnej sekcji upewnij się, że można uruchomić `dotnet`, `java`, `mvn``spark-shell` z poziomu wiersza polecenia. Czy istnieje lepszy sposób? [Otwórz problem](https://github.com/dotnet/spark/issues) i śmiało, aby współtworzyć.

> [!NOTE]
> Jeśli wszystkie zmienne środowiskowe zostały zaktualizowane, może być wymagane nowe wystąpienie wiersza polecenia.

## <a name="build"></a>{1&gt;Kompilacja&lt;1}

W pozostałej części tego przewodnika konieczne będzie sklonowanie repozytorium .NET for Apache Spark na komputerze. Można wybrać dowolną lokalizację dla sklonowanego repozytorium, np. `C:\github\dotnet-spark\`.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Kompiluj platformę .NET dla Apache Spark warstwy rozszerzeń Scala

Gdy przesyłasz aplikację .NET, platforma .NET dla Apache Spark ma niezbędną logikę zapisaną w Scala, która informuje Apache Spark, jak obsługiwać żądania (np. żądanie utworzenia nowej sesji platformy Spark, żądanie przeniesienia danych z platformy .NET do strony JVM itp.). Tę logikę można znaleźć w [kodzie źródłowym programu .net for Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).

Bez względu na to, czy używasz .NET Framework, czy platformy .NET Core, musisz skompilować platformę .NET dla Apache Spark Scala warstwy rozszerzeń:

```powershell
cd src\scala
mvn clean package 
```

Powinna zostać wyświetlona JARs utworzona dla obsługiwanych wersji platformy Spark:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Tworzenie przykładowych aplikacji platformy .NET dla platformy Spark

W tej sekcji opisano sposób tworzenia [przykładowych aplikacji](https://github.com/dotnet/spark/tree/master/examples) dla platformy .net dla Apache Spark. Te kroki ułatwią zrozumienie ogólnego procesu tworzenia aplikacji platformy .NET dla platformy Spark.

#### <a name="using-visual-studio-for-net-framework"></a>Korzystanie z programu Visual Studio dla .NET Framework

  1. Otwórz `src\csharp\Microsoft.Spark.sln` w programie Visual Studio i skompiluj projekt `Microsoft.Spark.CSharp.Examples` w folderze `examples` (spowoduje to również utworzenie projektu powiązań platformy .NET). Jeśli chcesz, możesz napisać własny kod w projekcie `Microsoft.Spark.Examples` ("input_file. JSON" w tym przykładzie to plik JSON z danymi, dla których chcesz utworzyć ramkę danych):
  
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

     Po pomyślnym zakończeniu kompilacji zostaną wyświetlone odpowiednie pliki binarne utworzone w katalogu wyjściowym.     
     Przykładowe dane wyjściowe konsoli:
     
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

#### <a name="using-net-core-cli-for-net-core"></a>Używanie interfejs wiersza polecenia platformy .NET Core dla platformy .NET Core

> [!NOTE]
> Obecnie pracujemy nad automatyzowaniem kompilacji platformy .NET Core dla platformy Spark .NET. Do tego czasu będziemy wdzięczni za cierpliwość wykonywania niektórych czynności ręcznie.

  1. Kompiluj proces roboczy:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      Przykładowe dane wyjściowe konsoli:

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

  2. Kompiluj przykłady:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      Przykładowe dane wyjściowe konsoli:

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

## <a name="run-the-net-for-spark-sample-applications"></a>Uruchamianie przykładowych aplikacji platformy .NET dla platformy Spark

Po skompilowaniu próbek ich uruchomienie będzie możliwe przez `spark-submit`, niezależnie od tego, czy jest przeznaczony .NET Framework czy .NET Core. Upewnij się, że wykonano sekcję [wymagania wstępne](#prerequisites) i zainstalowano Apache Spark.

  1. Ustaw zmienną środowiskową `DOTNET_WORKER_DIR` lub `PATH` w taki sposób, aby obejmowała ścieżkę, w której Wygenerowano `Microsoft.Spark.Worker` plik binarny (np. `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` dla .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` dla platformy .NET Core):

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Otwórz program PowerShell i przejdź do katalogu, w którym Wygenerowano plik binarny aplikacji (np. `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` dla .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` dla platformy .NET Core):

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. Uruchamianie aplikacji jest zgodne ze strukturą podstawową:

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Oto kilka przykładów, które można uruchomić:

     - **[Microsoft. Spark. przykłady. SQL. Batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft. Spark. przykłady. SQL. Streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft. Spark. przykłady. SQL. Streaming. StructuredKafkaWordCount (Maven dostępny)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft. Spark. przykłady. SQL. Streaming. StructuredKafkaWordCount (podano Jars)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
