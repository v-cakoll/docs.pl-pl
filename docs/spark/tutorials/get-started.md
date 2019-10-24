---
title: Wprowadzenie do platformy .NET dla Apache Spark
description: Dowiedz się, jak uruchomić aplikację .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 19efc8412d834d73069c61e1cc1ccd9e5eb8593b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774375"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="17218-103">Samouczek: Rozpoczynanie pracy z platformą .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="17218-104">W tym samouczku przedstawiono sposób uruchamiania aplikacji platformy .NET dla Apache Spark przy użyciu platformy .NET Core w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="17218-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="17218-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="17218-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="17218-106">Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="17218-107">Pobierz **pakiet Microsoft. Spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="17218-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="17218-108">Kompilowanie i uruchamianie prostej aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="17218-109">Przygotowywanie środowiska</span><span class="sxs-lookup"><span data-stu-id="17218-109">Prepare your environment</span></span>

<span data-ttu-id="17218-110">Przed rozpoczęciem upewnij się, że można uruchomić `dotnet`, `java`, `mvn`, `spark-shell` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17218-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="17218-111">Jeśli środowisko jest już przygotowane, możesz przejść do następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="17218-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="17218-112">Jeśli nie można uruchomić żadnego lub wszystkich poleceń, wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="17218-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="17218-113">Pobierz i zainstaluj [zestaw .NET Core 2.1 x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="17218-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="17218-114">Zainstalowanie zestawu SDK dodaje `dotnet` łańcucha narzędzi do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="17218-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="17218-115">Aby zweryfikować instalację, użyj polecenia programu PowerShell `dotnet --version`.</span><span class="sxs-lookup"><span data-stu-id="17218-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="17218-116">Zainstaluj [program Visual studio 2017](https://www.visualstudio.com/downloads/) lub [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) z najnowszymi aktualizacjami.</span><span class="sxs-lookup"><span data-stu-id="17218-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="17218-117">Możesz użyć społeczności, Professional lub Enterprise.</span><span class="sxs-lookup"><span data-stu-id="17218-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="17218-118">Wersja społeczności jest bezpłatna.</span><span class="sxs-lookup"><span data-stu-id="17218-118">The Community version is free.</span></span>

   <span data-ttu-id="17218-119">Podczas instalacji wybierz następujące obciążenia:</span><span class="sxs-lookup"><span data-stu-id="17218-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="17218-120">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="17218-120">.NET desktop development</span></span>
          * <span data-ttu-id="17218-121">Wszystkie wymagane składniki</span><span class="sxs-lookup"><span data-stu-id="17218-121">All required components</span></span>
          * <span data-ttu-id="17218-122">Narzędzia programistyczne .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="17218-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="17218-123">Programowanie dla wielu platform w środowisku .NET Core</span><span class="sxs-lookup"><span data-stu-id="17218-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="17218-124">Wszystkie wymagane składniki</span><span class="sxs-lookup"><span data-stu-id="17218-124">All required components</span></span>

3. <span data-ttu-id="17218-125">Zainstaluj [środowisko Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span><span class="sxs-lookup"><span data-stu-id="17218-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="17218-126">Wybierz odpowiednią wersję systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="17218-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="17218-127">Na przykład wybierz **JDK-8u201-Windows-x64. exe** dla komputera z systemem Windows x64.</span><span class="sxs-lookup"><span data-stu-id="17218-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="17218-128">Aby zweryfikować instalację, użyj polecenia programu PowerShell `java -version`.</span><span class="sxs-lookup"><span data-stu-id="17218-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="17218-129">Zainstaluj program [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi).</span><span class="sxs-lookup"><span data-stu-id="17218-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="17218-130">Pobierz [Apache Maven 3.6.2](http://mirror.metrocast.net/apache/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="17218-130">Download [Apache Maven 3.6.2](http://mirror.metrocast.net/apache/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.zip).</span></span>
    * <span data-ttu-id="17218-131">Wyodrębnij do katalogu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="17218-131">Extract to a local directory.</span></span> <span data-ttu-id="17218-132">Na przykład `c:\bin\apache-maven-3.6.2\`.</span><span class="sxs-lookup"><span data-stu-id="17218-132">For example, `c:\bin\apache-maven-3.6.2\`.</span></span>
    * <span data-ttu-id="17218-133">Dodaj Maven Apache do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="17218-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="17218-134">W przypadku wyodrębnienia do `c:\bin\apache-maven-3.6.2\` należy dodać `c:\bin\apache-maven-3.6.2\bin` do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="17218-134">If you extracted to `c:\bin\apache-maven-3.6.2\`, you would add `c:\bin\apache-maven-3.6.2\bin` to your PATH.</span></span>
    * <span data-ttu-id="17218-135">Aby zweryfikować instalację, użyj polecenia programu PowerShell `mvn -version`.</span><span class="sxs-lookup"><span data-stu-id="17218-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="17218-136">Zainstaluj [Apache Spark 2.3 +](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="17218-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="17218-137">Apache Spark 2.4 + nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="17218-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="17218-138">Pobierz [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) i wyodrębnij go do folderu lokalnego przy użyciu narzędzia, takiego jak [7-zip](https://www.7-zip.org/) lub [WinZip](https://www.winzip.com/).</span><span class="sxs-lookup"><span data-stu-id="17218-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="17218-139">Na przykład można wyodrębnić go do `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="17218-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="17218-140">Dodaj Apache Spark do [zmiennej środowiskowej PATH](https://www.java.com/en/download/help/path.xml).</span><span class="sxs-lookup"><span data-stu-id="17218-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="17218-141">W przypadku wyodrębnienia do `c:\bin\spark-2.3.2-bin-hadoop2.7\` należy dodać do ścieżki `c:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span><span class="sxs-lookup"><span data-stu-id="17218-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="17218-142">Dodaj [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) o nazwie `SPARK_HOME`.</span><span class="sxs-lookup"><span data-stu-id="17218-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="17218-143">W przypadku wyodrębnienia do `C:\bin\spark-2.3.2-bin-hadoop2.7\` należy użyć **wartości zmiennej**`C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="17218-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="17218-144">Sprawdź, czy można uruchomić `spark-shell` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17218-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="17218-145">Skonfiguruj [WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="17218-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="17218-146">Pobierz plik binarny **winutils. exe** z [repozytorium winutils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="17218-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="17218-147">Wybierz wersję usługi Hadoop, z którą została skompilowana dystrybucja platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="17218-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="17218-148">Na przykład użyjesz usługi **Hadoop-2.7.1** dla **platformy Spark 2.3.2**.</span><span class="sxs-lookup"><span data-stu-id="17218-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="17218-149">Wersja usługi Hadoop znajduje się na końcu nazwy folderu instalacji platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="17218-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="17218-150">Zapisz plik binarny **winutils. exe** w wybranym katalogu.</span><span class="sxs-lookup"><span data-stu-id="17218-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="17218-151">Na przykład `c:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="17218-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="17218-152">Ustaw `HADOOP_HOME`, aby odzwierciedlał katalog z **winutils. exe** bez `bin`.</span><span class="sxs-lookup"><span data-stu-id="17218-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="17218-153">Na przykład `c:\hadoop`.</span><span class="sxs-lookup"><span data-stu-id="17218-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="17218-154">Ustaw zmienną środowiskową PATH do uwzględnienia `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="17218-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="17218-155">Przed przejściem do następnej sekcji Sprawdź, czy można uruchomić `dotnet`, `java`, `mvn`, `spark-shell` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17218-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="17218-156">Pobierz wersję Microsoft. Spark. Worker</span><span class="sxs-lookup"><span data-stu-id="17218-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="17218-157">Pobierz wersję [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) z strony .net for Apache Spark Release releases na komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="17218-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="17218-158">Na przykład możesz pobrać go do ścieżki, `c:\bin\Microsoft.Spark.Worker\`.</span><span class="sxs-lookup"><span data-stu-id="17218-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="17218-159">Utwórz [nową zmienną środowiskową](https://www.java.com/en/download/help/path.xml) o nazwie `DOTNET_WORKER_DIR` i ustaw ją na katalog, w którym został pobrany i wyodrębniony element **Microsoft. Spark. Worker**.</span><span class="sxs-lookup"><span data-stu-id="17218-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="17218-160">Na przykład `c:\bin\Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="17218-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="17218-161">Klonowanie repozytorium programu .NET dla Apache Spark GitHub</span><span class="sxs-lookup"><span data-stu-id="17218-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="17218-162">Użyj następującego polecenia [GitBash](https://gitforwindows.org/) , aby sklonować Apache Spark repozytorium programu .NET do maszyny.</span><span class="sxs-lookup"><span data-stu-id="17218-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="17218-163">Napisz aplikację platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="17218-164">Otwórz **program Visual Studio** i przejdź do **pliku > utwórz nowy projekt > aplikacji konsolowej (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="17218-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="17218-165">Nadaj aplikacji nazwę **HelloSpark**.</span><span class="sxs-lookup"><span data-stu-id="17218-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="17218-166">Zainstaluj [pakiet NuGet Microsoft. Spark](https://www.nuget.org/profiles/spark).</span><span class="sxs-lookup"><span data-stu-id="17218-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="17218-167">Aby uzyskać więcej informacji na temat instalowania pakietów NuGet, zobacz [różne sposoby instalowania pakietu NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span><span class="sxs-lookup"><span data-stu-id="17218-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="17218-168">W **Eksplorator rozwiązań**Otwórz **program.cs** i Napisz następujący C# kod:</span><span class="sxs-lookup"><span data-stu-id="17218-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="17218-169">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="17218-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="17218-170">Uruchamianie aplikacji platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="17218-171">Otwórz program **PowerShell** i zmień katalog na folder, w którym jest przechowywana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="17218-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="17218-172">Utwórz plik o nazwie **ludzie. JSON** z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="17218-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="17218-173">Użyj następującego polecenia programu PowerShell, aby uruchomić aplikację:</span><span class="sxs-lookup"><span data-stu-id="17218-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="17218-174">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="17218-174">Congratulations!</span></span> <span data-ttu-id="17218-175">Pomyślnie utworzono i uruchomiono aplikację .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="17218-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="17218-176">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="17218-176">Next steps</span></span>

<span data-ttu-id="17218-177">W tym samouczku przedstawiono sposób wykonywania tych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="17218-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="17218-178">Przygotuj środowisko systemu Windows dla platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="17218-179">Pobierz **pakiet Microsoft. Spark. Worker**</span><span class="sxs-lookup"><span data-stu-id="17218-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="17218-180">Kompilowanie i uruchamianie prostej aplikacji .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="17218-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="17218-181">Zapoznaj się ze stroną zasobów, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="17218-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="17218-182">Platforma .NET dla Apache Spark zasobów</span><span class="sxs-lookup"><span data-stu-id="17218-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
