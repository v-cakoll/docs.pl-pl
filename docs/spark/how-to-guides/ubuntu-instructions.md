---
title: Tworzenie aplikacji .NET dla platformy Spark apache na Ubuntu
description: Dowiedz się, jak zbudować aplikację .NET dla Platformy Spark na Ubuntu
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 6dd6f60bb89a51c47fe17182fc47de818cd00b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187572"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="cbc4f-103">Dowiedz się, jak zbudować aplikację .NET dla Platformy Spark na Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cbc4f-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="cbc4f-104">W tym artykule dowiesz się, jak utworzyć aplikacje platformy .NET dla platformy Spark w ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbc4f-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="cbc4f-105">Prerequisites</span></span>

<span data-ttu-id="cbc4f-106">Jeśli masz już wszystkie poniższe wymagania wstępne, przejdź do kroków [kompilacji.](#build)</span><span class="sxs-lookup"><span data-stu-id="cbc4f-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="cbc4f-107">Pobierz i zainstaluj **[zestaw SDK .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)** lub **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** — zainstalowanie zestawu SDK dodaje pasek `dotnet` narzędzi do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="cbc4f-108">Obsługiwane są platformy .NET Core 2.1, 2.2 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="cbc4f-109">Zainstaluj **[OpenJDK 8](https://openjdk.java.net/install/)**.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="cbc4f-110">Można użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="cbc4f-111">Sprawdź, czy można `java` uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="cbc4f-112">Przykładowe dane wyjściowe wersji java:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="cbc4f-113">Jeśli masz już zainstalowaną wiele wersji OpenJDK i chcesz wybrać OpenJDK 8, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="cbc4f-114">Zainstaluj **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="cbc4f-115">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-115">Run the following command:</span></span>

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       <span data-ttu-id="cbc4f-116">Należy pamiętać, że te zmienne środowiskowe zostaną utracone po zamknięciu terminala.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="cbc4f-117">Jeśli zmiany mają być trwałe, `export` dodaj wiersze do `~/.bashrc` pliku.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="cbc4f-118">Sprawdź, czy można `mvn` uruchomić z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="cbc4f-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="cbc4f-119">Przykładowe wyjście mvn -version:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-119">Sample mvn -version output:</span></span>

       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="cbc4f-120">Zainstaluj **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="cbc4f-121">Pobierz [apache Spark 2.3+](https://spark.apache.org/downloads.html) i wyodrębnij go do `~/bin/spark-2.3.2-bin-hadoop2.7`lokalnego folderu (np. ).</span><span class="sxs-lookup"><span data-stu-id="cbc4f-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="cbc4f-122">(Obsługiwane wersje iskry to 2.3.\*, 2.4.0, 2.4.1, 2.4.3 i 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="cbc4f-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="cbc4f-123">Dodać niezbędne [zmienne środowiskowe](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` `~/bin/spark-2.3.2-bin-hadoop2.7/`(np.) `PATH` i (np. `$SPARK_HOME/bin:$PATH`)</span><span class="sxs-lookup"><span data-stu-id="cbc4f-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="cbc4f-124">Należy pamiętać, że te zmienne środowiskowe zostaną utracone po zamknięciu terminala.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="cbc4f-125">Jeśli zmiany mają być trwałe, `export` dodaj wiersze do `~/.bashrc` pliku.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="cbc4f-126">Sprawdź, czy można `spark-shell` uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="cbc4f-127">Przykładowe wyjście konsoli:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-127">Sample console output:</span></span>

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

<span data-ttu-id="cbc4f-128">Przed przejściem do `dotnet`następnej sekcji upewnij się, że można uruchomić program , `java`, `mvn` `spark-shell` z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="cbc4f-129">Czujesz, że jest lepszy sposób?</span><span class="sxs-lookup"><span data-stu-id="cbc4f-129">Feel there is a better way?</span></span> <span data-ttu-id="cbc4f-130">Proszę [otworzyć problem](https://github.com/dotnet/spark/issues) i nie krępuj się przyczynić.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="cbc4f-131">Kompilacja</span><span class="sxs-lookup"><span data-stu-id="cbc4f-131">Build</span></span>

<span data-ttu-id="cbc4f-132">Pozostała część tego przewodnika musi być sklonowana do komputera repozytorium .NET for Apache `~/dotnet.spark/`Spark np.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="cbc4f-133">Tworzenie warstwy rozszerzeń .NET dla platformy Spark Scala</span><span class="sxs-lookup"><span data-stu-id="cbc4f-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="cbc4f-134">Po przesłaniu aplikacji .NET.NET for Apache Spark ma niezbędną logikę zapisaną w Scali, która informuje Apache Spark, jak obsługiwać żądania (np. żądanie utworzenia nowej sesji Platformy Spark, żądanie przeniesienia danych ze strony .NET do strony JVM itp.).</span><span class="sxs-lookup"><span data-stu-id="cbc4f-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="cbc4f-135">Tę logikę można znaleźć w [.NET dla Kodu Źródłowego Apache Spark Scala](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="cbc4f-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="cbc4f-136">Następnym krokiem jest zbudowanie warstwy rozszerzenia .NET for Apache Spark Scala:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="cbc4f-137">Powinny być widoczne jars utworzone dla obsługiwanych wersji platformy Spark:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="cbc4f-138">Tworzenie przykładowych aplikacji platformy .NET przy użyciu interfejsu wiersza polecenia rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="cbc4f-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="cbc4f-139">W tej sekcji wyjaśniono, jak utworzyć [przykładowe aplikacje](https://github.com/dotnet/spark/tree/master/examples) dla platformy .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="cbc4f-140">Te kroki pomogą w zrozumieniu ogólnego procesu tworzenia dla dowolnej aplikacji platformy .NET for Spark.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="cbc4f-141">Zbuduj pracownika:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="cbc4f-142">Przykładowe wyjście konsoli:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-142">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. <span data-ttu-id="cbc4f-143">Tworzenie próbek:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="cbc4f-144">Przykładowe wyjście konsoli:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-144">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="cbc4f-145">Uruchamianie przykładowych aplikacji platformy .NET for Spark</span><span class="sxs-lookup"><span data-stu-id="cbc4f-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="cbc4f-146">Po utworzeniu przykładów można `spark-submit` użyć do przesłania aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="cbc4f-147">Upewnij się, że masz następujące [wymagania wstępne](#prerequisites) sekcji i zainstalowane Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="cbc4f-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="cbc4f-148">Ustaw `DOTNET_WORKER_DIR` zmienną środowiskową lub `PATH` zmienną środowiskową tak, aby `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`uwzględniała ścieżkę, w `Microsoft.Spark.Worker` której został wygenerowany plik binarny (np. ).</span><span class="sxs-lookup"><span data-stu-id="cbc4f-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="cbc4f-149">Otwórz terminal i przejdź do katalogu, w którym został wygenerowany `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`plik binarny aplikacji (np. ).</span><span class="sxs-lookup"><span data-stu-id="cbc4f-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="cbc4f-150">Uruchamianie aplikacji jest zgodne z podstawową strukturą:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="cbc4f-151">Oto kilka przykładów, które można uruchomić:</span><span class="sxs-lookup"><span data-stu-id="cbc4f-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="cbc4f-152">**[Program Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="cbc4f-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="cbc4f-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="cbc4f-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="cbc4f-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven dostępne)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="cbc4f-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="cbc4f-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (słoiki dostarczone)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="cbc4f-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
