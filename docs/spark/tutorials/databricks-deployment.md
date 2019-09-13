---
title: Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla Apache Spark w usłudze datakostki.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db374a47140392577872f6635eb7275682a7a547
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928552"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="da7c6-103">Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach</span><span class="sxs-lookup"><span data-stu-id="da7c6-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="da7c6-104">W tym samouczku przedstawiono sposób wdrażania programu .NET dla aplikacji Apache Spark w kostkach.</span><span class="sxs-lookup"><span data-stu-id="da7c6-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="da7c6-105">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="da7c6-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="da7c6-106">Przygotuj pakiet Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="da7c6-106">Prepare Microsoft.Spark.Worker</span></span>
> - <span data-ttu-id="da7c6-107">Publikowanie aplikacji platformy .NET Spark</span><span class="sxs-lookup"><span data-stu-id="da7c6-107">Publish your Spark .NET app</span></span>
> - <span data-ttu-id="da7c6-108">Wdrażanie aplikacji w kostkach danych</span><span class="sxs-lookup"><span data-stu-id="da7c6-108">Deploy your app to Databricks</span></span>
> - <span data-ttu-id="da7c6-109">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="da7c6-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da7c6-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="da7c6-110">Prerequisites</span></span>

<span data-ttu-id="da7c6-111">Przed rozpoczęciem wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="da7c6-111">Before you start, do the following:</span></span>

