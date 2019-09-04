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
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="57f85-103">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="57f85-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="57f85-104">W tym samouczku przedstawiono sposób wdrażania aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="57f85-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="57f85-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="57f85-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="57f85-106">Przygotuj pakiet Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="57f85-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="57f85-107">Publikowanie aplikacji platformy .NET Spark</span><span class="sxs-lookup"><span data-stu-id="57f85-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="57f85-108">Wdrażanie aplikacji w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="57f85-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="57f85-109">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="57f85-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57f85-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="57f85-110">Prerequisites</span></span>

<span data-ttu-id="57f85-111">Przed rozpoczęciem wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57f85-111">Before you start, do the following:</span></span>

* <span data-ttu-id="57f85-112">Pobierz [Eksplorator usługi Azure Storage](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="57f85-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="57f85-113">Pobierz [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) na komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="57f85-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="57f85-114">Jest to skrypt pomocnika używany później do kopiowania programu .NET pod kątem Apache Spark plików zależnych do węzłów procesu roboczego klastra platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="57f85-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="57f85-115">Przygotowanie zależności procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="57f85-115">Prepare worker dependencies</span></span>

<span data-ttu-id="57f85-116">**Microsoft. Spark. Worker** to składnik zaplecza, który znajduje się w poszczególnych węzłach procesu roboczego klastra Spark.</span><span class="sxs-lookup"><span data-stu-id="57f85-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="57f85-117">Jeśli chcesz wykonać funkcję C# UDF (zdefiniowaną przez użytkownika), platforma Spark musi zrozumieć, jak uruchomić program .NET CLR w celu wykonania UDF.</span><span class="sxs-lookup"><span data-stu-id="57f85-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="57f85-118">Element **Microsoft. Spark. Worker** udostępnia kolekcję klas na platformie Spark, które umożliwiają włączenie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="57f85-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="57f85-119">Wybierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, która ma zostać wdrożona w klastrze.</span><span class="sxs-lookup"><span data-stu-id="57f85-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="57f85-120">Jeśli na przykład chcesz `.NET for Apache Spark v0.1.0` użyć `netcoreapp2.1`, Pobierz [pakiet Microsoft. Spark. Worker. netcoreapp 2.1. linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="57f85-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="57f85-121">Przekazuj `Microsoft.Spark.Worker.<release>.tar.gz` i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (np. HDFS, WASB, ADLS), do którego klaster ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="57f85-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="57f85-122">Przygotowywanie aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="57f85-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="57f85-123">Postępuj zgodnie [z samouczkiem wprowadzenie,](get-started.md) aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="57f85-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="57f85-124">Opublikuj swoją aplikację platformy Spark .NET jako samodzielny.</span><span class="sxs-lookup"><span data-stu-id="57f85-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="57f85-125">Następujące polecenie można uruchomić w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="57f85-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="57f85-126">Twórz `<your app>.zip` pliki do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="57f85-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="57f85-127">Następujące polecenie można uruchomić w systemie Linux przy użyciu `zip`polecenia.</span><span class="sxs-lookup"><span data-stu-id="57f85-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="57f85-128">Przekaż następujące polecenie do rozproszonego systemu plików (np. HDFS, WASB, ADLS), do którego klaster ma dostęp:</span><span class="sxs-lookup"><span data-stu-id="57f85-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="57f85-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten plik JAR jest dołączany jako część pakietu NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) i znajduje się w katalogu danych wyjściowych kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57f85-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="57f85-130">Pliki (takie jak pliki zależności lub typowe dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL, które zawierają zdefiniowane przez użytkownika funkcje lub `app` biblioteki, od których zależy), zostaną umieszczone w katalogu roboczym każdego wykonawcy.</span><span class="sxs-lookup"><span data-stu-id="57f85-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="57f85-131">Wdróż do Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="57f85-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="57f85-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) jest implementacją firmy Microsoft Apache Spark w chmurze, która umożliwia użytkownikom uruchamianie i konfigurowanie klastrów platformy Spark na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="57f85-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="57f85-133">Za pomocą klastrów usługi HDInsight Spark można przetwarzać dane przechowywane w [usłudze Azure Storage](https://azure.microsoft.com/services/storage/) lub [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span><span class="sxs-lookup"><span data-stu-id="57f85-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="57f85-134">Azure HDInsight Spark jest oparty na systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="57f85-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="57f85-135">Jeśli interesuje Cię wdrażanie aplikacji w Azure HDInsight Spark, upewnij się, że aplikacja jest .NET Standard zgodna i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57f85-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="57f85-136">Wdróż aplikację Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="57f85-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="57f85-137">Ten krok jest wymagany tylko raz dla klastra.</span><span class="sxs-lookup"><span data-stu-id="57f85-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="57f85-138">Uruchom `install-worker.sh` w klastrze przy użyciu [akcji skryptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="57f85-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="57f85-139">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="57f85-139">Setting</span></span>|<span data-ttu-id="57f85-140">Wartość</span><span class="sxs-lookup"><span data-stu-id="57f85-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="57f85-141">Typ skryptu</span><span class="sxs-lookup"><span data-stu-id="57f85-141">Script type</span></span>|<span data-ttu-id="57f85-142">Celnej</span><span class="sxs-lookup"><span data-stu-id="57f85-142">Custom</span></span>|
|<span data-ttu-id="57f85-143">Nazwa</span><span class="sxs-lookup"><span data-stu-id="57f85-143">Name</span></span>|<span data-ttu-id="57f85-144">Zainstaluj pakiet Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="57f85-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="57f85-145">Identyfikator URI skryptu bash</span><span class="sxs-lookup"><span data-stu-id="57f85-145">Bash script URI</span></span>|<span data-ttu-id="57f85-146">Identyfikator URI, do którego został `install-worker.sh`przekazany.</span><span class="sxs-lookup"><span data-stu-id="57f85-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="57f85-147">Na przykład:`abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span><span class="sxs-lookup"><span data-stu-id="57f85-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="57f85-148">Typy węzłów</span><span class="sxs-lookup"><span data-stu-id="57f85-148">Node type(s)</span></span>|<span data-ttu-id="57f85-149">Odpowiedzialn</span><span class="sxs-lookup"><span data-stu-id="57f85-149">Worker</span></span>|
|<span data-ttu-id="57f85-150">Parametry</span><span class="sxs-lookup"><span data-stu-id="57f85-150">Parameters</span></span>|<span data-ttu-id="57f85-151">Parametry do `install-worker.sh`.</span><span class="sxs-lookup"><span data-stu-id="57f85-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="57f85-152">Na przykład jeśli przekazano `install-worker.sh` do Azure Data Lake generacji 2, będzie to możliwe. `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`</span><span class="sxs-lookup"><span data-stu-id="57f85-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![Obraz akcji skryptu](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="57f85-154">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="57f85-154">Run your app</span></span>

<span data-ttu-id="57f85-155">Zadanie można przesłać do usługi Azure HDInsight przy użyciu `spark-submit` programu lub Apache usługi Livy.</span><span class="sxs-lookup"><span data-stu-id="57f85-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="57f85-156">Korzystanie z platformy Spark — przesyłanie</span><span class="sxs-lookup"><span data-stu-id="57f85-156">Use spark-submit</span></span>

<span data-ttu-id="57f85-157">Możesz użyć polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) do przesyłania zadań programu .net dla Apache Spark do usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="57f85-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="57f85-158">`ssh`w jednym z węzłów głównych w klastrze.</span><span class="sxs-lookup"><span data-stu-id="57f85-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="57f85-159">Uruchom `spark-submit`:</span><span class="sxs-lookup"><span data-stu-id="57f85-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="57f85-160">Korzystanie z programu Apache usługi Livy</span><span class="sxs-lookup"><span data-stu-id="57f85-160">Use Apache Livy</span></span>

<span data-ttu-id="57f85-161">Aby przesłać Apache Spark zadań do klastra Azure HDInsight Spark, można użyć oprogramowania [Apache usługi Livy](https://livy.incubator.apache.org/), interfejsu API REST Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="57f85-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="57f85-162">Aby uzyskać więcej informacji, zobacz [zadania zdalne z Apache usługi Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="57f85-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="57f85-163">Następujące polecenie można uruchomić w systemie Linux przy użyciu `curl`:</span><span class="sxs-lookup"><span data-stu-id="57f85-163">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="57f85-164">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="57f85-164">Next steps</span></span>

<span data-ttu-id="57f85-165">W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="57f85-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="57f85-166">Aby dowiedzieć się więcej o usłudze HDInsight, przejdź do dokumentacji usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="57f85-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="57f85-167">Dokumentacja usługi Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="57f85-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
