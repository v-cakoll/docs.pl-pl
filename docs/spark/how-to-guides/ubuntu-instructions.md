---
title: Tworzenie aplikacji platformy .NET dla Apache Spark w systemie Ubuntu
description: Dowiedz się, jak utworzyć platformę .NET dla aplikacji Apache Spark w systemie Ubuntu
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: a12c861d0f231910f715a13fd41d1f3f0d6748a7
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928044"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Dowiedz się, jak utworzyć platformę .NET dla aplikacji Apache Spark w systemie Ubuntu

W tym artykule przedstawiono sposób kompilowania aplikacji platformy .NET dla Apache Spark w programie Ubuntu.

## <a name="prerequisites"></a>Wymagania wstępne

Jeśli masz już wszystkie poniższe wymagania wstępne, przejdź do kroków [kompilacji](#build) .

1. Pobranie i zainstalowanie zestawu **[.net core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** lub **[zestawu .NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** — zainstalowanie zestawu SDK dodaje `dotnet` łańcucha narzędzi do ścieżki.  Obsługiwane są programy .NET Core 2,1, 2,2 i 3,1.

2. Zainstaluj program **[OpenJDK 8](https://openjdk.java.net/install/)** . 

   - Możesz użyć następującego polecenia:

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Sprawdź, czy możesz uruchamiać `java` z poziomu wiersza polecenia.       

      Przykładowy kod Java — wersja wyjściowa:
          
      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Jeśli masz już zainstalowaną wiele wersji OpenJDK i chcesz wybrać OpenJDK 8, użyj następującego polecenia:

      ```bash
      sudo update-alternatives --config java
      ```

3. Zainstaluj program **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .

   * Uruchom następujące polecenie:

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
       
       Należy pamiętać, że te zmienne środowiskowe zostaną utracone po zamknięciu terminalu. Jeśli chcesz, aby zmiany były trwałe, Dodaj `export` wierszy do pliku `~/.bashrc`.

   * Sprawdź, czy możesz uruchamiać `mvn` z poziomu wiersza polecenia       

       Przykład MVN — wersja wyjściowa:
       
       ```
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. Zainstaluj **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .
Pobierz [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) i wyodrębnij go do folderu lokalnego (np. `~/bin/spark-2.3.2-bin-hadoop2.7`). (Obsługiwane wersje platformy Spark to 2,3. *, 2.4.0, 2.4.1, 2.4.3 i 2.4.4)

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * Dodaj wymagane [zmienne środowiskowe](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (np., `~/bin/spark-2.3.2-bin-hadoop2.7/`) i `PATH` (np. `$SPARK_HOME/bin:$PATH`)

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```
       
      Należy pamiętać, że te zmienne środowiskowe zostaną utracone po zamknięciu terminalu. Jeśli chcesz, aby zmiany były trwałe, Dodaj `export` wierszy do pliku `~/.bashrc`.

   * Sprawdź, czy możesz uruchamiać `spark-shell` z poziomu wiersza polecenia.

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

Przed przejściem do następnej sekcji upewnij się, że można uruchomić `dotnet`, `java`, `mvn``spark-shell` z poziomu wiersza polecenia. Czy istnieje lepszy sposób? [Otwórz problem](https://github.com/dotnet/spark/issues) i śmiało, aby współtworzyć.

## <a name="build"></a>{1&gt;Kompilacja&lt;1}

W pozostałej części tego przewodnika należy sklonować repozytorium .NET for Apache Spark na maszynę, np. `~/dotnet.spark/`.

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Warstwa kompilacji platformy .NET dla platformy Spark Scala

Gdy przesyłasz aplikację .NET, platforma .NET dla Apache Spark ma niezbędną logikę zapisaną w Scala, która informuje Apache Spark, jak obsługiwać żądania (np. żądanie utworzenia nowej sesji platformy Spark, żądanie przeniesienia danych z platformy .NET do strony JVM itp.). Tę logikę można znaleźć w programie [.net for Apache Spark Scala kod źródłowy](https://github.com/dotnet/spark/tree/master/src/scala).

Następnym krokiem jest skompilowanie warstwy rozszerzenia programu .NET for Apache Spark Scala:

```bash
cd src/scala
mvn clean package 
```

Powinna zostać wyświetlona JARs utworzona dla obsługiwanych wersji platformy Spark:

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>Tworzenie przykładowych aplikacji platformy .NET przy użyciu interfejs wiersza polecenia platformy .NET Core

W tej sekcji opisano sposób tworzenia [przykładowych aplikacji](https://github.com/dotnet/spark/tree/master/examples) dla platformy .net dla Apache Spark. Te kroki ułatwią zrozumienie ogólnego procesu tworzenia aplikacji platformy .NET dla platformy Spark.

1. Kompiluj proces roboczy:

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```
      
   Przykładowe dane wyjściowe konsoli:

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

2. Kompiluj przykłady:

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```
      
   Przykładowe dane wyjściowe konsoli:

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

## <a name="run-the-net-for-spark-sample-applications"></a>Uruchamianie przykładowych aplikacji platformy .NET dla platformy Spark

Po skompilowaniu przykładów można użyć `spark-submit` do przesyłania aplikacji platformy .NET Core. Upewnij się, że wykonano sekcję [wymagania wstępne](#prerequisites) i zainstalowano Apache Spark.

1. Ustaw zmienną środowiskową `DOTNET_WORKER_DIR` lub `PATH` w taki sposób, aby obejmowała ścieżkę, w której Wygenerowano `Microsoft.Spark.Worker` plik binarny (np. `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. Otwórz Terminal i przejdź do katalogu, w którym Wygenerowano plik binarny aplikacji (np. `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. Uruchamianie aplikacji jest zgodne ze strukturą podstawową:

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Oto kilka przykładów, które można uruchomić:

   * **[Microsoft. Spark. przykłady. SQL. Batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft. Spark. przykłady. SQL. Streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft. Spark. przykłady. SQL. Streaming. StructuredKafkaWordCount (Maven dostępny)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft. Spark. przykłady. SQL. Streaming. StructuredKafkaWordCount (podano Jars)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
