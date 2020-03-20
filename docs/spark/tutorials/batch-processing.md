---
title: Przetwarzanie wsadowe za pomocą samouczka .NET for Apache Spark
description: Dowiedz się, jak wykonać przetwarzanie wsadowe przy użyciu platformy .NET for Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187551"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="5e6ab-103">Samouczek: Wykonaj przetwarzanie wsadowe za pomocą platformy .NET dla platformy Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5e6ab-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="5e6ab-104">W tym samouczku dowiesz się, jak wykonać przetwarzanie wsadowe przy użyciu platformy .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="5e6ab-105">Przetwarzanie wsadowe jest przekształcenie danych w spoczynku, co oznacza, że dane źródłowe zostały już załadowane do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="5e6ab-106">Przetwarzanie wsadowe jest zazwyczaj wykonywane za generowane za wiele dużych, płaskich zestawów danych, które muszą być przygotowane do dalszej analizy.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="5e6ab-107">Przetwarzanie dzienników i magazynowanie danych są typowymi scenariuszami przetwarzania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="5e6ab-108">W tym scenariuszu można analizować informacje o projektach GitHub, takie jak liczba czasu różnych projektów zostały rozwidlione lub jak niedawno projekty zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="5e6ab-109">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5e6ab-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5e6ab-110">Tworzenie i uruchamianie aplikacji .NET dla aplikacji Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5e6ab-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="5e6ab-111">Odczytywanie danych w ramce DataFrame i przygotowywanie ich do analizy</span><span class="sxs-lookup"><span data-stu-id="5e6ab-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="5e6ab-112">Przetwarzanie danych przy użyciu programu Spark SQL</span><span class="sxs-lookup"><span data-stu-id="5e6ab-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e6ab-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5e6ab-113">Prerequisites</span></span>

<span data-ttu-id="5e6ab-114">Jeśli po raz pierwszy używasz platformy .NET for Apache Spark, zapoznaj się z samouczkiem [Wprowadzenie do platformy .NET for Apache Spark,](../tutorials/get-started.md) aby dowiedzieć się, jak przygotować środowisko i uruchomić pierwszą aplikację .NET dla platformy Spark apache.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="5e6ab-115">Pobieranie przykładowych danych</span><span class="sxs-lookup"><span data-stu-id="5e6ab-115">Download the sample data</span></span>

