---
title: Wdrażanie aplikacji platformy .NET dla platformy Spark apache w aplikacjach Databricks
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla platformy Spark apache w udziale w udziale w udziale w udziale w udziale w udziale w udziale w uchybieniach.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503964"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="16bb1-103">Samouczek: Wdrażanie aplikacji .NET dla platformy Spark apache w databricks</span><span class="sxs-lookup"><span data-stu-id="16bb1-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="16bb1-104">W tym samouczku dowiesz się, jak wdrożyć aplikację w chmurze za pośrednictwem platformy Azure Databricks, platformy analitycznej opartej na platformie Apache Spark z konfiguracją jednym kliknięciem, usprawnionymi przepływami pracy i interaktywnym obszarem roboczym umożliwiającym współpracę.</span><span class="sxs-lookup"><span data-stu-id="16bb1-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="16bb1-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="16bb1-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="16bb1-106">Tworzenie obszaru roboczego usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="16bb1-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="16bb1-107">Opublikuj aplikację .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="16bb1-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="16bb1-108">Tworzenie zadania platformy Spark i klastra platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="16bb1-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="16bb1-109">Uruchom aplikację w klastrze Platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="16bb1-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16bb1-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="16bb1-110">Prerequisites</span></span>

<span data-ttu-id="16bb1-111">Przed rozpoczęciem wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="16bb1-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="16bb1-112">Jeśli nie masz konta platformy Azure, utwórz [bezpłatne konto](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="16bb1-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="16bb1-113">Zaloguj się do [Portalu Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="16bb1-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="16bb1-114">Ukończ [samouczek .NET for Apache Spark — rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.</span><span class="sxs-lookup"><span data-stu-id="16bb1-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="16bb1-115">Tworzenie obszaru roboczego usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="16bb1-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="16bb1-116">Tego samouczka nie można przeprowadzić przy użyciu **bezpłatnej subskrypcji próbnej platformy Azure.**</span><span class="sxs-lookup"><span data-stu-id="16bb1-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="16bb1-117">Jeśli masz darmowe konto, przejdź do swojego profilu i zmień subskrypcję na **płatność zgodnie z rzeczywistymami.**</span><span class="sxs-lookup"><span data-stu-id="16bb1-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="16bb1-118">Aby uzyskać więcej informacji, zobacz [Bezpłatne konto platformy Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="16bb1-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="16bb1-119">Następnie [usuń limit wydatków](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)i [poproś o zwiększenie przydziału](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) dla procesorów wirtualnych w twoim regionie.</span><span class="sxs-lookup"><span data-stu-id="16bb1-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="16bb1-120">Podczas tworzenia obszaru roboczego usługi Azure Databricks, można wybrać **warstwę cenową trial (Premium — 14-dniowe bezpłatne dbu),** aby dać obszarowi roboczemu dostęp do bezpłatnych witryn dbu usługi Premium Azure Databricks przez 14 dni.</span><span class="sxs-lookup"><span data-stu-id="16bb1-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="16bb1-121">W tej sekcji utworzysz obszar roboczy usługi Azure Databricks przy użyciu witryny Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="16bb1-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="16bb1-122">W witrynie Azure portal wybierz pozycję **Utwórz zasób** > **Analytics** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Tworzenie zasobu usługi Azure Databricks w witrynie Azure portal](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="16bb1-124">W obszarze **Usługa Azure Databricks** podaj wartości umożliwiające utworzenie obszaru roboczego usługi Databricks.</span><span class="sxs-lookup"><span data-stu-id="16bb1-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="16bb1-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="16bb1-125">Property</span></span>  |<span data-ttu-id="16bb1-126">Opis</span><span class="sxs-lookup"><span data-stu-id="16bb1-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="16bb1-127">**Nazwa obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="16bb1-127">**Workspace name**</span></span>     | <span data-ttu-id="16bb1-128">Podaj nazwę obszaru roboczego usługi Databricks.</span><span class="sxs-lookup"><span data-stu-id="16bb1-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="16bb1-129">**Subskrypcja**</span><span class="sxs-lookup"><span data-stu-id="16bb1-129">**Subscription**</span></span>     | <span data-ttu-id="16bb1-130">Z listy rozwijanej wybierz subskrypcję platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="16bb1-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="16bb1-131">**Grupa zasobów**</span><span class="sxs-lookup"><span data-stu-id="16bb1-131">**Resource group**</span></span>     | <span data-ttu-id="16bb1-132">Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy.</span><span class="sxs-lookup"><span data-stu-id="16bb1-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="16bb1-133">Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="16bb1-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="16bb1-134">Aby uzyskać więcej informacji, zobacz [Omówienie usługi Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="16bb1-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="16bb1-135">**Lokalizacja**</span><span class="sxs-lookup"><span data-stu-id="16bb1-135">**Location**</span></span>     | <span data-ttu-id="16bb1-136">Wybierz preferowany region.</span><span class="sxs-lookup"><span data-stu-id="16bb1-136">Select your preferred region.</span></span> <span data-ttu-id="16bb1-137">Aby uzyskać informacje o dostępnych regionach, zobacz [Usługi platformy Azure dostępne według regionu](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="16bb1-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="16bb1-138">**Warstwa cenowa**</span><span class="sxs-lookup"><span data-stu-id="16bb1-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="16bb1-139">Wybierz między **Standard**, **Premium**lub **Trial**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="16bb1-140">Aby uzyskać więcej informacji o tych warstwach, zobacz [stronę usługi Databricks](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="16bb1-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="16bb1-141">**Sieć wirtualna**</span><span class="sxs-lookup"><span data-stu-id="16bb1-141">**Virtual Network**</span></span>     |   <span data-ttu-id="16bb1-142">Nie</span><span class="sxs-lookup"><span data-stu-id="16bb1-142">No</span></span>       |

3. <span data-ttu-id="16bb1-143">Wybierz **pozycję Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-143">Select **Create**.</span></span> <span data-ttu-id="16bb1-144">Tworzenie obszaru roboczego trwa kilka minut.</span><span class="sxs-lookup"><span data-stu-id="16bb1-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="16bb1-145">Podczas tworzenia obszaru roboczego można wyświetlić stan wdrożenia w **obszarze Powiadomienia**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="16bb1-146">Instalowanie narzędzi usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="16bb1-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="16bb1-147">Można użyć **Interfejsu wiersza polecenia Databricks,** aby połączyć się z klastrami usługi Azure Databricks i przekazać pliki do nich z komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="16bb1-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="16bb1-148">Klastry Databricks uzyskują dostęp do plików za pośrednictwem systemu plików DBFS (Databricks File System).</span><span class="sxs-lookup"><span data-stu-id="16bb1-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="16bb1-149">Interfejs wiersza polecenia Databricks wymaga języka Python 3.6 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="16bb1-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="16bb1-150">Jeśli masz już zainstalowany python, możesz pominąć ten krok.</span><span class="sxs-lookup"><span data-stu-id="16bb1-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="16bb1-151">**Dla systemu Windows:**</span><span class="sxs-lookup"><span data-stu-id="16bb1-151">**For Windows:**</span></span>

   [<span data-ttu-id="16bb1-152">Pobierz Python dla Windows</span><span class="sxs-lookup"><span data-stu-id="16bb1-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="16bb1-153">**Dla Linuksa:** Python jest preinstalowany w większości dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="16bb1-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="16bb1-154">Uruchom następujące polecenie, aby zobaczyć, która wersja została zainstalowana:</span><span class="sxs-lookup"><span data-stu-id="16bb1-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="16bb1-155">Użyj pip, aby zainstalować databricks CLI.</span><span class="sxs-lookup"><span data-stu-id="16bb1-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="16bb1-156">Python 3.4 i nowsze domyślnie zawierają pip.</span><span class="sxs-lookup"><span data-stu-id="16bb1-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="16bb1-157">Użyj pip3 dla Pythona 3.</span><span class="sxs-lookup"><span data-stu-id="16bb1-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="16bb1-158">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="16bb1-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="16bb1-159">Po zainstalowaniu interfejsu wiersza polecenia Databricks otwórz nowy `databricks`wiersz polecenia i uruchom polecenie .</span><span class="sxs-lookup"><span data-stu-id="16bb1-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="16bb1-160">Jeśli otrzymasz **"databricks" nie jest rozpoznawany jako wewnętrzny lub zewnętrzny błąd polecenia,** upewnij się, że otworzył nowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="16bb1-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="16bb1-161">Konfigurowanie usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="16bb1-161">Set up Azure Databricks</span></span>

<span data-ttu-id="16bb1-162">Teraz, gdy masz zainstalowany plik WIERSZ DATABricks, musisz skonfigurować szczegóły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="16bb1-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="16bb1-163">Uruchom polecenie `databricks configure --token`Databricks CLI .</span><span class="sxs-lookup"><span data-stu-id="16bb1-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="16bb1-164">Po uruchomieniu polecenia configure zostanie wyświetlony monit o wprowadzenie hosta.</span><span class="sxs-lookup"><span data-stu-id="16bb1-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="16bb1-165">Adres URL hosta używa formatu: **https://<\Location>.azuredatabricks.net**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="16bb1-166">Na przykład, jeśli wybrano **eastus2** podczas tworzenia usługi **https://eastus2.azuredatabricks.net**Azure Databricks, host będzie .</span><span class="sxs-lookup"><span data-stu-id="16bb1-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="16bb1-167">Po wejściu do hosta zostanie wyświetlony monit o wprowadzenie tokenu.</span><span class="sxs-lookup"><span data-stu-id="16bb1-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="16bb1-168">W witrynie Azure portal wybierz pozycję **Uruchom obszar roboczy,** aby uruchomić obszar roboczy usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="16bb1-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Uruchamianie obszaru roboczego usługi Azure Databricks](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="16bb1-170">Na stronie głównej obszaru roboczego wybierz pozycję **Ustawienia użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Ustawienia użytkownika w obszarze roboczym usługi Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="16bb1-172">Na stronie Ustawienia użytkownika można wygenerować nowy token.</span><span class="sxs-lookup"><span data-stu-id="16bb1-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="16bb1-173">Skopiuj wygenerowany token i wklej go z powrotem do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="16bb1-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Generowanie nowego tokenu dostępu w obszarze roboczym usługi Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="16bb1-175">Teraz powinieneś mieć dostęp do wszystkich klastrów usługi Azure Databricks, które tworzysz i przekazujesz pliki do usługi DBFS.</span><span class="sxs-lookup"><span data-stu-id="16bb1-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="16bb1-176">Pobieranie zależności procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="16bb1-176">Download worker dependencies</span></span>

1. <span data-ttu-id="16bb1-177">Microsoft.Spark.Worker pomaga apache Spark wykonać aplikację, takich jak wszystkie funkcje zdefiniowane przez użytkownika (UDFs) może być napisane.</span><span class="sxs-lookup"><span data-stu-id="16bb1-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="16bb1-178">Pobierz [plik Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="16bb1-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="16bb1-179">*install-worker.sh* to skrypt, który umożliwia kopiowanie plików zależnych platformy .NET dla platformy Apache Spark do węzłów klastra.</span><span class="sxs-lookup"><span data-stu-id="16bb1-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="16bb1-180">Utwórz nowy plik o nazwie **install-worker.sh** na komputerze lokalnym i wklej [zawartość install-worker.sh znajdującą](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) się w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="16bb1-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="16bb1-181">*db-init.sh* to skrypt, który instaluje zależności w klastrze Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="16bb1-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="16bb1-182">Utwórz nowy plik o nazwie **db-init.sh** na komputerze lokalnym i wklej [zawartość db-init.sh znajdującą](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) się w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="16bb1-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="16bb1-183">W właśnie utworzonym pliku `DOTNET_SPARK_RELEASE` ustaw `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`zmienną na .</span><span class="sxs-lookup"><span data-stu-id="16bb1-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="16bb1-184">Pozostaw resztę *pliku db-init.sh* w stanie nie ma stanu"</span><span class="sxs-lookup"><span data-stu-id="16bb1-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="16bb1-185">Jeśli używasz systemu Windows, sprawdź, czy zakończenia wierszy w *skryptach install-worker.sh* i *db-init.sh* są w stylu Uniksa (LF).</span><span class="sxs-lookup"><span data-stu-id="16bb1-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="16bb1-186">Zakończenia wierszy można zmieniać za pomocą edytorów tekstu, takich jak Notatnik++ i Atom.</span><span class="sxs-lookup"><span data-stu-id="16bb1-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="16bb1-187">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="16bb1-187">Publish your app</span></span>

<span data-ttu-id="16bb1-188">Następnie publikujesz *mySparkApp* utworzony w [.NET for Apache Spark — Wprowadzenie w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, aby upewnić się, że klaster platformy Spark ma dostęp do wszystkich plików, których potrzebuje do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16bb1-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="16bb1-189">Uruchom następujące polecenia, aby opublikować *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="16bb1-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="16bb1-190">Wykonaj następujące zadania, aby skompresować opublikowane pliki aplikacji, aby łatwo przesłać je do klastra Databricks Spark.</span><span class="sxs-lookup"><span data-stu-id="16bb1-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="16bb1-191">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="16bb1-191">**On Windows:**</span></span>

   <span data-ttu-id="16bb1-192">Przejdź do mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="16bb1-192">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="16bb1-193">Następnie kliknij prawym przyciskiem myszy folder **Publikuj** i wybierz polecenie **Wyślij do > skompresowany (spakowany) folder**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="16bb1-194">Nazwij nowy folder **publish.zip**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="16bb1-195">**W systemie Linux uruchom następujące polecenie:**</span><span class="sxs-lookup"><span data-stu-id="16bb1-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="16bb1-196">Przekazywanie plików</span><span class="sxs-lookup"><span data-stu-id="16bb1-196">Upload files</span></span>

<span data-ttu-id="16bb1-197">W tej sekcji należy przekazać kilka plików do usługi DBFS, dzięki czemu klaster ma wszystko, czego potrzebuje do uruchomienia aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="16bb1-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="16bb1-198">Za każdym razem, gdy przesyłasz plik do usługi DBFS, upewnij się, że znajdujesz się w katalogu, w którym znajduje się ten plik na komputerze.</span><span class="sxs-lookup"><span data-stu-id="16bb1-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="16bb1-199">Uruchom następujące polecenia, aby przekazać *db-init.sh* *, install-worker.sh*i *Microsoft.Spark.Worker* do DBFS:</span><span class="sxs-lookup"><span data-stu-id="16bb1-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="16bb1-200">Uruchom następujące polecenia, aby przekazać pozostałe pliki, które klaster będzie musiał uruchomić aplikację: spakowany folder publikowania, *plik input.txt*i *microsoft-spark-2.4.x-0.3.0.jar*.</span><span class="sxs-lookup"><span data-stu-id="16bb1-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="16bb1-201">Tworzenie zadania</span><span class="sxs-lookup"><span data-stu-id="16bb1-201">Create a job</span></span>

<span data-ttu-id="16bb1-202">Aplikacja jest uruchamiana na platformie Azure Databricks za pomocą zadania **uruchamianego spark-submit**, które jest poleceniem używanym do uruchamiania zadań platformy .NET dla platformy Spark apache.</span><span class="sxs-lookup"><span data-stu-id="16bb1-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="16bb1-203">W obszarze roboczym usługi Azure Databricks wybierz ikonę **Zadania,** a następnie **+ Utwórz zadanie**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Tworzenie zadania usługi Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="16bb1-205">Wybierz tytuł zadania, a następnie wybierz pozycję **Konfiguruj spark-submit**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Konfigurowanie spark-submit dla zadania Databricks](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="16bb1-207">Wklej następujące parametry w konfiguracji zadania.</span><span class="sxs-lookup"><span data-stu-id="16bb1-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="16bb1-208">Następnie wybierz pozycję **Potwierdź**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="16bb1-209">Tworzenie klastra</span><span class="sxs-lookup"><span data-stu-id="16bb1-209">Create a cluster</span></span>

1. <span data-ttu-id="16bb1-210">Przejdź do zadania i wybierz pozycję **Edytuj,** aby skonfigurować klaster zadania.</span><span class="sxs-lookup"><span data-stu-id="16bb1-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="16bb1-211">Ustaw klaster na **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="16bb1-212">Następnie wybierz opcję **Zaawansowane opcje** > **Skrypty init**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="16bb1-213">Ustaw ścieżkę skryptu Init jako `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="16bb1-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Konfigurowanie klastra iskrowego w usłudze Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="16bb1-215">Wybierz **pozycję Potwierdź,** aby potwierdzić ustawienia klastra.</span><span class="sxs-lookup"><span data-stu-id="16bb1-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="16bb1-216">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="16bb1-216">Run your app</span></span>

1. <span data-ttu-id="16bb1-217">Przejdź do zadania i wybierz pozycję **Uruchom teraz,** aby uruchomić zadanie w nowo skonfigurowanym klastrze platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="16bb1-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="16bb1-218">Utworzenie klastra zadania zajmuje kilka minut.</span><span class="sxs-lookup"><span data-stu-id="16bb1-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="16bb1-219">Po jego utworzeniu zadanie zostanie przesłane i będzie można wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="16bb1-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="16bb1-220">Wybierz **polecenie Klastry** z lewego menu, a następnie nazwę i przebieg zadania.</span><span class="sxs-lookup"><span data-stu-id="16bb1-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="16bb1-221">Wybierz **dzienniki sterowników,** aby wyświetlić dane wyjściowe zadania.</span><span class="sxs-lookup"><span data-stu-id="16bb1-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="16bb1-222">Po zakończeniu wykonywania aplikacji, zobaczysz tę samą tabelę liczby wyrazów z uruchamiania lokalnego uruchamiania na początku zapisane do standardowej konsoli wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="16bb1-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Tabela wyjściowa zadania usługi Azure Databricks](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="16bb1-224">Gratulacje, uruchomiliście pierwszą aplikację .NET dla Apache Spark w chmurze!</span><span class="sxs-lookup"><span data-stu-id="16bb1-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="16bb1-225">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="16bb1-225">Clean up resources</span></span>

<span data-ttu-id="16bb1-226">Jeśli nie potrzebujesz już obszaru roboczego Databricks, możesz usunąć zasób usługi Azure Databricks w witrynie Azure portal.</span><span class="sxs-lookup"><span data-stu-id="16bb1-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="16bb1-227">Dodatkowo możesz wybrać nazwę grupy zasobów, aby otworzyć stronę grupy zasobów, a następnie wybrać pozycję **Usuń grupę zasobów**.</span><span class="sxs-lookup"><span data-stu-id="16bb1-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16bb1-228">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="16bb1-228">Next steps</span></span>

<span data-ttu-id="16bb1-229">W tym samouczku wdrożono aplikację platformy .NET for Apache Spark w witrynie Databricks.</span><span class="sxs-lookup"><span data-stu-id="16bb1-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="16bb1-230">Aby dowiedzieć się więcej o Databricks, przejdź do dokumentacji usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="16bb1-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16bb1-231">Dokumentacja usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="16bb1-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
