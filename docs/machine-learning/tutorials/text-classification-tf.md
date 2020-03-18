---
title: 'Samouczek: Analizowanie opinii za pomocą modelu TensorFlow'
description: W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach do witryny. Klasyfikator tonacji binarnych jest aplikacją konsoli Języka C# opracowaną przy użyciu programu Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241120"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="30992-104">Samouczek: Analizowanie opinii o filmach przy użyciu wstępnie przeszkolonego modelu TensorFlow w ML.NET</span><span class="sxs-lookup"><span data-stu-id="30992-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="30992-105">W tym samouczku pokazano, jak używać wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach do witryny.</span><span class="sxs-lookup"><span data-stu-id="30992-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="30992-106">Klasyfikator tonacji binarnych jest aplikacją konsoli Języka C# opracowaną przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30992-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="30992-107">Model TensorFlow używany w tym samouczku został przeszkolony przy użyciu recenzji filmów z bazy danych IMDB.</span><span class="sxs-lookup"><span data-stu-id="30992-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="30992-108">Po zakończeniu tworzenia aplikacji, będzie można dostarczyć tekst przeglądu filmu i aplikacja powie, czy przegląd ma pozytywne lub negatywne uczucia.</span><span class="sxs-lookup"><span data-stu-id="30992-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="30992-109">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="30992-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="30992-110">Załaduj wstępnie przeszkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="30992-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="30992-111">Przekształcaj tekst komentarza strony internetowej w funkcje odpowiednie dla modelu</span><span class="sxs-lookup"><span data-stu-id="30992-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="30992-112">Użyj modelu, aby dokonać przewidywania</span><span class="sxs-lookup"><span data-stu-id="30992-112">Use the model to make a prediction</span></span>

<span data-ttu-id="30992-113">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)</span><span class="sxs-lookup"><span data-stu-id="30992-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="30992-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="30992-114">Prerequisites</span></span>

* <span data-ttu-id="30992-115">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core programistorna wieloplatformowa".</span><span class="sxs-lookup"><span data-stu-id="30992-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="30992-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="30992-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="30992-117">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="30992-117">Create the application</span></span>

