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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="118ba-103">Prześlij zadanie platformy .NET dla platformy Apache Spark do usługi Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="118ba-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="118ba-104">Istnieją dwa sposoby wdrażania zadania platformy .NET dla platformy `spark-submit` Apache Spark w witrynie HDInsight: i Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="118ba-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="118ba-105">Wdrażanie przy użyciu spark-submit</span><span class="sxs-lookup"><span data-stu-id="118ba-105">Deploy using spark-submit</span></span>

<span data-ttu-id="118ba-106">Za pomocą polecenia [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać zadania platformy .NET dla platformy Apache Spark do usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="118ba-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="118ba-107">Przejdź do klastra platformy SPARK usługi HDInsight w witrynie Azure portal, a następnie wybierz pozycję **SSH + Cluster login**.</span><span class="sxs-lookup"><span data-stu-id="118ba-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="118ba-108">Skopiuj dane logowania do ssh i wklej login do terminalu.</span><span class="sxs-lookup"><span data-stu-id="118ba-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="118ba-109">Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="118ba-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="118ba-110">Powinieneś zobaczyć wiadomości witające Cię do Ubuntu i Spark.</span><span class="sxs-lookup"><span data-stu-id="118ba-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="118ba-111">Użyj polecenia **spark-submit,** aby uruchomić aplikację w klastrze HDInsight.</span><span class="sxs-lookup"><span data-stu-id="118ba-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="118ba-112">Pamiętaj, aby zastąpić **mycontainer** i **mystorageaccount** w przykładowym skrypcie rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="118ba-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="118ba-113">Ponadto należy zastąpić `microsoft-spark-2.3.x-0.6.0.jar` odpowiednim plikiem jar, którego używasz do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="118ba-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="118ba-114">`2.3.x`reprezentuje wersję programu Apache `0.6.0` Spark i reprezentuje wersję [pracownika platformy .NET dla programu Apache Spark](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="118ba-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="118ba-115">Wdrażanie przy użyciu Apache Livy</span><span class="sxs-lookup"><span data-stu-id="118ba-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="118ba-116">Za pomocą [apache Livy](https://livy.incubator.apache.org/), interfejsu API Rest platformy Apache Spark, można przesłać zadania platformy .NET dla platformy Apache Spark do klastra platformy Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="118ba-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="118ba-117">Aby uzyskać więcej informacji, zobacz [Zadania zdalne z apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="118ba-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="118ba-118">Możesz uruchomić następujące polecenie na `curl`Linuksie za pomocą:</span><span class="sxs-lookup"><span data-stu-id="118ba-118">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="118ba-119">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="118ba-119">Next steps</span></span>

* [<span data-ttu-id="118ba-120">Wprowadzenie do platformy .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="118ba-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="118ba-121">Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="118ba-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="118ba-122">Dokumentacja hdinsight</span><span class="sxs-lookup"><span data-stu-id="118ba-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
