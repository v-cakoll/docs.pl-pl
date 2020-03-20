---
title: Ustrukturyzowane przesyłanie strumieniowe za pomocą samouczka .NET for Apache Spark
description: W tym samouczku dowiesz się, jak używać platformy .NET for Apache Spark for Spark Structured Streaming.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186512"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="e138b-103">Samouczek: Zorganizowane przesyłanie strumieniowe z .NET dla platformy Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e138b-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="e138b-104">W tym samouczku dowiesz się, jak wywołać usługi Spark Structured Streaming przy użyciu platformy .NET dla platformy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="e138b-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="e138b-105">Spark Structured Streaming to obsługa apache Spark do przetwarzania strumieni danych w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="e138b-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="e138b-106">Przetwarzanie strumienia oznacza analizowanie danych na żywo podczas ich tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e138b-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="e138b-107">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e138b-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e138b-108">Tworzenie i uruchamianie aplikacji .NET dla aplikacji Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e138b-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="e138b-109">Tworzenie strumienia danych za pomocą netcata</span><span class="sxs-lookup"><span data-stu-id="e138b-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="e138b-110">Używanie funkcji zdefiniowanych przez użytkownika i sparksql do analizowania danych przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="e138b-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e138b-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e138b-111">Prerequisites</span></span>

<span data-ttu-id="e138b-112">Jeśli jest to twoja pierwsza aplikacja .NET dla platformy Apache Spark, zacznij od [samouczka Wprowadzenie,](get-started.md) aby zapoznać się z podstawami.</span><span class="sxs-lookup"><span data-stu-id="e138b-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e138b-113">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e138b-113">Create a console application</span></span>

