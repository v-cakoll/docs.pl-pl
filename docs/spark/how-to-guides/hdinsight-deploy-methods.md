---
title: Prześlij zadanie platformy .NET dla platformy Apache Spark do usługi Azure HDInsight
description: Dowiedz się, jak przesłać zadanie platformy .NET dla platformy Apache Spark do usługi Azure HDInsight przy użyciu spark-submit i Apache Livy.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185797"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Prześlij zadanie platformy .NET dla platformy Apache Spark do usługi Azure HDInsight

Istnieją dwa sposoby wdrażania zadania platformy .NET dla platformy `spark-submit` Apache Spark w witrynie HDInsight: i Apache Livy.

## <a name="deploy-using-spark-submit"></a>Wdrażanie przy użyciu spark-submit

Za pomocą polecenia [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać zadania platformy .NET dla platformy Apache Spark do usługi Azure HDInsight.

1. Przejdź do klastra platformy SPARK usługi HDInsight w witrynie Azure portal, a następnie wybierz pozycję **SSH + Cluster login**.

2. Skopiuj dane logowania do ssh i wklej login do terminalu. Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra. Powinieneś zobaczyć wiadomości witające Cię do Ubuntu i Spark.

3. Użyj polecenia **spark-submit,** aby uruchomić aplikację w klastrze HDInsight. Pamiętaj, aby zastąpić **mycontainer** i **mystorageaccount** w przykładowym skrypcie rzeczywistymi nazwami kontenera obiektów blob i konta magazynu. Ponadto należy zastąpić `microsoft-spark-2.3.x-0.6.0.jar` odpowiednim plikiem jar, którego używasz do wdrożenia. `2.3.x`reprezentuje wersję programu Apache `0.6.0` Spark i reprezentuje wersję [pracownika platformy .NET dla programu Apache Spark](https://github.com/dotnet/spark/releases).

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Wdrażanie przy użyciu Apache Livy

Za pomocą [apache Livy](https://livy.incubator.apache.org/), interfejsu API Rest platformy Apache Spark, można przesłać zadania platformy .NET dla platformy Apache Spark do klastra platformy Azure HDInsight Spark. Aby uzyskać więcej informacji, zobacz [Zadania zdalne z apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Możesz uruchomić następujące polecenie na `curl`Linuksie za pomocą:

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

* [Wprowadzenie do platformy .NET for Apache Spark](../tutorials/get-started.md)
* [Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [Dokumentacja hdinsight](https://docs.microsoft.com/azure/hdinsight/)
