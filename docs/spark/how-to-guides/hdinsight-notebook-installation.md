---
title: Zainstaluj platformę .NET dla Apache Spark w notesach Jupyter w klastrach Azure HDInsight Spark
description: Dowiedz się, jak zainstalować platformę .NET dla Apache Spark w notesach Jupyter usługi Azure HDInsight.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617746"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="804ac-103">Zainstaluj platformę .NET dla Apache Spark w notesach Jupyter w klastrach Azure HDInsight Spark</span><span class="sxs-lookup"><span data-stu-id="804ac-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="804ac-104">W tym artykule przedstawiono sposób instalowania programu .NET for Apache Spark w notesach Jupyter w klastrach Azure HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="804ac-105">Platformę .NET dla Apache Spark w klastrach usługi Azure HDInsight można wdrożyć za pomocą kombinacji wiersza polecenia i Azure Portal (Aby uzyskać więcej informacji, zobacz artykuł [jak wdrożyć aplikację .net for Apache Spark w usłudze Azure HDInsight](../tutorials/hdinsight-deployment.md)), ale notesy zapewniają bardziej interaktywną i iteracyjną pracę.</span><span class="sxs-lookup"><span data-stu-id="804ac-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="804ac-106">Klastry usługi Azure HDInsight są już dołączone do notesów Jupyter, więc wystarczy skonfigurować notesy Jupyter do uruchamiania programu .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="804ac-107">Aby można było używać platformy .NET do Apache Spark w notesach Jupyter, w języku c# REPL jest potrzebny do wykonania kodu w języku C# i zachowania stanu wykonywania w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="804ac-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="804ac-108">[Wypróbuj platformę .NET](https://github.com/dotnet/try) jako oficjalną REPL .NET.</span><span class="sxs-lookup"><span data-stu-id="804ac-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="804ac-109">Aby włączyć platformę .NET dla Apache Spark za pomocą środowiska Jupyter notesy, należy wykonać kilka ręcznych czynności za pomocą [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) i przesłać [Akcje skryptu](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) w klastrze usługi HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="804ac-110">Ta funkcja jest *eksperymentalna* i nie jest obsługiwana przez zespół usługi HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="804ac-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="804ac-111">Prerequisites</span></span>

<span data-ttu-id="804ac-112">Jeśli jeszcze tego nie masz, Utwórz klaster [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) .</span><span class="sxs-lookup"><span data-stu-id="804ac-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="804ac-113">Odwiedź [Azure Portal](https://portal.azure.com) i wybierz pozycję **+ Utwórz zasób**.</span><span class="sxs-lookup"><span data-stu-id="804ac-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="804ac-114">Utwórz nowy zasób klastra usługi Azure HDInsight.</span><span class="sxs-lookup"><span data-stu-id="804ac-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="804ac-115">Wybierz pozycję **Spark 2,4** i **HDI 4,0** podczas tworzenia klastra.</span><span class="sxs-lookup"><span data-stu-id="804ac-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="804ac-116">Zainstaluj platformę .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="804ac-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="804ac-117">W Azure Portal wybierz **klaster HDInsight Spark** utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="804ac-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="804ac-118">Zatrzymaj serwer usługi Livy</span><span class="sxs-lookup"><span data-stu-id="804ac-118">Stop the Livy server</span></span>

1. <span data-ttu-id="804ac-119">W portalu wybierz pozycję **Przegląd**, a następnie wybierz pozycję **Strona główna Ambari**.</span><span class="sxs-lookup"><span data-stu-id="804ac-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="804ac-120">Jeśli zostanie wyświetlony monit, wprowadź poświadczenia logowania dla klastra.</span><span class="sxs-lookup"><span data-stu-id="804ac-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Zatrzymaj serwer usługi Livy](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="804ac-122">Wybierz pozycję **Spark2** w menu nawigacji po lewej stronie, a następnie wybierz pozycję **usługi LIVY dla Spark2 Server**.</span><span class="sxs-lookup"><span data-stu-id="804ac-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Zatrzymaj serwer usługi Livy](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="804ac-124">Wybierz **hn0... Host**.</span><span class="sxs-lookup"><span data-stu-id="804ac-124">Select **hn0... host**.</span></span>

   ![Zatrzymaj serwer usługi Livy](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="804ac-126">Wybierz wielokropek obok pozycji **usługi Livy dla serwera Spark2** i wybierz pozycję **Zatrzymaj**.</span><span class="sxs-lookup"><span data-stu-id="804ac-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="804ac-127">Po wyświetleniu monitu wybierz pozycję **OK** , aby wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="804ac-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="804ac-128">Zatrzymaj usługi Livy dla serwera Spark2.</span><span class="sxs-lookup"><span data-stu-id="804ac-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="804ac-129">![Zatrzymaj serwer usługi Livy](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="804ac-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="804ac-130">Powtórz poprzednie kroki dla **hn1... Host**.</span><span class="sxs-lookup"><span data-stu-id="804ac-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="804ac-131">Prześlij akcję skryptu usługi HDInsight</span><span class="sxs-lookup"><span data-stu-id="804ac-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="804ac-132">`install-interactive-notebook.sh`To skrypt instalujący platformę .NET dla Apache Spark i wprowadza zmiany w oprogramowaniu Apache usługi Livy i sparkmagic.</span><span class="sxs-lookup"><span data-stu-id="804ac-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="804ac-133">Przed przesłaniem akcji skryptu do usługi HDInsight należy utworzyć i przekazać `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="804ac-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="804ac-134">Utwórz nowy plik o nazwie **Install-Interactive-Notebook.sh** na komputerze lokalnym i wklej zawartość [Install-Interactive-Notebook.sh zawartości](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span><span class="sxs-lookup"><span data-stu-id="804ac-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="804ac-135">Przekaż skrypt do [identyfikatora URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) , który jest dostępny z klastra usługi HDInsight.</span><span class="sxs-lookup"><span data-stu-id="804ac-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="804ac-136">Na przykład `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="804ac-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="804ac-137">Uruchom `install-interactive-notebook.sh` w klastrze przy użyciu [akcji skryptu HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span><span class="sxs-lookup"><span data-stu-id="804ac-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="804ac-138">Wróć do klastra HDI w Azure Portal i wybierz pozycję **Akcje skryptu** z opcji po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="804ac-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="804ac-139">Przesyłasz jedną akcję skryptu do wdrożenia platformy .NET dla Apache Spark REPL w klastrze usługi HDInsight Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="804ac-140">Użyj następujących ustawień:</span><span class="sxs-lookup"><span data-stu-id="804ac-140">Use the following settings:</span></span>

   |<span data-ttu-id="804ac-141">Właściwość</span><span class="sxs-lookup"><span data-stu-id="804ac-141">Property</span></span>  |<span data-ttu-id="804ac-142">Opis</span><span class="sxs-lookup"><span data-stu-id="804ac-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="804ac-143">Typ skryptu</span><span class="sxs-lookup"><span data-stu-id="804ac-143">Script type</span></span> | <span data-ttu-id="804ac-144">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="804ac-144">Custom</span></span> |
   | <span data-ttu-id="804ac-145">Nazwa</span><span class="sxs-lookup"><span data-stu-id="804ac-145">Name</span></span> | <span data-ttu-id="804ac-146">*Zainstaluj program .NET dla Apache Spark interaktywnego środowiska notesu*</span><span class="sxs-lookup"><span data-stu-id="804ac-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="804ac-147">Identyfikator URI skryptu bash</span><span class="sxs-lookup"><span data-stu-id="804ac-147">Bash script URI</span></span> | <span data-ttu-id="804ac-148">Identyfikator URI, do którego został przekazany `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="804ac-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="804ac-149">Typy węzłów</span><span class="sxs-lookup"><span data-stu-id="804ac-149">Node type(s)</span></span>| <span data-ttu-id="804ac-150">Kierownik i proces roboczy</span><span class="sxs-lookup"><span data-stu-id="804ac-150">Head and Worker</span></span> |
   | <span data-ttu-id="804ac-151">Parametry</span><span class="sxs-lookup"><span data-stu-id="804ac-151">Parameters</span></span> | <span data-ttu-id="804ac-152">Wersja platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="804ac-153">Możesz sprawdzić, czy program [.net ma Apache Spark wydania](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="804ac-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="804ac-154">Na przykład jeśli chcesz zainstalować program Sparkdotnet w wersji 0.6.0, może to być `0.6.0` .</span><span class="sxs-lookup"><span data-stu-id="804ac-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="804ac-155">Przejdź do następnego kroku, gdy zielony znacznik wyboru pojawia się obok stanu akcji skryptu.</span><span class="sxs-lookup"><span data-stu-id="804ac-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="804ac-156">Uruchom serwer usługi Livy</span><span class="sxs-lookup"><span data-stu-id="804ac-156">Start the Livy server</span></span>

<span data-ttu-id="804ac-157">Postępuj zgodnie z instrukcjami w sekcji [Zatrzymaj usługi Livy Server](#stop-the-livy-server) , aby **uruchomić** (zamiast **zatrzymać**) usługi Livy for Spark2 Server for hosts **hn0** and **hn1**.</span><span class="sxs-lookup"><span data-stu-id="804ac-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="804ac-158">Konfigurowanie domyślnych konfiguracji platformy Spark</span><span class="sxs-lookup"><span data-stu-id="804ac-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="804ac-159">W portalu wybierz pozycję **Przegląd**, a następnie wybierz pozycję **Strona główna Ambari**.</span><span class="sxs-lookup"><span data-stu-id="804ac-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="804ac-160">Jeśli zostanie wyświetlony monit, wprowadź poświadczenia logowania dla klastra.</span><span class="sxs-lookup"><span data-stu-id="804ac-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="804ac-161">Wybierz pozycję **Spark2** i **configs**.</span><span class="sxs-lookup"><span data-stu-id="804ac-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="804ac-162">Następnie wybierz pozycję **niestandardowe spark2 — ustawienia domyślne**.</span><span class="sxs-lookup"><span data-stu-id="804ac-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Ustawienia konfiguracji](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="804ac-164">Wybierz pozycję **Dodaj właściwość...** , aby dodać domyślne ustawienia platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Dodaj właściwość](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="804ac-166">Istnieją trzy poszczególne właściwości.</span><span class="sxs-lookup"><span data-stu-id="804ac-166">There are three individual properties.</span></span> <span data-ttu-id="804ac-167">Dodaj je pojedynczo przy użyciu typu właściwości **Text** w trybie dodawania pojedynczej właściwości.</span><span class="sxs-lookup"><span data-stu-id="804ac-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="804ac-168">Sprawdź, czy nie masz żadnych dodatkowych spacji przed ani po żadnym z kluczy/wartości.</span><span class="sxs-lookup"><span data-stu-id="804ac-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="804ac-169">**Właściwość 1**</span><span class="sxs-lookup"><span data-stu-id="804ac-169">**Property 1**</span></span>
       * <span data-ttu-id="804ac-170">Głównych&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="804ac-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="804ac-171">Wartość:`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="804ac-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="804ac-172">**Właściwość 2** Użyj wersji platformy .NET dla Apache Spark, która została uwzględniona w poprzedniej akcji skryptu.</span><span class="sxs-lookup"><span data-stu-id="804ac-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="804ac-173">Głównych&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="804ac-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="804ac-174">Wartość:`["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="804ac-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="804ac-175">**Właściwość 3**</span><span class="sxs-lookup"><span data-stu-id="804ac-175">**Property 3**</span></span>
       * <span data-ttu-id="804ac-176">Głównych&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="804ac-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="804ac-177">Wartość:`try`</span><span class="sxs-lookup"><span data-stu-id="804ac-177">Value: `try`</span></span>

   <span data-ttu-id="804ac-178">Na przykład poniższy obraz przechwytuje ustawienie do dodawania właściwości 1:</span><span class="sxs-lookup"><span data-stu-id="804ac-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Ustawienia konfiguracji](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="804ac-180">Po dodaniu trzech właściwości wybierz pozycję **Zapisz**.</span><span class="sxs-lookup"><span data-stu-id="804ac-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="804ac-181">Jeśli widzisz ekran ostrzegawczy zaleceń dotyczących konfiguracji, wybierz pozycję **nadal mimo wszystko**.</span><span class="sxs-lookup"><span data-stu-id="804ac-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="804ac-182">Uruchom ponownie składniki, których to dotyczy.</span><span class="sxs-lookup"><span data-stu-id="804ac-182">Restart affected components.</span></span>

   <span data-ttu-id="804ac-183">Po dodaniu nowych właściwości należy ponownie uruchomić składniki, na które miały wpływ zmiany.</span><span class="sxs-lookup"><span data-stu-id="804ac-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="804ac-184">W górnej części wybierz pozycję **Uruchom ponownie**, a następnie **ponownie uruchom wszystkie** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="804ac-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Ustawienia konfiguracji](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="804ac-186">Po wyświetleniu monitu wybierz pozycję **Potwierdź ponowne uruchomienie wszystkiego** , aby kontynuować, a następnie kliknij przycisk **OK** , aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="804ac-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="804ac-187">Przesyłanie zadań za pomocą notesu Jupyter</span><span class="sxs-lookup"><span data-stu-id="804ac-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="804ac-188">Po zakończeniu poprzednich kroków można teraz przesyłać zadania platformy .NET dla Apache Spark za pomocą notesów Jupyter.</span><span class="sxs-lookup"><span data-stu-id="804ac-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="804ac-189">Utwórz nowy Notes platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="804ac-190">Uruchom Notes Jupyter z klastra HDI w Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="804ac-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Jupyter Notebook uruchamiania](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="804ac-192">Następnie wybierz pozycję **Nowy**  >  **.NET Spark (C#)** , aby utworzyć Notes.</span><span class="sxs-lookup"><span data-stu-id="804ac-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="804ac-194">Przesyłanie zadań przy użyciu platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="804ac-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="804ac-195">Użyj poniższego fragmentu kodu, aby utworzyć ramkę danych:</span><span class="sxs-lookup"><span data-stu-id="804ac-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Prześlij zadanie platformy Spark](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="804ac-197">Poniższy fragment kodu służy do rejestrowania funkcji zdefiniowanej przez użytkownika (UDF) i używania UDF z ramkami danych:</span><span class="sxs-lookup"><span data-stu-id="804ac-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Prześlij zadanie platformy Spark](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="804ac-199">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="804ac-199">Next steps</span></span>

* [<span data-ttu-id="804ac-200">Wdrażanie aplikacji platformy .NET dla Apache Spark w usłudze Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="804ac-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="804ac-201">Dokumentacja usługi HDInsight</span><span class="sxs-lookup"><span data-stu-id="804ac-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
