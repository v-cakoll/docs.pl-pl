---
title: Wprowadzenie do platformy .NET for Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla platformy Spark przy użyciu platformy .NET Core w systemach Windows, MacOS i Ubuntu.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187546"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="01c0d-103">Samouczek: Wprowadzenie do platformy .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="01c0d-104">W tym samouczku dowiesz się, jak uruchomić aplikację .NET for Apache Spark przy użyciu platformy .NET Core w systemach Windows, MacOS i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="01c0d-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="01c0d-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="01c0d-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="01c0d-106">Przygotowanie środowiska dla platformy .NET dla platformy Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="01c0d-107">Napisz swoją pierwszą aplikację .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="01c0d-108">Tworzenie i uruchamianie prostej aplikacji .NET dla platformy Spark Apache</span><span class="sxs-lookup"><span data-stu-id="01c0d-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="01c0d-109">Przygotowywanie środowiska</span><span class="sxs-lookup"><span data-stu-id="01c0d-109">Prepare your environment</span></span>

<span data-ttu-id="01c0d-110">Przed rozpoczęciem pisania aplikacji należy skonfigurować niektóre zależności wymagane.</span><span class="sxs-lookup"><span data-stu-id="01c0d-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="01c0d-111">Jeśli można `dotnet`uruchomić `java` `mvn`, `spark-shell` , , ze środowiska wiersza polecenia, a następnie środowisko jest już przygotowane i można przejść do następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="01c0d-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="01c0d-112">Jeśli nie można uruchomić żadnych lub wszystkich poleceń, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="01c0d-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="01c0d-113">1. Zainstaluj .NET</span><span class="sxs-lookup"><span data-stu-id="01c0d-113">1. Install .NET</span></span>

<span data-ttu-id="01c0d-114">Aby rozpocząć tworzenie aplikacji platformy .NET, należy pobrać i zainstalować zestaw .NET SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="01c0d-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="01c0d-115">Pobierz i zainstaluj [pakiet .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span><span class="sxs-lookup"><span data-stu-id="01c0d-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="01c0d-116">Zainstalowanie zestawu SDK powoduje dodanie paska `dotnet` narzędzi do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="01c0d-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="01c0d-117">Po zainstalowaniu pliku .NET Core SDK otwórz nowy wiersz `dotnet`polecenia lub terminal i uruchom program .</span><span class="sxs-lookup"><span data-stu-id="01c0d-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="01c0d-118">Jeśli polecenie uruchamia i drukuje informacje o tym, jak korzystać z dotnet, można przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="01c0d-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="01c0d-119">Jeśli pojawi `'dotnet' is not recognized as an internal or external command` się błąd, przed uruchomieniem polecenia należy otworzyć **nowy** wiersz polecenia lub terminal.</span><span class="sxs-lookup"><span data-stu-id="01c0d-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="01c0d-120">2. Zainstaluj język Java</span><span class="sxs-lookup"><span data-stu-id="01c0d-120">2. Install Java</span></span>

