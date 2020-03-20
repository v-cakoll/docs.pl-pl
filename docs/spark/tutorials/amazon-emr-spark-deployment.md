---
title: Wdrażanie aplikacji .NET for Apache Spark w amazon emr spark
description: Dowiedz się, jak wdrożyć aplikację platformy .NET for Apache Spark w amazon emr spark.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73454936"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="06292-103">Wdrażanie aplikacji .NET for Apache Spark w amazon emr spark</span><span class="sxs-lookup"><span data-stu-id="06292-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="06292-104">W tym samouczku opisano, jak wdrożyć aplikację .NET for Apache Spark w amazon emr spark.</span><span class="sxs-lookup"><span data-stu-id="06292-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="06292-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="06292-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="06292-106">Przygotowanie programu Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="06292-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="06292-107">Publikowanie aplikacji Spark .NET</span><span class="sxs-lookup"><span data-stu-id="06292-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="06292-108">Wdrażanie aplikacji w amazon emr spark</span><span class="sxs-lookup"><span data-stu-id="06292-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="06292-109">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="06292-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06292-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="06292-110">Prerequisites</span></span>

<span data-ttu-id="06292-111">Przed rozpoczęciem wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="06292-111">Before you start, do the following:</span></span>

* <span data-ttu-id="06292-112">Pobierz [plik AWS CLI](https://aws.amazon.com/cli/).</span><span class="sxs-lookup"><span data-stu-id="06292-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="06292-113">Pobierz [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do lokalnego komputera.</span><span class="sxs-lookup"><span data-stu-id="06292-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="06292-114">Jest to skrypt pomocniczy, którego później używasz do kopiowania plików zależnych platformy .NET dla platformy Apache Spark do węzłów procesu roboczego klastra Platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="06292-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="06292-115">Przygotowywanie zależności procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="06292-115">Prepare worker dependencies</span></span>

<span data-ttu-id="06292-116">**Microsoft.Spark.Worker** jest składnikiem wewnętrznej bazy danych, który działa na poszczególnych węzłach procesu roboczego klastra platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="06292-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="06292-117">Jeśli chcesz wykonać C# UDF (funkcja zdefiniowana przez użytkownika), Spark musi zrozumieć, jak uruchomić .NET CLR do wykonania UDF.</span><span class="sxs-lookup"><span data-stu-id="06292-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="06292-118">**Microsoft.Spark.Worker** udostępnia kolekcję klas do platformy Spark, które włączają tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="06292-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="06292-119">Wybierz wersję netcoreapp [systemu Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) linux, która ma zostać wdrożona w klastrze.</span><span class="sxs-lookup"><span data-stu-id="06292-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="06292-120">Na przykład, jeśli `.NET for Apache Spark v0.1.0` `netcoreapp2.1`chcesz użyć , chcesz pobrać [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="06292-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="06292-121">Przekazywanie `Microsoft.Spark.Worker.<release>.tar.gz` i [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (np. S3), do których klaster ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="06292-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="06292-122">Przygotowanie aplikacji .NET dla aplikacji Apache Spark</span><span class="sxs-lookup"><span data-stu-id="06292-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="06292-123">Postępuj zgodnie z samouczkiem [Wprowadzenie,](get-started.md) aby utworzyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="06292-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="06292-124">Opublikuj aplikację Spark .NET jako samodzielną.</span><span class="sxs-lookup"><span data-stu-id="06292-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="06292-125">Uruchom następujące polecenie w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="06292-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="06292-126">Tworzenie `<your app>.zip` dla opublikowanych plików.</span><span class="sxs-lookup"><span data-stu-id="06292-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="06292-127">Uruchom następujące polecenie na `zip`Linuksie za pomocą .</span><span class="sxs-lookup"><span data-stu-id="06292-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="06292-128">Przekaż następujące elementy do rozproszonego systemu plików (np. S3), do których klaster ma dostęp:</span><span class="sxs-lookup"><span data-stu-id="06292-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="06292-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten słoik jest dołączony jako część pakietu [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet i jest współlokowany w katalogu wyjściowym kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06292-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="06292-130">Pliki (takie jak pliki zależności lub wspólne dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL zawierające funkcje zdefiniowane przez użytkownika lub biblioteki, od których zależy aplikacja), które mają zostać umieszczone w katalogu roboczym każdego wykonawcy.</span><span class="sxs-lookup"><span data-stu-id="06292-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="06292-131">Wdrożenie w Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="06292-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="06292-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) to zarządzana platforma klastrowa, która upraszcza uruchamianie platform danych big data w aws.</span><span class="sxs-lookup"><span data-stu-id="06292-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="06292-133">Amazon EMR Spark jest oparty na linuksie.</span><span class="sxs-lookup"><span data-stu-id="06292-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="06292-134">W związku z tym jeśli jesteś zainteresowany wdrożeniem aplikacji do Amazon EMR Spark, upewnij się, że aplikacja jest zgodna ze standardem .NET i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06292-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="06292-135">Wdrażanie programu Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="06292-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="06292-136">Ten krok jest wymagany tylko w tworzeniu klastra.</span><span class="sxs-lookup"><span data-stu-id="06292-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="06292-137">Uruchamianie `install-worker.sh` podczas tworzenia klastra przy użyciu [akcji Bootstrap](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span><span class="sxs-lookup"><span data-stu-id="06292-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="06292-138">Uruchom następujące polecenie na linuksie przy użyciu interfejsu wiersza polecenia AWS.</span><span class="sxs-lookup"><span data-stu-id="06292-138">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="06292-139">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="06292-139">Run your app</span></span>

<span data-ttu-id="06292-140">Istnieją dwa sposoby uruchamiania aplikacji w Amazon EMR Spark: spark-submit i Amazon EMR Steps.</span><span class="sxs-lookup"><span data-stu-id="06292-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="06292-141">Użyj spark-submit</span><span class="sxs-lookup"><span data-stu-id="06292-141">Use spark-submit</span></span>

<span data-ttu-id="06292-142">Za pomocą polecenia [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać zadania platformy .NET dla platformy Apache Spark do platformy Amazon EMR Spark.</span><span class="sxs-lookup"><span data-stu-id="06292-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="06292-143">`ssh`do jednego z węzłów w klastrze.</span><span class="sxs-lookup"><span data-stu-id="06292-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="06292-144">Uruchom polecenie `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="06292-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="06292-145">Użyj kroków Amazon EMR</span><span class="sxs-lookup"><span data-stu-id="06292-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="06292-146">[Kroki EMR Amazon](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) mogą być używane do przesyłania zadań do platformy Spark zainstalowanej w klastrze EMR.</span><span class="sxs-lookup"><span data-stu-id="06292-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="06292-147">Uruchom następujące polecenie na linuksie przy użyciu interfejsu wiersza polecenia AWS.</span><span class="sxs-lookup"><span data-stu-id="06292-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="06292-148">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="06292-148">Next steps</span></span>

<span data-ttu-id="06292-149">W tym samouczku wdrożono aplikację .NET for Apache Spark w amazon emr spark.</span><span class="sxs-lookup"><span data-stu-id="06292-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="06292-150">W przypadku przykładowych projektów platformy .NET for Apache Spark przejdź do usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="06292-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="06292-151">.NET dla próbek platformy Spark apache</span><span class="sxs-lookup"><span data-stu-id="06292-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
