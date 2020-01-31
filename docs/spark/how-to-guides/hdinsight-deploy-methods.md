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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="ba456-103">Przesyłanie zadania platformy .NET dla Apache Spark do usługi Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ba456-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="ba456-104">Istnieją dwa sposoby wdrażania zadania programu .NET dla Apache Spark w usłudze HDInsight: `spark-submit` i Apache usługi Livy.</span><span class="sxs-lookup"><span data-stu-id="ba456-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="ba456-105">Wdrażanie przy użyciu platformy Spark — przesyłanie</span><span class="sxs-lookup"><span data-stu-id="ba456-105">Deploy using spark-submit</span></span>

<span data-ttu-id="ba456-106">Możesz użyć polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) do przesyłania zadań programu .net dla Apache Spark do usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ba456-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="ba456-107">Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **SSH + logowanie do klastra**.</span><span class="sxs-lookup"><span data-stu-id="ba456-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="ba456-108">Skopiuj informacje logowania SSH i wklej nazwę logowania do terminalu.</span><span class="sxs-lookup"><span data-stu-id="ba456-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="ba456-109">Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="ba456-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="ba456-110">Powinny pojawić się komunikaty z powitaniem do Ubuntu i Spark.</span><span class="sxs-lookup"><span data-stu-id="ba456-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="ba456-111">Użyj polecenia **Spark-Submit** , aby uruchomić aplikację w klastrze usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="ba456-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="ba456-112">Pamiętaj **, aby zastąpić obiekt** **mojekontomagazynu** i go w przykładowym skrypcie z rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="ba456-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="ba456-113">Pamiętaj również, aby zamienić `microsoft-spark-2.3.x-0.6.0.jar` na odpowiedni plik JAR używany do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="ba456-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="ba456-114">`2.3.x` reprezentuje wersję Apache Spark, a `0.6.0` reprezentuje wersję programu [.net for Apache Spark Worker](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="ba456-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="ba456-115">Wdrażanie przy użyciu oprogramowania Apache usługi Livy</span><span class="sxs-lookup"><span data-stu-id="ba456-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="ba456-116">Aby przesłać Apache Spark zadań do klastra Azure HDInsight Spark, można użyć oprogramowania [Apache usługi Livy](https://livy.incubator.apache.org/), interfejsu API REST Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="ba456-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="ba456-117">Aby uzyskać więcej informacji, zobacz [zadania zdalne z Apache usługi Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="ba456-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="ba456-118">Następujące polecenie można uruchomić w systemie Linux przy użyciu `curl`:</span><span class="sxs-lookup"><span data-stu-id="ba456-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="ba456-119">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ba456-119">Next steps</span></span>

* [<span data-ttu-id="ba456-120">Wprowadzenie do platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ba456-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="ba456-121">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="ba456-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="ba456-122">Dokumentacja usługi HDInsight</span><span class="sxs-lookup"><span data-stu-id="ba456-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
