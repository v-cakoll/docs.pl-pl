---
title: Tworzenie strukturalnego przesyłania strumieniowego za pomocą platformy .NET dla Apache Spark — samouczek
description: W ramach tego samouczka nauczysz się używać platformy .NET do Apache Spark na potrzeby przesyłania strumieniowego platformy Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 5420fe081db1704d7af647e8c88826c1bcf614d9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617846"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="a3d8a-103">Samouczek: strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a3d8a-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="a3d8a-104">W tym samouczku pokazano, jak wywoływać strukturalne przesyłanie strumieniowe platformy Spark przy użyciu platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="a3d8a-105">Przetwarzanie strumieni danych w czasie rzeczywistym jest obsługiwane Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="a3d8a-106">Przetwarzanie strumieniowe oznacza analizowanie danych na żywo w miarę ich produkcji.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="a3d8a-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a3d8a-108">Utwórz i Uruchom platformę .NET dla aplikacji Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a3d8a-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a3d8a-109">Tworzenie strumienia danych za pomocą netcat</span><span class="sxs-lookup"><span data-stu-id="a3d8a-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="a3d8a-110">Korzystanie z funkcji zdefiniowanych przez użytkownika i SparkSQL do analizowania danych przesyłanych strumieniowo</span><span class="sxs-lookup"><span data-stu-id="a3d8a-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="a3d8a-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a3d8a-111">Prerequisites</span></span>

<span data-ttu-id="a3d8a-112">Jeśli jest to pierwsza aplikacja .NET dla Apache Spark, Zacznij od [samouczka Wprowadzenie](get-started.md) , aby zapoznać się z podstawowymi informacjami.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a3d8a-113">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a3d8a-113">Create a console application</span></span>