1. <span data-ttu-id="30992-118">Utwórz **aplikację .NET Core Console** o nazwie "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="30992-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="30992-119">Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="30992-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="30992-120">Zainstaluj **pakiet Microsoft.ML NuGet:**</span><span class="sxs-lookup"><span data-stu-id="30992-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="30992-121">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="30992-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="30992-122">Wybierz "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj.** Wyszukaj **Microsoft.ML**wybierz odpowiedni pakiet, a następnie wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="30992-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="30992-123">Kontynuuj instalację, zgadzając się na warunki licencyjne dla wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="30992-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="30992-124">Powtórz te kroki dla **microsoft.ML.TensorFlow** i **SciSharp.TensorFlow.Redist**.</span><span class="sxs-lookup"><span data-stu-id="30992-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="30992-125">Dodawanie modelu TensorFlow do projektu</span><span class="sxs-lookup"><span data-stu-id="30992-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="30992-126">Model tego samouczka pochodzi z repotentu [github dotnet/machinelearning-testdata.](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model)</span><span class="sxs-lookup"><span data-stu-id="30992-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="30992-127">Model jest w formacie TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="30992-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="30992-128">Pobierz [sentiment_model plik zip](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="30992-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="30992-129">Plik zip zawiera:</span><span class="sxs-lookup"><span data-stu-id="30992-129">The zip file contains:</span></span>

    * <span data-ttu-id="30992-130">`saved_model.pb`: sam model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="30992-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="30992-131">Model przyjmuje tablicę całkowitą o stałej długości (rozmiar 600) funkcji reprezentujących tekst w ciągu przeglądu IMDB i generuje dwa prawdopodobieństwa, które sumują się do 1: prawdopodobieństwo, że przegląd wejściowy ma pozytywne nastawienie i prawdopodobieństwo, że przegląd wejściowy ma negatywnych nastrojów.</span><span class="sxs-lookup"><span data-stu-id="30992-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="30992-132">`imdb_word_index.csv`: mapowanie z poszczególnych wyrazów do wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="30992-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="30992-133">Mapowanie służy do generowania funkcji wejściowych dla modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="30992-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="30992-134">Skopiuj zawartość `sentiment_model` najbardziej wewnętrznego katalogu `sentiment_model` do katalogu projektu *TextClassificationTF.*</span><span class="sxs-lookup"><span data-stu-id="30992-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="30992-135">Ten katalog zawiera model i dodatkowe pliki pomocy technicznej potrzebne w tym samouczku, jak pokazano na poniższym obrazku:</span><span class="sxs-lookup"><span data-stu-id="30992-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model zawartość katalogu](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="30992-137">W Eksploratorze rozwiązań kliknij `sentiment_model` prawym przyciskiem myszy każdy z plików w katalogu i podkatalogu i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="30992-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="30992-138">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="30992-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="30992-139">Dodawanie za pomocą instrukcji i zmiennych globalnych</span><span class="sxs-lookup"><span data-stu-id="30992-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="30992-140">Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="30992-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="30992-141">Utwórz dwie zmienne globalne `Main` tuż nad metodą przechowywania zapisanej ścieżki pliku modelu oraz długość wektora operacji.</span><span class="sxs-lookup"><span data-stu-id="30992-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="30992-142">`_modelPath`jest ścieżką pliku uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="30992-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="30992-143">`FeatureLength`jest długością tablicy operacji liczby całkowitej, której oczekuje model.</span><span class="sxs-lookup"><span data-stu-id="30992-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="30992-144">Modelowanie danych</span><span class="sxs-lookup"><span data-stu-id="30992-144">Model the data</span></span>

<span data-ttu-id="30992-145">Recenzje filmów są tekstem w formie dowolnych.</span><span class="sxs-lookup"><span data-stu-id="30992-145">Movie reviews are free form text.</span></span> <span data-ttu-id="30992-146">Aplikacja konwertuje tekst do formatu wejściowego oczekiwanego przez model w wielu dyskretnych etapach.</span><span class="sxs-lookup"><span data-stu-id="30992-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="30992-147">Pierwszym z nich jest podzielenie tekstu na oddzielne wyrazy i użycie dostarczonego pliku mapowania do mapowania każdego wyrazu na kodowanie całkowitej.</span><span class="sxs-lookup"><span data-stu-id="30992-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="30992-148">Wynikiem tej transformacji jest tablica całkowita o zmiennej długości o długości odpowiadającej liczbie wyrazów w zdaniu.</span><span class="sxs-lookup"><span data-stu-id="30992-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="30992-149">Właściwość</span><span class="sxs-lookup"><span data-stu-id="30992-149">Property</span></span>| <span data-ttu-id="30992-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="30992-150">Value</span></span>|<span data-ttu-id="30992-151">Typ</span><span class="sxs-lookup"><span data-stu-id="30992-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="30992-152">ReviewText (Tekst recenzji)</span><span class="sxs-lookup"><span data-stu-id="30992-152">ReviewText</span></span>|<span data-ttu-id="30992-153">ten film jest naprawdę dobry</span><span class="sxs-lookup"><span data-stu-id="30992-153">this film is really good</span></span>|<span data-ttu-id="30992-154">ciąg</span><span class="sxs-lookup"><span data-stu-id="30992-154">string</span></span>|
|<span data-ttu-id="30992-155">Funkcje variablelengthFeatures</span><span class="sxs-lookup"><span data-stu-id="30992-155">VariableLengthFeatures</span></span>|<span data-ttu-id="30992-156">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="30992-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="30992-157">int[]</span><span class="sxs-lookup"><span data-stu-id="30992-157">int[]</span></span>|

<span data-ttu-id="30992-158">Tablica operacji o zmiennej długości jest następnie zmieniana na stałą długość 600.</span><span class="sxs-lookup"><span data-stu-id="30992-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="30992-159">Jest to długość, że model TensorFlow oczekuje.</span><span class="sxs-lookup"><span data-stu-id="30992-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="30992-160">Właściwość</span><span class="sxs-lookup"><span data-stu-id="30992-160">Property</span></span>| <span data-ttu-id="30992-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="30992-161">Value</span></span>|<span data-ttu-id="30992-162">Typ</span><span class="sxs-lookup"><span data-stu-id="30992-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="30992-163">ReviewText (Tekst recenzji)</span><span class="sxs-lookup"><span data-stu-id="30992-163">ReviewText</span></span>|<span data-ttu-id="30992-164">ten film jest naprawdę dobry</span><span class="sxs-lookup"><span data-stu-id="30992-164">this film is really good</span></span>|<span data-ttu-id="30992-165">ciąg</span><span class="sxs-lookup"><span data-stu-id="30992-165">string</span></span>|
|<span data-ttu-id="30992-166">Funkcje variablelengthFeatures</span><span class="sxs-lookup"><span data-stu-id="30992-166">VariableLengthFeatures</span></span>|<span data-ttu-id="30992-167">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="30992-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="30992-168">int[]</span><span class="sxs-lookup"><span data-stu-id="30992-168">int[]</span></span>|
|<span data-ttu-id="30992-169">Funkcje</span><span class="sxs-lookup"><span data-stu-id="30992-169">Features</span></span>|<span data-ttu-id="30992-170">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="30992-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="30992-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="30992-171">int[600]</span></span>|

1. <span data-ttu-id="30992-172">Utwórz klasę dla danych wejściowych, po metodzie: `Main`</span><span class="sxs-lookup"><span data-stu-id="30992-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="30992-173">Klasa danych wejściowych, `MovieReview` `string` ma komentarze`ReviewText`dla użytkowników ( ).</span><span class="sxs-lookup"><span data-stu-id="30992-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="30992-174">Utwórz klasę dla operacji o `Main` zmiennej długości, po metodzie:</span><span class="sxs-lookup"><span data-stu-id="30992-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="30992-175">Właściwość `VariableLengthFeatures` ma [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) atrybut, aby wyznaczyć go jako wektor.</span><span class="sxs-lookup"><span data-stu-id="30992-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="30992-176">Wszystkie elementy wektorowe muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="30992-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="30992-177">W zestawach danych z dużą liczbą kolumn ładowanie wielu kolumn jako pojedynczego wektora zmniejsza liczbę przebiegów danych po zastosowaniu przekształceń danych.</span><span class="sxs-lookup"><span data-stu-id="30992-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="30992-178">Ta klasa jest `ResizeFeatures` używana w akcji.</span><span class="sxs-lookup"><span data-stu-id="30992-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="30992-179">Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania, które kolumny w DataView mogą służyć jako _dane wejściowe_ do akcji mapowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="30992-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="30992-180">Utwórz klasę dla operacji o `Main` stałej długości, po metodzie:</span><span class="sxs-lookup"><span data-stu-id="30992-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="30992-181">Ta klasa jest `ResizeFeatures` używana w akcji.</span><span class="sxs-lookup"><span data-stu-id="30992-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="30992-182">Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania, które kolumny w DataView mogą służyć jako _dane wyjściowe_ akcji mapowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="30992-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="30992-183">Należy zauważyć, że `Features` nazwa właściwości jest określana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="30992-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="30992-184">Nie można zmienić tej nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="30992-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="30992-185">Utwórz klasę dla przewidywania `Main` po metodzie:</span><span class="sxs-lookup"><span data-stu-id="30992-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="30992-186">`MovieReviewSentimentPrediction`jest klasa przewidywania używane po treningu modelu.</span><span class="sxs-lookup"><span data-stu-id="30992-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="30992-187">`MovieReviewSentimentPrediction`ma pojedynczą `float` `Prediction`tablicę `VectorType` ( ) i atrybut.</span><span class="sxs-lookup"><span data-stu-id="30992-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="30992-188">Tworzenie funkcji MLContext, wyszukiwania i akcji w celu zmiany rozmiaru obiektów</span><span class="sxs-lookup"><span data-stu-id="30992-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="30992-189">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET.</span><span class="sxs-lookup"><span data-stu-id="30992-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="30992-190">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="30992-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="30992-191">Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="30992-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="30992-192">Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="30992-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="30992-193">Utwórz słownik do kodowania wyrazów jako liczb [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) całkowitych za pomocą metody ładowania danych mapowania z pliku, jak widać w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="30992-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="30992-194">Word</span><span class="sxs-lookup"><span data-stu-id="30992-194">Word</span></span>     |<span data-ttu-id="30992-195">Indeks</span><span class="sxs-lookup"><span data-stu-id="30992-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="30992-196">Dzieci</span><span class="sxs-lookup"><span data-stu-id="30992-196">kids</span></span>     |  <span data-ttu-id="30992-197">362</span><span class="sxs-lookup"><span data-stu-id="30992-197">362</span></span>    |
    |<span data-ttu-id="30992-198">chcesz</span><span class="sxs-lookup"><span data-stu-id="30992-198">want</span></span>     |  <span data-ttu-id="30992-199">181</span><span class="sxs-lookup"><span data-stu-id="30992-199">181</span></span>    |
    |<span data-ttu-id="30992-200">Nieodpowiednim</span><span class="sxs-lookup"><span data-stu-id="30992-200">wrong</span></span>    |  <span data-ttu-id="30992-201">355</span><span class="sxs-lookup"><span data-stu-id="30992-201">355</span></span>    |
    |<span data-ttu-id="30992-202">effects</span><span class="sxs-lookup"><span data-stu-id="30992-202">effects</span></span>  |  <span data-ttu-id="30992-203">302</span><span class="sxs-lookup"><span data-stu-id="30992-203">302</span></span>    |
    |<span data-ttu-id="30992-204">Uczucie</span><span class="sxs-lookup"><span data-stu-id="30992-204">feeling</span></span>  |  <span data-ttu-id="30992-205">547</span><span class="sxs-lookup"><span data-stu-id="30992-205">547</span></span>    |

    <span data-ttu-id="30992-206">Dodaj poniższy kod, aby utworzyć mapę odzewu:</span><span class="sxs-lookup"><span data-stu-id="30992-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="30992-207">Dodaj `Action` rozmiar tablicy całkowitej wyrazu o zmiennej długości do tablicy całkowitej o stałym rozmiarze, z kolejnymi wierszami kodu:</span><span class="sxs-lookup"><span data-stu-id="30992-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="30992-208">Załaduj wstępnie przeszkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="30992-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="30992-209">Dodaj kod, aby załadować model TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="30992-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="30992-210">Po załadowaniu modelu można wyodrębnić jego schemat danych wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="30992-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="30992-211">Schemy są wyświetlane tylko dla zainteresowania i uczenia się.</span><span class="sxs-lookup"><span data-stu-id="30992-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="30992-212">Nie potrzebujesz tego kodu do działania aplikacji końcowej:</span><span class="sxs-lookup"><span data-stu-id="30992-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    <span data-ttu-id="30992-213">Schemat wejściowy jest tablicą o stałej długości wyrazów zakodowanych całkowitą.</span><span class="sxs-lookup"><span data-stu-id="30992-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="30992-214">Schemat danych wyjściowych jest zmienną tablicą prawdopodobieństwa wskazującą, czy sentyment recenzji jest ujemny, czy dodatni.</span><span class="sxs-lookup"><span data-stu-id="30992-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="30992-215">Wartości te sumują się do 1, ponieważ prawdopodobieństwo pozytywnego jest uzupełnieniem prawdopodobieństwa, że sentyment jest ujemny.</span><span class="sxs-lookup"><span data-stu-id="30992-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="30992-216">Tworzenie potoku ML.NET</span><span class="sxs-lookup"><span data-stu-id="30992-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="30992-217">Utwórz potok i podziel tekst wejściowy na słowa za pomocą transformacji [TokenizeIntoWords,](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) aby podzielić tekst na słowa jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="30992-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="30992-218">Transformacja [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) używa spacji do analizowania tekstu/ciągu w słowa.</span><span class="sxs-lookup"><span data-stu-id="30992-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="30992-219">Tworzy nową kolumnę i dzieli każdy ciąg wejściowy na wektor podciągów na podstawie separatora zdefiniowanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="30992-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="30992-220">Mapowanie wyrazów na ich kodowanie liczby całkowitej za pomocą tabeli odzewów, które zadeklarowano powyżej:</span><span class="sxs-lookup"><span data-stu-id="30992-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. <span data-ttu-id="30992-221">Zmień rozmiar kodowania liczb całkowitych o zmiennej długości na kodowanie o stałej długości wymagane przez model:</span><span class="sxs-lookup"><span data-stu-id="30992-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. <span data-ttu-id="30992-222">Sklasyfikować dane wejściowe z załadowanym modelem TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="30992-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="30992-223">Wyjście modelu TensorFlow `Prediction/Softmax`nosi nazwę .</span><span class="sxs-lookup"><span data-stu-id="30992-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="30992-224">Należy zauważyć, `Prediction/Softmax` że nazwa jest określana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="30992-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="30992-225">Nie można zmienić tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="30992-225">You cannot change this name.</span></span>

1. <span data-ttu-id="30992-226">Utwórz nową kolumnę dla przewidywania danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="30992-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="30992-227">Należy skopiować `Prediction/Softmax` kolumnę do jednej z nazwą, która może być używana `Prediction`jako właściwość w klasie C#: .</span><span class="sxs-lookup"><span data-stu-id="30992-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="30992-228">Znak `/` nie jest dozwolone w nazwie właściwości Języka C#.</span><span class="sxs-lookup"><span data-stu-id="30992-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="30992-229">Tworzenie modelu ML.NET z potoku</span><span class="sxs-lookup"><span data-stu-id="30992-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="30992-230">Dodaj kod, aby utworzyć model z potoku:</span><span class="sxs-lookup"><span data-stu-id="30992-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="30992-231">Model ML.NET jest tworzony z łańcucha estymatorów w `Fit` potoku przez wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="30992-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="30992-232">W takim przypadku nie są dopasowane żadnych danych do utworzenia modelu, jak model TensorFlow został już wcześniej przeszkolony.</span><span class="sxs-lookup"><span data-stu-id="30992-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="30992-233">Dostarczamy obiekt pustego widoku danych, `Fit` aby spełnić wymagania metody.</span><span class="sxs-lookup"><span data-stu-id="30992-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="30992-234">Użyj modelu, aby dokonać przewidywania</span><span class="sxs-lookup"><span data-stu-id="30992-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="30992-235">Dodaj `PredictSentiment` metodę poniżej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="30992-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="30992-236">Dodaj następujący kod, `PredictionEngine` aby utworzyć jako `PredictSentiment()` pierwszy wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="30992-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="30992-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="30992-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="30992-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici.</span><span class="sxs-lookup"><span data-stu-id="30992-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="30992-239">Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="30992-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="30992-240">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30992-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="30992-241">Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="30992-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="30992-242">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="30992-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="30992-243">Dodaj komentarz, aby przetestować przewidywanie `Predict()` uczonego modelu `MovieReview`w metodzie, tworząc wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="30992-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. <span data-ttu-id="30992-244">Przekaż dane komentarza testowego do dodawania `Prediction Engine` kolejnych `PredictSentiment()` wierszy kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="30992-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. <span data-ttu-id="30992-245">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie dla pojedynczego wiersza danych:</span><span class="sxs-lookup"><span data-stu-id="30992-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="30992-246">Właściwość</span><span class="sxs-lookup"><span data-stu-id="30992-246">Property</span></span>| <span data-ttu-id="30992-247">Wartość</span><span class="sxs-lookup"><span data-stu-id="30992-247">Value</span></span>|<span data-ttu-id="30992-248">Typ</span><span class="sxs-lookup"><span data-stu-id="30992-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="30992-249">Prediction (Prognoza)</span><span class="sxs-lookup"><span data-stu-id="30992-249">Prediction</span></span>|<span data-ttu-id="30992-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="30992-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="30992-251">pływak[]</span><span class="sxs-lookup"><span data-stu-id="30992-251">float[]</span></span>|

1. <span data-ttu-id="30992-252">Wyświetl przewidywanie tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="30992-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="30992-253">Dodaj wywołanie `PredictSentiment` na końcu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="30992-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="30992-254">Wyniki</span><span class="sxs-lookup"><span data-stu-id="30992-254">Results</span></span>

<span data-ttu-id="30992-255">Tworzenie i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30992-255">Build and run your application.</span></span>

<span data-ttu-id="30992-256">Wyniki powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="30992-256">Your results should be similar to the following.</span></span> <span data-ttu-id="30992-257">Podczas przetwarzania są wyświetlane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="30992-257">During processing, messages are displayed.</span></span> <span data-ttu-id="30992-258">Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="30992-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="30992-259">Te komunikaty zostały usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="30992-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="30992-260">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="30992-260">Congratulations!</span></span> <span data-ttu-id="30992-261">Teraz pomyślnie skonstruowano model uczenia maszynowego do klasyfikowania i przewidywania tonacji `TensorFlow` wiadomości przez ponowne użycie wstępnie uczonego modelu w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="30992-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="30992-262">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF)</span><span class="sxs-lookup"><span data-stu-id="30992-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="30992-263">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="30992-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="30992-264">Załaduj wstępnie przeszkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="30992-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="30992-265">Przekształcaj tekst komentarza strony internetowej w funkcje odpowiednie dla modelu</span><span class="sxs-lookup"><span data-stu-id="30992-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="30992-266">Użyj modelu, aby dokonać przewidywania</span><span class="sxs-lookup"><span data-stu-id="30992-266">Use the model to make a prediction</span></span>
