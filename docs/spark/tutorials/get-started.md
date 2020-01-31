---
title: Wprowadzenie do platformy .NET dla Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743203"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="b4948-103">Samouczek: Rozpoczynanie pracy z platformą .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="b4948-104">W tym samouczku przedstawiono sposób uruchamiania aplikacji platformy .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="b4948-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="b4948-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b4948-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="b4948-106">Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="b4948-107">Napisz swoją pierwszą aplikację .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="b4948-108">Kompiluj i uruchamiaj prostą aplikację platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="b4948-109">Przygotowywanie środowiska</span><span class="sxs-lookup"><span data-stu-id="b4948-109">Prepare your environment</span></span>

<span data-ttu-id="b4948-110">Przed rozpoczęciem pisania aplikacji należy skonfigurować niektóre zależności wymagane wstępnie.</span><span class="sxs-lookup"><span data-stu-id="b4948-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="b4948-111">Jeśli można uruchomić `dotnet`, `java`, `mvn``spark-shell` ze środowiska wiersza polecenia, środowisko jest już przygotowane i można przejść do następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b4948-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="b4948-112">Jeśli nie można uruchomić żadnego lub wszystkich poleceń, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="b4948-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="b4948-113">1. Zainstaluj platformę .NET</span><span class="sxs-lookup"><span data-stu-id="b4948-113">1. Install .NET</span></span>

