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
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="c82e9-103">Dowiedz się, jak skompilować aplikację platformy .NET dla Apache Spark w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="c82e9-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="c82e9-104">W tym artykule przedstawiono sposób kompilowania aplikacji platformy .NET dla Apache Spark w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="c82e9-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c82e9-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c82e9-105">Prerequisites</span></span>

<span data-ttu-id="c82e9-106">Jeśli masz już wszystkie poniższe wymagania wstępne, przejdź do kroków [kompilacji](#build) .</span><span class="sxs-lookup"><span data-stu-id="c82e9-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="c82e9-107">Pobierz i zainstaluj **[zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** — Instalacja zestawu SDK spowoduje dodanie do ścieżki `dotnet` łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c82e9-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="c82e9-108">Obsługiwane są programy .NET Core 2,1, 2,2 i 3,1.</span><span class="sxs-lookup"><span data-stu-id="c82e9-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="c82e9-109">Zainstaluj **[program Visual Studio 2019](https://www.visualstudio.com/downloads/)** (wersja 16,3 lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="c82e9-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="c82e9-110">Wersja społeczności jest całkowicie bezpłatna.</span><span class="sxs-lookup"><span data-stu-id="c82e9-110">The Community version is completely free.</span></span> <span data-ttu-id="c82e9-111">Podczas konfigurowania instalacji należy uwzględnić następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="c82e9-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="c82e9-112">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c82e9-112">.NET desktop development</span></span>
       * <span data-ttu-id="c82e9-113">Wszystkie wymagane składniki</span><span class="sxs-lookup"><span data-stu-id="c82e9-113">All Required Components</span></span>
         * <span data-ttu-id="c82e9-114">Narzędzia programistyczne .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="c82e9-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="c82e9-115">Programowanie dla wielu platform w środowisku .NET Core</span><span class="sxs-lookup"><span data-stu-id="c82e9-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="c82e9-116">Wszystkie wymagane składniki</span><span class="sxs-lookup"><span data-stu-id="c82e9-116">All Required Components</span></span>
  3. <span data-ttu-id="c82e9-117">Zainstaluj **[środowisko Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** .</span><span class="sxs-lookup"><span data-stu-id="c82e9-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span> 
     - <span data-ttu-id="c82e9-118">Wybierz odpowiednią wersję systemu operacyjnego, np. JDK-8u201-Windows-x64. exe dla komputera z systemem win x64.</span><span class="sxs-lookup"><span data-stu-id="c82e9-118">Select the appropriate version for your operating system e.g., jdk-8u201-windows-x64.exe for Win x64 machine.</span></span>
     - <span data-ttu-id="c82e9-119">Zainstaluj program przy użyciu Instalatora i sprawdź, czy można uruchamiać `java` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c82e9-119">Install using the installer and verify you are able to run `java` from your command-line.</span></span>
  4. <span data-ttu-id="c82e9-120">Zainstaluj program **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .</span><span class="sxs-lookup"><span data-stu-id="c82e9-120">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="c82e9-121">Pobierz [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="c82e9-121">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
     - <span data-ttu-id="c82e9-122">Wyodrębnij do katalogu lokalnego, np., `C:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-122">Extract to a local directory e.g., `C:\bin\apache-maven-3.6.0\`.</span></span>
     - <span data-ttu-id="c82e9-123">Dodaj Maven Apache do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml) , np., `C:\bin\apache-maven-3.6.0\bin`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-123">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\apache-maven-3.6.0\bin`.</span></span>
     - <span data-ttu-id="c82e9-124">Sprawdź, czy możesz uruchamiać `mvn` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c82e9-124">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="c82e9-125">Zainstaluj **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .</span><span class="sxs-lookup"><span data-stu-id="c82e9-125">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="c82e9-126">Pobierz [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) i wyodrębnij go do folderu lokalnego (np. `C:\bin\spark-2.3.2-bin-hadoop2.7\`) przy użyciu [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="c82e9-126">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`) using [7-zip](https://www.7-zip.org/).</span></span> <span data-ttu-id="c82e9-127">(Obsługiwane wersje platformy Spark to 2,3. \*, 2.4.0, 2.4.1, 2.4.3 i 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="c82e9-127">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="c82e9-128">Dodaj [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` np., `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-128">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - <span data-ttu-id="c82e9-129">Dodaj Apache Spark do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml) , np., `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-129">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span></span>

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - <span data-ttu-id="c82e9-130">Sprawdź, czy możesz uruchamiać `spark-shell` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c82e9-130">Verify you are able to run `spark-shell` from your command-line.</span></span>        
        <span data-ttu-id="c82e9-131">Przykładowe dane wyjściowe konsoli:</span><span class="sxs-lookup"><span data-stu-id="c82e9-131">Sample console output:</span></span>

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

  6. <span data-ttu-id="c82e9-132">Zainstaluj **[WinUtils](https://github.com/steveloughran/winutils)** .</span><span class="sxs-lookup"><span data-stu-id="c82e9-132">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="c82e9-133">Pobierz plik binarny `winutils.exe` z [repozytorium WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="c82e9-133">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="c82e9-134">Należy wybrać wersję usługi Hadoop, z którą została skompilowana dystrybucja platformy Spark, np. przy użyciu usługi Hadoop-2.7.1 dla platformy Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="c82e9-134">You should select the version of Hadoop the Spark distribution was compiled with, e.g. use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="c82e9-135">Zapisz `winutils.exe` dane binarne w wybranym katalogu, np., `C:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-135">Save `winutils.exe` binary to a directory of your choice e.g., `C:\hadoop\bin`.</span></span>
     - <span data-ttu-id="c82e9-136">Ustaw `HADOOP_HOME` tak, aby odzwierciedlał katalog z winutils. exe (bez bin).</span><span class="sxs-lookup"><span data-stu-id="c82e9-136">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="c82e9-137">Na przykład za pomocą wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="c82e9-137">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="c82e9-138">Ustaw zmienną środowiskową PATH do uwzględnienia `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-138">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="c82e9-139">Na przykład za pomocą wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="c82e9-139">For instance, using command-line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="c82e9-140">Przed przejściem do następnej sekcji upewnij się, że można uruchomić `dotnet`, `java`, `mvn``spark-shell` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c82e9-140">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="c82e9-141">Czy istnieje lepszy sposób?</span><span class="sxs-lookup"><span data-stu-id="c82e9-141">Feel there is a better way?</span></span> <span data-ttu-id="c82e9-142">[Otwórz problem](https://github.com/dotnet/spark/issues) i śmiało, aby współtworzyć.</span><span class="sxs-lookup"><span data-stu-id="c82e9-142">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="c82e9-143">Jeśli wszystkie zmienne środowiskowe zostały zaktualizowane, może być wymagane nowe wystąpienie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c82e9-143">A new instance of the command-line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="c82e9-144">{1&gt;Kompilacja&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c82e9-144">Build</span></span>

<span data-ttu-id="c82e9-145">W pozostałej części tego przewodnika konieczne będzie sklonowanie repozytorium .NET for Apache Spark na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c82e9-145">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="c82e9-146">Można wybrać dowolną lokalizację dla sklonowanego repozytorium, np. `C:\github\dotnet-spark\`.</span><span class="sxs-lookup"><span data-stu-id="c82e9-146">You can choose any location for the cloned repository, e.g., `C:\github\dotnet-spark\`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="c82e9-147">Kompiluj platformę .NET dla Apache Spark warstwy rozszerzeń Scala</span><span class="sxs-lookup"><span data-stu-id="c82e9-147">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="c82e9-148">Gdy przesyłasz aplikację .NET, platforma .NET dla Apache Spark ma niezbędną logikę zapisaną w Scala, która informuje Apache Spark, jak obsługiwać żądania (np. żądanie utworzenia nowej sesji platformy Spark, żądanie przeniesienia danych z platformy .NET do strony JVM itp.).</span><span class="sxs-lookup"><span data-stu-id="c82e9-148">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="c82e9-149">Tę logikę można znaleźć w [kodzie źródłowym programu .net for Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="c82e9-149">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="c82e9-150">Bez względu na to, czy używasz .NET Framework, czy platformy .NET Core, musisz skompilować platformę .NET dla Apache Spark Scala warstwy rozszerzeń:</span><span class="sxs-lookup"><span data-stu-id="c82e9-150">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package 
```

<span data-ttu-id="c82e9-151">Powinna zostać wyświetlona JARs utworzona dla obsługiwanych wersji platformy Spark:</span><span class="sxs-lookup"><span data-stu-id="c82e9-151">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="c82e9-152">Tworzenie przykładowych aplikacji platformy .NET dla platformy Spark</span><span class="sxs-lookup"><span data-stu-id="c82e9-152">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="c82e9-153">W tej sekcji opisano sposób tworzenia [przykładowych aplikacji](https://github.com/dotnet/spark/tree/master/examples) dla platformy .net dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="c82e9-153">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="c82e9-154">Te kroki ułatwią zrozumienie ogólnego procesu tworzenia aplikacji platformy .NET dla platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="c82e9-154">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="c82e9-155">Korzystanie z programu Visual Studio dla .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c82e9-155">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="c82e9-156">Otwórz `src\csharp\Microsoft.Spark.sln` w programie Visual Studio i skompiluj projekt `Microsoft.Spark.CSharp.Examples` w folderze `examples` (spowoduje to również utworzenie projektu powiązań platformy .NET).</span><span class="sxs-lookup"><span data-stu-id="c82e9-156">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="c82e9-157">Jeśli chcesz, możesz napisać własny kod w projekcie `Microsoft.Spark.Examples` ("input_file. JSON" w tym przykładzie to plik JSON z danymi, dla których chcesz utworzyć ramkę danych):</span><span class="sxs-lookup"><span data-stu-id="c82e9-157">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
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

     <span data-ttu-id="c82e9-158">Po pomyślnym zakończeniu kompilacji zostaną wyświetlone odpowiednie pliki binarne utworzone w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="c82e9-158">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>     
     <span data-ttu-id="c82e9-159">Przykładowe dane wyjściowe konsoli:</span><span class="sxs-lookup"><span data-stu-id="c82e9-159">Sample console output:</span></span>
     
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

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="c82e9-160">Używanie interfejs wiersza polecenia platformy .NET Core dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="c82e9-160">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="c82e9-161">Obecnie pracujemy nad automatyzowaniem kompilacji platformy .NET Core dla platformy Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="c82e9-161">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="c82e9-162">Do tego czasu będziemy wdzięczni za cierpliwość wykonywania niektórych czynności ręcznie.</span><span class="sxs-lookup"><span data-stu-id="c82e9-162">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="c82e9-163">Kompiluj proces roboczy:</span><span class="sxs-lookup"><span data-stu-id="c82e9-163">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      <span data-ttu-id="c82e9-164">Przykładowe dane wyjściowe konsoli:</span><span class="sxs-lookup"><span data-stu-id="c82e9-164">Sample console output:</span></span>

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

  2. <span data-ttu-id="c82e9-165">Kompiluj przykłady:</span><span class="sxs-lookup"><span data-stu-id="c82e9-165">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      <span data-ttu-id="c82e9-166">Przykładowe dane wyjściowe konsoli:</span><span class="sxs-lookup"><span data-stu-id="c82e9-166">Sample console output:</span></span>

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

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="c82e9-167">Uruchamianie przykładowych aplikacji platformy .NET dla platformy Spark</span><span class="sxs-lookup"><span data-stu-id="c82e9-167">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="c82e9-168">Po skompilowaniu próbek ich uruchomienie będzie możliwe przez `spark-submit`, niezależnie od tego, czy jest przeznaczony .NET Framework czy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c82e9-168">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="c82e9-169">Upewnij się, że wykonano sekcję [wymagania wstępne](#prerequisites) i zainstalowano Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="c82e9-169">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="c82e9-170">Ustaw zmienną środowiskową `DOTNET_WORKER_DIR` lub `PATH` w taki sposób, aby obejmowała ścieżkę, w której Wygenerowano `Microsoft.Spark.Worker` plik binarny (np. `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` dla .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` dla platformy .NET Core):</span><span class="sxs-lookup"><span data-stu-id="c82e9-170">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="c82e9-171">Otwórz program PowerShell i przejdź do katalogu, w którym Wygenerowano plik binarny aplikacji (np. `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` dla .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` dla platformy .NET Core):</span><span class="sxs-lookup"><span data-stu-id="c82e9-171">Open Powershell and go to the directory where your app binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="c82e9-172">Uruchamianie aplikacji jest zgodne ze strukturą podstawową:</span><span class="sxs-lookup"><span data-stu-id="c82e9-172">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="c82e9-173">Oto kilka przykładów, które można uruchomić:</span><span class="sxs-lookup"><span data-stu-id="c82e9-173">Here are some examples you can run:</span></span>

     - <span data-ttu-id="c82e9-174">**[Microsoft. Spark. przykłady. SQL. Batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="c82e9-174">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="c82e9-175">**[Microsoft. Spark. przykłady. SQL. Streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="c82e9-175">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="c82e9-176">**[Microsoft. Spark. przykłady. SQL. Streaming. StructuredKafkaWordCount (Maven dostępny)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="c82e9-176">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="c82e9-177">**[Microsoft. Spark. przykłady. SQL. Streaming. StructuredKafkaWordCount (podano Jars)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="c82e9-177">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
