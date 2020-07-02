---
title: Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla Apache Spark w usłudze HDInsight.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e6b2fdd1818250c47ce6cb64439ecab58ae99ad8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617642"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="7f86d-103">Samouczek: wdrażanie aplikacji .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="7f86d-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="7f86d-104">W tym samouczku przedstawiono sposób wdrażania aplikacji platformy .NET dla Apache Spark w chmurze za pomocą klastra usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="7f86d-105">Usługa HDInsight ułatwia tworzenie i Konfigurowanie klastra Spark na platformie Azure, ponieważ klastry Spark w usłudze HDInsight są zgodne z usługą Azure Storage i Azure Data Lake Storage.</span><span class="sxs-lookup"><span data-stu-id="7f86d-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="7f86d-106">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7f86d-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7f86d-107">Uzyskaj dostęp do kont magazynu przy użyciu Eksplorator usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="7f86d-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="7f86d-108">Utwórz klaster usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="7f86d-109">Opublikuj aplikację .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="7f86d-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="7f86d-110">Utwórz i uruchom akcję skryptu usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="7f86d-111">Uruchom aplikację .NET dla Apache Spark w klastrze usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="7f86d-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7f86d-112">Prerequisites</span></span>

<span data-ttu-id="7f86d-113">Przed rozpoczęciem wykonaj następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="7f86d-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="7f86d-114">Jeśli nie masz subskrypcji platformy Azure, Utwórz [bezpłatne konto](https://azure.microsoft.com/free/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="7f86d-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="7f86d-115">Zaloguj się do [portalu Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="7f86d-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="7f86d-116">Zainstaluj Eksplorator usługi Azure Storage na komputerze z [systemem Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)lub [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) .</span><span class="sxs-lookup"><span data-stu-id="7f86d-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="7f86d-117">Ukończ [platformę .NET dla Apache Spark — Rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.</span><span class="sxs-lookup"><span data-stu-id="7f86d-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="7f86d-118">Dostęp do kont magazynu</span><span class="sxs-lookup"><span data-stu-id="7f86d-118">Access your storage accounts</span></span>

1. <span data-ttu-id="7f86d-119">Otwórz Eksplorator usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="7f86d-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="7f86d-120">W menu po lewej stronie wybierz pozycję **Dodaj konto** , a następnie zaloguj się do konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="7f86d-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Zaloguj się do konta platformy Azure z poziomu Eksplorator usługi Storage](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="7f86d-122">Po zalogowaniu się powinny zostać wyświetlone wszystkie konta magazynu i wszystkie zasoby, które zostały przekazane do kont magazynu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="7f86d-123">Tworzenie klastra HDInsight</span><span class="sxs-lookup"><span data-stu-id="7f86d-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f86d-124">Opłaty za klastry usługi HDInsight są naliczane proporcjonalnie do liczby minut, nawet jeśli nie są używane.</span><span class="sxs-lookup"><span data-stu-id="7f86d-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="7f86d-125">Pamiętaj o usunięciu klastra po zakończeniu korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="7f86d-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="7f86d-126">Aby uzyskać więcej informacji, zobacz sekcję [czyszczenie zasobów](#clean-up-resources) w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="7f86d-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="7f86d-127">Odwiedź [Azure Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="7f86d-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="7f86d-128">Wybierz pozycję **+ Utwórz zasób**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="7f86d-129">Następnie wybierz pozycję **HDInsight** z kategorii **Analytics** .</span><span class="sxs-lookup"><span data-stu-id="7f86d-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Utwórz zasób usługi HDInsight na podstawie Azure Portal](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="7f86d-131">W obszarze **Podstawy** podaj następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="7f86d-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="7f86d-132">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7f86d-132">Property</span></span>  |<span data-ttu-id="7f86d-133">Opis</span><span class="sxs-lookup"><span data-stu-id="7f86d-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="7f86d-134">Subskrypcja</span><span class="sxs-lookup"><span data-stu-id="7f86d-134">Subscription</span></span>  | <span data-ttu-id="7f86d-135">Z listy rozwijanej wybierz jedną z aktywnych subskrypcji platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="7f86d-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="7f86d-136">Grupa zasobów</span><span class="sxs-lookup"><span data-stu-id="7f86d-136">Resource group</span></span> | <span data-ttu-id="7f86d-137">Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy.</span><span class="sxs-lookup"><span data-stu-id="7f86d-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="7f86d-138">Grupa zasobów to kontener zawierający powiązane zasoby dla rozwiązania platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="7f86d-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="7f86d-139">Nazwa klastra</span><span class="sxs-lookup"><span data-stu-id="7f86d-139">Cluster name</span></span> | <span data-ttu-id="7f86d-140">Podaj nazwę klastra Spark w usłudze HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="7f86d-141">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="7f86d-141">Location</span></span>   | <span data-ttu-id="7f86d-142">Wybierz lokalizację dla grupy zasobów.</span><span class="sxs-lookup"><span data-stu-id="7f86d-142">Select a location for the resource group.</span></span> <span data-ttu-id="7f86d-143">Szablon używa tej lokalizacji do tworzenia klastra oraz na potrzeby domyślnego magazynu klastra.</span><span class="sxs-lookup"><span data-stu-id="7f86d-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="7f86d-144">Typ klastra</span><span class="sxs-lookup"><span data-stu-id="7f86d-144">Cluster type</span></span>| <span data-ttu-id="7f86d-145">Wybierz pozycję **Spark** jako typ klastra.</span><span class="sxs-lookup"><span data-stu-id="7f86d-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="7f86d-146">Wersja klastra</span><span class="sxs-lookup"><span data-stu-id="7f86d-146">Cluster version</span></span>|<span data-ttu-id="7f86d-147">Po wybraniu typu klastra w tym polu zostanie automatycznie wypełniona domyślna wersja.</span><span class="sxs-lookup"><span data-stu-id="7f86d-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="7f86d-148">Wybierz 2,3 lub 2,4 wersję platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="7f86d-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="7f86d-149">Nazwa użytkownika logowania klastra</span><span class="sxs-lookup"><span data-stu-id="7f86d-149">Cluster login username</span></span>| <span data-ttu-id="7f86d-150">Wprowadź nazwę użytkownika logowania klastra.</span><span class="sxs-lookup"><span data-stu-id="7f86d-150">Enter the cluster login username.</span></span>  <span data-ttu-id="7f86d-151">Nazwa domyślna to *admin*.</span><span class="sxs-lookup"><span data-stu-id="7f86d-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="7f86d-152">Hasło logowania klastra</span><span class="sxs-lookup"><span data-stu-id="7f86d-152">Cluster login password</span></span>| <span data-ttu-id="7f86d-153">Wprowadź hasło logowania.</span><span class="sxs-lookup"><span data-stu-id="7f86d-153">Enter any login password.</span></span> |
    |<span data-ttu-id="7f86d-154">Nazwa użytkownika protokołu SSH (Secure Shell)</span><span class="sxs-lookup"><span data-stu-id="7f86d-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="7f86d-155">Wprowadź nazwę użytkownika protokołu SSH.</span><span class="sxs-lookup"><span data-stu-id="7f86d-155">Enter the SSH username.</span></span> <span data-ttu-id="7f86d-156">Domyślnie to konto współdzieli hasło z kontem *Nazwa użytkownika logowania klastra*.</span><span class="sxs-lookup"><span data-stu-id="7f86d-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="7f86d-157">Wybierz pozycję **Dalej: magazyn >>** , aby kontynuować na stronie **Magazyn** .</span><span class="sxs-lookup"><span data-stu-id="7f86d-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="7f86d-158">W obszarze **Magazyn** podaj następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="7f86d-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="7f86d-159">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7f86d-159">Property</span></span>  |<span data-ttu-id="7f86d-160">Opis</span><span class="sxs-lookup"><span data-stu-id="7f86d-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="7f86d-161">Podstawowy typ magazynu</span><span class="sxs-lookup"><span data-stu-id="7f86d-161">Primary storage type</span></span>|<span data-ttu-id="7f86d-162">Użyj wartości domyślnej **usługi Azure Storage**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="7f86d-163">Metoda wybierania</span><span class="sxs-lookup"><span data-stu-id="7f86d-163">Selection method</span></span>|<span data-ttu-id="7f86d-164">Użyj wartości domyślnej **Wybierz z listy**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="7f86d-165">Konto magazynu podstawowego</span><span class="sxs-lookup"><span data-stu-id="7f86d-165">Primary storage account</span></span>|<span data-ttu-id="7f86d-166">Wybierz swoją subskrypcję i jedno z aktywnych kont magazynu w ramach tej subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="7f86d-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="7f86d-167">Kontener</span><span class="sxs-lookup"><span data-stu-id="7f86d-167">Container</span></span>|<span data-ttu-id="7f86d-168">Ten kontener to konkretny kontener obiektów BLOB na koncie magazynu, w którym klaster szuka plików do uruchomienia aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="7f86d-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="7f86d-169">Możesz nadać mu dowolną nazwę.</span><span class="sxs-lookup"><span data-stu-id="7f86d-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="7f86d-170">W obszarze **Recenzja + tworzenie**wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="7f86d-171">Utworzenie klastra trwa około 20 minut.</span><span class="sxs-lookup"><span data-stu-id="7f86d-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="7f86d-172">Przed przejściem do następnego kroku należy utworzyć klaster.</span><span class="sxs-lookup"><span data-stu-id="7f86d-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="7f86d-173">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f86d-173">Publish your app</span></span>

<span data-ttu-id="7f86d-174">Następnie opublikujesz *mySparkApp* utworzone w programie [.NET dla Apache Spark — Rozpocznij w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, co umożliwia klastrowi Spark dostęp do wszystkich plików potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7f86d-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="7f86d-175">Uruchom następujące polecenia, aby opublikować *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="7f86d-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="7f86d-176">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="7f86d-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="7f86d-177">**W systemie Linux:**</span><span class="sxs-lookup"><span data-stu-id="7f86d-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="7f86d-178">Wykonaj następujące zadania w celu przesłania plików opublikowanych aplikacji, aby można je było łatwo przekazać do klastra usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="7f86d-179">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="7f86d-179">**On Windows:**</span></span>

   <span data-ttu-id="7f86d-180">Przejdź do *mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*.</span><span class="sxs-lookup"><span data-stu-id="7f86d-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="7f86d-181">Następnie kliknij prawym przyciskiem myszy folder **Publikowanie** i wybierz polecenie **Wyślij do > folder skompresowany (zip)**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="7f86d-182">Nadaj nazwę nowemu folderowi **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="7f86d-183">**W systemie Linux Uruchom następujące polecenie:**</span><span class="sxs-lookup"><span data-stu-id="7f86d-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="7f86d-184">Przekazywanie plików na platformę Azure</span><span class="sxs-lookup"><span data-stu-id="7f86d-184">Upload files to Azure</span></span>

<span data-ttu-id="7f86d-185">Następnie użyj Eksplorator usługi Azure Storage do przekazania następujących pięciu plików do kontenera obiektów BLOB wybranego dla magazynu klastra:</span><span class="sxs-lookup"><span data-stu-id="7f86d-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="7f86d-186">Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="7f86d-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="7f86d-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="7f86d-187">install-worker.sh</span></span>
* <span data-ttu-id="7f86d-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="7f86d-188">publish.zip</span></span>
* <span data-ttu-id="7f86d-189">Microsoft-Spark-2.3. x-0.3.0. jar</span><span class="sxs-lookup"><span data-stu-id="7f86d-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="7f86d-190">input.txt.</span><span class="sxs-lookup"><span data-stu-id="7f86d-190">input.txt.</span></span>

1. <span data-ttu-id="7f86d-191">Otwórz Eksplorator usługi Azure Storage i przejdź do swojego konta magazynu z menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="7f86d-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="7f86d-192">Przejdź do szczegółów kontenera obiektów BLOB klastra w kontenerach **obiektów BLOB** na koncie magazynu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="7f86d-193">Aplikacja *Microsoft. Spark. Worker* ułatwia Apache Spark wykonywanie aplikacji, na przykład dowolnych funkcji zdefiniowanych przez użytkownika (UDF).</span><span class="sxs-lookup"><span data-stu-id="7f86d-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="7f86d-194">Pobierz [pakiet Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="7f86d-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="7f86d-195">Następnie wybierz pozycję **Przekaż** w Eksplorator usługi Azure Storage, aby przekazać proces roboczy.</span><span class="sxs-lookup"><span data-stu-id="7f86d-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Przekaż pliki do Eksplorator usługi Azure Storage](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="7f86d-197">*Install-Worker.sh* to skrypt, który umożliwia skopiowanie programu .net dla Apache Spark plików zależnych do węzłów klastra.</span><span class="sxs-lookup"><span data-stu-id="7f86d-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="7f86d-198">Utwórz nowy plik o nazwie **Install-Worker.sh** komputera lokalnego i wklej [zawartość Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) znajdującą się w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="7f86d-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="7f86d-199">Następnie Przekaż *Install-Worker.sh* do kontenera obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="7f86d-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="7f86d-200">Klaster wymaga pliku publish.zip, który zawiera pliki opublikowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7f86d-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="7f86d-201">Przejdź do opublikowanego folderu, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**i Znajdź **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="7f86d-202">Następnie Przekaż *publish.zip* do kontenera obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="7f86d-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="7f86d-203">Klaster wymaga kodu aplikacji spakowanego w pliku JAR.</span><span class="sxs-lookup"><span data-stu-id="7f86d-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="7f86d-204">Przejdź do opublikowanego folderu, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**i Znajdź **Microsoft-Spark-2.3. x-0.3.0. jar**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="7f86d-205">Następnie Przekaż plik jar do kontenera obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="7f86d-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="7f86d-206">Może istnieć wiele plików jar (dla wersji 2.3. x i 2.4. x z platformy Spark).</span><span class="sxs-lookup"><span data-stu-id="7f86d-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="7f86d-207">Musisz wybrać plik JAR, który jest zgodny z wersją platformy Spark wybraną podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="7f86d-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="7f86d-208">Na przykład wybierz *Microsoft-Spark-2.3. x-0.3.0. jar* , jeśli podczas tworzenia klastra wybrano platformę Spark.</span><span class="sxs-lookup"><span data-stu-id="7f86d-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="7f86d-209">Klaster wymaga danych wejściowych do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7f86d-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="7f86d-210">Przejdź do katalogu **mySparkApp** i Znajdź **input.txt**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="7f86d-211">Przekaż plik wejściowy do katalogu **User/sshuser** w kontenerze obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="7f86d-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="7f86d-212">Nastąpi połączenie z klastrem za pośrednictwem protokołu SSH, a ten folder wskazuje, że Twój klaster szuka jego danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="7f86d-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="7f86d-213">Plik *input.txt* to jedyny plik przekazany do określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="7f86d-214">Uruchamianie akcji skryptu HDInsight</span><span class="sxs-lookup"><span data-stu-id="7f86d-214">Run the HDInsight script action</span></span>

<span data-ttu-id="7f86d-215">Po uruchomieniu klastra i przekazaniu plików na platformę Azure należy uruchomić skrypt **Install-Worker.sh** w klastrze.</span><span class="sxs-lookup"><span data-stu-id="7f86d-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="7f86d-216">Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **Akcje skryptu**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="7f86d-217">Wybierz pozycję **+ Prześlij nową** i podaj następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="7f86d-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="7f86d-218">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7f86d-218">Property</span></span>  |<span data-ttu-id="7f86d-219">Opis</span><span class="sxs-lookup"><span data-stu-id="7f86d-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="7f86d-220">Typ skryptu</span><span class="sxs-lookup"><span data-stu-id="7f86d-220">Script type</span></span> |<span data-ttu-id="7f86d-221">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="7f86d-221">Custom</span></span>|
   | <span data-ttu-id="7f86d-222">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7f86d-222">Name</span></span> | <span data-ttu-id="7f86d-223">Zainstaluj proces roboczy</span><span class="sxs-lookup"><span data-stu-id="7f86d-223">Install Worker</span></span>|
   | <span data-ttu-id="7f86d-224">Identyfikator URI skryptu bash</span><span class="sxs-lookup"><span data-stu-id="7f86d-224">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="7f86d-225">Aby potwierdzić ten identyfikator URI, kliknij prawym przyciskiem myszy pozycję install-worker.sh w Eksplorator usługi Azure Storage a następnie wybierz pozycję Właściwości.</span><span class="sxs-lookup"><span data-stu-id="7f86d-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="7f86d-226">Typy węzłów</span><span class="sxs-lookup"><span data-stu-id="7f86d-226">Node type(s)</span></span>| <span data-ttu-id="7f86d-227">Odpowiedzialn</span><span class="sxs-lookup"><span data-stu-id="7f86d-227">Worker</span></span>|
   | <span data-ttu-id="7f86d-228">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f86d-228">Parameters</span></span> | <span data-ttu-id="7f86d-229">Azure</span><span class="sxs-lookup"><span data-stu-id="7f86d-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="7f86d-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="7f86d-230">/usr/local/bin</span></span>

3. <span data-ttu-id="7f86d-231">Wybierz pozycję **Utwórz** , aby przesłać swój skrypt.</span><span class="sxs-lookup"><span data-stu-id="7f86d-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="7f86d-232">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f86d-232">Run your app</span></span>

1. <span data-ttu-id="7f86d-233">Przejdź do klastra usługi HDInsight Spark w Azure Portal, a następnie wybierz pozycję **SSH + logowanie do klastra**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="7f86d-234">Skopiuj informacje logowania SSH i wklej nazwę logowania do terminalu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="7f86d-235">Zaloguj się do klastra przy użyciu hasła ustawionego podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="7f86d-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="7f86d-236">Powinny pojawić się komunikaty z powitaniem do Ubuntu i Spark.</span><span class="sxs-lookup"><span data-stu-id="7f86d-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="7f86d-237">Użyj polecenia **Spark-Submit** , aby uruchomić aplikację w klastrze usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="7f86d-238">Pamiętaj **, aby zastąpić obiekt** **mojekontomagazynu** i go w przykładowym skrypcie z rzeczywistymi nazwami kontenera obiektów blob i konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="7f86d-239">Gdy aplikacja zostanie uruchomiona, zobaczysz tę samą tabelę Count wyrazów z uruchomienia lokalnego uruchamiania zarejestrowanego w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="7f86d-240">Gratulacje, uruchomiono pierwszą aplikację platformy .NET dla Apache Spark w chmurze!</span><span class="sxs-lookup"><span data-stu-id="7f86d-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="7f86d-241">Czyszczenie zasobów</span><span class="sxs-lookup"><span data-stu-id="7f86d-241">Clean up resources</span></span>

<span data-ttu-id="7f86d-242">Usługa HDInsight zapisuje dane w usłudze Azure Storage, dzięki czemu można bezpiecznie usunąć klaster, gdy nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="7f86d-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="7f86d-243">Opłaty za klaster usługi HDInsight są naliczane nawet wtedy, gdy nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="7f86d-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="7f86d-244">Ponieważ opłaty za klaster są wielokrotnie większe niż opłaty za magazyn, ze względów ekonomicznych warto usuwać klastry, gdy nie są używane.</span><span class="sxs-lookup"><span data-stu-id="7f86d-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="7f86d-245">Dodatkowo możesz wybrać nazwę grupy zasobów, aby otworzyć stronę grupy zasobów, a następnie wybrać pozycję **Usuń grupę zasobów**.</span><span class="sxs-lookup"><span data-stu-id="7f86d-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="7f86d-246">Usunięcie grupy zasobów powoduje usunięcie zarówno klastra Spark w usłudze HDInsight, jak i domyślnego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="7f86d-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7f86d-247">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7f86d-247">Next steps</span></span>

<span data-ttu-id="7f86d-248">W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="7f86d-249">Aby dowiedzieć się więcej o usłudze HDInsight, przejdź do dokumentacji usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="7f86d-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7f86d-250">Dokumentacja usługi Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="7f86d-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