<span data-ttu-id="01c0d-121">Zainstaluj [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) dla Windows i MacOS lub [OpenJDK 8](https://openjdk.java.net/install/) dla Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="01c0d-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="01c0d-122">Wybierz odpowiednią wersję dla danego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="01c0d-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="01c0d-123">Na przykład wybierz **jdk-8u201-windows-x64.exe** dla komputera x64 z systemem Windows (jak pokazano poniżej) lub **jdk-8u231-macosx-x64.dmg** dla systemu MacOS.</span><span class="sxs-lookup"><span data-stu-id="01c0d-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="01c0d-124">Następnie użyj polecenia, `java` aby zweryfikować instalację.</span><span class="sxs-lookup"><span data-stu-id="01c0d-124">Then, use the command `java` to verify the installation.</span></span>

![Pobieranie w języku Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="01c0d-126">3. Zainstaluj oprogramowanie do kompresji</span><span class="sxs-lookup"><span data-stu-id="01c0d-126">3. Install compression software</span></span>

<span data-ttu-id="01c0d-127">Apache Spark jest pobierany jako skompresowany plik .tgz.</span><span class="sxs-lookup"><span data-stu-id="01c0d-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="01c0d-128">Użyj programu ekstrakcji, takiego jak [7-Zip](https://www.7-zip.org/) lub [WinZip,](https://www.winzip.com/)aby wyodrębnić plik.</span><span class="sxs-lookup"><span data-stu-id="01c0d-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="01c0d-129">4. Zainstaluj Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-129">4. Install Apache Spark</span></span>

<span data-ttu-id="01c0d-130">[Pobierz i zainstaluj Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="01c0d-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="01c0d-131">Musisz wybrać wersję 2.3.\* lub 2.4.0, 2.4.1, 2.4.3 lub 2.4.4 (.NET dla Apache Spark nie jest kompatybilny z innymi wersjami Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="01c0d-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="01c0d-132">Polecenia użyte w poniższych krokach zakładają, że [pobrano i zainstalowano Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="01c0d-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="01c0d-133">Jeśli chcesz użyć innej wersji, zastąp **2.4.1** odpowiednim numerem wersji.</span><span class="sxs-lookup"><span data-stu-id="01c0d-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="01c0d-134">Następnie wyodrębnij plik **.tar** i pliki Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="01c0d-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="01c0d-135">Aby wyodrębnić zagnieżdżony plik **.tar:**</span><span class="sxs-lookup"><span data-stu-id="01c0d-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="01c0d-136">Znajdź pobrany plik **spark-2.4.1-bin-hadoop2.7.tgz.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="01c0d-137">Kliknij prawym przyciskiem myszy na plik i wybierz **7-Zip -> Wyodrębnij tutaj**.</span><span class="sxs-lookup"><span data-stu-id="01c0d-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="01c0d-138">**spark-2.4.1-bin-hadoop2.7.tar** jest tworzony obok pobranego pliku **.tgz.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="01c0d-139">Aby wyodrębnić pliki Platformy Spark Apache:</span><span class="sxs-lookup"><span data-stu-id="01c0d-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="01c0d-140">Kliknij prawym przyciskiem myszy na **spark-2.4.1-bin-hadoop2.7.tar** i wybierz **7-Zip -> Wyodrębnij pliki ...**</span><span class="sxs-lookup"><span data-stu-id="01c0d-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="01c0d-141">Wprowadź **C:\bin** w polu **Wyodrębnij do.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="01c0d-142">Wyewidencjonuj pole wyboru poniżej pola **Wyodrębnij do.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="01c0d-143">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="01c0d-143">Select **OK**.</span></span>
* <span data-ttu-id="01c0d-144">Pliki Platformy Spark Apache są wyodrębniane do folderu C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="01c0d-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Zainstaluj iskrę](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="01c0d-146">Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania programu Apache Spark w systemie **Windows:**</span><span class="sxs-lookup"><span data-stu-id="01c0d-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="01c0d-147">Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania apache Spark w **systemach MacOS** i **Ubuntu:**</span><span class="sxs-lookup"><span data-stu-id="01c0d-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="01c0d-148">Po zainstalowaniu wszystkiego i ustawieniu zmiennych środowiskowych otwórz **nowy** wiersz polecenia lub terminal i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01c0d-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="01c0d-149">Jeśli polecenie uruchamia i drukuje informacje o wersji, można przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="01c0d-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="01c0d-150">Jeśli zostanie `'spark-submit' is not recognized as an internal or external command` wyświetlony błąd, upewnij się, że otwarto **nowy** wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="01c0d-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="01c0d-151">5. Zainstaluj .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="01c0d-152">Pobierz zwolnienie [microsoft.spark.worker](https://github.com/dotnet/spark/releases) z platformy .NET dla platformy .NET dla platformy Akwizycjowej Usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="01c0d-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="01c0d-153">Na przykład, jeśli korzystasz z komputera z systemem Windows i planujesz używać programu .NET Core, [pobierz wersję netcoreapp3.1 dla systemu Windows](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span><span class="sxs-lookup"><span data-stu-id="01c0d-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="01c0d-154">Aby wyodrębnić plik Microsoft.Spark.Worker:</span><span class="sxs-lookup"><span data-stu-id="01c0d-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="01c0d-155">Znajdź pobrany plik **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="01c0d-156">Kliknij prawym przyciskiem myszy i wybierz **7-Zip -> Wyodrębnij pliki...**.</span><span class="sxs-lookup"><span data-stu-id="01c0d-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="01c0d-157">Wprowadź **C:\bin** w polu **Wyodrębnij do.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="01c0d-158">Wyewidencjonuj pole wyboru poniżej pola **Wyodrębnij do.**</span><span class="sxs-lookup"><span data-stu-id="01c0d-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="01c0d-159">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="01c0d-159">Select **OK**.</span></span>

![Instalowanie platformy .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="01c0d-161">6. Zainstaluj WinUtils (tylko windows)</span><span class="sxs-lookup"><span data-stu-id="01c0d-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="01c0d-162">.NET for Apache Spark wymaga, aby winUtils został zainstalowany obok platformy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="01c0d-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="01c0d-163">[Pobierz winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="01c0d-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="01c0d-164">Następnie skopiuj winutils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="01c0d-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="01c0d-165">Jeśli używasz innej wersji programu Hadoop, która jest opisywana na końcu nazwy folderu instalacji Platformy Spark, [wybierz wersję programu WinUtils,](https://github.com/steveloughran/winutils) która jest zgodna z Twoją wersją programu Hadoop.</span><span class="sxs-lookup"><span data-stu-id="01c0d-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="01c0d-166">7. Ustawianie DOTNET_WORKER_DIR i sprawdzanie zależności</span><span class="sxs-lookup"><span data-stu-id="01c0d-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="01c0d-167">Uruchom jedno z następujących poleceń, aby ustawić zmienną środowiskową, `DOTNET_WORKER_DIR` która jest używana przez aplikacje platformy .NET do lokalizowania platformy .NET dla platformy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="01c0d-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="01c0d-168">W **systemie Windows**utwórz nową [zmienną](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` środowiskową i ustaw ją na katalogu, `C:\bin\Microsoft.Spark.Worker\`w którym pobrano i wyodrębniłeś plik Microsoft.Spark.Worker (na przykład ).</span><span class="sxs-lookup"><span data-stu-id="01c0d-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="01c0d-169">W **systemie MacOS**utwórz `export DOTNET_WORKER_DIR <your_path>` nową zmienną środowiskową za pomocą i ustaw ją w katalogu, w którym pobrano i wyodrębniłeś plik Microsoft.Spark.Worker (na przykład *~/bin/Microsoft.Spark.Worker/*).</span><span class="sxs-lookup"><span data-stu-id="01c0d-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="01c0d-170">W **ubuntu**utwórz [nową zmienną](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` środowiskową i ustaw ją na katalogu, w którym pobrano i wyodrębniłeś plik Microsoft.Spark.Worker (na przykład *~/bin/Microsoft.Spark.Worker*).</span><span class="sxs-lookup"><span data-stu-id="01c0d-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="01c0d-171">Na koniec należy dokładnie sprawdzić, `dotnet` `java`czy `mvn` `spark-shell` można uruchomić , , z wiersza polecenia przed przejściem do następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="01c0d-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="01c0d-172">Napisz aplikację .NET dla Aplikacji Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="01c0d-173">1. Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="01c0d-173">1. Create a console app</span></span>

<span data-ttu-id="01c0d-174">W wierszu polecenia lub terminalu uruchom następujące polecenia, aby utworzyć nową aplikację konsoli:</span><span class="sxs-lookup"><span data-stu-id="01c0d-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="01c0d-175">Polecenie `dotnet` tworzy `new` aplikację typu `console` dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="01c0d-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="01c0d-176">Parametr `-o` tworzy katalog o nazwie *mySparkApp,* w którym aplikacja jest przechowywana i wypełnia go wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="01c0d-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="01c0d-177">Polecenie `cd mySparkApp` zmienia katalog na katalog aplikacji, który został właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="01c0d-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="01c0d-178">2. Zainstaluj pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="01c0d-178">2. Install NuGet package</span></span>

<span data-ttu-id="01c0d-179">Aby użyć platformy .NET for Apache Spark w aplikacji, należy zainstalować pakiet Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="01c0d-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="01c0d-180">W wierszu polecenia lub terminalu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01c0d-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="01c0d-181">3. Koduj swoją aplikację</span><span class="sxs-lookup"><span data-stu-id="01c0d-181">3. Code your app</span></span>

<span data-ttu-id="01c0d-182">Otwórz *Program.cs* w programie Visual Studio Code lub dowolnym edytorze tekstu i zastąp cały kod następującymi funkcjami:</span><span class="sxs-lookup"><span data-stu-id="01c0d-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="01c0d-183">4. Tworzenie i dodawanie pliku danych</span><span class="sxs-lookup"><span data-stu-id="01c0d-183">4. Create and add a data file</span></span>

<span data-ttu-id="01c0d-184">Otwórz wiersz polecenia lub terminal i przejdź do folderu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01c0d-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="01c0d-185">Aplikacja przetwarza plik zawierający wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="01c0d-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="01c0d-186">Utwórz plik *input.txt* w katalogu *mySparkApp* zawierający następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="01c0d-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="01c0d-187">Uruchamianie aplikacji .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="01c0d-188">Uruchom następujące polecenie, aby utworzyć aplikację:</span><span class="sxs-lookup"><span data-stu-id="01c0d-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="01c0d-189">Uruchom następujące polecenie, aby przesłać aplikację do uruchomienia w programie Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="01c0d-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="01c0d-190">To polecenie zakłada, że pobrano apache spark i dodano go do `spark-submit`zmiennej środowiskowej PATH, aby móc używać .</span><span class="sxs-lookup"><span data-stu-id="01c0d-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="01c0d-191">W przeciwnym razie należy użyć pełnej ścieżki (na przykład *C:\bin\apache-spark\bin\spark-submit* lub *~/spark/bin/spark-submit*).</span><span class="sxs-lookup"><span data-stu-id="01c0d-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="01c0d-192">Po uruchomieniu aplikacji dane liczby wyrazów pliku *input.txt* są zapisywane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="01c0d-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="01c0d-193">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="01c0d-193">Congratulations!</span></span> <span data-ttu-id="01c0d-194">Pomyślnie została nagrana i uruchomiono aplikację .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="01c0d-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="01c0d-195">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="01c0d-195">Next steps</span></span>

<span data-ttu-id="01c0d-196">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="01c0d-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="01c0d-197">Przygotowanie środowiska systemu Windows dla platformy .NET dla platformy Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="01c0d-198">Napisz swoją pierwszą aplikację .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="01c0d-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="01c0d-199">Tworzenie i uruchamianie prostej aplikacji .NET dla platformy Spark Apache</span><span class="sxs-lookup"><span data-stu-id="01c0d-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="01c0d-200">Aby zobaczyć film wyjaśniający powyższe kroki, sprawdź [serię wideo .NET for Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="01c0d-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="01c0d-201">Sprawdź stronę zasobów, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="01c0d-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="01c0d-202">.NET dla zasobów platformy Spark apache</span><span class="sxs-lookup"><span data-stu-id="01c0d-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
