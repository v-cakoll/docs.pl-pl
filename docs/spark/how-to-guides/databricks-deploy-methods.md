---
title: Prześlij zadanie platformy .NET dla platformy Spark apache do databricks
description: Dowiedz się, jak przesłać zadanie platformy .NET dla platformy Apache Spark do programu Databricks przy użyciu spark-submit i Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187607"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="266cd-103">Prześlij zadanie platformy .NET dla platformy Spark apache do databricks</span><span class="sxs-lookup"><span data-stu-id="266cd-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="266cd-104">Istnieją dwa sposoby wdrażania zadania platformy .NET dla platformy Spark `spark-submit` dla aplikacji Databricks: i Ustaw jar.</span><span class="sxs-lookup"><span data-stu-id="266cd-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="266cd-105">Wdrażanie przy użyciu spark-submit</span><span class="sxs-lookup"><span data-stu-id="266cd-105">Deploy using spark-submit</span></span>

<span data-ttu-id="266cd-106">Za pomocą polecenia [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) można przesłać zadania platformy .NET dla platformy Apache Spark do programu Databricks.</span><span class="sxs-lookup"><span data-stu-id="266cd-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="266cd-107">`spark-submit`umożliwia przesyłanie tylko do klastra, który zostanie utworzony na żądanie.</span><span class="sxs-lookup"><span data-stu-id="266cd-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="266cd-108">Przejdź do obszaru roboczego Databricks i utwórz zadanie.</span><span class="sxs-lookup"><span data-stu-id="266cd-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="266cd-109">Wybierz tytuł zadania, a następnie wybierz pozycję **Konfiguruj spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="266cd-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="266cd-110">Wklej następujące parametry w konfiguracji zadania, a następnie wybierz pozycję **Potwierdź**.</span><span class="sxs-lookup"><span data-stu-id="266cd-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="266cd-111">Zaktualizuj zawartość powyższego parametru na podstawie określonych plików i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="266cd-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="266cd-112">Na przykład odwołaj się do wersji pliku jar Microsoft.Spark, który został przekazany do usługi DBFS, i użyj odpowiedniej nazwy aplikacji i opublikowanego pliku zip aplikacji.</span><span class="sxs-lookup"><span data-stu-id="266cd-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="266cd-113">Przejdź do zadania i wybierz pozycję **Edytuj,** aby skonfigurować klaster zadania.</span><span class="sxs-lookup"><span data-stu-id="266cd-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="266cd-114">Ustaw wersję środowiska uruchomieniowego Databricks na podstawie wersji platformy Apache Spark, której chcesz użyć we wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="266cd-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="266cd-115">Następnie wybierz opcję **Opcje zaawansowane > skryptów init**i `dbfs:/spark-dotnet/db-init.sh`ustaw ścieżkę skryptu init jako .</span><span class="sxs-lookup"><span data-stu-id="266cd-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="266cd-116">Wybierz **pozycję Potwierdź,** aby potwierdzić ustawienia klastra.</span><span class="sxs-lookup"><span data-stu-id="266cd-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="266cd-117">Przejdź do zadania i wybierz pozycję **Uruchom teraz,** aby uruchomić zadanie w nowo skonfigurowanym klastrze platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="266cd-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="266cd-118">Utworzenie klastra zadania zajmuje kilka minut.</span><span class="sxs-lookup"><span data-stu-id="266cd-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="266cd-119">Po jego utworzeniu twoje zadanie zostanie przesłane.</span><span class="sxs-lookup"><span data-stu-id="266cd-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="266cd-120">Dane wyjściowe można wyświetlić, wybierając **pozycję Klastry** z lewego menu obszaru roboczego Databricks, a następnie wybierz pozycję **Dzienniki sterowników**.</span><span class="sxs-lookup"><span data-stu-id="266cd-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="266cd-121">Wdrażanie przy użyciu zestawu Jar</span><span class="sxs-lookup"><span data-stu-id="266cd-121">Deploy using Set Jar</span></span>

<span data-ttu-id="266cd-122">Alternatywnie można użyć [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) w obszarze roboczym Databricks do przesyłania zadań platformy .NET dla platformy Spark apache do databricks.</span><span class="sxs-lookup"><span data-stu-id="266cd-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="266cd-123">*Ustaw jar* umożliwia przesyłanie zadania do istniejącego aktywnego klastra.</span><span class="sxs-lookup"><span data-stu-id="266cd-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="266cd-124">Konfiguracja jednorazowa</span><span class="sxs-lookup"><span data-stu-id="266cd-124">One-time setup</span></span>

1. <span data-ttu-id="266cd-125">Przejdź do klastra Databricks i wybierz **pozycję Zadania** z menu po lewej stronie, a następnie **ustaw JAR**.</span><span class="sxs-lookup"><span data-stu-id="266cd-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="266cd-126">Prześlij odpowiedni `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`plik .</span><span class="sxs-lookup"><span data-stu-id="266cd-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="266cd-127">Zmodyfikuj następujące parametry, aby uwzględnić poprawną `<your-app-name>`nazwę pliku wykonywalnego opublikowanego zamiast:</span><span class="sxs-lookup"><span data-stu-id="266cd-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="266cd-128">Skonfiguruj klaster tak, aby wskazywał istniejący klaster, dla którego został już ustawiony skrypt init.</span><span class="sxs-lookup"><span data-stu-id="266cd-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="266cd-129">Publikowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="266cd-129">Publish and run your app</span></span>

1. <span data-ttu-id="266cd-130">Upewnij się, że aplikacja została opublikowana i `SparkSession.Stop()`że kod aplikacji nie jest używany .</span><span class="sxs-lookup"><span data-stu-id="266cd-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="266cd-131">Użyj [interfejsu wiersza polecenia Databricks,](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) aby przekazać aplikację do klastra Databricks.</span><span class="sxs-lookup"><span data-stu-id="266cd-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="266cd-132">Na przykład użyj następującego polecenia, aby przekazać opublikowaną aplikację do klastra:</span><span class="sxs-lookup"><span data-stu-id="266cd-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="266cd-133">Jeśli w aplikacji są dostępne funkcje zdefiniowane przez użytkownika, zestawy aplikacji, takie jak biblioteki DLL zawierające funkcje zdefiniowane przez użytkownika wraz z ich zależnościami, muszą zostać umieszczone w katalogu roboczym każdego programu *Microsoft.Spark.Worker.*</span><span class="sxs-lookup"><span data-stu-id="266cd-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="266cd-134">Przekaż zestawy aplikacji do klastra Databricks:</span><span class="sxs-lookup"><span data-stu-id="266cd-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="266cd-135">Odkomentuj i zmodyfikuj sekcję zależności aplikacji w [db-init.sh,](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) aby wskazać ścieżkę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="266cd-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="266cd-136">Następnie przekaż zaktualizowane *db-init.sh* do klastra:</span><span class="sxs-lookup"><span data-stu-id="266cd-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="266cd-137">Przejdź do **usługi Databricks cluster > Jobs > [Nazwa zadania] > Uruchom teraz,** aby uruchomić zadanie.</span><span class="sxs-lookup"><span data-stu-id="266cd-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="266cd-138">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="266cd-138">Next steps</span></span>

* [<span data-ttu-id="266cd-139">Wprowadzenie do platformy .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="266cd-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="266cd-140">Wdrażanie aplikacji platformy .NET dla platformy Spark apache w aplikacjach Databricks</span><span class="sxs-lookup"><span data-stu-id="266cd-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="266cd-141">Dokumentacja usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="266cd-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
