---
title: Instalowanie platformy .NET for Apache Spark w notesach jupyter w klastrach platformy Azure HDInsight Spark
description: Dowiedz się, jak zainstalować program .NET for Apache Spark w notesach jupyter usługi Azure HDInsight.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 953bffe5f6ec56cd0adf4224afd2eedfe0001aa9
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607418"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="87033-103">Instalowanie platformy .NET for Apache Spark w notesach jupyter w klastrach platformy Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="87033-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="87033-104">W tym artykule dowiesz się, jak zainstalować program .NET for Apache Spark w notesach jupyter w klastrach platformy Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="87033-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="87033-105">Program .NET for Apache Spark można wdrożyć w klastrach usługi Azure HDInsight za pomocą kombinacji wiersza polecenia i portalu Azure (aby uzyskać więcej informacji, zobacz [jak wdrożyć aplikację platformy .NET for Apache Spark w usłudze Azure HDInsight),](../tutorials/hdinsight-deployment.md)ale notesy zapewniają bardziej interaktywne i iteracyjne środowisko.</span><span class="sxs-lookup"><span data-stu-id="87033-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="87033-106">Klastry usługi Azure HDInsight są już wyposażone w notesy Jupyter, więc wszystko, co musisz zrobić, to skonfigurować notesy Jupyter do uruchamiania platformy .NET dla platformy Spark apache.</span><span class="sxs-lookup"><span data-stu-id="87033-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="87033-107">Aby użyć platformy .NET for Apache Spark w notesach jupyter, potrzebny jest wartość REPL języka C# do wykonania wiersza według wiersza kodu języka C# i zachowania stanu wykonania w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="87033-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="87033-108">[Try .NET](https://github.com/dotnet/try) został zintegrowany jako oficjalny .NET REPL.</span><span class="sxs-lookup"><span data-stu-id="87033-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="87033-109">Aby włączyć program .NET for Apache Spark za pośrednictwem obsługi notesów Jupyter, należy wykonać kilka ręcznych kroków za pomocą [programu Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) i przesłać [akcje skryptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) w klastrze platformy SPARK usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="87033-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="87033-110">Ta funkcja jest *eksperymentalna* i nie jest obsługiwana przez zespół HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="87033-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="87033-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="87033-111">Prerequisites</span></span>

<span data-ttu-id="87033-112">Jeśli jeszcze go nie masz, utwórz klaster [platformy Azure HDInsight Spark.](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight)</span><span class="sxs-lookup"><span data-stu-id="87033-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="87033-113">Odwiedź [witrynę Azure portal](https://portal.azure.com) i wybierz **pozycję + Utwórz zasób**.</span><span class="sxs-lookup"><span data-stu-id="87033-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="87033-114">Utwórz nowy zasób klastra usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="87033-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="87033-115">Wybierz **Spark 2.4** i **HDI 4.0** podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="87033-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="87033-116">Instalowanie platformy .NET dla platformy Spark</span><span class="sxs-lookup"><span data-stu-id="87033-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="87033-117">W witrynie Azure portal wybierz **klaster platformy SPARK usługi HDInsight** utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="87033-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="87033-118">Zatrzymaj serwer Livy</span><span class="sxs-lookup"><span data-stu-id="87033-118">Stop the Livy server</span></span>

1. <span data-ttu-id="87033-119">W portalu wybierz **pozycję Przegląd**, a następnie wybierz pozycję **Ambari home**.</span><span class="sxs-lookup"><span data-stu-id="87033-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="87033-120">Jeśli zostanie wyświetlony monit, wprowadź poświadczenia logowania dla klastra.</span><span class="sxs-lookup"><span data-stu-id="87033-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="87033-122">Z lewego menu nawigacji wybierz **opcję Spark2** i wybierz opcję **LIVY FOR SPARK2 SERVER**.</span><span class="sxs-lookup"><span data-stu-id="87033-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="87033-124">Wybierz **hn0... hosta**.</span><span class="sxs-lookup"><span data-stu-id="87033-124">Select **hn0... host**.</span></span>

   ![Zatrzymaj livy server](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="87033-126">Wybierz wielokropek obok **pozycji Livy for Spark2 Server** i wybierz pozycję **Zatrzymaj**.</span><span class="sxs-lookup"><span data-stu-id="87033-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="87033-127">Po wyświetleniu monitu wybierz przycisk **OK,** aby kontynuować.</span><span class="sxs-lookup"><span data-stu-id="87033-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="87033-128">Zatrzymaj Livy dla serwera Spark2.</span><span class="sxs-lookup"><span data-stu-id="87033-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="87033-129">![Zatrzymaj livy server](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="87033-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="87033-130">Powtórz poprzednie kroki dla **hn1... hosta**.</span><span class="sxs-lookup"><span data-stu-id="87033-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="87033-131">Przesyłanie akcji skryptu HDInsight</span><span class="sxs-lookup"><span data-stu-id="87033-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="87033-132">Jest `install-interactive-notebook.sh` to skrypt, który instaluje .NET dla Apache Spark i wprowadza zmiany do Apache Livy i sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="87033-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="87033-133">Przed przesłaniem akcji skryptu do pliku HDInsight `install-interactive-notebook.sh`należy utworzyć i przesłać plik .</span><span class="sxs-lookup"><span data-stu-id="87033-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="87033-134">Utwórz nowy plik o nazwie **install-interactive-notebook.sh** na komputerze lokalnym i wklej zawartość [install-interactive-notebook.sh zawartości](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="87033-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="87033-135">Przekaż skrypt do identyfikatora [URI,](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) który jest dostępny z klastra HDInsight.</span><span class="sxs-lookup"><span data-stu-id="87033-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="87033-136">Na przykład `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="87033-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="87033-137">Uruchom `install-interactive-notebook.sh` w klastrze przy użyciu [akcji skryptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="87033-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="87033-138">Wróć do klastra HDI w witrynie Azure portal i wybierz **akcje skryptu** z opcji po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="87033-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="87033-139">Prześlij jedną akcję skryptu, aby wdrożyć .NET for Apache Spark REPL w klastrze platformy SPARK usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="87033-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="87033-140">Użyj następujących ustawień:</span><span class="sxs-lookup"><span data-stu-id="87033-140">Use the following settings:</span></span>

   |<span data-ttu-id="87033-141">Właściwość</span><span class="sxs-lookup"><span data-stu-id="87033-141">Property</span></span>  |<span data-ttu-id="87033-142">Opis</span><span class="sxs-lookup"><span data-stu-id="87033-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="87033-143">Typ skryptu</span><span class="sxs-lookup"><span data-stu-id="87033-143">Script type</span></span> | <span data-ttu-id="87033-144">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="87033-144">Custom</span></span> |
   | <span data-ttu-id="87033-145">Nazwa</span><span class="sxs-lookup"><span data-stu-id="87033-145">Name</span></span> | <span data-ttu-id="87033-146">*Instalowanie programu .NET dla interaktywnego notebooka Apache Spark*</span><span class="sxs-lookup"><span data-stu-id="87033-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="87033-147">Identyfikator URI skryptu bash</span><span class="sxs-lookup"><span data-stu-id="87033-147">Bash script URI</span></span> | <span data-ttu-id="87033-148">Identyfikator URI, do `install-interactive-notebook.sh`którego został przesłany .</span><span class="sxs-lookup"><span data-stu-id="87033-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="87033-149">Typy węzłów</span><span class="sxs-lookup"><span data-stu-id="87033-149">Node type(s)</span></span>| <span data-ttu-id="87033-150">Głowa i pracownik</span><span class="sxs-lookup"><span data-stu-id="87033-150">Head and Worker</span></span> |
   | <span data-ttu-id="87033-151">Parametry</span><span class="sxs-lookup"><span data-stu-id="87033-151">Parameters</span></span> | <span data-ttu-id="87033-152">.NET dla wersji Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="87033-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="87033-153">Możesz sprawdzić [.NET dla apache Spark wydań](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="87033-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="87033-154">Na przykład, jeśli chcesz zainstalować Sparkdotnet w wersji 0.6.0 to będzie `0.6.0`.</span><span class="sxs-lookup"><span data-stu-id="87033-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="87033-155">Przejdź do następnego kroku, gdy obok stanu akcji skryptu pojawią się zielone znaczniki wyboru.</span><span class="sxs-lookup"><span data-stu-id="87033-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="87033-156">Uruchamianie serwera Livy</span><span class="sxs-lookup"><span data-stu-id="87033-156">Start the Livy server</span></span>

<span data-ttu-id="87033-157">Postępuj zgodnie z instrukcjami w sekcji [Zatrzymaj serwer Livy,](#stop-the-livy-server) aby **uruchomić** (a nie **zatrzymać)** serwer Livy dla Spark2 dla hostów **hn0** i **hn1.**</span><span class="sxs-lookup"><span data-stu-id="87033-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="87033-158">Konfigurowanie domyślnych konfiguracji platformy Spark</span><span class="sxs-lookup"><span data-stu-id="87033-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="87033-159">W portalu wybierz **pozycję Przegląd**, a następnie wybierz pozycję **Ambari home**.</span><span class="sxs-lookup"><span data-stu-id="87033-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="87033-160">Jeśli zostanie wyświetlony monit, wprowadź poświadczenia logowania dla klastra.</span><span class="sxs-lookup"><span data-stu-id="87033-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="87033-161">Wybierz **Spark2** i **CONFIGS**.</span><span class="sxs-lookup"><span data-stu-id="87033-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="87033-162">Następnie wybierz pozycję **Niestandardowe iskrzenie2-domyślne**.</span><span class="sxs-lookup"><span data-stu-id="87033-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Ustawianie konfiguracji](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="87033-164">Wybierz **pozycję Dodaj właściwość...,** aby dodać domyślne ustawienia platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="87033-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Dodaj właściwość](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="87033-166">Istnieją trzy indywidualne właściwości.</span><span class="sxs-lookup"><span data-stu-id="87033-166">There are three individual properties.</span></span> <span data-ttu-id="87033-167">Dodaj je pojedynczo przy użyciu text typu **właściwości** w trybie dodawania właściwości Single.</span><span class="sxs-lookup"><span data-stu-id="87033-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="87033-168">Sprawdź, czy nie masz żadnych dodatkowych spacji przed lub po żadnym z kluczy /wartości.</span><span class="sxs-lookup"><span data-stu-id="87033-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="87033-169">**Nieruchomość 1**</span><span class="sxs-lookup"><span data-stu-id="87033-169">**Property 1**</span></span>
       * <span data-ttu-id="87033-170">Klucz:&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="87033-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="87033-171">Wartość:`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="87033-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="87033-172">**Nieruchomość 2** Użyj wersji platformy .NET dla platformy Apache Spark, która została uwzględniona w poprzedniej akcji skryptu.</span><span class="sxs-lookup"><span data-stu-id="87033-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="87033-173">Klucz:&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="87033-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="87033-174">Wartość:`["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="87033-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="87033-175">**Nieruchomość 3**</span><span class="sxs-lookup"><span data-stu-id="87033-175">**Property 3**</span></span>
       * <span data-ttu-id="87033-176">Klucz:&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="87033-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="87033-177">Wartość:`try`</span><span class="sxs-lookup"><span data-stu-id="87033-177">Value: `try`</span></span>

   <span data-ttu-id="87033-178">Na przykład poniższy obraz przechwytuje ustawienie dodawania właściwości 1:</span><span class="sxs-lookup"><span data-stu-id="87033-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Ustawianie konfiguracji](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="87033-180">Po dodaniu trzech właściwości wybierz pozycję **ZAPISZ**.</span><span class="sxs-lookup"><span data-stu-id="87033-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="87033-181">Jeśli widzisz ekran ostrzegawczy rekomendacji konfigura, wybierz **PROCEED ANYWAY**.</span><span class="sxs-lookup"><span data-stu-id="87033-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="87033-182">Uruchom ponownie składniki, których dotyczy problem.</span><span class="sxs-lookup"><span data-stu-id="87033-182">Restart affected components.</span></span>

   <span data-ttu-id="87033-183">Po dodaniu nowych właściwości należy ponownie uruchomić składniki, których zmiany miały wpływ.</span><span class="sxs-lookup"><span data-stu-id="87033-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="87033-184">U góry wybierz pozycję **RESTART**, a następnie **uruchom ponownie wszystkie, których dotyczy problem** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="87033-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Ustawianie konfiguracji](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="87033-186">Po wyświetleniu monitu wybierz pozycję **POTWIERDŹ PONOWNIE WSZYSTKO,** aby kontynuować, a następnie kliknij przycisk **OK,** aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="87033-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="87033-187">Przesyłanie zadań za pośrednictwem notesu Jupyter</span><span class="sxs-lookup"><span data-stu-id="87033-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="87033-188">Po zakończeniu poprzednich kroków można teraz przesłać zadania platformy .NET dla platformy Apache Spark za pośrednictwem notesów Jupyter.</span><span class="sxs-lookup"><span data-stu-id="87033-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="87033-189">Utwórz nowy notes platformy .NET dla platformy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="87033-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="87033-190">Uruchom notes Jupyter z klastra HDI w witrynie Azure portal.</span><span class="sxs-lookup"><span data-stu-id="87033-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Uruchom notebook Jupyter](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="87033-192">Następnie wybierz pozycję **Nowa** > **platforma Iskrowa .NET (C#),** aby utworzyć notes.</span><span class="sxs-lookup"><span data-stu-id="87033-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="87033-194">Prześlij zadania przy użyciu platformy .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="87033-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="87033-195">Użyj następującego fragmentu kodu, aby utworzyć ramkę DataFrame:</span><span class="sxs-lookup"><span data-stu-id="87033-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Prześlij zadanie spark](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="87033-197">Użyj następującego fragmentu kodu, aby zarejestrować funkcję zdefiniowaną przez użytkownika (UDF) i użyć UDF z dataframes:</span><span class="sxs-lookup"><span data-stu-id="87033-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Prześlij zadanie spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="87033-199">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="87033-199">Next steps</span></span>

* [<span data-ttu-id="87033-200">Wdrażanie aplikacji platformy .NET dla platformy Spark usługi Apache w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="87033-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="87033-201">Dokumentacja hdinsight</span><span class="sxs-lookup"><span data-stu-id="87033-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
