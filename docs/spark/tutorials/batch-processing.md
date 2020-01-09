---
title: Przetwarzanie wsadowe za pomocą platformy .NET dla Apache Spark — samouczek
description: Dowiedz się, jak przeprowadzić przetwarzanie wsadowe przy użyciu platformy .NET dla Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: bd91fb401b9beb6ae74c4599b25e43284473f8b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75466414"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="f1bd1-103">Samouczek: wykonywanie przetwarzania wsadowego za pomocą platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f1bd1-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="f1bd1-104">W tym samouczku dowiesz się, jak przeprowadzić przetwarzanie wsadowe przy użyciu platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="f1bd1-105">Przetwarzanie wsadowe to transformacja danych magazynowanych, co oznacza, że dane źródłowe zostały już załadowane do magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span> 

<span data-ttu-id="f1bd1-106">Przetwarzanie wsadowe jest zwykle wykonywane nad dużymi, płaskimi zestawami danych, które muszą zostać przygotowane do dalszej analizy.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="f1bd1-107">Przetwarzanie dzienników i magazynowanie danych to typowe scenariusze przetwarzania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="f1bd1-108">W tym scenariuszu analizujesz informacje o projektach GitHub, takich jak liczba różnych projektów przewidzianych do przetworzenia lub czas ich aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span> 

<span data-ttu-id="f1bd1-109">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f1bd1-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f1bd1-110">Utwórz i Uruchom platformę .NET dla aplikacji Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f1bd1-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="f1bd1-111">Odczytywanie danych do ramki Dataframe i przygotowywanie jej do analizy</span><span class="sxs-lookup"><span data-stu-id="f1bd1-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="f1bd1-112">Przetwarzanie danych przy użyciu platformy Spark SQL</span><span class="sxs-lookup"><span data-stu-id="f1bd1-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1bd1-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f1bd1-113">Prerequisites</span></span> 

<span data-ttu-id="f1bd1-114">Jeśli korzystasz z platformy .NET dla Apache Spark, zapoznaj się z samouczkiem wprowadzenie do [platformy .NET dla Apache Spark](../tutorials/get-started.md) , aby dowiedzieć się, jak przygotować środowisko i uruchomić pierwszą aplikację .net for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="f1bd1-115">Pobieranie przykładowych danych</span><span class="sxs-lookup"><span data-stu-id="f1bd1-115">Download the sample data</span></span>

