---
title: Wdrażanie aplikacji platformy .NET dla Apache Spark w kostkach
description: Dowiedz się, jak wdrożyć aplikację platformy .NET dla Apache Spark w usłudze datakostki.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c1c1a57fb2b79826218f8ed94d568b37d4689560
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454276"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="b4c52-103">Samouczek: wdrażanie aplikacji .NET dla Apache Spark w kostkach</span><span class="sxs-lookup"><span data-stu-id="b4c52-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="b4c52-104">W tym samouczku przedstawiono sposób wdrażania aplikacji w chmurze za pośrednictwem Azure Databricks, opartej na Apache Sparkj platformie analitycznej z instalacją jednym kliknięciem, usprawnionych przepływów pracy i interaktywnego obszaru roboczego, który umożliwia współpracę.</span><span class="sxs-lookup"><span data-stu-id="b4c52-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="b4c52-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b4c52-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b4c52-106">Utwórz obszar roboczy Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="b4c52-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="b4c52-107">Opublikuj aplikację .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b4c52-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="b4c52-108">Utwórz zadanie platformy Spark i klaster Spark.</span><span class="sxs-lookup"><span data-stu-id="b4c52-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="b4c52-109">Uruchom aplikację w klastrze Spark.</span><span class="sxs-lookup"><span data-stu-id="b4c52-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4c52-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b4c52-110">Prerequisites</span></span>

