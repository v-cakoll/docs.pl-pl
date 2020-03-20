---
title: Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla platformy Spark w aplikacji HDInsight.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504162"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="11f2a-103">Samouczek: Wdrażanie aplikacji platformy .NET dla platformy Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="11f2a-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="11f2a-104">W tym samouczku opisano, jak wdrożyć aplikację platformy .NET dla platformy Spark w chmurze za pośrednictwem klastra usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="11f2a-105">Usługa HDInsight ułatwia tworzenie i konfigurowanie klastra platformy Spark na platformie Azure, ponieważ klastry platformy Spark w usłudze HDInsight są zgodne z usługą Azure Storage i usług Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="11f2a-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="11f2a-106">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="11f2a-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="11f2a-107">Uzyskaj dostęp do kont magazynu przy użyciu Eksploratora usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="11f2a-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="11f2a-108">Tworzenie klastra usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="11f2a-109">Opublikuj aplikację .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="11f2a-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="11f2a-110">Utwórz i uruchom akcję skryptu HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="11f2a-111">Uruchom aplikację .NET for Apache Spark w klastrze HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11f2a-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="11f2a-112">Prerequisites</span></span>

<span data-ttu-id="11f2a-113">Przed rozpoczęciem wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="11f2a-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="11f2a-114">Jeśli nie masz subskrypcji platformy Azure, utwórz [bezpłatne konto](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="11f2a-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="11f2a-115">Zaloguj się do [Portalu Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="11f2a-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="11f2a-116">Zainstaluj Eksploratora usługi Azure Storage na komputerze [z systemem Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)lub [MacOS.](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="11f2a-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="11f2a-117">Ukończ [samouczek .NET for Apache Spark — rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.</span><span class="sxs-lookup"><span data-stu-id="11f2a-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="11f2a-118">Uzyskiwanie dostępu do kont magazynu</span><span class="sxs-lookup"><span data-stu-id="11f2a-118">Access your storage accounts</span></span>

1. <span data-ttu-id="11f2a-119">Otwórz Eksploratora usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="11f2a-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="11f2a-120">Wybierz **pozycję Dodaj konto** w menu po lewej stronie i zaloguj się do swojego konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="11f2a-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Logowanie się do konta platformy Azure w Eksploratorze usługi Storage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="11f2a-122">Po zalogowaniu się powinny być widoczne wszystkie posiadane konta magazynu oraz wszystkie zasoby przekazane na konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="11f2a-123">Tworzenie klastra HDInsight</span><span class="sxs-lookup"><span data-stu-id="11f2a-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11f2a-124">Rozliczenia dla klastrów HDInsight są naliczane proporcjonalnie na minutę, nawet jeśli ich nie używasz.</span><span class="sxs-lookup"><span data-stu-id="11f2a-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="11f2a-125">Pamiętaj o usunięciu klastra po zakończeniu korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="11f2a-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="11f2a-126">Aby uzyskać więcej informacji, zobacz sekcję [Oczyszczanie zasobów](#clean-up-resources) w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="11f2a-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="11f2a-127">Odwiedź [witrynę Azure portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="11f2a-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="11f2a-128">Wybierz pozycję **+ Utwórz zasób**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="11f2a-129">Następnie wybierz **HDInsight** z kategorii **Analytics.**</span><span class="sxs-lookup"><span data-stu-id="11f2a-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Tworzenie zasobu USŁUGI HDInsight z witryny Azure portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="11f2a-131">W obszarze **Podstawy** podaj następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="11f2a-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="11f2a-132">Właściwość</span><span class="sxs-lookup"><span data-stu-id="11f2a-132">Property</span></span>  |<span data-ttu-id="11f2a-133">Opis</span><span class="sxs-lookup"><span data-stu-id="11f2a-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="11f2a-134">Subskrypcja</span><span class="sxs-lookup"><span data-stu-id="11f2a-134">Subscription</span></span>  | <span data-ttu-id="11f2a-135">Z listy rozwijanej wybierz jedną z aktywnych subskrypcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="11f2a-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="11f2a-136">Grupa zasobów</span><span class="sxs-lookup"><span data-stu-id="11f2a-136">Resource group</span></span> | <span data-ttu-id="11f2a-137">Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy.</span><span class="sxs-lookup"><span data-stu-id="11f2a-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="11f2a-138">Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="11f2a-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="11f2a-139">Nazwa klastra</span><span class="sxs-lookup"><span data-stu-id="11f2a-139">Cluster name</span></span> | <span data-ttu-id="11f2a-140">Podaj nazwę klastra Spark w usłudze HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="11f2a-141">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="11f2a-141">Location</span></span>   | <span data-ttu-id="11f2a-142">Wybierz lokalizację dla grupy zasobów.</span><span class="sxs-lookup"><span data-stu-id="11f2a-142">Select a location for the resource group.</span></span> <span data-ttu-id="11f2a-143">Szablon używa tej lokalizacji do tworzenia klastra oraz na potrzeby domyślnego magazynu klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="11f2a-144">Typ klastra</span><span class="sxs-lookup"><span data-stu-id="11f2a-144">Cluster type</span></span>| <span data-ttu-id="11f2a-145">Wybierz **opcję Iskra** jako typ klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="11f2a-146">Wersja klastra</span><span class="sxs-lookup"><span data-stu-id="11f2a-146">Cluster version</span></span>|<span data-ttu-id="11f2a-147">To pole zostanie automatycznie zapełnione wersją domyślną po wybraniu typu klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="11f2a-148">Wybierz wersję Spark 2.3 lub 2.4.</span><span class="sxs-lookup"><span data-stu-id="11f2a-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="11f2a-149">Nazwa użytkownika logowania klastra</span><span class="sxs-lookup"><span data-stu-id="11f2a-149">Cluster login username</span></span>| <span data-ttu-id="11f2a-150">Wprowadź nazwę użytkownika logowania klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-150">Enter the cluster login username.</span></span>  <span data-ttu-id="11f2a-151">Nazwa domyślna to *admin*.</span><span class="sxs-lookup"><span data-stu-id="11f2a-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="11f2a-152">Hasło logowania klastra</span><span class="sxs-lookup"><span data-stu-id="11f2a-152">Cluster login password</span></span>| <span data-ttu-id="11f2a-153">Wprowadź hasło logowania.</span><span class="sxs-lookup"><span data-stu-id="11f2a-153">Enter any login password.</span></span> |
    |<span data-ttu-id="11f2a-154">Nazwa użytkownika protokołu SSH (Secure Shell)</span><span class="sxs-lookup"><span data-stu-id="11f2a-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="11f2a-155">Wprowadź nazwę użytkownika protokołu SSH.</span><span class="sxs-lookup"><span data-stu-id="11f2a-155">Enter the SSH username.</span></span> <span data-ttu-id="11f2a-156">Domyślnie to konto współdzieli hasło z kontem *Nazwa użytkownika logowania klastra*.</span><span class="sxs-lookup"><span data-stu-id="11f2a-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="11f2a-157">Wybierz **dalej: >>magazynowania,** aby przejść do strony **Magazyn.**</span><span class="sxs-lookup"><span data-stu-id="11f2a-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="11f2a-158">W obszarze **Magazyn** podaj następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="11f2a-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="11f2a-159">Właściwość</span><span class="sxs-lookup"><span data-stu-id="11f2a-159">Property</span></span>  |<span data-ttu-id="11f2a-160">Opis</span><span class="sxs-lookup"><span data-stu-id="11f2a-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="11f2a-161">Podstawowy typ magazynu</span><span class="sxs-lookup"><span data-stu-id="11f2a-161">Primary storage type</span></span>|<span data-ttu-id="11f2a-162">Użyj wartości domyślnej **usługi Azure Storage**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="11f2a-163">Metoda wybierania</span><span class="sxs-lookup"><span data-stu-id="11f2a-163">Selection method</span></span>|<span data-ttu-id="11f2a-164">Użyj wartości domyślnej **Wybierz z listy**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="11f2a-165">Konto magazynu podstawowego</span><span class="sxs-lookup"><span data-stu-id="11f2a-165">Primary storage account</span></span>|<span data-ttu-id="11f2a-166">Wybierz subskrypcję i jedno z kont aktywnego miejsca w ramach tej subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="11f2a-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="11f2a-167">Kontener</span><span class="sxs-lookup"><span data-stu-id="11f2a-167">Container</span></span>|<span data-ttu-id="11f2a-168">Ten kontener jest kontenerem określonego obiektu blob na koncie magazynu, w którym klaster szuka plików do uruchomienia aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="11f2a-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="11f2a-169">Możesz nadać mu dowolną dostępną nazwę.</span><span class="sxs-lookup"><span data-stu-id="11f2a-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="11f2a-170">W obszarze **Recenzja + utwórz**wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="11f2a-171">Utworzenie klastra trwa około 20 minut.</span><span class="sxs-lookup"><span data-stu-id="11f2a-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="11f2a-172">Klaster musi zostać utworzony, zanim będzie można przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="11f2a-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="11f2a-173">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="11f2a-173">Publish your app</span></span>

<span data-ttu-id="11f2a-174">Następnie publikujesz *mySparkApp* utworzony w [.NET for Apache Spark — Wprowadzenie w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, który daje klastrowi Platformy Spark dostęp do wszystkich plików, których potrzebuje do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11f2a-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="11f2a-175">Uruchom następujące polecenia, aby opublikować *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="11f2a-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="11f2a-176">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="11f2a-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="11f2a-177">**W systemie Linux:**</span><span class="sxs-lookup"><span data-stu-id="11f2a-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="11f2a-178">Wykonaj następujące zadania, aby skompresować opublikowane pliki aplikacji, aby łatwo przesłać je do klastra HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="11f2a-179">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="11f2a-179">**On Windows:**</span></span>

   <span data-ttu-id="11f2a-180">Przejdź do *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="11f2a-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="11f2a-181">Następnie kliknij prawym przyciskiem myszy folder **Publikuj** i wybierz polecenie **Wyślij do > skompresowany (spakowany) folder**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="11f2a-182">Nazwij nowy folder **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="11f2a-183">**W systemie Linux uruchom następujące polecenie:**</span><span class="sxs-lookup"><span data-stu-id="11f2a-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="11f2a-184">Przekazywanie plików na platformę Azure</span><span class="sxs-lookup"><span data-stu-id="11f2a-184">Upload files to Azure</span></span>

<span data-ttu-id="11f2a-185">Następnie użyj Eksploratora usługi Azure Storage, aby przekazać następujące pięć plików do kontenera obiektów blob wybranego dla magazynu klastra:</span><span class="sxs-lookup"><span data-stu-id="11f2a-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="11f2a-186">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="11f2a-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="11f2a-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="11f2a-187">install-worker.sh</span></span>
* <span data-ttu-id="11f2a-188">publikuj.zip</span><span class="sxs-lookup"><span data-stu-id="11f2a-188">publish.zip</span></span>
* <span data-ttu-id="11f2a-189">microsoft-spark-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="11f2a-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="11f2a-190">plik input.txt.</span><span class="sxs-lookup"><span data-stu-id="11f2a-190">input.txt.</span></span>

1. <span data-ttu-id="11f2a-191">Otwórz Eksploratora usługi Azure Storage i przejdź do konta magazynu z lewego menu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="11f2a-192">Przechodzenie do szczegółów kontenera obiektów blob dla klastra w **kontenerach obiektów blob** na koncie magazynu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="11f2a-193">*Microsoft.Spark.Worker* pomaga apache Spark wykonać aplikację, takich jak wszystkie funkcje zdefiniowane przez użytkownika (UDFs) może być napisane.</span><span class="sxs-lookup"><span data-stu-id="11f2a-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="11f2a-194">Pobierz [plik Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="11f2a-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="11f2a-195">Następnie wybierz pozycję **Przekaż** w Eksploratorze usługi Azure Storage, aby przekazać pracownika.</span><span class="sxs-lookup"><span data-stu-id="11f2a-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Przekazywanie plików do Eksploratora usługi Azure Storage](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="11f2a-197">*install-worker.sh* to skrypt, który umożliwia kopiowanie plików zależnych platformy .NET dla platformy Apache Spark do węzłów klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="11f2a-198">Utwórz nowy plik o nazwie **install-worker.sh** komputerze lokalnym i wklej [zawartość install-worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) znajdującą się w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="11f2a-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="11f2a-199">Następnie przekaż *install-worker.sh* do kontenera obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="11f2a-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="11f2a-200">Klaster potrzebuje pliku publish.zip zawierającego opublikowane pliki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11f2a-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="11f2a-201">Przejdź do opublikowanego **folderu, mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**i znajdź **plik publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="11f2a-202">Następnie przekaż *publish.zip* do kontenera obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="11f2a-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="11f2a-203">Klaster potrzebuje kodu aplikacji, który został spakowany do pliku jar.</span><span class="sxs-lookup"><span data-stu-id="11f2a-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="11f2a-204">Przejdź do opublikowanego **folderu, mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**i znajdź **microsoft-spark-2.3.x-0.3.0.jar**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="11f2a-205">Następnie przekaż plik jar do kontenera obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="11f2a-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="11f2a-206">Może istnieć wiele plików .jar (dla wersji 2.3.x i 2.4.x programu Spark).</span><span class="sxs-lookup"><span data-stu-id="11f2a-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="11f2a-207">Należy wybrać plik jar, który pasuje do wersji platformy Spark wybranej podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="11f2a-208">Na przykład wybierz *microsoft-spark-2.3.x-0.3.0.jar,* jeśli podczas tworzenia klastra została wybrana platforma Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="11f2a-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="11f2a-209">Klaster wymaga danych wejściowych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11f2a-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="11f2a-210">Przejdź do katalogu **mySparkApp** i znajdź **plik input.txt**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="11f2a-211">Przekaż plik wejściowy do katalogu **użytkownika/sshusera** w kontenerze obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="11f2a-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="11f2a-212">Będziesz łączyć się z klastrem za pośrednictwem ssh, a ten folder jest, gdzie klaster szuka jego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="11f2a-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="11f2a-213">Plik *input.txt* jest jedynym plikiem przekazanym do określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="11f2a-214">Uruchamianie akcji skryptu HDInsight</span><span class="sxs-lookup"><span data-stu-id="11f2a-214">Run the HDInsight script action</span></span>

<span data-ttu-id="11f2a-215">Po uruchomieniu klastra i przekazaniu plików na platformę Azure uruchom skrypt **install-worker.sh** w klastrze.</span><span class="sxs-lookup"><span data-stu-id="11f2a-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="11f2a-216">Przejdź do klastra platformy SPARK usługi HDInsight w witrynie Azure portal, a następnie wybierz pozycję **Akcje skryptu**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="11f2a-217">Wybierz **+ Prześlij nowe** i podaj następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="11f2a-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="11f2a-218">Właściwość</span><span class="sxs-lookup"><span data-stu-id="11f2a-218">Property</span></span>  |<span data-ttu-id="11f2a-219">Opis</span><span class="sxs-lookup"><span data-stu-id="11f2a-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="11f2a-220">Typ skryptu</span><span class="sxs-lookup"><span data-stu-id="11f2a-220">Script type</span></span> |<span data-ttu-id="11f2a-221">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="11f2a-221">Custom</span></span>|
   | <span data-ttu-id="11f2a-222">Nazwa</span><span class="sxs-lookup"><span data-stu-id="11f2a-222">Name</span></span> | <span data-ttu-id="11f2a-223">Instalowanie pracownika</span><span class="sxs-lookup"><span data-stu-id="11f2a-223">Install Worker</span></span>|
   | <span data-ttu-id="11f2a-224">Identyfikator URI skryptu bash</span><span class="sxs-lookup"><span data-stu-id="11f2a-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="11f2a-225">Aby potwierdzić ten identyfikator URI, kliknij prawym przyciskiem myszy install-worker.sh w Eksploratorze usługi Azure Storage i wybierz polecenie Właściwości.</span><span class="sxs-lookup"><span data-stu-id="11f2a-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="11f2a-226">Typy węzłów</span><span class="sxs-lookup"><span data-stu-id="11f2a-226">Node type(s)</span></span>| <span data-ttu-id="11f2a-227">Pracownik</span><span class="sxs-lookup"><span data-stu-id="11f2a-227">Worker</span></span>|
   | <span data-ttu-id="11f2a-228">Parametry</span><span class="sxs-lookup"><span data-stu-id="11f2a-228">Parameters</span></span> | <span data-ttu-id="11f2a-229">Azure</span><span class="sxs-lookup"><span data-stu-id="11f2a-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="11f2a-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="11f2a-230">/usr/local/bin</span></span>

3. <span data-ttu-id="11f2a-231">Wybierz **pozycję Utwórz,** aby przesłać skrypt.</span><span class="sxs-lookup"><span data-stu-id="11f2a-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="11f2a-232">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="11f2a-232">Run your app</span></span>

1. <span data-ttu-id="11f2a-233">Przejdź do klastra platformy SPARK usługi HDInsight w witrynie Azure portal, a następnie wybierz pozycję **SSH + Cluster login**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="11f2a-234">Skopiuj dane logowania do ssh i wklej login do terminalu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="11f2a-235">Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="11f2a-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="11f2a-236">Powinieneś zobaczyć wiadomości witające Cię do Ubuntu i Spark.</span><span class="sxs-lookup"><span data-stu-id="11f2a-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="11f2a-237">Użyj polecenia **spark-submit,** aby uruchomić aplikację w klastrze HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="11f2a-238">Pamiętaj, aby zastąpić **mycontainer** i **mystorageaccount** w przykładowym skrypcie rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="11f2a-239">Po uruchomieniu aplikacji zostanie wyświetlona ta sama tabela zliczania wyrazów z uruchomionego przebiegu lokalnego napisanego na konsoli.</span><span class="sxs-lookup"><span data-stu-id="11f2a-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="11f2a-240">Gratulacje, uruchomiliście pierwszą aplikację .NET dla Apache Spark w chmurze!</span><span class="sxs-lookup"><span data-stu-id="11f2a-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="11f2a-241">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="11f2a-241">Clean up resources</span></span>

<span data-ttu-id="11f2a-242">Usługa HDInsight zapisuje dane w usłudze Azure Storage, dzięki czemu można bezpiecznie usunąć klaster, gdy nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="11f2a-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="11f2a-243">Opłaty za klaster usługi HDInsight są naliczane nawet wtedy, gdy nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="11f2a-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="11f2a-244">Ponieważ opłaty za klaster są wielokrotnie większe niż opłaty za magazyn, ze względów ekonomicznych warto usuwać klastry, gdy nie są używane.</span><span class="sxs-lookup"><span data-stu-id="11f2a-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="11f2a-245">Dodatkowo możesz wybrać nazwę grupy zasobów, aby otworzyć stronę grupy zasobów, a następnie wybrać pozycję **Usuń grupę zasobów**.</span><span class="sxs-lookup"><span data-stu-id="11f2a-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="11f2a-246">Usunięcie grupy zasobów powoduje usunięcie zarówno klastra Spark w usłudze HDInsight, jak i domyślnego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="11f2a-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11f2a-247">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="11f2a-247">Next steps</span></span>

<span data-ttu-id="11f2a-248">W tym samouczku wdrożono aplikację platformy .NET for Apache Spark w usłudze Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="11f2a-249">Aby dowiedzieć się więcej o hdinsight, przejdź do dokumentacji usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="11f2a-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="11f2a-250">Dokumentacja usługi Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="11f2a-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