<span data-ttu-id="b4948-114">Aby rozpocząć tworzenie aplikacji platformy .NET, należy pobrać i zainstalować zestaw .NET SDK (Software Development Kit).</span><span class="sxs-lookup"><span data-stu-id="b4948-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="b4948-115">Pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="b4948-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="b4948-116">Zainstalowanie zestawu SDK dodaje `dotnet` łańcucha narzędzi do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b4948-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="b4948-117">Po zainstalowaniu zestaw .NET Core SDK Otwórz nowy wiersz polecenia i uruchom `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="b4948-117">Once you've installed the .NET Core SDK, open a new command prompt and run `dotnet`.</span></span>

<span data-ttu-id="b4948-118">Jeśli polecenie jest uruchamiane i drukuje informacje o sposobach korzystania z programu dotnet, można przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="b4948-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="b4948-119">Jeśli wystąpi błąd `'dotnet' is not recognized as an internal or external command`, przed uruchomieniem polecenia upewnij się, że otwarto **Nowy** wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="b4948-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="b4948-120">2. Zainstaluj środowisko Java</span><span class="sxs-lookup"><span data-stu-id="b4948-120">2. Install Java</span></span>

<span data-ttu-id="b4948-121">Zainstaluj [środowisko Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="b4948-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

<span data-ttu-id="b4948-122">Wybierz odpowiednią wersję systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b4948-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="b4948-123">Na przykład wybierz **JDK-8u201-Windows-x64. exe** dla komputera z systemem Windows x64.</span><span class="sxs-lookup"><span data-stu-id="b4948-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span> <span data-ttu-id="b4948-124">Następnie użyj `java` polecenia, aby sprawdzić poprawność instalacji.</span><span class="sxs-lookup"><span data-stu-id="b4948-124">Then, use the command `java` to verify the installation.</span></span>

![Pobieranie w języku Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a><span data-ttu-id="b4948-126">3. Zainstaluj 7-zip</span><span class="sxs-lookup"><span data-stu-id="b4948-126">3. Install 7-zip</span></span>

<span data-ttu-id="b4948-127">Apache Spark jest pobierany jako skompresowany plik TGZ.</span><span class="sxs-lookup"><span data-stu-id="b4948-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="b4948-128">Użyj programu wyodrębniania, takiego jak 7-zip, aby wyodrębnić plik.</span><span class="sxs-lookup"><span data-stu-id="b4948-128">Use an extraction program, like 7-zip, to extract the file.</span></span>

* <span data-ttu-id="b4948-129">Odwiedź stronę [7 — pobieranie plików zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="b4948-129">Visit [7-Zip downloads](https://www.7-zip.org/).</span></span>
* <span data-ttu-id="b4948-130">W pierwszej tabeli na stronie Wybierz pobieranie 32-bitowe x86 lub 64-bit x64, w zależności od używanego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b4948-130">In the first table on the page, select the 32-bit x86 or 64-bit x64 download, depending on your operating system.</span></span>
* <span data-ttu-id="b4948-131">Po zakończeniu pobierania uruchom Instalatora.</span><span class="sxs-lookup"><span data-stu-id="b4948-131">When the download completes, run the installer.</span></span>

![Pobieranie 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a><span data-ttu-id="b4948-133">4. Zainstaluj Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-133">4. Install Apache Spark</span></span>

<span data-ttu-id="b4948-134">[Pobierz i zainstaluj Apache Spark](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="b4948-134">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="b4948-135">Należy wybrać jedną z wersji 2,3. \* lub 2.4.0, 2.4.1, 2.4.3 lub 2.4.4 (.NET dla Apache Spark nie jest zgodna z innymi wersjami Apache Spark).</span><span class="sxs-lookup"><span data-stu-id="b4948-135">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="b4948-136">W poniższych krokach przyjęto założenie, że [pobrano i zainstalowano Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span><span class="sxs-lookup"><span data-stu-id="b4948-136">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="b4948-137">Jeśli chcesz użyć innej wersji, Zastąp wartość **2.4.1** odpowiednim numerem wersji.</span><span class="sxs-lookup"><span data-stu-id="b4948-137">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="b4948-138">Następnie wyodrębnij plik **. tar** i pliki Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b4948-138">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="b4948-139">Aby wyodrębnić zagnieżdżony plik **tar** :</span><span class="sxs-lookup"><span data-stu-id="b4948-139">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="b4948-140">Znajdź pobrany plik **Spark-2.4.1-bin-Hadoop 2.7. tgz** .</span><span class="sxs-lookup"><span data-stu-id="b4948-140">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="b4948-141">Kliknij prawym przyciskiem myszy plik i wybierz **7-zip-> Wyodrębnij tutaj**.</span><span class="sxs-lookup"><span data-stu-id="b4948-141">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="b4948-142">**Spark-2.4.1-bin-Hadoop 2.7. tar** jest tworzony obok pobranego pliku **. tgz** .</span><span class="sxs-lookup"><span data-stu-id="b4948-142">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="b4948-143">Aby wyodrębnić pliki Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="b4948-143">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="b4948-144">Kliknij prawym przyciskiem myszy **Spark-2.4.1-bin-Hadoop 2.7. tar** i wybierz **7-zip-> Wyodrębnianie plików...**</span><span class="sxs-lookup"><span data-stu-id="b4948-144">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="b4948-145">Wprowadź **C:\Bin** w polu **Wyodrębnij do** .</span><span class="sxs-lookup"><span data-stu-id="b4948-145">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="b4948-146">Usuń zaznaczenie pola wyboru pod polem **Wyodrębnij do** .</span><span class="sxs-lookup"><span data-stu-id="b4948-146">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="b4948-147">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4948-147">Select **OK**.</span></span>
* <span data-ttu-id="b4948-148">Pliki Apache Spark są wyodrębniane do C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="b4948-148">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Zainstaluj platformę Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="b4948-150">Uruchom następujące polecenia, aby ustawić zmienne środowiskowe używane do lokalizowania Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="b4948-150">Run the following commands to set the environment variables used to locate Apache Spark:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="b4948-151">Po zainstalowaniu wszystkiego i ustawieniu zmiennych środowiskowych Otwórz **Nowy** wiersz polecenia i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b4948-151">Once you've installed everything and set your environment variables, open a **new** command prompt and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="b4948-152">Jeśli polecenie jest uruchamiane i drukuje informacje o wersji, można przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="b4948-152">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="b4948-153">Jeśli wystąpi błąd `'spark-submit' is not recognized as an internal or external command`, upewnij się, że otwarto **Nowy** wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="b4948-153">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="b4948-154">5. Zainstaluj program .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-154">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="b4948-155">Pobierz wydanie [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) z platformy .net dla Apache Spark GitHub.</span><span class="sxs-lookup"><span data-stu-id="b4948-155">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="b4948-156">Na przykład jeśli korzystasz z komputera z systemem Windows i planujesz korzystać z platformy .NET Core, [Pobierz wydanie systemu Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span><span class="sxs-lookup"><span data-stu-id="b4948-156">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp2.1 release](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span></span>

<span data-ttu-id="b4948-157">Aby wyodrębnić pakiet Microsoft. Spark. Worker:</span><span class="sxs-lookup"><span data-stu-id="b4948-157">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="b4948-158">Znajdź pobrany plik **Microsoft. Spark. Worker. netcoreapp 2.1. win-x64-0.6.0. zip** .</span><span class="sxs-lookup"><span data-stu-id="b4948-158">Locate the **Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="b4948-159">Kliknij prawym przyciskiem myszy i wybierz **7-zip-> Wyodrębnianie plików.** ...</span><span class="sxs-lookup"><span data-stu-id="b4948-159">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="b4948-160">Wprowadź **C:\Bin** w polu **Wyodrębnij do** .</span><span class="sxs-lookup"><span data-stu-id="b4948-160">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="b4948-161">Usuń zaznaczenie pola wyboru pod polem **Wyodrębnij do** .</span><span class="sxs-lookup"><span data-stu-id="b4948-161">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="b4948-162">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4948-162">Select **OK**.</span></span>

![Zainstaluj platformę .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a><span data-ttu-id="b4948-164">6. Zainstaluj WinUtils</span><span class="sxs-lookup"><span data-stu-id="b4948-164">6. Install WinUtils</span></span>

<span data-ttu-id="b4948-165">Platforma .NET dla Apache Spark wymaga zainstalowania WinUtils razem z Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b4948-165">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="b4948-166">[Pobierz winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="b4948-166">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="b4948-167">Następnie skopiuj WinUtils do **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span><span class="sxs-lookup"><span data-stu-id="b4948-167">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="b4948-168">Jeśli używasz innej wersji usługi Hadoop, która ma adnotację na końcu nazwy folderu instalacji platformy Spark, [Wybierz wersję WinUtils](https://github.com/steveloughran/winutils) zgodną z wersją usługi Hadoop.</span><span class="sxs-lookup"><span data-stu-id="b4948-168">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="b4948-169">7. Ustaw DOTNET_WORKER_DIR i sprawdź zależności</span><span class="sxs-lookup"><span data-stu-id="b4948-169">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="b4948-170">Uruchom następujące polecenie, aby ustawić zmienną środowiskową `DOTNET_WORKER_DIR`, która jest używana przez aplikacje platformy .NET do lokalizowania programu .NET dla Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="b4948-170">Run the following command to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark:</span></span>

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

<span data-ttu-id="b4948-171">Na koniec sprawdź, czy można uruchomić `dotnet`, `java`, `mvn``spark-shell` z poziomu wiersza polecenia przed przejściem do następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b4948-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="b4948-172">Napisz aplikację platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="b4948-173">1. Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="b4948-173">1. Create a console app</span></span>

<span data-ttu-id="b4948-174">W wierszu polecenia Uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:</span><span class="sxs-lookup"><span data-stu-id="b4948-174">In your command prompt, run the following commands to create a new console application:</span></span>

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="b4948-175">`dotnet` polecenie tworzy `new` aplikacji typu `console`.</span><span class="sxs-lookup"><span data-stu-id="b4948-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="b4948-176">Parametr `-o` tworzy katalog o nazwie *mySparkApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="b4948-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="b4948-177">`cd mySparkApp` polecenie zmienia katalog na właśnie utworzony katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4948-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="b4948-178">2. Zainstaluj pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="b4948-178">2. Install NuGet package</span></span>

<span data-ttu-id="b4948-179">Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="b4948-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="b4948-180">W wierszu polecenia Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b4948-180">In your command prompt, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a><span data-ttu-id="b4948-181">3. kod aplikacji</span><span class="sxs-lookup"><span data-stu-id="b4948-181">3. Code your app</span></span>

<span data-ttu-id="b4948-182">Otwórz *program.cs* w Visual Studio Code lub dowolnym edytorze tekstów i Zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="b4948-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
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

### <a name="4-add-data-file"></a><span data-ttu-id="b4948-183">4. Dodaj plik danych</span><span class="sxs-lookup"><span data-stu-id="b4948-183">4. Add data file</span></span>

<span data-ttu-id="b4948-184">Aplikacja przetwarza plik zawierający wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="b4948-184">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="b4948-185">Utwórz plik *Input. txt* w katalogu *mySparkApp* , zawierający następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="b4948-185">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="b4948-186">Uruchamianie aplikacji platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-186">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="b4948-187">Uruchom następujące polecenie, aby skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="b4948-187">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="b4948-188">Uruchom następujące polecenie, aby przesłać aplikację do uruchamiania na Apache Spark:</span><span class="sxs-lookup"><span data-stu-id="b4948-188">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. <span data-ttu-id="b4948-189">Gdy aplikacja zostanie uruchomiona, dane zliczania plików *wejściowych. txt* są zapisywane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="b4948-189">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="b4948-190">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="b4948-190">Congratulations!</span></span> <span data-ttu-id="b4948-191">Pomyślnie utworzono i uruchomiono aplikację .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="b4948-191">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b4948-192">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b4948-192">Next steps</span></span>

<span data-ttu-id="b4948-193">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b4948-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="b4948-194">Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-194">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="b4948-195">Napisz swoją pierwszą aplikację .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-195">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="b4948-196">Kompiluj i uruchamiaj prostą aplikację platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b4948-196">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="b4948-197">Aby wyświetlić film wideo z objaśnieniem powyższych kroków, Zaewidencjonuj [serie wideo dla programu .net for Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span><span class="sxs-lookup"><span data-stu-id="b4948-197">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="b4948-198">Zapoznaj się ze stroną zasobów, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="b4948-198">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b4948-199">Platforma .NET dla Apache Spark zasobów</span><span class="sxs-lookup"><span data-stu-id="b4948-199">.NET for Apache Spark Resources</span></span>](../resources/index.md)