<span data-ttu-id="b4c52-111">Przed rozpoczęciem wykonaj następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="b4c52-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="b4c52-112">Jeśli nie masz konta platformy Azure, Utwórz [bezpłatne konto](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="b4c52-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="b4c52-113">Zaloguj się do [Azure Portal](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="b4c52-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="b4c52-114">Ukończ [platformę .NET dla Apache Spark — Rozpocznij pracę w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku.</span><span class="sxs-lookup"><span data-stu-id="b4c52-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="b4c52-115">Tworzenie obszaru roboczego Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="b4c52-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="b4c52-116">Tego samouczka nie można przeprowadzić za pomocą **subskrypcji bezpłatnej wersji próbnej platformy Azure**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="b4c52-117">Jeśli masz bezpłatne konto, przejdź do swojego profilu i Zmień subskrypcję na **płatność zgodnie z rzeczywistym**użyciem.</span><span class="sxs-lookup"><span data-stu-id="b4c52-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="b4c52-118">Aby uzyskać więcej informacji, zobacz [bezpłatne konto platformy Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="b4c52-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="b4c52-119">Następnie [Usuń limit wydatków](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)i [Poproś o zwiększenie limitu przydziału](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) dla procesorów wirtualnych vCPU w Twoim regionie.</span><span class="sxs-lookup"><span data-stu-id="b4c52-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="b4c52-120">Podczas tworzenia obszaru roboczego Azure Databricks możesz wybrać warstwę cenową **wersji próbnej (Premium-14-Days Free dBu)** , aby umożliwić dostęp do obszaru roboczego bezpłatnie Azure Databricks DBU przez 14 dni.</span><span class="sxs-lookup"><span data-stu-id="b4c52-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="b4c52-121">W tej sekcji utworzysz obszar roboczy Azure Databricks przy użyciu Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="b4c52-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="b4c52-122">W Azure Portal wybierz pozycję **Utwórz zasób** > **Analytics** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Tworzenie zasobu Azure Databricks w Azure Portal](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="b4c52-124">W obszarze **usługa Azure Databricks**podaj wartości, aby utworzyć obszar roboczy datakostki.</span><span class="sxs-lookup"><span data-stu-id="b4c52-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="b4c52-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b4c52-125">Property</span></span>  |<span data-ttu-id="b4c52-126">Opis</span><span class="sxs-lookup"><span data-stu-id="b4c52-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="b4c52-127">**Nazwa obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="b4c52-127">**Workspace name**</span></span>     | <span data-ttu-id="b4c52-128">Podaj nazwę obszaru roboczego datakostki.</span><span class="sxs-lookup"><span data-stu-id="b4c52-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="b4c52-129">**Ramach**</span><span class="sxs-lookup"><span data-stu-id="b4c52-129">**Subscription**</span></span>     | <span data-ttu-id="b4c52-130">Z listy rozwijanej wybierz subskrypcję platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b4c52-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="b4c52-131">**Grupa zasobów**</span><span class="sxs-lookup"><span data-stu-id="b4c52-131">**Resource group**</span></span>     | <span data-ttu-id="b4c52-132">Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej.</span><span class="sxs-lookup"><span data-stu-id="b4c52-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="b4c52-133">Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b4c52-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="b4c52-134">Aby uzyskać więcej informacji, zobacz [Omówienie grupy zasobów platformy Azure](/azure/azure-databricks/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="b4c52-134">For more information, see [Azure Resource Group overview](/azure/azure-databricks/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="b4c52-135">**Lokalizacja**</span><span class="sxs-lookup"><span data-stu-id="b4c52-135">**Location**</span></span>     | <span data-ttu-id="b4c52-136">Wybierz preferowany region.</span><span class="sxs-lookup"><span data-stu-id="b4c52-136">Select your preferred region.</span></span> <span data-ttu-id="b4c52-137">Aby uzyskać informacje na temat dostępnych regionów, zobacz [usługi platformy Azure dostępne według regionów](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="b4c52-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="b4c52-138">**Warstwa cenowa**</span><span class="sxs-lookup"><span data-stu-id="b4c52-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="b4c52-139">Wybierz warstwę **standardowa**, **Premium**lub **wersja próbna**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="b4c52-140">Aby uzyskać więcej informacji o tych warstwach, zobacz [stronę cennika usługi datacegły](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="b4c52-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="b4c52-141">**Virtual Network**</span><span class="sxs-lookup"><span data-stu-id="b4c52-141">**Virtual Network**</span></span>     |   <span data-ttu-id="b4c52-142">Nie</span><span class="sxs-lookup"><span data-stu-id="b4c52-142">No</span></span>       |

3. <span data-ttu-id="b4c52-143">Wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-143">Select **Create**.</span></span> <span data-ttu-id="b4c52-144">Tworzenie obszaru roboczego trwa kilka minut.</span><span class="sxs-lookup"><span data-stu-id="b4c52-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="b4c52-145">Podczas tworzenia obszaru roboczego można wyświetlić stan wdrożenia w obszarze **powiadomienia**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="b4c52-146">Zainstaluj narzędzia Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="b4c52-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="b4c52-147">Korzystając z **interfejsu wiersza polecenia datacegłs** , można nawiązać połączenie z klastrami Azure Databricks i przekazywać do nich pliki z komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b4c52-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="b4c52-148">Klastry datacegły uzyskują dostęp do plików za poorednictwem DBFS (system plików).</span><span class="sxs-lookup"><span data-stu-id="b4c52-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="b4c52-149">Interfejs wiersza polecenia datakostki wymaga języka Python 3,6 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="b4c52-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="b4c52-150">Jeśli masz już zainstalowany język Python, możesz pominąć ten krok.</span><span class="sxs-lookup"><span data-stu-id="b4c52-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="b4c52-151">**Dla systemu Windows:**</span><span class="sxs-lookup"><span data-stu-id="b4c52-151">**For Windows:**</span></span>

   [<span data-ttu-id="b4c52-152">Pobierz Język Python dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4c52-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="b4c52-153">**Dla systemu Linux:** Środowisko Python jest preinstalowane na większości dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b4c52-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="b4c52-154">Uruchom następujące polecenie, aby sprawdzić, która wersja została zainstalowana:</span><span class="sxs-lookup"><span data-stu-id="b4c52-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="b4c52-155">Użyj narzędzia PIP, aby zainstalować interfejs wiersza polecenia datakosteks.</span><span class="sxs-lookup"><span data-stu-id="b4c52-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="b4c52-156">Środowisko Python 3,4 i nowsze zawierają domyślnie funkcję PIP.</span><span class="sxs-lookup"><span data-stu-id="b4c52-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="b4c52-157">Użyj PIP3 dla języka Python 3.</span><span class="sxs-lookup"><span data-stu-id="b4c52-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="b4c52-158">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b4c52-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="b4c52-159">Po zainstalowaniu interfejsu wiersza polecenia datakostki Otwórz nowy wiersz poleceń i uruchom polecenie `databricks`.</span><span class="sxs-lookup"><span data-stu-id="b4c52-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="b4c52-160">Jeśli zostanie wyświetlony komunikat " **" nie jest rozpoznawany jako błąd wewnętrzny lub zewnętrzny**, upewnij się, że otwarto nowy wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="b4c52-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="b4c52-161">Skonfiguruj Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="b4c52-161">Set up Azure Databricks</span></span>

<span data-ttu-id="b4c52-162">Teraz, gdy masz zainstalowany interfejs wiersza polecenia datakosteks, musisz skonfigurować szczegóły uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="b4c52-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="b4c52-163">Uruchom interfejs wiersza polecenia dla `databricks configure --token`.</span><span class="sxs-lookup"><span data-stu-id="b4c52-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="b4c52-164">Po uruchomieniu polecenia Konfiguruj zostanie wyświetlony monit o wprowadzenie hosta.</span><span class="sxs-lookup"><span data-stu-id="b4c52-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="b4c52-165">Adres URL hosta używa formatu: **https://< \Location >. azuredatabricks. NET**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="b4c52-166">Na przykład w przypadku wybrania **eastus2** podczas tworzenia usługi Azure Databricks host zostanie **https://eastus2.azuredatabricks.net** .</span><span class="sxs-lookup"><span data-stu-id="b4c52-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="b4c52-167">Po wprowadzeniu hosta zostanie wyświetlony monit o wprowadzenie tokenu.</span><span class="sxs-lookup"><span data-stu-id="b4c52-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="b4c52-168">W Azure Portal wybierz pozycję **Uruchom obszar roboczy** , aby uruchomić Azure Databricks obszar roboczy.</span><span class="sxs-lookup"><span data-stu-id="b4c52-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Uruchom Azure Databricks obszar roboczy](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="b4c52-170">Na stronie głównej obszaru roboczego wybierz pozycję **Ustawienia użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Ustawienia użytkownika w obszarze roboczym Azure Databricks](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="b4c52-172">Na stronie Ustawienia użytkownika można wygenerować nowy token.</span><span class="sxs-lookup"><span data-stu-id="b4c52-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="b4c52-173">Skopiuj wygenerowany token i wklej go z powrotem do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b4c52-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Generuj nowy token dostępu w obszarze roboczym Azure Databricks](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="b4c52-175">Teraz powinno być możliwe uzyskanie dostępu do dowolnych klastrów Azure Databricks tworzenia i przekazywania plików do DBFS.</span><span class="sxs-lookup"><span data-stu-id="b4c52-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="b4c52-176">Pobierz zależności procesów roboczych</span><span class="sxs-lookup"><span data-stu-id="b4c52-176">Download worker dependencies</span></span>

1. <span data-ttu-id="b4c52-177">Aplikacja Microsoft. Spark. Worker ułatwia Apache Spark wykonywanie aplikacji, na przykład dowolnych funkcji zdefiniowanych przez użytkownika (UDF).</span><span class="sxs-lookup"><span data-stu-id="b4c52-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="b4c52-178">Pobierz [pakiet Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="b4c52-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="b4c52-179">*Install-Worker.sh* to skrypt, który umożliwia skopiowanie programu .net dla Apache Spark plików zależnych do węzłów klastra.</span><span class="sxs-lookup"><span data-stu-id="b4c52-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="b4c52-180">Utwórz nowy plik o nazwie **Install-Worker.sh** na komputerze lokalnym i wklej [zawartość Install-Worker.sh](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) znajdującą się w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="b4c52-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="b4c52-181">*DB-init.sh* to skrypt służący do instalowania zależności w klastrze danych platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="b4c52-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="b4c52-182">Utwórz nowy plik o nazwie **DB-init.sh** na komputerze lokalnym i wklej [zawartość DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) znajdującą się w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="b4c52-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="b4c52-183">W właśnie utworzonym pliku Ustaw zmienną `DOTNET_SPARK_RELEASE` na `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="b4c52-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="b4c52-184">Pozostaw resztę pliku *DB-init.sh* .</span><span class="sxs-lookup"><span data-stu-id="b4c52-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="b4c52-185">Jeśli używasz systemu Windows, upewnij się, że końce wiersza w skryptach *Install-Worker.sh* i *DB-init.sh* są w stylu systemu UNIX (LF).</span><span class="sxs-lookup"><span data-stu-id="b4c52-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="b4c52-186">Końce wierszy można zmienić za pomocą edytorów tekstu, takich jak Notatnik + + i Atom.</span><span class="sxs-lookup"><span data-stu-id="b4c52-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="b4c52-187">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b4c52-187">Publish your app</span></span>

<span data-ttu-id="b4c52-188">Następnie opublikujesz *mySparkApp* utworzoną w programie [.net for Apache Spark — Rozpocznij w 10-minutowym](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) samouczku, aby zapewnić, że klaster Spark ma dostęp do wszystkich plików potrzebnych do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4c52-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="b4c52-189">Uruchom następujące polecenia, aby opublikować *mySparkApp*:</span><span class="sxs-lookup"><span data-stu-id="b4c52-189">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="b4c52-190">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="b4c52-190">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x6
   ```

   <span data-ttu-id="b4c52-191">**W systemie Linux:**</span><span class="sxs-lookup"><span data-stu-id="b4c52-191">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="b4c52-192">Wykonaj następujące zadania w celu przesłania plików opublikowanych aplikacji, aby można je było łatwo przekazać do klastra Spark.</span><span class="sxs-lookup"><span data-stu-id="b4c52-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="b4c52-193">**W systemie Windows:**</span><span class="sxs-lookup"><span data-stu-id="b4c52-193">**On Windows:**</span></span>

   <span data-ttu-id="b4c52-194">Przejdź do mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64.</span><span class="sxs-lookup"><span data-stu-id="b4c52-194">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="b4c52-195">Następnie kliknij prawym przyciskiem myszy folder **Publikowanie** i wybierz polecenie **Wyślij do > folder skompresowany (zip)** .</span><span class="sxs-lookup"><span data-stu-id="b4c52-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="b4c52-196">Nadaj nowemu folderowi nazwę **Publish. zip**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="b4c52-197">**W systemie Linux Uruchom następujące polecenie:**</span><span class="sxs-lookup"><span data-stu-id="b4c52-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="b4c52-198">Przekazywanie plików</span><span class="sxs-lookup"><span data-stu-id="b4c52-198">Upload files</span></span>

<span data-ttu-id="b4c52-199">W tej sekcji przekazano kilka plików do DBFS, aby klaster miał wszystko, czego potrzebuje do uruchomienia aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b4c52-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="b4c52-200">Za każdym razem, gdy przekażesz plik do DBFS, upewnij się, że znajduje się w katalogu, w którym znajduje się ten plik na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b4c52-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="b4c52-201">Uruchom następujące polecenia, aby przekazać *DB-init.sh*, *Install-Worker.sh*i *Microsoft. Spark. Worker* do DBFS:</span><span class="sxs-lookup"><span data-stu-id="b4c52-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="b4c52-202">Uruchom następujące polecenia, aby przekazać pozostałe pliki, do których klaster będzie musiał uruchomić aplikację: spakowanego folderu publikowania, *Input. txt*i *Microsoft-Spark-2.4. x-0.3.0. jar*.</span><span class="sxs-lookup"><span data-stu-id="b4c52-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="b4c52-203">Tworzenie zadania</span><span class="sxs-lookup"><span data-stu-id="b4c52-203">Create a job</span></span>

<span data-ttu-id="b4c52-204">Aplikacja jest uruchamiana na Azure Databricks za pomocą zadania uruchamiającego żądanie uruchomienia platformy **Spark**, które jest poleceniem używanym do uruchamiania programu .net dla Apache Spark zadań.</span><span class="sxs-lookup"><span data-stu-id="b4c52-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="b4c52-205">W obszarze roboczym Azure Databricks wybierz ikonę **zadania** , a następnie pozycję **+ Utwórz zadanie**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Tworzenie zadania Azure Databricks](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="b4c52-207">Wybierz tytuł zadania, a następnie wybierz pozycję Skonfiguruj platformę **Spark-Submit**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Konfigurowanie usługi Spark-Submit dla zadań datakostek](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="b4c52-209">Wklej następujące parametry w konfiguracji zadania.</span><span class="sxs-lookup"><span data-stu-id="b4c52-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="b4c52-210">Następnie wybierz pozycję **Potwierdź**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="b4c52-211">Tworzenie klastra</span><span class="sxs-lookup"><span data-stu-id="b4c52-211">Create a cluster</span></span>

1. <span data-ttu-id="b4c52-212">Przejdź do zadania i wybierz pozycję **Edytuj** , aby skonfigurować klaster zadania.</span><span class="sxs-lookup"><span data-stu-id="b4c52-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="b4c52-213">Ustaw klaster na platformę **Spark 2.4.1**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="b4c52-214">Następnie wybierz pozycję **Opcje zaawansowane** > **init scripts**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="b4c52-215">Ustaw ścieżkę skryptu init jako `dbfs:/spark-dotnet/db-init.sh`.</span><span class="sxs-lookup"><span data-stu-id="b4c52-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Skonfiguruj klaster Spark w Azure Databricks](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="b4c52-217">Wybierz pozycję **Potwierdź** , aby potwierdzić ustawienia klastra.</span><span class="sxs-lookup"><span data-stu-id="b4c52-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="b4c52-218">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b4c52-218">Run your app</span></span>

1. <span data-ttu-id="b4c52-219">Przejdź do zadania i wybierz pozycję **Uruchom teraz** , aby uruchomić zadanie w nowo skonfigurowanym klastrze Spark.</span><span class="sxs-lookup"><span data-stu-id="b4c52-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="b4c52-220">Utworzenie klastra zadania może potrwać kilka minut.</span><span class="sxs-lookup"><span data-stu-id="b4c52-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="b4c52-221">Po jego utworzeniu zadanie zostanie przesłane i będzie można wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b4c52-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="b4c52-222">Z menu po lewej stronie wybierz pozycję **klastry** , a następnie nazwę i uruchomienie zadania.</span><span class="sxs-lookup"><span data-stu-id="b4c52-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="b4c52-223">Wybierz pozycję **dzienniki sterowników** , aby wyświetlić dane wyjściowe zadania.</span><span class="sxs-lookup"><span data-stu-id="b4c52-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="b4c52-224">Gdy aplikacja zakończy wykonywanie, zobaczysz tę samą tabelę Count wyrazów z uruchomienia lokalnego uruchamiania zapisaną w standardowej konsoli wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="b4c52-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks tabeli wyjściowej zadania](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="b4c52-226">Gratulacje, uruchomiono pierwszą aplikację platformy .NET dla Apache Spark w chmurze!</span><span class="sxs-lookup"><span data-stu-id="b4c52-226">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="b4c52-227">Czyszczenie zasobów</span><span class="sxs-lookup"><span data-stu-id="b4c52-227">Clean up resources</span></span>

<span data-ttu-id="b4c52-228">Jeśli obszar roboczy datakostki nie jest już potrzebny, możesz usunąć zasób Azure Databricks w Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="b4c52-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="b4c52-229">Możesz również wybrać nazwę grupy zasobów, aby otworzyć stronę Grupa zasobów, a następnie wybierz pozycję **Usuń grupę zasobów**.</span><span class="sxs-lookup"><span data-stu-id="b4c52-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b4c52-230">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b4c52-230">Next steps</span></span>

<span data-ttu-id="b4c52-231">W tym samouczku wdrożono aplikację .NET dla Apache Spark w usłudze datakostki.</span><span class="sxs-lookup"><span data-stu-id="b4c52-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="b4c52-232">Aby dowiedzieć się więcej na temat datakostki, przejdź do dokumentacji Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="b4c52-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4c52-233">Dokumentacja Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="b4c52-233">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
