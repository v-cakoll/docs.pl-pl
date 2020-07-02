---
title: Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark
description: Dowiedz się, jak wdrożyć aplikację .NET for Apache Spark w usłudze Amazon EMR Spark.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6cf26044693c5d923d11e1bbc72232e7009fe73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618262"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="5c11a-103">Wdrażanie aplikacji .NET dla Apache Spark w usłudze Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="5c11a-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="5c11a-104">W tym samouczku przedstawiono sposób wdrażania aplikacji .NET for Apache Spark w usłudze Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="5c11a-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="5c11a-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5c11a-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5c11a-106">Przygotuj pakiet Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="5c11a-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="5c11a-107">Publikowanie aplikacji platformy .NET Spark</span><span class="sxs-lookup"><span data-stu-id="5c11a-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="5c11a-108">Wdrażanie aplikacji w usłudze Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="5c11a-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="5c11a-109">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5c11a-109">Run your app</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="5c11a-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5c11a-110">Prerequisites</span></span>

<span data-ttu-id="5c11a-111">Przed rozpoczęciem wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5c11a-111">Before you start, do the following:</span></span>

* <span data-ttu-id="5c11a-112">Pobierz [interfejs wiersza polecenia AWS](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="5c11a-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="5c11a-113">Pobierz [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) na komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="5c11a-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="5c11a-114">Jest to skrypt pomocnika używany później do kopiowania programu .NET pod kątem Apache Spark plików zależnych do węzłów procesu roboczego klastra platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="5c11a-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="5c11a-115">Przygotowanie zależności procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="5c11a-115">Prepare worker dependencies</span></span>

<span data-ttu-id="5c11a-116">**Microsoft. Spark. Worker** to składnik zaplecza, który znajduje się w poszczególnych węzłach procesu roboczego klastra Spark.</span><span class="sxs-lookup"><span data-stu-id="5c11a-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="5c11a-117">Jeśli chcesz wykonać funkcję UDF w języku C# (funkcja zdefiniowana przez użytkownika), platforma Spark musi zrozumieć, jak uruchomić środowisko CLR środowiska .NET, aby wykonać operację UDF.</span><span class="sxs-lookup"><span data-stu-id="5c11a-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="5c11a-118">Element **Microsoft. Spark. Worker** udostępnia kolekcję klas na platformie Spark, które umożliwiają włączenie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5c11a-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="5c11a-119">Wybierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, która ma zostać wdrożona w klastrze.</span><span class="sxs-lookup"><span data-stu-id="5c11a-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="5c11a-120">Jeśli na przykład chcesz `.NET for Apache Spark v0.1.0` użyć `netcoreapp2.1` , Pobierz [pakiet Microsoft. Spark. Worker. netcoreapp 2.1. linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="5c11a-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="5c11a-121">Przekazuj `Microsoft.Spark.Worker.<release>.tar.gz` i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (np. S3), do którego ma dostęp klaster.</span><span class="sxs-lookup"><span data-stu-id="5c11a-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="5c11a-122">Przygotowywanie aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5c11a-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="5c11a-123">Postępuj zgodnie [z samouczkiem wprowadzenie,](get-started.md) aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="5c11a-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="5c11a-124">Opublikuj swoją aplikację platformy Spark .NET jako samodzielny.</span><span class="sxs-lookup"><span data-stu-id="5c11a-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="5c11a-125">Uruchom następujące polecenie w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="5c11a-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="5c11a-126">Twórz `<your app>.zip` pliki do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="5c11a-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="5c11a-127">Uruchom następujące polecenie w systemie Linux przy użyciu polecenia `zip` .</span><span class="sxs-lookup"><span data-stu-id="5c11a-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="5c11a-128">Przekaż następujące elementy do rozproszonego systemu plików (np. S3), do którego klaster ma dostęp:</span><span class="sxs-lookup"><span data-stu-id="5c11a-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="5c11a-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten plik JAR jest dołączony jako część pakietu NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) i znajduje się w katalogu danych wyjściowych kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c11a-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="5c11a-130">Pliki (takie jak pliki zależności lub typowe dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL, które zawierają zdefiniowane przez użytkownika funkcje lub biblioteki, od których zależy aplikacja), zostaną umieszczone w katalogu roboczym każdego wykonawcy.</span><span class="sxs-lookup"><span data-stu-id="5c11a-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="5c11a-131">Wdrażanie w usłudze Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="5c11a-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="5c11a-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) to zarządzana platforma klastra, która upraszcza uruchamianie platform danych Big Data w systemie AWS.</span><span class="sxs-lookup"><span data-stu-id="5c11a-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="5c11a-133">System Amazon EMR Spark jest oparty na systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="5c11a-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="5c11a-134">W związku z tym, Jeśli interesuje Cię wdrażanie aplikacji w usłudze Amazon EMR Spark, upewnij się, że aplikacja jest zgodna .NET Standard i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c11a-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="5c11a-135">Wdróż aplikację Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="5c11a-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="5c11a-136">Ten krok jest wymagany tylko podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="5c11a-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="5c11a-137">Uruchamiany `install-worker.sh` podczas tworzenia klastra za pomocą [akcji Bootstrap](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="5c11a-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="5c11a-138">Uruchom następujące polecenie w systemie Linux przy użyciu interfejsu wiersza polecenia AWS.</span><span class="sxs-lookup"><span data-stu-id="5c11a-138">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="5c11a-139">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5c11a-139">Run your app</span></span>

<span data-ttu-id="5c11a-140">Istnieją dwa sposoby uruchamiania aplikacji w usłudze Amazon EMR Spark: Spark-Submit i Amazon EMR.</span><span class="sxs-lookup"><span data-stu-id="5c11a-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="5c11a-141">Korzystanie z platformy Spark — przesyłanie</span><span class="sxs-lookup"><span data-stu-id="5c11a-141">Use spark-submit</span></span>

<span data-ttu-id="5c11a-142">Za pomocą polecenia [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać Apache Spark zadań programu .NET do usługi Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="5c11a-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="5c11a-143">`ssh`w jednym z węzłów w klastrze.</span><span class="sxs-lookup"><span data-stu-id="5c11a-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="5c11a-144">Uruchom polecenie `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="5c11a-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="5c11a-145">Korzystanie z kroków EMR Amazon</span><span class="sxs-lookup"><span data-stu-id="5c11a-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="5c11a-146">[Procedury Amazon EMR](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) mogą służyć do przesyłania zadań do platformy Spark zainstalowanej w klastrze EMR.</span><span class="sxs-lookup"><span data-stu-id="5c11a-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="5c11a-147">Uruchom następujące polecenie w systemie Linux przy użyciu interfejsu wiersza polecenia AWS.</span><span class="sxs-lookup"><span data-stu-id="5c11a-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="5c11a-148">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5c11a-148">Next steps</span></span>

<span data-ttu-id="5c11a-149">W tym samouczku wdrożono aplikację .NET for Apache Spark w usłudze Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="5c11a-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="5c11a-150">W przypadku platformy .NET do Apache Spark przykładowe projekty przejdź do witryny GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c11a-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5c11a-151">.NET for Apache Spark — przykłady</span><span class="sxs-lookup"><span data-stu-id="5c11a-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