<span data-ttu-id="5e6ab-116">[GHTorrent](http://ghtorrent.org/) monitoruje wszystkie publiczne zdarzenia Usługi GitHub, takie jak informacje o projektach, zatwierdzeniach i obserwatorach, i przechowuje zdarzenia i ich strukturę w bazach danych.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="5e6ab-117">Dane zbierane w różnych okresach są dostępne jako archiwa do pobrania.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="5e6ab-118">Ponieważ pliki zrzutu są bardzo duże, w tym przewodniku użyto [obciętej wersji pliku zrzutu,](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) który można pobrać z gitHub.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="5e6ab-119">Zestaw danych GHTorrent jest dystrybuowany w ramach systemu podwójnego licencjonowania[(Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="5e6ab-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="5e6ab-120">Do celów niekomercyjnych (w tym między innymi do celów edukacyjnych, badawczych lub osobistych) zestaw danych jest rozpowszechniany na [licencji CC-BY-SA.](https://creativecommons.org/licenses/by-sa/4.0/)</span><span class="sxs-lookup"><span data-stu-id="5e6ab-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5e6ab-121">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="5e6ab-121">Create a console application</span></span>

1. <span data-ttu-id="5e6ab-122">W wierszu polecenia uruchom następujące polecenia, aby utworzyć nową aplikację konsoli:</span><span class="sxs-lookup"><span data-stu-id="5e6ab-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="5e6ab-123">Polecenie `dotnet` tworzy `new` aplikację typu `console` dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="5e6ab-124">Parametr `-o` tworzy katalog o nazwie *mySparkBatchApp,* w którym aplikacja jest przechowywana i wypełnia go wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="5e6ab-125">Polecenie `cd mySparkBatchApp` zmienia katalog na katalog aplikacji, który został właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="5e6ab-126">Aby użyć platformy .NET for Apache Spark w aplikacji, należy zainstalować pakiet Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="5e6ab-127">W konsoli uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5e6ab-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="5e6ab-128">Tworzenie sparkSession</span><span class="sxs-lookup"><span data-stu-id="5e6ab-128">Create a SparkSession</span></span>

1. <span data-ttu-id="5e6ab-129">Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs* w *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="5e6ab-130">Dodaj następujący kod do obszaru nazw projektu.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="5e6ab-131">*s_referenceData* jest używany w dalszej części programu do filtrowania na podstawie daty.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="5e6ab-132">Dodaj następujący kod wewnątrz main metody, aby ustanowić nowy SparkSession.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="5e6ab-133">SparkSession jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API DataFrame.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="5e6ab-134">Wywołując `spark` obiekt, można uzyskać dostęp do funkcji Platformy Spark i DataFrame w całym programie.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="5e6ab-135">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="5e6ab-135">Prepare the data</span></span>

1. <span data-ttu-id="5e6ab-136">Odczyt pliku wejściowego `DataFrame`do pliku , który jest rozproszoną kolekcją danych zorganizowanych w nazwane kolumny.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="5e6ab-137">Kolumny danych można ustawić za <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="5e6ab-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="5e6ab-138">Użyj <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> tej metody, aby wyświetlić dane w dataframe.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="5e6ab-139">Pamiętaj, aby zaktualizować ścieżkę pliku CSV do lokalizacji pobranych danych GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. <span data-ttu-id="5e6ab-140">Użyj <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> metody, aby upuścić wiersze z wartościami NA (null) i metodę usuwania <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> niektórych kolumn z danych.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="5e6ab-141">Pomaga to zapobiegać błędom podczas próby analizowania danych lub kolumn null, które nie są istotne dla ostatecznej analizy.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="5e6ab-142">Analizowanie danych</span><span class="sxs-lookup"><span data-stu-id="5e6ab-142">Analyze the data</span></span>

<span data-ttu-id="5e6ab-143">Spark SQL umożliwia wykonywanie wywołań SQL na danych.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="5e6ab-144">Często łączy się funkcje zdefiniowane przez użytkownika i program Spark SQL w celu zastosowania funkcji zdefiniowanej przez użytkownika do wszystkich wierszy elementu DataFrame.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="5e6ab-145">Można w szczególności `spark.Sql` wywołać naśladować standardowe wywołania SQL widoczne w innych typach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="5e6ab-146">Można również wywołać <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> metody, takie jak i w szczególności łączyć, filtrować i wykonywać obliczenia na danych.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="5e6ab-147">Celem tej aplikacji jest uzyskanie pewnych spostrzeżeń na temat danych projektów GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="5e6ab-148">Dodaj do programu następujące fragmenty kodu, aby analizować dane.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="5e6ab-149">Dodaj następujący blok kodu znajduje liczbę razy każdy język został rozwidleczony.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="5e6ab-150">Po pierwsze dane są pogrupowane według języka.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-150">First, the data is grouped by language.</span></span> <span data-ttu-id="5e6ab-151">Następnie pobierana jest średnia liczba wideł z każdego języka.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="5e6ab-152">Dodaj następujący blok kodu, aby zamówić średnią liczbę widelców w malejącej kolejności, aby zobaczyć, które języki są najbardziej rozwidli.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="5e6ab-153">Oznacza to, że największa liczba wideł pojawi się jako pierwsza.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="5e6ab-154">Następny blok kodu pokazuje, jak niedawno projekty zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="5e6ab-155">Rejestrujesz nową funkcję zdefiniowaną przez użytkownika o nazwie *MyUDF* i porównujesz ją z *datą, s_referenceDate*, która została zadeklarowana na początku samouczka.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="5e6ab-156">Data dla każdego projektu jest porównywana z datą odwołania.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="5e6ab-157">Następnie program Spark SQL jest używany do wywoływania UDF w każdym wierszu danych do analizowania każdego projektu w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. <span data-ttu-id="5e6ab-158">Zadzwoń, `spark.Stop()` aby zakończyć SparkSession.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="5e6ab-159">Uruchamianie aplikacji za pomocą spark-submit</span><span class="sxs-lookup"><span data-stu-id="5e6ab-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="5e6ab-160">Użyj następującego polecenia, aby utworzyć aplikację .NET:</span><span class="sxs-lookup"><span data-stu-id="5e6ab-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="5e6ab-161">Uruchom aplikację `spark-submit`za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="5e6ab-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="5e6ab-162">Pamiętaj, aby zaktualizować następujące polecenie za pomocą rzeczywistych ścieżek do pliku jar platformy Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="5e6ab-163">Uzyskiwanie kodu</span><span class="sxs-lookup"><span data-stu-id="5e6ab-163">Get the code</span></span>

<span data-ttu-id="5e6ab-164">Możesz zobaczyć [pełne rozwiązanie](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) na GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5e6ab-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5e6ab-165">Next steps</span></span>

<span data-ttu-id="5e6ab-166">Przejdź do następnego artykułu, aby dowiedzieć się, jak przetwarzać dane strumieniowe za pomocą platformy .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="5e6ab-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5e6ab-167">Samouczek: Zorganizowane przesyłanie strumieniowe z .NET dla platformy Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5e6ab-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
