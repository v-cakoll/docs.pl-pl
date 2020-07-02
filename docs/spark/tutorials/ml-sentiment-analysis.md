---
title: Analiza tonacji za pomocą platformy .NET dla Apache Spark i samouczka ML.NET
description: W ramach tego samouczka nauczysz się używać ML.NET z platformą .NET do Apache Spark na potrzeby analizy tonacji.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 69deb30419b98536fa309547d94f59bb266e413c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617586"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="37675-103">Samouczek: Analiza tonacji z platformą .NET dla Apache Spark i ML.NET</span><span class="sxs-lookup"><span data-stu-id="37675-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="37675-104">W tym samouczku przedstawiono, jak przeprowadzić analizę tonacjiych przeglądów online przy użyciu ML.NET i platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37675-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="37675-105">[Ml.NET](http://dot.net/ml) to bezpłatna, międzyplatformowa platforma uczenia maszynowego typu open source.</span><span class="sxs-lookup"><span data-stu-id="37675-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="37675-106">Możesz użyć ML.NET z platformą .NET dla Apache Spark do skalowania szkoleń i przewidywania algorytmów uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="37675-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="37675-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="37675-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="37675-108">Utwórz model analizy tonacji przy użyciu konstruktora modelu ML.NET w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37675-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="37675-109">Utwórz aplikację konsolową platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37675-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="37675-110">Pisanie i implementowanie funkcji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="37675-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="37675-111">Uruchom aplikację konsolową platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37675-111">Run a .NET for Apache Spark console app.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="37675-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="37675-112">Prerequisites</span></span>

* <span data-ttu-id="37675-113">Jeśli jeszcze nie opracowano aplikacji .NET for Apache Spark, Zacznij od [samouczka Wprowadzenie](get-started.md) , aby zapoznać się z podstawowymi informacjami.</span><span class="sxs-lookup"><span data-stu-id="37675-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="37675-114">Przed kontynuowaniem pracy z tym samouczkiem wykonaj wszystkie wymagania wstępne dotyczące samouczka Wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="37675-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="37675-115">Ten samouczek używa programu ML.NET model Builder (wersja zapoznawcza) — interfejsu wizualizacji dostępnego w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37675-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="37675-116">Jeśli nie masz jeszcze programu Visual Studio, możesz bezpłatnie [pobrać wersję społeczności programu Visual Studio](https://visualstudio.microsoft.com/downloads/) .</span><span class="sxs-lookup"><span data-stu-id="37675-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="37675-117">[Pobierz i zainstaluj](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET model Builder (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="37675-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="37675-118">Pobierz zestawy danych [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) i [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.</span><span class="sxs-lookup"><span data-stu-id="37675-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="37675-119">Przejrzyj dane</span><span class="sxs-lookup"><span data-stu-id="37675-119">Review the data</span></span>

<span data-ttu-id="37675-120">Zestaw danych Yelp Reviews zawiera przeglądy online Yelp dotyczące różnych usług.</span><span class="sxs-lookup"><span data-stu-id="37675-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="37675-121">Otwórz [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) i zwróć uwagę na strukturę danych.</span><span class="sxs-lookup"><span data-stu-id="37675-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="37675-122">Pierwsza kolumna zawiera tekst przeglądu, a druga kolumna zawiera wyniki tonacji.</span><span class="sxs-lookup"><span data-stu-id="37675-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="37675-123">Jeśli wynik tonacji wynosi 1, przegląd jest dodatni i jeśli wynik tonacji jest równy 0, przegląd jest ujemny.</span><span class="sxs-lookup"><span data-stu-id="37675-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="37675-124">Poniższa tabela zawiera przykładowe dane:</span><span class="sxs-lookup"><span data-stu-id="37675-124">The following table contains sample data:</span></span>

|<span data-ttu-id="37675-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="37675-125">ReviewText</span></span>|<span data-ttu-id="37675-126">Opinia</span><span class="sxs-lookup"><span data-stu-id="37675-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="37675-127">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="37675-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="37675-128">1</span><span class="sxs-lookup"><span data-stu-id="37675-128">1</span></span>|
|<span data-ttu-id="37675-129">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="37675-129">Crust is not good.</span></span>|    <span data-ttu-id="37675-130">0</span><span class="sxs-lookup"><span data-stu-id="37675-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="37675-131">Kompilowanie modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="37675-131">Build your machine learning model</span></span>

1. <span data-ttu-id="37675-132">Otwórz program Visual Studio i Utwórz nową aplikację konsolową w języku C# (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="37675-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="37675-133">Nazwij projekt *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="37675-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="37675-134">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt *MLSparkModel* .</span><span class="sxs-lookup"><span data-stu-id="37675-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="37675-135">Następnie wybierz pozycję **dodaj > Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="37675-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="37675-136">Z konstruktora modelu ML.NET wybierz kafelek scenariusz **Analiza tonacji** .</span><span class="sxs-lookup"><span data-stu-id="37675-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="37675-137">Na stronie **Dodawanie danych** Przekaż zestaw danych *yelptrain.csv* .</span><span class="sxs-lookup"><span data-stu-id="37675-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="37675-138">Wybierz pozycję *tonacji* z listy rozwijanej **kolumny do prognozowania** .</span><span class="sxs-lookup"><span data-stu-id="37675-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="37675-139">Na stronie **uczenie** Ustaw czas uczenia na *60 sekund* i wybierz pozycję **Rozpocznij szkolenie**.</span><span class="sxs-lookup"><span data-stu-id="37675-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="37675-140">Zwróć uwagę na stan szkolenia w **toku**.</span><span class="sxs-lookup"><span data-stu-id="37675-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="37675-141">Po zakończeniu szkolenia konstruktora modeli **Oceń** wyniki szkolenia.</span><span class="sxs-lookup"><span data-stu-id="37675-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="37675-142">Możesz wpisać frazy w polu tekstowym poniżej **Wypróbuj model** i wybrać pozycję **przewidywanie** , aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="37675-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="37675-143">Wybierz pozycję **kod** , a następnie wybierz pozycję **Dodaj projekty** , aby dodać model ml do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37675-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="37675-144">Zwróć uwagę, że dwa projekty są dodawane do rozwiązań: **MLSparkModelML. ConsoleApp** i **MLSparkModelML. model**.</span><span class="sxs-lookup"><span data-stu-id="37675-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="37675-145">Kliknij dwukrotnie projekt *MLSpark* C# i zwróć uwagę, że dodano następujące odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="37675-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="37675-146">tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="37675-146">Create a console app</span></span>

<span data-ttu-id="37675-147">Konstruktor modelu tworzy aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="37675-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="37675-148">Kliknij prawym przyciskiem myszy pozycję **MLSparkModelML. Console** w Eksplorator rozwiązań i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="37675-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="37675-149">Wyszukaj ciąg **Microsoft. Spark** i zainstaluj pakiet.</span><span class="sxs-lookup"><span data-stu-id="37675-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="37675-150">Program **Microsoft.ml** jest automatycznie instalowany przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="37675-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="37675-151">Utwórz SparkSession</span><span class="sxs-lookup"><span data-stu-id="37675-151">Create a SparkSession</span></span>

1. <span data-ttu-id="37675-152">Otwórz plik *program.cs* dla **MLSparkModelML. ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="37675-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="37675-153">Ten plik został automatycznie wygenerowany przez konstruktora modelu.</span><span class="sxs-lookup"><span data-stu-id="37675-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="37675-154">Usuń `using` instrukcje, zawartość metody Main () i `CreateSingleDataSample` region.</span><span class="sxs-lookup"><span data-stu-id="37675-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="37675-155">Dodaj następujące dodatkowe `using` instrukcje na początku *program.cs*:</span><span class="sxs-lookup"><span data-stu-id="37675-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="37675-156">Zmień `DATA_FILEPATH` ścieżkę na *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="37675-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="37675-157">Dodaj następujący kod do `Main` metody, aby utworzyć nowy `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="37675-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="37675-158">Sesja platformy Spark jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API Dataframe.</span><span class="sxs-lookup"><span data-stu-id="37675-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="37675-159">Wywołanie obiektu *Spark* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i Dataframe w programie.</span><span class="sxs-lookup"><span data-stu-id="37675-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="37675-160">Tworzenie ramki danych i drukowanie do konsoli</span><span class="sxs-lookup"><span data-stu-id="37675-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="37675-161">Przeczytaj dane Yelp z pliku *yelptest.csv* jako `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="37675-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="37675-162">`header`Opcje include i `inferSchema` .</span><span class="sxs-lookup"><span data-stu-id="37675-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="37675-163">`header`Opcja odczytuje pierwszy wiersz *yelptest.csv* jako nazwy kolumn, a nie dane.</span><span class="sxs-lookup"><span data-stu-id="37675-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="37675-164">`inferSchema`Opcja dla typów kolumn na podstawie danych.</span><span class="sxs-lookup"><span data-stu-id="37675-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="37675-165">Rejestrowanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="37675-165">Register a user-defined function</span></span>

<span data-ttu-id="37675-166">W aplikacjach platformy Spark można używać funkcji UDF, *zdefiniowanych przez użytkownika*w celu wykonywania obliczeń i analizy danych.</span><span class="sxs-lookup"><span data-stu-id="37675-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="37675-167">W tym samouczku użyjesz ML.NET z UDF, aby oszacować każdy Yelp przegląd.</span><span class="sxs-lookup"><span data-stu-id="37675-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="37675-168">Dodaj następujący kod do `Main` metody, aby zarejestrować funkcję UDF o nazwie `MLudf` .</span><span class="sxs-lookup"><span data-stu-id="37675-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="37675-169">Ten format UDF Pobiera ciąg Yelp jako dane wejściowe i generuje odpowiednio wartość true lub false dla wartości dodatnich lub ujemnych mową.</span><span class="sxs-lookup"><span data-stu-id="37675-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="37675-170">Używa metody *predykcyjnej ()* zdefiniowanej w późniejszym kroku.</span><span class="sxs-lookup"><span data-stu-id="37675-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="37675-171">Używanie platformy Spark SQL do wywoływania UDF</span><span class="sxs-lookup"><span data-stu-id="37675-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="37675-172">Teraz, po odczytaniu danych i dołączanej ML, Użyj języka Spark SQL, aby wywołać funkcję UDF, która będzie uruchamiać analizę tonacji na każdym wierszu ramki danych.</span><span class="sxs-lookup"><span data-stu-id="37675-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="37675-173">Dodaj następujący kod do `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="37675-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="37675-174">Create predykcyjny () — Metoda</span><span class="sxs-lookup"><span data-stu-id="37675-174">Create predict() method</span></span>

<span data-ttu-id="37675-175">Dodaj następujący kod przed `Main()` metodą.</span><span class="sxs-lookup"><span data-stu-id="37675-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="37675-176">Ten kod jest podobny do działania utworzonego przez konstruktora modelu w *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="37675-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="37675-177">Przeniesienie tej metody do konsoli ładuje model ładujący za każdym razem, gdy uruchamiasz aplikację.</span><span class="sxs-lookup"><span data-stu-id="37675-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="37675-178">Dodawanie modelu do aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="37675-178">Add the model to your console app</span></span>

<span data-ttu-id="37675-179">W Eksplorator rozwiązań Skopiuj plik *MLModel.zip* z projektu **MLSparkModelML. model** i wklej go w projekcie **MLSparkModelML. ConsoleApp** .</span><span class="sxs-lookup"><span data-stu-id="37675-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="37675-180">Odwołanie jest automatycznie dodawane do *MLSparkModelML. ConsoleApp. csproj*.</span><span class="sxs-lookup"><span data-stu-id="37675-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="37675-181">Uruchamianie kodu</span><span class="sxs-lookup"><span data-stu-id="37675-181">Run your code</span></span>

<span data-ttu-id="37675-182">Użyj `spark-submit` do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="37675-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="37675-183">Przejdź do folderu głównego aplikacji konsolowej przy użyciu wiersza polecenia i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="37675-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="37675-184">Najpierw Oczyść i Opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="37675-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="37675-185">Następnie przejdź do folderu publikowania aplikacji konsoli i uruchom następujące `spark-submit` polecenie.</span><span class="sxs-lookup"><span data-stu-id="37675-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="37675-186">Pamiętaj, aby zaktualizować polecenie za pomocą rzeczywistej ścieżki pliku JAR Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="37675-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="37675-187">Uzyskiwanie kodu</span><span class="sxs-lookup"><span data-stu-id="37675-187">Get the code</span></span>

<span data-ttu-id="37675-188">Ten samouczek jest podobny do kodu z [Analiza tonacji z przykładem danych Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) .</span><span class="sxs-lookup"><span data-stu-id="37675-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="37675-189">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="37675-189">Next steps</span></span>

<span data-ttu-id="37675-190">Przejdź do następnego artykułu, aby dowiedzieć się, jak wykonywać strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="37675-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="37675-191">Samouczek: strukturalne przesyłanie strumieniowe za pomocą platformy .NET dla Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37675-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
