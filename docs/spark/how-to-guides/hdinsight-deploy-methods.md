---
title: Przesyłanie zadania platformy .NET dla Apache Spark do usługi Azure HDInsight
description: Dowiedz się, jak przesłać zadanie platformy .NET dla Apache Spark do usługi Azure HDInsight przy użyciu platformy Spark — przesyłanie i Apache usługi Livy.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 50611b1f62934a446e5b80a8c53698efe23cd1fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617694"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="896bc-103">Przesyłanie zadania platformy .NET dla Apache Spark do usługi Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="896bc-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="896bc-104">Istnieją dwa sposoby wdrażania zadania programu .NET dla Apache Spark w usłudze HDInsight: `spark-submit` i Apache usługi Livy.</span><span class="sxs-lookup"><span data-stu-id="896bc-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="896bc-105">Wdrażanie przy użyciu platformy Spark — przesyłanie</span><span class="sxs-lookup"><span data-stu-id="896bc-105">Deploy using spark-submit</span></span>

<span data-ttu-id="896bc-106">Możesz użyć polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) do przesyłania zadań programu .net dla Apache Spark do usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="896bc-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="896bc-107">Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **SSH + logowanie do klastra**.</span><span class="sxs-lookup"><span data-stu-id="896bc-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="896bc-108">Skopiuj informacje logowania SSH i wklej nazwę logowania do terminalu.</span><span class="sxs-lookup"><span data-stu-id="896bc-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="896bc-109">Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="896bc-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="896bc-110">Powinny pojawić się komunikaty z powitaniem do Ubuntu i Spark.</span><span class="sxs-lookup"><span data-stu-id="896bc-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="896bc-111">Użyj polecenia **Spark-Submit** , aby uruchomić aplikację w klastrze usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="896bc-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="896bc-112">Pamiętaj **, aby zastąpić obiekt** **mojekontomagazynu** i go w przykładowym skrypcie z rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="896bc-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="896bc-113">Pamiętaj również, aby zamienić na `microsoft-spark-2.3.x-0.6.0.jar` odpowiedni plik JAR używany do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="896bc-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="896bc-114">`2.3.x`reprezentuje wersję Apache Spark i `0.6.0` reprezentuje wersję [platformy .net dla Apache Spark procesu roboczego](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="896bc-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="896bc-115">Wdrażanie przy użyciu oprogramowania Apache usługi Livy</span><span class="sxs-lookup"><span data-stu-id="896bc-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="896bc-116">Aby przesłać Apache Spark zadań do klastra Azure HDInsight Spark, można użyć oprogramowania [Apache usługi Livy](https://livy.incubator.apache.org/), interfejsu API REST Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="896bc-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="896bc-117">Aby uzyskać więcej informacji, zobacz [zadania zdalne z Apache usługi Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="896bc-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="896bc-118">Następujące polecenie można uruchomić w systemie Linux przy użyciu `curl` :</span><span class="sxs-lookup"><span data-stu-id="896bc-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="896bc-119">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="896bc-119">Next steps</span></span>

* [<span data-ttu-id="896bc-120">Wprowadzenie do platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="896bc-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="896bc-121">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="896bc-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="896bc-122">Dokumentacja usługi HDInsight</span><span class="sxs-lookup"><span data-stu-id="896bc-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