- <span data-ttu-id="da7c6-112">Pobierz [interfejs wiersza polecenia datakosteks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="da7c6-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
- <span data-ttu-id="da7c6-113">Pobierz [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) na komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="da7c6-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="da7c6-114">Jest to skrypt pomocnika używany później do kopiowania programu .NET pod kątem Apache Spark plików zależnych do węzłów procesu roboczego klastra platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="da7c6-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="da7c6-115">Przygotowanie zależności procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="da7c6-115">Prepare worker dependencies</span></span>

<span data-ttu-id="da7c6-116">**Microsoft. Spark. Worker** to składnik zaplecza, który znajduje się w poszczególnych węzłach procesu roboczego klastra Spark.</span><span class="sxs-lookup"><span data-stu-id="da7c6-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="da7c6-117">Jeśli chcesz wykonać funkcję C# UDF (zdefiniowaną przez użytkownika), platforma Spark musi zrozumieć, jak uruchomić program .NET CLR w celu wykonania UDF.</span><span class="sxs-lookup"><span data-stu-id="da7c6-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="da7c6-118">Element **Microsoft. Spark. Worker** udostępnia kolekcję klas na platformie Spark, które umożliwiają włączenie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="da7c6-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="da7c6-119">Wybierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp, która ma zostać wdrożona w klastrze.</span><span class="sxs-lookup"><span data-stu-id="da7c6-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="da7c6-120">Jeśli na przykład chcesz `.NET for Apache Spark v0.1.0` użyć `netcoreapp2.1`, Pobierz [pakiet Microsoft. Spark. Worker. netcoreapp 2.1. linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="da7c6-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="da7c6-121">Przekazuj `Microsoft.Spark.Worker.<release>.tar.gz` i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) do rozproszonego systemu plików (na przykład DBFS), do którego ma dostęp klaster.</span><span class="sxs-lookup"><span data-stu-id="da7c6-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="da7c6-122">Przygotowywanie aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="da7c6-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="da7c6-123">Postępuj zgodnie [z samouczkiem wprowadzenie,](get-started.md) aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="da7c6-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="da7c6-124">Opublikuj swoją aplikację platformy Spark .NET jako samodzielny.</span><span class="sxs-lookup"><span data-stu-id="da7c6-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="da7c6-125">Następujące polecenie można uruchomić w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="da7c6-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="da7c6-126">Twórz `<your app>.zip` pliki do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="da7c6-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="da7c6-127">Następujące polecenie można uruchomić w systemie Linux przy użyciu `zip`polecenia.</span><span class="sxs-lookup"><span data-stu-id="da7c6-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="da7c6-128">Przekaż następujące polecenie do rozproszonego systemu plików (na przykład DBFS), do którego klaster ma dostęp:</span><span class="sxs-lookup"><span data-stu-id="da7c6-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   - <span data-ttu-id="da7c6-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Ten plik JAR jest dołączany jako część pakietu NuGet [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) i znajduje się w katalogu danych wyjściowych kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da7c6-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   - `<your app>.zip`
   - <span data-ttu-id="da7c6-130">Pliki (takie jak pliki zależności lub typowe dane dostępne dla każdego pracownika) lub zestawy (takie jak biblioteki DLL, które zawierają zdefiniowane przez użytkownika funkcje lub biblioteki, od których zależy aplikacja), zostaną umieszczone w katalogu roboczym każdego wykonawcy.</span><span class="sxs-lookup"><span data-stu-id="da7c6-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="da7c6-131">Wdrażanie w usłudze Databricks</span><span class="sxs-lookup"><span data-stu-id="da7c6-131">Deploy to Databricks</span></span>

<span data-ttu-id="da7c6-132">[Datakostki](https://databricks.com) to platforma, która zapewnia oparte na chmurze przetwarzanie danych Big Data przy użyciu Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="da7c6-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="da7c6-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) i [AWS datakostki](https://databricks.com/aws) są oparte na systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="da7c6-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="da7c6-134">W związku z tym, Jeśli interesuje Cię wdrażanie aplikacji w kostkach, upewnij się, że aplikacja jest .NET Standard zgodna i że używasz [kompilatora .NET Core](https://dotnet.microsoft.com/download) do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="da7c6-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="da7c6-135">Usługi datakostki umożliwiają przesyłanie programu .NET dla aplikacji Apache Spark do istniejącego aktywnego klastra lub tworzenie nowego klastra przy każdym uruchomieniu zadania.</span><span class="sxs-lookup"><span data-stu-id="da7c6-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="da7c6-136">Wymaga to zainstalowania **programu Microsoft. Spark. Worker** przed przesłaniem aplikacji platformy .net dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="da7c6-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="da7c6-137">Wdróż aplikację Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="da7c6-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="da7c6-138">Ten krok jest wymagany tylko raz dla klastra.</span><span class="sxs-lookup"><span data-stu-id="da7c6-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="da7c6-139">Pobierz [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) i [Install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) na komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="da7c6-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="da7c6-140">Zmodyfikuj **DB-init.sh** w taki sposób, aby wskazywała wersję **Microsoft. Spark. Worker** , którą chcesz pobrać i zainstalować w klastrze.</span><span class="sxs-lookup"><span data-stu-id="da7c6-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="da7c6-141">Zainstaluj [interfejs wiersza polecenia datakosteks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="da7c6-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="da7c6-142">[Skonfiguruj szczegóły uwierzytelniania](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) dla interfejsu wiersza polecenia datakosteks.</span><span class="sxs-lookup"><span data-stu-id="da7c6-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="da7c6-143">Przekaż pliki do klastra datakostks przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="da7c6-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="da7c6-144">Przejdź do obszaru roboczego usługi Databricks.</span><span class="sxs-lookup"><span data-stu-id="da7c6-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="da7c6-145">Wybierz pozycję **klastry** z menu po lewej stronie, a następnie wybierz pozycję **Utwórz klaster**.</span><span class="sxs-lookup"><span data-stu-id="da7c6-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="da7c6-146">Po odpowiednim skonfigurowaniu klastra Ustaw **skrypt init** i Utwórz klaster.</span><span class="sxs-lookup"><span data-stu-id="da7c6-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Obraz akcji skryptu](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="da7c6-148">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="da7c6-148">Run your app</span></span> 

<span data-ttu-id="da7c6-149">Możesz użyć `set JAR` lub `spark-submit` , aby przesłać zadanie do datakostki.</span><span class="sxs-lookup"><span data-stu-id="da7c6-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="da7c6-150">Użyj ustawienia JAR</span><span class="sxs-lookup"><span data-stu-id="da7c6-150">Use Set JAR</span></span>

<span data-ttu-id="da7c6-151">[Ustawienie jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) pozwala przesłać zadanie do istniejącego aktywnego klastra.</span><span class="sxs-lookup"><span data-stu-id="da7c6-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="da7c6-152">Konfiguracja jednorazowa</span><span class="sxs-lookup"><span data-stu-id="da7c6-152">One-time setup</span></span>

1. <span data-ttu-id="da7c6-153">Przejdź do klastra datakosteks i wybierz pozycję **Jobs (zadania** ) z menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="da7c6-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="da7c6-154">Następnie wybierz pozycję **Ustaw jar**.</span><span class="sxs-lookup"><span data-stu-id="da7c6-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="da7c6-155">Przekaż odpowiedni `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` plik.</span><span class="sxs-lookup"><span data-stu-id="da7c6-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="da7c6-156">Ustaw odpowiednio parametry.</span><span class="sxs-lookup"><span data-stu-id="da7c6-156">Set the parameters appropriately.</span></span>

   ```
   Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. <span data-ttu-id="da7c6-157">Skonfiguruj **klaster** tak, aby wskazywał istniejący klaster, który utworzył **skrypt init** dla programu w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="da7c6-157">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="da7c6-158">Publikowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="da7c6-158">Publish and run your app</span></span>

1. <span data-ttu-id="da7c6-159">Użyj [interfejsu wiersza polecenia datakosteks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) , aby przekazać aplikację do klastra datakostks.</span><span class="sxs-lookup"><span data-stu-id="da7c6-159">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="da7c6-160">Ten krok jest wymagany tylko wtedy, gdy zestawy aplikacji (na przykład biblioteki DLL, które zawierają funkcje zdefiniowane przez użytkownika wraz z ich zależnościami), muszą być umieszczone w katalogu roboczym każdego **Microsoft. Spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="da7c6-160">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="da7c6-161">Przekazywanie zestawów aplikacji do klastra datakostki</span><span class="sxs-lookup"><span data-stu-id="da7c6-161">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="da7c6-162">Usuń komentarz i Zmodyfikuj sekcję zależności aplikacji w programie [DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) , aby wskazywała ścieżkę zależności aplikacji i przekazać ją do klastra datakostki.</span><span class="sxs-lookup"><span data-stu-id="da7c6-162">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="da7c6-163">Uruchom ponownie klaster.</span><span class="sxs-lookup"><span data-stu-id="da7c6-163">Restart your cluster.</span></span>

3. <span data-ttu-id="da7c6-164">Przejdź do klastra datacegły w obszarze roboczym datakostki.</span><span class="sxs-lookup"><span data-stu-id="da7c6-164">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="da7c6-165">W obszarze **zadania**wybierz zadanie, a następnie wybierz pozycję **Uruchom teraz** , aby uruchomić zadanie.</span><span class="sxs-lookup"><span data-stu-id="da7c6-165">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="da7c6-166">Korzystanie z platformy Spark — przesyłanie</span><span class="sxs-lookup"><span data-stu-id="da7c6-166">Use spark-submit</span></span>

<span data-ttu-id="da7c6-167">Polecenie [Spark-Submit](https://spark.apache.org/docs/latest/submitting-applications.html) pozwala przesłać zadanie do nowego klastra.</span><span class="sxs-lookup"><span data-stu-id="da7c6-167">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="da7c6-168">[Utwórz zadanie](https://docs.databricks.com/user-guide/jobs.html) i wybierz pozycję **Skonfiguruj platformę Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="da7c6-168">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="da7c6-169">Skonfiguruj `spark-submit` przy użyciu następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="da7c6-169">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="da7c6-170">Przejdź do klastra datacegły w obszarze roboczym datakostki.</span><span class="sxs-lookup"><span data-stu-id="da7c6-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="da7c6-171">W obszarze **zadania**wybierz zadanie, a następnie wybierz pozycję **Uruchom teraz** , aby uruchomić zadanie.</span><span class="sxs-lookup"><span data-stu-id="da7c6-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="da7c6-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="da7c6-172">Next steps</span></span>

<span data-ttu-id="da7c6-173">W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze datakostki.</span><span class="sxs-lookup"><span data-stu-id="da7c6-173">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="da7c6-174">Aby dowiedzieć się więcej na temat datakostki, przejdź do dokumentacji Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="da7c6-174">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="da7c6-175">Dokumentacja Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="da7c6-175">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