1. <span data-ttu-id="e138b-114">W wierszu polecenia uruchom następujące polecenia, aby utworzyć nową aplikację konsoli:</span><span class="sxs-lookup"><span data-stu-id="e138b-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="e138b-115">Polecenie `dotnet` tworzy `new` aplikację typu `console` dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="e138b-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="e138b-116">Parametr `-o` tworzy katalog o nazwie *mySparkStreamingApp,* w którym aplikacja jest przechowywana i wypełnia go wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="e138b-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="e138b-117">Polecenie `cd mySparkStreamingApp` zmienia katalog na katalog aplikacji, który został właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="e138b-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="e138b-118">Aby użyć platformy .NET for Apache Spark w aplikacji, należy zainstalować pakiet Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="e138b-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="e138b-119">W konsoli uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e138b-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="e138b-120">Ustanawianie strumienia danych i łączenie się z nią</span><span class="sxs-lookup"><span data-stu-id="e138b-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="e138b-121">Jednym z popularnych sposobów testowania przetwarzania strumienia jest za pośrednictwem **netcat**.</span><span class="sxs-lookup"><span data-stu-id="e138b-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="e138b-122">netcat (znany również jako *nc)* pozwala na odczyt i zapis do połączeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="e138b-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="e138b-123">Nawiązujesz połączenie sieciowe z netcatem przez okno terminala.</span><span class="sxs-lookup"><span data-stu-id="e138b-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="e138b-124">Tworzenie strumienia danych za pomocą netcat</span><span class="sxs-lookup"><span data-stu-id="e138b-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="e138b-125">[Pobierz netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="e138b-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="e138b-126">Następnie wyodrębnij plik z pobierania zip i dołącz katalog wyodrębniony do zmiennej środowiskowej "PATH".</span><span class="sxs-lookup"><span data-stu-id="e138b-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="e138b-127">Aby rozpocząć nowe połączenie, otwórz nową konsolę i uruchom następujące polecenie, które łączy się z localhostem na porcie 9999.</span><span class="sxs-lookup"><span data-stu-id="e138b-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="e138b-128">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="e138b-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="e138b-129">W systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="e138b-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="e138b-130">Program Spark nasłuchuje wpisanych danych wejściowych w tym wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e138b-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="e138b-131">Tworzenie sparkSession</span><span class="sxs-lookup"><span data-stu-id="e138b-131">Create a SparkSession</span></span>

1. <span data-ttu-id="e138b-132">Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs* w *mySparkStreamingApp:*</span><span class="sxs-lookup"><span data-stu-id="e138b-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="e138b-133">Dodaj następujący kod `Main` do metody, `SparkSession`aby utworzyć nowy plik .</span><span class="sxs-lookup"><span data-stu-id="e138b-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="e138b-134">Sesja iskry jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API DataFrame.</span><span class="sxs-lookup"><span data-stu-id="e138b-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="e138b-135">Wywołanie obiektu *iskrzącego* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i DataFrame w całym programie.</span><span class="sxs-lookup"><span data-stu-id="e138b-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="e138b-136">Łączenie się ze strumieniem za pomocą readstream()</span><span class="sxs-lookup"><span data-stu-id="e138b-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="e138b-137">Metoda `ReadStream()` `DataStreamReader` zwraca, który może służyć do odczytu `DataFrame`przesyłania strumieniowego danych w jako .</span><span class="sxs-lookup"><span data-stu-id="e138b-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="e138b-138">Dołącz informacje o hoście i porcie, aby poinformować aplikację Spark, gdzie należy się spodziewać jej danych przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="e138b-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="e138b-139">Rejestrowanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e138b-139">Register a user-defined function</span></span>

<span data-ttu-id="e138b-140">W aplikacjach Spark można używać plików UDF, *funkcji zdefiniowanych przez użytkownika,* do wykonywania obliczeń i analiz danych.</span><span class="sxs-lookup"><span data-stu-id="e138b-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="e138b-141">Dodaj następujący kod `Main` do metody, aby `udfArray`zarejestrować UDF o nazwie .</span><span class="sxs-lookup"><span data-stu-id="e138b-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="e138b-142">Ten UDF przetwarza każdy ciąg odbierany z terminala netcat do produkcji tablicy, która zawiera oryginalny ciąg (zawarte w *str*), a następnie oryginalny ciąg połączony z długością oryginalnego ciągu.</span><span class="sxs-lookup"><span data-stu-id="e138b-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="e138b-143">Na przykład wejście *Hello world* w terminalu netcat tworzy tablicę, w której:</span><span class="sxs-lookup"><span data-stu-id="e138b-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="e138b-144">tablica\[0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="e138b-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="e138b-145">tablica\[1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="e138b-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="e138b-146">Użyj SparkSQL</span><span class="sxs-lookup"><span data-stu-id="e138b-146">Use SparkSQL</span></span>

<span data-ttu-id="e138b-147">Użyj SparkSQL do wykonywania różnych funkcji na danych przechowywanych w dataframe.</span><span class="sxs-lookup"><span data-stu-id="e138b-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="e138b-148">Często łączyć pliki UDF i SparkSQL, aby zastosować UDF do każdego wiersza elementu DataFrame.</span><span class="sxs-lookup"><span data-stu-id="e138b-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="e138b-149">Ten fragment kodu stosuje *udfArray* do każdej wartości w dataframe, która reprezentuje każdy ciąg odczytu z terminala netcat.</span><span class="sxs-lookup"><span data-stu-id="e138b-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="e138b-150">Zastosuj SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> metody, aby umieścić każdy wpis tablicy w swoim własnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e138b-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="e138b-151">Na koniec <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> użyj umieścić kolumny, które zostały wyprodukowane w nowej *dataframe arrayDF.*</span><span class="sxs-lookup"><span data-stu-id="e138b-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="e138b-152">Wyświetlanie strumienia</span><span class="sxs-lookup"><span data-stu-id="e138b-152">Display your stream</span></span>

<span data-ttu-id="e138b-153">Służy <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> do ustanawiania cech danych wyjściowych, takich jak drukowanie wyników na konsoli i wyświetlanie tylko najnowszych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e138b-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="e138b-154">Uruchom swój kod</span><span class="sxs-lookup"><span data-stu-id="e138b-154">Run your code</span></span>

<span data-ttu-id="e138b-155">Przetwarzanie w ustrukturyzowanym programie Spark przetwarza dane za pośrednictwem serii małych **partii.**</span><span class="sxs-lookup"><span data-stu-id="e138b-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="e138b-156">Po uruchomieniu programu wiersz polecenia, w którym nawiązano połączenie netcat, umożliwia rozpoczęcie pisania.</span><span class="sxs-lookup"><span data-stu-id="e138b-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="e138b-157">Za każdym razem, gdy po naciśnięciu klawisza Enter po wpisaniu danych w tym wierszu polecenia spark uznaje wpis za partię i uruchamia UDF.</span><span class="sxs-lookup"><span data-stu-id="e138b-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="e138b-158">Uruchamianie aplikacji za pomocą spark-submit</span><span class="sxs-lookup"><span data-stu-id="e138b-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="e138b-159">Po uruchomieniu nowej sesji netcat otwórz nowy `spark-submit` terminal i uruchom polecenie, podobne do następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e138b-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="e138b-160">Pamiętaj, aby zaktualizować powyższe polecenie za pomocą rzeczywistej ścieżki do pliku jar platformy Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="e138b-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="e138b-161">Powyższe polecenie zakłada również, że serwer netcat jest uruchomiony na porcie localhost 9999.</span><span class="sxs-lookup"><span data-stu-id="e138b-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="e138b-162">Uzyskiwanie kodu</span><span class="sxs-lookup"><span data-stu-id="e138b-162">Get the code</span></span>

<span data-ttu-id="e138b-163">W tym samouczku użyto [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) przykładu, ale istnieją trzy inne przykłady przetwarzania pełnego strumienia w usłudze GitHub:</span><span class="sxs-lookup"><span data-stu-id="e138b-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="e138b-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): liczba słów na danych przesyłanych strumieniowo z dowolnego źródła</span><span class="sxs-lookup"><span data-stu-id="e138b-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="e138b-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): liczba słów na danych z logiką okna</span><span class="sxs-lookup"><span data-stu-id="e138b-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="e138b-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): liczba słów na dane przesyłane strumieniowo z Platformy Kafka</span><span class="sxs-lookup"><span data-stu-id="e138b-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="e138b-167">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e138b-167">Next steps</span></span>

<span data-ttu-id="e138b-168">Przejdź do następnego artykułu, aby dowiedzieć się, jak wdrożyć aplikację platformy .NET for Apache Spark w witrynie Databricks.</span><span class="sxs-lookup"><span data-stu-id="e138b-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e138b-169">Samouczek: Wdrażanie aplikacji .NET dla platformy Spark apache w databricks</span><span class="sxs-lookup"><span data-stu-id="e138b-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
