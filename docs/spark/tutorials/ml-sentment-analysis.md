---
title: Analiza tonacji za pomocą platformy .NET dla platformy Apache Spark i samouczka ML.NET
description: W tym samouczku dowiesz się, jak używać ML.NET z .NET dla platformy Apache Spark do analizy tonacji.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345342"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="3dd87-103">Samouczek: Analiza tonacji za pomocą platformy .NET dla platformy Spark i ML.NET</span><span class="sxs-lookup"><span data-stu-id="3dd87-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="3dd87-104">Ten samouczek uczy, jak to zrobić analiza tonacji opinii online przy użyciu ML.NET i .NET dla Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3dd87-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="3dd87-105">[ML.NET](http://dot.net/ml) jest bezpłatną, wieloplatformową platformą uczenia maszynowego typu open source.</span><span class="sxs-lookup"><span data-stu-id="3dd87-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="3dd87-106">ML.NET z .NET for Apache Spark można użyć do skalowania szkolenia i przewidywania algorytmów uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="3dd87-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="3dd87-107">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3dd87-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="3dd87-108">Tworzenie modelu analizy tonacji przy użyciu ML.NET kreatora modeli w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3dd87-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="3dd87-109">Utwórz aplikację konsoli .NET dla platformy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3dd87-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="3dd87-110">Napisz i zaimplementuj funkcję zdefiniowaną przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3dd87-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="3dd87-111">Uruchom aplikację konsoli .NET for Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3dd87-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3dd87-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3dd87-112">Prerequisites</span></span>

* <span data-ttu-id="3dd87-113">Jeśli nie zostały opracowane .NET dla aplikacji Platformy Apache Spark przed, należy rozpocząć od [wprowadzenie samouczek,](get-started.md) aby zapoznać się z podstawami.</span><span class="sxs-lookup"><span data-stu-id="3dd87-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="3dd87-114">Wypełnij wszystkie wymagania wstępne samouczka Wprowadzenie przed kontynuowaniem tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="3dd87-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="3dd87-115">W tym samouczku użyto ML.NET Programu Model Builder (preview), interfejsu wizualnego dostępnego w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3dd87-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="3dd87-116">Jeśli nie masz jeszcze programu Visual Studio, możesz [pobrać wersję społecznościową programu Visual Studio](https://visualstudio.microsoft.com/downloads/) za darmo.</span><span class="sxs-lookup"><span data-stu-id="3dd87-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="3dd87-117">[Pobieranie i instalowanie](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Kreator modeli (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="3dd87-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="3dd87-118">Pobierz zestawy danych [recenzji yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) i [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.</span><span class="sxs-lookup"><span data-stu-id="3dd87-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="3dd87-119">Przejrzyj dane</span><span class="sxs-lookup"><span data-stu-id="3dd87-119">Review the data</span></span>

<span data-ttu-id="3dd87-120">Zestaw danych opinii Yelp zawiera opinie online Yelp o różnych usługach.</span><span class="sxs-lookup"><span data-stu-id="3dd87-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="3dd87-121">Otwórz [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) i zwróć uwagę na strukturę danych.</span><span class="sxs-lookup"><span data-stu-id="3dd87-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="3dd87-122">Pierwsza kolumna zawiera tekst recenzji, a druga zawiera wyniki tonacji.</span><span class="sxs-lookup"><span data-stu-id="3dd87-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="3dd87-123">Jeśli wynik tonacji wynosi 1, recenzja jest pozytywna, a wynik tonacji wynosi 0, ocena jest negatywna.</span><span class="sxs-lookup"><span data-stu-id="3dd87-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="3dd87-124">Poniższa tabela zawiera przykładowe dane:</span><span class="sxs-lookup"><span data-stu-id="3dd87-124">The following table contains sample data:</span></span>

|<span data-ttu-id="3dd87-125">Tekst recenzji</span><span class="sxs-lookup"><span data-stu-id="3dd87-125">ReviewText</span></span>|<span data-ttu-id="3dd87-126">Opinia</span><span class="sxs-lookup"><span data-stu-id="3dd87-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="3dd87-127">Wow... Bardzo dobre miejsce na życie.</span><span class="sxs-lookup"><span data-stu-id="3dd87-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="3dd87-128">1</span><span class="sxs-lookup"><span data-stu-id="3dd87-128">1</span></span>|
|<span data-ttu-id="3dd87-129">Skorupa nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="3dd87-129">Crust is not good.</span></span>|    <span data-ttu-id="3dd87-130">0</span><span class="sxs-lookup"><span data-stu-id="3dd87-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="3dd87-131">Tworzenie modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="3dd87-131">Build your machine learning model</span></span>

1. <span data-ttu-id="3dd87-132">Otwórz program Visual Studio i utwórz nową aplikację konsoli języka C# (Core.NET).</span><span class="sxs-lookup"><span data-stu-id="3dd87-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="3dd87-133">Nazwij projekt *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="3dd87-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="3dd87-134">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt *MLSparkModel.*</span><span class="sxs-lookup"><span data-stu-id="3dd87-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="3dd87-135">Następnie wybierz pozycję **Dodaj > uczenie maszynowe**.</span><span class="sxs-lookup"><span data-stu-id="3dd87-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="3dd87-136">W ML.NET Konstruktora modeli wybierz kafelek scenariusz **analizy tonacji.**</span><span class="sxs-lookup"><span data-stu-id="3dd87-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="3dd87-137">Na stronie **Dodawanie danych** prześlij zestaw danych *yelptrain.csv.*</span><span class="sxs-lookup"><span data-stu-id="3dd87-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="3dd87-138">Wybierz *pozycję Sentyment* z listy rozwijanej **Kolumny, aby przewidzieć.**</span><span class="sxs-lookup"><span data-stu-id="3dd87-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="3dd87-139">Na stronie **Pociąg** ustaw czas treningu na *60 sekund* i wybierz **pozycję Rozpocznij szkolenie**.</span><span class="sxs-lookup"><span data-stu-id="3dd87-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="3dd87-140">Zwróć uwagę na status treningu w obszarze **Postęp**.</span><span class="sxs-lookup"><span data-stu-id="3dd87-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="3dd87-141">Po zakończeniu szkolenia kreatora modeli **oceń** wyniki szkolenia.</span><span class="sxs-lookup"><span data-stu-id="3dd87-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="3dd87-142">Możesz wpisać frazy w polu tekstowym poniżej **Wypróbuj model** i wybierz **pozycję Przewiduj,** aby wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3dd87-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="3dd87-143">Wybierz **pozycję Kod,** a następnie wybierz pozycję **Dodaj projekty,** aby dodać model ml do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3dd87-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="3dd87-144">Należy zauważyć, że dwa projekty są dodawane do rozwiązań: **MLSparkModelML.ConsoleApp** i **MLSparkModelML.Model**.</span><span class="sxs-lookup"><span data-stu-id="3dd87-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="3dd87-145">Kliknij dwukrotnie projekt *MLSpark* C# i zwróć uwagę, że dodano następujące odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="3dd87-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="3dd87-146">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="3dd87-146">Create a console app</span></span>

<span data-ttu-id="3dd87-147">Kreator modeli tworzy aplikację konsoli dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="3dd87-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="3dd87-148">Kliknij prawym przyciskiem myszy **mlsparkModelML.Console** w Eksploratorze rozwiązań i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3dd87-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="3dd87-149">Wyszukaj witrynę **Microsoft.Spark** i zainstaluj pakiet.</span><span class="sxs-lookup"><span data-stu-id="3dd87-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="3dd87-150">**Microsoft.ML** jest automatycznie instalowany przez Program Model Builder.</span><span class="sxs-lookup"><span data-stu-id="3dd87-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="3dd87-151">Tworzenie sparkSession</span><span class="sxs-lookup"><span data-stu-id="3dd87-151">Create a SparkSession</span></span>

1. <span data-ttu-id="3dd87-152">Otwórz plik *Program.cs* dla **aplikacji MLSparkModelML.ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="3dd87-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="3dd87-153">Ten plik został automatycznie zwykli przez Kreatora modeli.</span><span class="sxs-lookup"><span data-stu-id="3dd87-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="3dd87-154">Usuń `using` instrukcje, zawartość Main() metody i `CreateSingleDataSample` regionu.</span><span class="sxs-lookup"><span data-stu-id="3dd87-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="3dd87-155">Dodaj następujące `using` dodatkowe instrukcje do górnej części *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="3dd87-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="3dd87-156">Zmień `DATA_FILEPATH` ścieżkę swojego *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="3dd87-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="3dd87-157">Dodaj następujący kod `Main` do metody, `SparkSession`aby utworzyć nowy plik .</span><span class="sxs-lookup"><span data-stu-id="3dd87-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="3dd87-158">Sesja iskry jest punktem wejścia do programowania platformy Spark za pomocą zestawu danych i interfejsu API DataFrame.</span><span class="sxs-lookup"><span data-stu-id="3dd87-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="3dd87-159">Wywołanie obiektu *iskrzącego* utworzonego powyżej umożliwia dostęp do funkcji platformy Spark i DataFrame w całym programie.</span><span class="sxs-lookup"><span data-stu-id="3dd87-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="3dd87-160">Tworzenie elementu DataFrame i drukowanie na konsoli</span><span class="sxs-lookup"><span data-stu-id="3dd87-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="3dd87-161">Przeczytaj w yelp przeglądu danych z pliku *yelptest.csv* jako `DataFrame`.</span><span class="sxs-lookup"><span data-stu-id="3dd87-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="3dd87-162">Dołącz `header` `inferSchema` i opcje.</span><span class="sxs-lookup"><span data-stu-id="3dd87-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="3dd87-163">Opcja `header` odczytuje pierwszy wiersz *yelptest.csv* jako nazwy kolumn zamiast danych.</span><span class="sxs-lookup"><span data-stu-id="3dd87-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="3dd87-164">Opcja `inferSchema` wywnioskować typy kolumn na podstawie danych.</span><span class="sxs-lookup"><span data-stu-id="3dd87-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="3dd87-165">Rejestrowanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="3dd87-165">Register a user-defined function</span></span>

<span data-ttu-id="3dd87-166">W aplikacjach Spark można używać plików UDF, *funkcji zdefiniowanych przez użytkownika,* aby wykonywać obliczenia i analizy danych.</span><span class="sxs-lookup"><span data-stu-id="3dd87-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="3dd87-167">W tym samouczku używasz ML.NET z UDF do oceny każdej recenzji Yelp.</span><span class="sxs-lookup"><span data-stu-id="3dd87-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="3dd87-168">Dodaj następujący kod `Main` do metody, aby `MLudf`zarejestrować UDF o nazwie .</span><span class="sxs-lookup"><span data-stu-id="3dd87-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="3dd87-169">Ten UDF przyjmuje ciąg przeglądu Yelp jako dane wejściowe i wyprowadza prawdziwe lub fałszywe dla pozytywnych lub negatywnych nastrojów, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3dd87-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="3dd87-170">Używa *predict()* metody zdefiniowanej w późniejszym kroku.</span><span class="sxs-lookup"><span data-stu-id="3dd87-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="3dd87-171">Wywoływanie usługi UDF za pomocą programu Spark SQL</span><span class="sxs-lookup"><span data-stu-id="3dd87-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="3dd87-172">Teraz, gdy zostały przeczytane w danych i włączone ML, użyj Spark SQL do wywołania UDF, który będzie uruchamiać analizę tonacji w każdym wierszu dataframe.</span><span class="sxs-lookup"><span data-stu-id="3dd87-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="3dd87-173">Dodaj następujący kod `Main` do swojej metody:</span><span class="sxs-lookup"><span data-stu-id="3dd87-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="3dd87-174">Utwórz metodę predict()</span><span class="sxs-lookup"><span data-stu-id="3dd87-174">Create predict() method</span></span>

<span data-ttu-id="3dd87-175">Dodaj następujący kod `Main()` przed metodą.</span><span class="sxs-lookup"><span data-stu-id="3dd87-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="3dd87-176">Ten kod jest podobny do tego, co jest produkowane przez Model Builder w *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="3dd87-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="3dd87-177">Przeniesienie tej metody na konsolę powoduje załadowanie modelu przy każdym uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3dd87-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="3dd87-178">Dodawanie modelu do aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="3dd87-178">Add the model to your console app</span></span>

<span data-ttu-id="3dd87-179">W Eksploratorze rozwiązań skopiuj plik *MLModel.zip* z projektu **MLSparkModelML.Model** i wklej go w projekcie **MLSparkModelML.ConsoleApp.**</span><span class="sxs-lookup"><span data-stu-id="3dd87-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="3dd87-180">Odwołanie jest automatycznie dodawane w *pliku MLSparkModelML.ConsoleApp.csproj*.</span><span class="sxs-lookup"><span data-stu-id="3dd87-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="3dd87-181">Uruchom swój kod</span><span class="sxs-lookup"><span data-stu-id="3dd87-181">Run your code</span></span>

<span data-ttu-id="3dd87-182">Użyj `spark-submit` do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="3dd87-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="3dd87-183">Przejdź do folderu głównego aplikacji konsoli za pomocą wiersza polecenia i uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="3dd87-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="3dd87-184">Najpierw oczyść i opublikuj aplikację.</span><span class="sxs-lookup"><span data-stu-id="3dd87-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="3dd87-185">Następnie przejdź do folderu publikowania aplikacji konsoli `spark-submit` i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="3dd87-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="3dd87-186">Pamiętaj, aby zaktualizować polecenie za pomocą rzeczywistej ścieżki pliku jar programu Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="3dd87-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="3dd87-187">Uzyskiwanie kodu</span><span class="sxs-lookup"><span data-stu-id="3dd87-187">Get the code</span></span>

<span data-ttu-id="3dd87-188">Ten samouczek jest podobny do kodu z [analizy tonacji z](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) big data przykład.</span><span class="sxs-lookup"><span data-stu-id="3dd87-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3dd87-189">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3dd87-189">Next steps</span></span>

<span data-ttu-id="3dd87-190">Przejdź do następnego artykułu, aby dowiedzieć się, jak wykonać ustrukturyzowane przesyłanie strumieniowe za pomocą platformy .NET dla platformy Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3dd87-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3dd87-191">Samouczek: Zorganizowane przesyłanie strumieniowe z .NET dla platformy Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3dd87-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