1. <span data-ttu-id="a3d8a-114">W wierszu polecenia Uruchom następujące polecenia, aby utworzyć nową aplikację konsolową:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="a3d8a-115">`dotnet`Polecenie tworzy `new` aplikację typu `console` .</span><span class="sxs-lookup"><span data-stu-id="a3d8a-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="a3d8a-116">`-o`Parametr tworzy katalog o nazwie *mySparkStreamingApp* , w którym jest przechowywana aplikacja i wypełnia je wymaganymi plikami.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a3d8a-117">`cd mySparkStreamingApp`Polecenie zmienia katalog na właśnie utworzony katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="a3d8a-118">Aby używać platformy .NET do Apache Spark w aplikacji, zainstaluj pakiet Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="a3d8a-119">W konsoli programu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="a3d8a-120">Ustanawianie strumienia danych i nawiązywanie z nim połączenia</span><span class="sxs-lookup"><span data-stu-id="a3d8a-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="a3d8a-121">Jednym z popularnych sposobów testowania przetwarzania strumienia jest użycie **netcat**.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="a3d8a-122">netcat (znany również jako *NC*) umożliwia odczytywanie i zapisywanie połączeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="a3d8a-123">Nawiązywane jest połączenie sieciowe z netcat za pomocą okna terminalu.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="a3d8a-124">Tworzenie strumienia danych za pomocą netcat</span><span class="sxs-lookup"><span data-stu-id="a3d8a-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="a3d8a-125">[Pobierz netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="a3d8a-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="a3d8a-126">Następnie wyodrębnij plik z pliku zip i Dołącz wyodrębniony katalog do zmiennej środowiskowej "PATH".</span><span class="sxs-lookup"><span data-stu-id="a3d8a-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="a3d8a-127">Aby rozpocząć nowe połączenie, Otwórz nową konsolę i uruchom następujące polecenie, które nawiązuje połączenie z hostem localhost na porcie 9999.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="a3d8a-128">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="a3d8a-129">W systemie Linux:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="a3d8a-130">Program Spark nasłuchuje danych wejściowych wpisywanych w tym wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="a3d8a-131">Utwórz SparkSession</span><span class="sxs-lookup"><span data-stu-id="a3d8a-131">Create a SparkSession</span></span>

1. <span data-ttu-id="a3d8a-132">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* w *mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="a3d8a-133">Dodaj następujący kod do `Main` metody, aby utworzyć nowy `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="a3d8a-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="a3d8a-134">Sesja platformy Spark jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API Dataframe.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="a3d8a-135">Wywołanie obiektu *Spark* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i Dataframe w programie.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="a3d8a-136">Łączenie ze strumieniem za pomocą ReadStream ()</span><span class="sxs-lookup"><span data-stu-id="a3d8a-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="a3d8a-137">`ReadStream()`Metoda zwraca metodę `DataStreamReader` , która może służyć do odczytu danych przesyłanych strumieniowo w jako `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="a3d8a-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="a3d8a-138">Dołącz informacje o hoście i porcie, aby określić, gdzie aplikacja platformy Spark ma oczekiwać, że dane przesyłane strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="a3d8a-139">Rejestrowanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="a3d8a-139">Register a user-defined function</span></span>

<span data-ttu-id="a3d8a-140">W aplikacjach platformy Spark można używać funkcji UDF, *zdefiniowanych przez użytkownika*w celu wykonywania obliczeń i analizy danych.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="a3d8a-141">Dodaj następujący kod do `Main` metody, aby zarejestrować funkcję UDF o nazwie `udfArray` .</span><span class="sxs-lookup"><span data-stu-id="a3d8a-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="a3d8a-142">Ten format UDF przetwarza każdy ciąg otrzymany od terminalu netcat, aby utworzyć tablicę, która zawiera oryginalny ciąg (zawarty w *str*), a następnie oryginalny ciąg połączony z długością oryginalnego ciągu.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="a3d8a-143">Na przykład wprowadzenie do usługi *Hello World* w terminalu netcat tworzy tablicę, w której:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="a3d8a-144">Tablica \[ 0] = Hello World</span><span class="sxs-lookup"><span data-stu-id="a3d8a-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="a3d8a-145">Tablica \[ 1] = Hello World 11</span><span class="sxs-lookup"><span data-stu-id="a3d8a-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="a3d8a-146">Użyj SparkSQL</span><span class="sxs-lookup"><span data-stu-id="a3d8a-146">Use SparkSQL</span></span>

<span data-ttu-id="a3d8a-147">Użyj SparkSQL do wykonywania różnych funkcji na danych przechowywanych w ramce Dataframe.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="a3d8a-148">Często należy połączyć UDF i SparkSQL, aby zastosować UDF do każdego wiersza ramki danych.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="a3d8a-149">Ten fragment kodu stosuje *udfArray* do każdej wartości w ramce Dataframe, która reprezentuje każdy ciąg odczytywany z terminala netcat.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="a3d8a-150">Zastosuj metodę SparkSQL, <xref:Microsoft.Spark.Sql.Functions.Explode%2A> Aby umieścić każdy wpis tablicy w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="a3d8a-151">Na koniec użyj, <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> Aby umieścić kolumny, które zostały utworzone w nowej ramce Dataframe *arrayDF.*</span><span class="sxs-lookup"><span data-stu-id="a3d8a-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="a3d8a-152">Wyświetlanie strumienia</span><span class="sxs-lookup"><span data-stu-id="a3d8a-152">Display your stream</span></span>

<span data-ttu-id="a3d8a-153">Służy <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> do ustalenia charakterystyki danych wyjściowych, takich jak drukowanie wyników do konsoli i wyświetlanie tylko najnowszych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="a3d8a-154">Uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="a3d8a-154">Run your code</span></span>

<span data-ttu-id="a3d8a-155">Strukturalne przesyłanie strumieniowe w usłudze Spark przetwarza dane przez serię małych **partii**.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="a3d8a-156">Po uruchomieniu programu w wierszu polecenia, w którym ustanawiane jest połączenie netcat, można zacząć pisać.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="a3d8a-157">Za każdym razem, gdy naciśniesz klawisz Enter po wpisaniu danych w tym wierszu polecenia, platforma Spark traktuje wpis jako zadanie wsadowe i uruchomi UDF.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="a3d8a-158">Korzystanie z platformy Spark — przesyłanie w celu uruchomienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3d8a-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="a3d8a-159">Po uruchomieniu nowej sesji netcat Otwórz nowy terminal i uruchom `spark-submit` polecenie, podobnie jak następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="a3d8a-160">Pamiętaj, aby zaktualizować powyższe polecenie z rzeczywistą ścieżką do pliku JAR Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="a3d8a-161">Powyższe polecenie zakłada również, że serwer netcat jest uruchomiony na porcie lokalnym hosta 9999.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="a3d8a-162">Uzyskiwanie kodu</span><span class="sxs-lookup"><span data-stu-id="a3d8a-162">Get the code</span></span>

<span data-ttu-id="a3d8a-163">Ten samouczek używa przykładu [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , ale istnieją trzy inne przykłady przetwarzania pełnego strumienia w witrynie GitHub:</span><span class="sxs-lookup"><span data-stu-id="a3d8a-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="a3d8a-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): liczba wyrazów dla danych przesyłanych strumieniowo z dowolnego źródła</span><span class="sxs-lookup"><span data-stu-id="a3d8a-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="a3d8a-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): liczba wyrazów dla danych z logiką okna</span><span class="sxs-lookup"><span data-stu-id="a3d8a-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="a3d8a-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): liczba wyrazów dla danych przesyłanych strumieniowo z Kafka</span><span class="sxs-lookup"><span data-stu-id="a3d8a-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3d8a-167">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a3d8a-167">Next steps</span></span>

<span data-ttu-id="a3d8a-168">Przejdź do następnego artykułu, aby dowiedzieć się, jak wdrożyć aplikację .NET dla Apache Spark w usłudze datakostki.</span><span class="sxs-lookup"><span data-stu-id="a3d8a-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a3d8a-169">Samouczek: wdrażanie aplikacji .NET dla Apache Spark w kostkach</span><span class="sxs-lookup"><span data-stu-id="a3d8a-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