<span data-ttu-id="f1bd1-116">[GHTorrent](http://ghtorrent.org/) monitoruje wszystkie publiczne zdarzenia usługi GitHub, takie jak informacje o projektach, zatwierdzeń i Obserwatorach, a także przechowuje zdarzenia i ich strukturę w bazach danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="f1bd1-117">Dane zbierane przez różne okresy są dostępne jako archiwa do pobrania.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="f1bd1-118">Ponieważ pliki zrzutu są bardzo duże, ten przewodnik używa [obciętej wersji pliku zrzutu](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) , który można pobrać z witryny GitHub.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bd1-119">Zestaw danych GHTorrent jest dystrybuowany w ramach podwójnego planu licencjonowania ([Creative Commons Attribution +](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="f1bd1-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="f1bd1-120">W przypadku niekomercyjnych celów (w tym, ale nie ograniczonych do, edukacyjnych, badawczych lub prywatnych), zestaw danych jest dystrybuowany w ramach [licencji CC-by-sa](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="f1bd1-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f1bd1-121">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="f1bd1-121">Create a console application</span></span>

1. <span data-ttu-id="f1bd1-122">W wierszu polecenia Uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:</span><span class="sxs-lookup"><span data-stu-id="f1bd1-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="f1bd1-123">`dotnet` polecenie tworzy `new` aplikacji typu `console`.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="f1bd1-124">Parametr `-o` tworzy katalog o nazwie *mySparkBatchApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="f1bd1-125">`cd mySparkBatchApp` polecenie zmienia katalog na właśnie utworzony katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="f1bd1-126">Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="f1bd1-127">W konsoli programu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f1bd1-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="f1bd1-128">Utwórz SparkSession</span><span class="sxs-lookup"><span data-stu-id="f1bd1-128">Create a SparkSession</span></span>

1. <span data-ttu-id="f1bd1-129">Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* w *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="f1bd1-130">Dodaj następujący kod do przestrzeni nazw projektu.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="f1bd1-131">*s_referenceData* jest używany później w programie do filtrowania na podstawie daty.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="f1bd1-132">Dodaj następujący kod wewnątrz metody Main, aby określić nowy SparkSession.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="f1bd1-133">SparkSession jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API Dataframe.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="f1bd1-134">Wywołując obiekt `spark`, można uzyskać dostęp do funkcji Spark i Dataframe w całym programie.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="f1bd1-135">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="f1bd1-135">Prepare the data</span></span>

1. <span data-ttu-id="f1bd1-136">Odczytaj plik wejściowy do `DataFrame`, czyli rozproszonej kolekcji danych zorganizowanych w nazwanych kolumn.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="f1bd1-137">Możesz ustawić kolumny dla danych za pomocą <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="f1bd1-138">Użyj metody <xref:Microsoft.Spark.Sql.DataFrame.Show%2A>, aby wyświetlić dane w ramce Dataframe.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="f1bd1-139">Pamiętaj, aby zaktualizować ścieżkę pliku CSV do lokalizacji pobranych danych usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="f1bd1-140">Użyj metody <xref:Microsoft.Spark.Sql.DataFrame.Na%2A>, aby porzucić wiersze z wartościami NA (null), i metodę <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A>, aby usunąć niektóre kolumny z danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="f1bd1-141">Pozwala to zapobiec błędom, jeśli próbujesz analizować dane o wartości null lub kolumny, które nie są istotne dla ostatniej analizy.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="f1bd1-142">Analizowanie danych</span><span class="sxs-lookup"><span data-stu-id="f1bd1-142">Analyze the data</span></span>

<span data-ttu-id="f1bd1-143">Platforma Spark SQL umożliwia wykonywanie wywołań SQL na danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="f1bd1-144">Często istnieje możliwość łączenia funkcji zdefiniowanych przez użytkownika i platformy Spark SQL w celu zastosowania funkcji zdefiniowanej przez użytkownika do wszystkich wierszy ramki danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="f1bd1-145">Możesz wywoływać `spark.Sql`, aby naśladować standardowe wywołania SQL widoczne w innych typach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="f1bd1-146">Możesz również wywołać metody, takie jak <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> i <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A>, aby w sposób umożliwiał łączenie, filtrowanie i wykonywanie obliczeń na danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="f1bd1-147">Celem tej aplikacji jest uzyskanie szczegółowych informacji o danych projektów usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="f1bd1-148">Dodaj następujące fragmenty kodu do programu w celu przeanalizowania danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="f1bd1-149">Dodaj następujący blok kodu Znajdź liczbę przypadków, w których każdy język został przerozwidleni.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="f1bd1-150">Najpierw dane są pogrupowane według języka.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-150">First, the data is grouped by language.</span></span> <span data-ttu-id="f1bd1-151">Następnie jest wykonywana średnia liczba rozwidleniów z każdego języka.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="f1bd1-152">Dodaj następujący blok kodu w celu uporządkowania oredniej liczby rozwidleniów w kolejności malejącej, aby zobaczyć, które języki są najbardziej rozwidlenie.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="f1bd1-153">Oznacza to, że największa liczba rozwidleniów zostanie wyświetlona jako pierwsza.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show(); 
   ```

1. <span data-ttu-id="f1bd1-154">Następny blok kodu pokazuje, jak ostatnio projekty zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="f1bd1-155">Należy zarejestrować nową funkcję zdefiniowaną przez użytkownika o nazwie *MyUDF* i porównać ją z datą, *s_referenceDate*, która została zadeklarowana na początku samouczka.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="f1bd1-156">Data dla każdego projektu jest porównywana z datą odwołania.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="f1bd1-157">Następnie program Spark SQL jest używany do wywołania funkcji UDF w każdym wierszu danych w celu przeanalizowania każdego projektu w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="f1bd1-158">Wywołaj `spark.Stop()`, aby zakończyć SparkSession.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="f1bd1-159">Korzystanie z platformy Spark — przesyłanie w celu uruchomienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="f1bd1-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="f1bd1-160">Użyj następującego polecenia, aby skompilować aplikację .NET:</span><span class="sxs-lookup"><span data-stu-id="f1bd1-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="f1bd1-161">Uruchom aplikację za pomocą `spark-submit`.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="f1bd1-162">Pamiętaj, aby zaktualizować następujące polecenie z rzeczywistymi ścieżkami do pliku JAR Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="f1bd1-163">Uzyskaj kod</span><span class="sxs-lookup"><span data-stu-id="f1bd1-163">Get the code</span></span>

<span data-ttu-id="f1bd1-164">Możesz zobaczyć [pełne rozwiązanie](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f1bd1-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f1bd1-165">Next steps</span></span>

<span data-ttu-id="f1bd1-166">Przejdź do następnego artykułu, aby dowiedzieć się, jak przetwarzać dane przesyłane strumieniowo przy użyciu platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="f1bd1-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f1bd1-167">Samouczek: strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="f1bd1-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
