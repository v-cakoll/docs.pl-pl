---
title: Wprowadzenie do platformy .NET dla Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577072"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Samouczek: Wprowadzenie do platformy .NET dla Apache Spark

W tym samouczku przedstawiono sposób uruchamiania aplikacji platformy .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark
> * Pobierz **pakiet Microsoft. Spark. Worker**
> * Kompilowanie i uruchamianie prostej aplikacji .NET dla Apache Spark

## <a name="prepare-your-environment"></a>Przygotowywanie środowiska

Przed rozpoczęciem upewnij się, że można uruchomić `dotnet` `mvn`polecenie `java`, `spark-shell` , z wiersza polecenia. Jeśli środowisko jest już przygotowane, możesz przejść do następnej sekcji. Jeśli nie można uruchomić żadnego lub wszystkich poleceń, wykonaj poniższe kroki.

1. Pobierz i zainstaluj [zestaw .NET Core 2.1 x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1). Zainstalowanie zestawu SDK dodaje `dotnet` łańcucha narzędzi do ścieżki. Aby sprawdzić instalację, `dotnet --version` Użyj polecenia programu PowerShell.

2. Zainstaluj [program Visual studio 2017](https://www.visualstudio.com/downloads/) lub [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) z najnowszymi aktualizacjami. Możesz użyć społeczności, Professional lub Enterprise. Wersja społeczności jest bezpłatna.

   Podczas instalacji wybierz następujące obciążenia:
      * Programowanie aplikacji klasycznych dla platformy .NET
          * Wszystkie wymagane składniki
          * Narzędzia programistyczne .NET Framework 4.6.1
      * Programowanie dla wielu platform .NET core
          * Wszystkie wymagane składniki

3. Zainstaluj [środowisko Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

    * Wybierz odpowiednią wersję systemu operacyjnego. Na przykład wybierz **JDK-8u201-Windows-x64. exe** dla komputera z systemem Windows x64.
    * Aby sprawdzić instalację, `java -version` Użyj polecenia programu PowerShell.

4. Zainstaluj program [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).
    * Pobierz [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).
    * Wyodrębnij do katalogu lokalnego. Na przykład `c:\bin\apache-maven-3.6.0\`.
    * Dodaj Maven Apache do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml). W przypadku wyodrębnienia `c:\bin\apache-maven-3.6.0\`do programu należy dodać `c:\bin\apache-maven-3.6.0\bin` do swojej ścieżki.
    * Aby sprawdzić instalację, `mvn -version` Użyj polecenia programu PowerShell.

5. Zainstaluj [Apache Spark 2.3 +](https://spark.apache.org/downloads.html). Apache Spark 2.4 + nie jest obsługiwana.
    * Pobierz [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) i wyodrębnij go do folderu lokalnego przy użyciu narzędzia, takiego jak [7-zip](https://www.7-zip.org/) lub [WinZip](https://www.winzip.com/). Na przykład można wyodrębnić go do `c:\bin\spark-2.3.2-bin-hadoop2.7\`.
    * Dodaj Apache Spark do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml). W przypadku wyodrębnienia `c:\bin\spark-2.3.2-bin-hadoop2.7\`do programu należy dodać `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` do swojej ścieżki.
    * Dodaj [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) o `SPARK_HOME`nazwie. W przypadku wyodrębnienia `C:\bin\spark-2.3.2-bin-hadoop2.7\`do programu `C:\bin\spark-2.3.2-bin-hadoop2.7\` Użyj **wartości zmiennej**.
    * Upewnij się, że można uruchomić `spark-shell` z poziomu wiersza polecenia.

6. Skonfiguruj [WinUtils](https://github.com/steveloughran/winutils).
    * Pobierz plik binarny **winutils. exe** z [repozytorium winutils](https://github.com/steveloughran/winutils). Wybierz wersję usługi Hadoop, z którą została skompilowana dystrybucja platformy Spark. Na przykład użyjesz usługi **Hadoop-2.7.1** dla **platformy Spark 2.3.2**. Wersja usługi Hadoop znajduje się na końcu nazwy folderu instalacji platformy Spark.
    * Zapisz plik binarny **winutils. exe** w wybranym katalogu. Na przykład `c:\hadoop\bin`.
    * Ustaw `HADOOP_HOME` , aby odzwierciedlał katalog z **winutils. exe** bez `bin`. Na przykład `c:\hadoop`.
    * Ustaw zmienną środowiskową PATH do uwzględnienia `%HADOOP_HOME%\bin`.

Przed przejściem do następnej sekcji `dotnet`Sprawdź `java`, czy `spark-shell` można uruchomić,, `mvn`, z wiersza polecenia.

## <a name="download-the-microsoftsparkworker-release"></a>Pobierz wersję Microsoft. Spark. Worker

1. Pobierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) z strony .net for Apache Spark Release releases na komputer lokalny. Na przykład możesz pobrać go do ścieżki, `c:\bin\Microsoft.Spark.Worker\`.

2. Utwórz [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) o `DotnetWorkerPath` nazwie i ustaw ją na katalog, w którym został pobrany i wyodrębniony element **Microsoft. Spark. Worker**. Na przykład `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Klonowanie repozytorium programu .NET dla Apache Spark GitHub

Użyj następującego polecenia [GitBash](https://gitforwindows.org/) , aby sklonować Apache Spark repozytorium programu .NET do maszyny.

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Napisz aplikację platformy .NET dla Apache Spark

1. Otwórz **program Visual Studio** i przejdź do **pliku > utwórz nowy projekt > aplikacji konsolowej (.NET Core)** . Nadaj aplikacji nazwę **HelloSpark**.

2. Zainstaluj [pakiet NuGet Microsoft. Spark](https://www.nuget.org/profiles/spark). Aby uzyskać więcej informacji na temat instalowania pakietów NuGet, zobacz [różne sposoby instalowania pakietu NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. W **Eksplorator rozwiązań**Otwórz **program.cs** i Napisz następujący C# kod:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Skompiluj rozwiązanie.

## <a name="run-your-net-for-apache-spark-app"></a>Uruchamianie aplikacji platformy .NET dla Apache Spark

1. Otwórz program **PowerShell** i zmień katalog na folder, w którym jest przechowywana aplikacja.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Utwórz plik o nazwie **ludzie. JSON** z następującą zawartością:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Użyj następującego polecenia programu PowerShell, aby uruchomić aplikację:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Gratulacje! Pomyślnie utworzono i uruchomiono aplikację .NET dla Apache Spark.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark
> * Pobierz **pakiet Microsoft. Spark. Worker**
> * Kompilowanie i uruchamianie prostej aplikacji .NET dla Apache Spark

Zapoznaj się ze stroną zasobów, aby dowiedzieć się więcej.
> [!div class="nextstepaction"]
> [Platforma .NET dla Apache Spark zasobów](../resources/index.md)
