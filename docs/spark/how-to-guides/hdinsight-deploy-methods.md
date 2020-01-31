---
title: Przesyłanie zadania platformy .NET dla Apache Spark do usługi Azure HDInsight
description: Dowiedz się, jak przesłać zadanie platformy .NET dla Apache Spark do usługi Azure HDInsight przy użyciu platformy Spark — przesyłanie i Apache usługi Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: d558234a53cc22d65540a380ac7f5b3ac03ba0ae
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868021"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Przesyłanie zadania platformy .NET dla Apache Spark do usługi Azure HDInsight

Istnieją dwa sposoby wdrażania zadania programu .NET dla Apache Spark w usłudze HDInsight: `spark-submit` i Apache usługi Livy.

## <a name="deploy-using-spark-submit"></a>Wdrażanie przy użyciu platformy Spark — przesyłanie

Możesz użyć polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) do przesyłania zadań programu .net dla Apache Spark do usługi Azure HDInsight.
 
1. Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **SSH + logowanie do klastra**.

2. Skopiuj informacje logowania SSH i wklej nazwę logowania do terminalu. Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra. Powinny pojawić się komunikaty z powitaniem do Ubuntu i Spark.

3. Użyj polecenia **Spark-Submit** , aby uruchomić aplikację w klastrze usługi HDInsight. Pamiętaj **, aby zastąpić obiekt** **mojekontomagazynu** i go w przykładowym skrypcie z rzeczywistymi nazwami kontenera obiektów blob i konta magazynu. Pamiętaj również, aby zamienić `microsoft-spark-2.3.x-0.6.0.jar` na odpowiedni plik JAR używany do wdrożenia. `2.3.x` reprezentuje wersję Apache Spark, a `0.6.0` reprezentuje wersję programu [.net for Apache Spark Worker](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Wdrażanie przy użyciu oprogramowania Apache usługi Livy

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

* [Wprowadzenie do platformy .NET dla Apache Spark](../tutorials/get-started.md)
* [Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentacja usługi HDInsight](https://docs.microsoft.com/azure/hdinsight/)
