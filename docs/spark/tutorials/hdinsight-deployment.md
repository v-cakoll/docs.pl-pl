---
title: Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla Apache Spark w usłudze HDInsight.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 81d1af1fd4e3329c4a289eea388edf8af57d7c4e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243946"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight

W tym samouczku przedstawiono sposób wdrażania aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
> * Przygotuj pakiet Microsoft. Spark. Worker
> * Publikowanie aplikacji platformy .NET Spark
> * Wdrażanie aplikacji w usłudze Azure HDInsight
> * Uruchamianie aplikacji

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem wykonaj następujące czynności:

* Pobierz [Eksplorator usługi Azure Storage](https://azure.microsoft.com/features/storage-explorer/).
* Pobierz [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) na komputer lokalny. Jest to skrypt pomocnika używany później do kopiowania programu .NET pod kątem Apache Spark plików zależnych do węzłów procesu roboczego klastra platformy Spark.

## <a name="prepare-worker-dependencies"></a>Przygotowanie zależności procesu roboczego

**Microsoft. Spark. Worker** to składnik zaplecza, który znajduje się w poszczególnych węzłach procesu roboczego klastra Spark. Jeśli chcesz wykonać funkcję C# UDF (zdefiniowaną przez użytkownika), platforma Spark musi zrozumieć, jak uruchomić program .NET CLR w celu wykonania UDF. Element **Microsoft. Spark. Worker** udostępnia kolekcję klas na platformie Spark, które umożliwiają włączenie tej funkcji.

1. Wybierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, która ma zostać wdrożona w klastrze.

   Jeśli na przykład chcesz `.NET for Apache Spark v0.1.0` użyć `netcoreapp2.1`, Pobierz [pakiet Microsoft. Spark. Worker. netcoreapp 2.1. linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).

2. Przekazuj `Microsoft.Spark.Worker.<release>.tar.gz` i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (np. HDFS, WASB, ADLS), do którego klaster ma dostęp.

## <a name="prepare-your-net-for-apache-spark-app"></a>Przygotowywanie aplikacji .NET dla Apache Spark

1. Postępuj zgodnie [z samouczkiem wprowadzenie,](get-started.md) aby skompilować aplikację.

2. Opublikuj swoją aplikację platformy Spark .NET jako samodzielny.

   Następujące polecenie można uruchomić w systemie Linux.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Twórz `<your app>.zip` pliki do opublikowania.

   Następujące polecenie można uruchomić w systemie Linux przy użyciu `zip`polecenia.

   ```bash
   zip -r <your app>.zip .
   ```

4. Przekaż następujące polecenie do rozproszonego systemu plików (np. HDFS, WASB, ADLS), do którego klaster ma dostęp:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten plik JAR jest dołączany jako część pakietu NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) i znajduje się w katalogu danych wyjściowych kompilacji aplikacji.
   * `<your app>.zip`
   * Pliki (takie jak pliki zależności lub typowe dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL, które zawierają zdefiniowane przez użytkownika funkcje lub `app` biblioteki, od których zależy), zostaną umieszczone w katalogu roboczym każdego wykonawcy.

## <a name="deploy-to-azure-hdinsight-spark"></a>Wdróż do Azure HDInsight Spark

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) jest implementacją firmy Microsoft Apache Spark w chmurze, która umożliwia użytkownikom uruchamianie i konfigurowanie klastrów platformy Spark na platformie Azure. Za pomocą klastrów usługi HDInsight Spark można przetwarzać dane przechowywane w [usłudze Azure Storage](https://azure.microsoft.com/services/storage/) lub [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).

> [!NOTE]
> Azure HDInsight Spark jest oparty na systemie Linux. Jeśli interesuje Cię wdrażanie aplikacji w Azure HDInsight Spark, upewnij się, że aplikacja jest .NET Standard zgodna i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.

### <a name="deploy-microsoftsparkworker"></a>Wdróż aplikację Microsoft. Spark. Worker

Ten krok jest wymagany tylko raz dla klastra.

Uruchom `install-worker.sh` w klastrze przy użyciu [akcji skryptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).

|Ustawienie|Wartość|
|-------|-----|
|Typ skryptu|Celnej|
|Nazwa|Zainstaluj pakiet Microsoft. Spark. Worker|
|Identyfikator URI skryptu bash|Identyfikator URI, do którego został `install-worker.sh`przekazany. Na przykład:`abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|Typy węzłów|Odpowiedzialn|
|Parametry|Parametry do `install-worker.sh`. Na przykład jeśli przekazano `install-worker.sh` do Azure Data Lake generacji 2, będzie to możliwe. `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`|

![Obraz akcji skryptu](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Uruchamianie aplikacji

Zadanie można przesłać do usługi Azure HDInsight przy użyciu `spark-submit` programu lub Apache usługi Livy.

### <a name="use-spark-submit"></a>Korzystanie z platformy Spark — przesyłanie

Możesz użyć polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) do przesyłania zadań programu .net dla Apache Spark do usługi Azure HDInsight.
 
1. `ssh`w jednym z węzłów głównych w klastrze.

1. Uruchom `spark-submit`:

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Korzystanie z programu Apache usługi Livy

Aby przesłać Apache Spark zadań do klastra Azure HDInsight Spark, można użyć oprogramowania [Apache usługi Livy](https://livy.incubator.apache.org/), interfejsu API REST Apache Spark. Aby uzyskać więcej informacji, zobacz [zadania zdalne z Apache usługi Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Następujące polecenie można uruchomić w systemie Linux przy użyciu `curl`:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Następne kroki

W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze Azure HDInsight. Aby dowiedzieć się więcej o usłudze HDInsight, przejdź do dokumentacji usługi Azure HDInsight.

> [!div class="nextstepaction"]
> [Dokumentacja usługi Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/)
