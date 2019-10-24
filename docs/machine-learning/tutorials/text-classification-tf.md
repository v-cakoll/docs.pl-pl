---
title: 'Samouczek: analizowanie tonacji przeglądów filmów przy użyciu wstępnie przeszkolonego modelu TensorFlow'
description: W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach w witrynie sieci Web. Tonacji klasyfikator binarny jest aplikacją C# konsolową opracowaną przy użyciu programu Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 417abb5052df95c8496d97894d3e11d2956d7a1a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774395"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="59d63-104">Samouczek: analizowanie tonacji przeglądów filmów przy użyciu wstępnie przeszkolonego modelu TensorFlow w ML.NET</span><span class="sxs-lookup"><span data-stu-id="59d63-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="59d63-105">W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach w witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="59d63-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="59d63-106">Tonacji klasyfikator binarny jest aplikacją C# konsolową opracowaną przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59d63-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="59d63-107">Model TensorFlow używany w tym samouczku został przeszkolony przy użyciu recenzji filmów z bazy danych IMDB.</span><span class="sxs-lookup"><span data-stu-id="59d63-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="59d63-108">Po zakończeniu opracowywania aplikacji będzie można dostarczyć tekst z recenzji filmu, a aplikacja poinformuje użytkownika o tym, czy przegląd ma pozytywne czy negatywne tonacji.</span><span class="sxs-lookup"><span data-stu-id="59d63-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="59d63-109">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="59d63-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="59d63-110">Załaduj wstępnie szkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="59d63-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="59d63-111">Przekształć tekst komentarza witryny internetowej w funkcje odpowiednie dla modelu</span><span class="sxs-lookup"><span data-stu-id="59d63-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="59d63-112">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="59d63-112">Use the model to make a prediction</span></span>

<span data-ttu-id="59d63-113">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="59d63-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59d63-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="59d63-114">Prerequisites</span></span>

* <span data-ttu-id="59d63-115">[Program Visual Studio 2017 w wersji 15,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform w środowisku .NET Core".</span><span class="sxs-lookup"><span data-stu-id="59d63-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="59d63-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="59d63-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="59d63-117">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="59d63-117">Create the application</span></span>

1. <span data-ttu-id="59d63-118">Utwórz **aplikację konsolową .NET Core** o nazwie "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="59d63-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="59d63-119">Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="59d63-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="59d63-120">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="59d63-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="59d63-121">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="59d63-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="59d63-122">Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj** . wyszukaj pozycję **Microsoft.ml**, wybierz pakiet, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="59d63-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="59d63-123">Kontynuuj instalację, zgadzając się z postanowieniami licencyjnymi dotyczącymi wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="59d63-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="59d63-124">Powtórz te kroki dla **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="59d63-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="59d63-125">Dodawanie modelu TensorFlow do projektu</span><span class="sxs-lookup"><span data-stu-id="59d63-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="59d63-126">Model tego samouczka pochodzi z repozytorium w witrynie GitHub [/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="59d63-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="59d63-127">Model jest w formacie TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="59d63-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="59d63-128">Pobierz [plik zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="59d63-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="59d63-129">Plik zip zawiera:</span><span class="sxs-lookup"><span data-stu-id="59d63-129">The zip file contains:</span></span>

    * <span data-ttu-id="59d63-130">`saved_model.pb`: sam model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="59d63-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="59d63-131">Model przyjmuje stałą długość (w rozmiarze 600) tablicę funkcji reprezentujących tekst w ciągu przeglądu IMDB i wyprowadza dwa prawdopodobieństwa, które są sumowane do 1: prawdopodobieństwo, że przegląd danych wejściowych ma pozytywne tonacji, i prawdopodobieństwo, że przegląd danych wejściowych ma ujemna tonacji.</span><span class="sxs-lookup"><span data-stu-id="59d63-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="59d63-132">`imdb_word_index.csv`: mapowanie poszczególnych wyrazów na wartość całkowitą.</span><span class="sxs-lookup"><span data-stu-id="59d63-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="59d63-133">Mapowanie jest używane do generowania funkcji wejściowych dla modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="59d63-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="59d63-134">Skopiuj zawartość wewnętrznego katalogu `sentiment_model` do katalogu `sentiment_model` projektu *TextClassificationTF* .</span><span class="sxs-lookup"><span data-stu-id="59d63-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="59d63-135">Ten katalog zawiera model i dodatkowe pliki pomocnicze, które są odpowiednie dla tego samouczka, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="59d63-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![zawartość katalogu sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="59d63-137">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w katalogu `sentiment_model` i podkatalogu, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="59d63-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="59d63-138">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="59d63-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="59d63-139">Dodaj instrukcje using i zmienne globalne</span><span class="sxs-lookup"><span data-stu-id="59d63-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="59d63-140">Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="59d63-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="59d63-141">Utwórz dwie zmienne globalne bezpośrednio nad metodą `Main`, aby przechowywać ścieżkę do zapisanego pliku modelu i długość wektora funkcji.</span><span class="sxs-lookup"><span data-stu-id="59d63-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="59d63-142">`_modelPath` jest ścieżką do pliku nauczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="59d63-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="59d63-143">`FeatureLength` jest długością tablicy funkcji liczb całkowitych, która oczekuje model.</span><span class="sxs-lookup"><span data-stu-id="59d63-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="59d63-144">Modelowanie danych</span><span class="sxs-lookup"><span data-stu-id="59d63-144">Model the data</span></span>

<span data-ttu-id="59d63-145">Przeglądy filmów są bezpłatne tekstu.</span><span class="sxs-lookup"><span data-stu-id="59d63-145">Movie reviews are free form text.</span></span> <span data-ttu-id="59d63-146">Aplikacja konwertuje tekst na format wejściowy oczekiwany przez model w wielu odrębnych etapach.</span><span class="sxs-lookup"><span data-stu-id="59d63-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="59d63-147">Pierwszym jest podział tekstu na oddzielne słowa i użycie podanego pliku mapowania do mapowania każdego wyrazu na kodowanie całkowite.</span><span class="sxs-lookup"><span data-stu-id="59d63-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="59d63-148">Wynikiem tej transformacji jest tablica o zmiennej długości całkowitej o długości odpowiadającej liczbie wyrazów w zdaniu.</span><span class="sxs-lookup"><span data-stu-id="59d63-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="59d63-149">Właściwość</span><span class="sxs-lookup"><span data-stu-id="59d63-149">Property</span></span>| <span data-ttu-id="59d63-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="59d63-150">Value</span></span>|<span data-ttu-id="59d63-151">Typ</span><span class="sxs-lookup"><span data-stu-id="59d63-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="59d63-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="59d63-152">ReviewText</span></span>|<span data-ttu-id="59d63-153">Ta folia jest naprawdę dobra</span><span class="sxs-lookup"><span data-stu-id="59d63-153">this film is really good</span></span>|<span data-ttu-id="59d63-154">string</span><span class="sxs-lookup"><span data-stu-id="59d63-154">string</span></span>|
|<span data-ttu-id="59d63-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="59d63-155">VariableLengthFeatures</span></span>|<span data-ttu-id="59d63-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="59d63-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="59d63-157">int []</span><span class="sxs-lookup"><span data-stu-id="59d63-157">int[]</span></span>|

<span data-ttu-id="59d63-158">Rozmiar tablicy funkcji o zmiennej długości jest zmieniany na stałą długość wynoszącą 600.</span><span class="sxs-lookup"><span data-stu-id="59d63-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="59d63-159">Jest to długość oczekiwana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="59d63-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="59d63-160">Właściwość</span><span class="sxs-lookup"><span data-stu-id="59d63-160">Property</span></span>| <span data-ttu-id="59d63-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="59d63-161">Value</span></span>|<span data-ttu-id="59d63-162">Typ</span><span class="sxs-lookup"><span data-stu-id="59d63-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="59d63-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="59d63-163">ReviewText</span></span>|<span data-ttu-id="59d63-164">Ta folia jest naprawdę dobra</span><span class="sxs-lookup"><span data-stu-id="59d63-164">this film is really good</span></span>|<span data-ttu-id="59d63-165">string</span><span class="sxs-lookup"><span data-stu-id="59d63-165">string</span></span>|
|<span data-ttu-id="59d63-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="59d63-166">VariableLengthFeatures</span></span>|<span data-ttu-id="59d63-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="59d63-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="59d63-168">int []</span><span class="sxs-lookup"><span data-stu-id="59d63-168">int[]</span></span>|
|<span data-ttu-id="59d63-169">Funkcje</span><span class="sxs-lookup"><span data-stu-id="59d63-169">Features</span></span>|<span data-ttu-id="59d63-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="59d63-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="59d63-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="59d63-171">int[600]</span></span>|

1. <span data-ttu-id="59d63-172">Utwórz klasę danych wejściowych po metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="59d63-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="59d63-173">Klasa danych wejściowych `MovieReview` ma `string` do komentarzy użytkowników (`ReviewText`).</span><span class="sxs-lookup"><span data-stu-id="59d63-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="59d63-174">Utwórz klasę dla funkcji o zmiennej długości, po metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="59d63-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="59d63-175">Właściwość `VariableLengthFeatures` ma atrybut [vectortype](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) służący do wyznaczania go jako wektor.</span><span class="sxs-lookup"><span data-stu-id="59d63-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="59d63-176">Wszystkie elementy wektorowe muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="59d63-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="59d63-177">W przypadku zestawów danych z dużą liczbą kolumn ładowanie wielu kolumn jako jednego wektora zmniejsza liczbę danych przekazywanych w przypadku zastosowania transformacji danych.</span><span class="sxs-lookup"><span data-stu-id="59d63-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="59d63-178">Ta klasa jest używana w akcji `ResizeFeatures`.</span><span class="sxs-lookup"><span data-stu-id="59d63-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="59d63-179">Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania kolumn w widoku danych, które mogą być używane jako _dane wejściowe_ niestandardowej akcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="59d63-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="59d63-180">Utwórz klasę dla funkcji o stałej długości po metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="59d63-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="59d63-181">Ta klasa jest używana w akcji `ResizeFeatures`.</span><span class="sxs-lookup"><span data-stu-id="59d63-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="59d63-182">Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania kolumn w widoku danych, które mogą być używane jako _dane wyjściowe_ niestandardowej akcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="59d63-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="59d63-183">Należy zauważyć, że nazwa właściwości `Features` jest określana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="59d63-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="59d63-184">Nie można zmienić tej nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="59d63-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="59d63-185">Utwórz klasę dla przewidywania po metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="59d63-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="59d63-186">`MovieReviewSentimentPrediction` jest klasą przewidywania używaną po przekształceniu modelu.</span><span class="sxs-lookup"><span data-stu-id="59d63-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="59d63-187">`MovieReviewSentimentPrediction` ma jedną `float` tablicę (`Prediction`) i atrybut `VectorType`.</span><span class="sxs-lookup"><span data-stu-id="59d63-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="59d63-188">Tworzenie MLContext, słownika wyszukiwania i akcji w celu zmiany rozmiaru funkcji</span><span class="sxs-lookup"><span data-stu-id="59d63-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="59d63-189">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET.</span><span class="sxs-lookup"><span data-stu-id="59d63-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="59d63-190">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="59d63-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="59d63-191">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="59d63-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="59d63-192">Zastąp wiersz `Console.WriteLine("Hello World!")` w metodzie `Main` następującym kodem, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="59d63-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="59d63-193">Utwórz słownik służący do kodowania wyrazów jako liczby całkowite przy użyciu metody [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) do ładowania danych mapowania z pliku, jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="59d63-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="59d63-194">Word</span><span class="sxs-lookup"><span data-stu-id="59d63-194">Word</span></span>     |<span data-ttu-id="59d63-195">Indeks</span><span class="sxs-lookup"><span data-stu-id="59d63-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="59d63-196">bezpiecznego</span><span class="sxs-lookup"><span data-stu-id="59d63-196">kids</span></span>     |  <span data-ttu-id="59d63-197">362</span><span class="sxs-lookup"><span data-stu-id="59d63-197">362</span></span>    |
    |<span data-ttu-id="59d63-198">Możesz</span><span class="sxs-lookup"><span data-stu-id="59d63-198">want</span></span>     |  <span data-ttu-id="59d63-199">181</span><span class="sxs-lookup"><span data-stu-id="59d63-199">181</span></span>    |
    |<span data-ttu-id="59d63-200">odpowiednich</span><span class="sxs-lookup"><span data-stu-id="59d63-200">wrong</span></span>    |  <span data-ttu-id="59d63-201">355</span><span class="sxs-lookup"><span data-stu-id="59d63-201">355</span></span>    |
    |<span data-ttu-id="59d63-202">efekty</span><span class="sxs-lookup"><span data-stu-id="59d63-202">effects</span></span>  |  <span data-ttu-id="59d63-203">302</span><span class="sxs-lookup"><span data-stu-id="59d63-203">302</span></span>    |
    |<span data-ttu-id="59d63-204">całkiem</span><span class="sxs-lookup"><span data-stu-id="59d63-204">feeling</span></span>  |  <span data-ttu-id="59d63-205">547</span><span class="sxs-lookup"><span data-stu-id="59d63-205">547</span></span>    |

    <span data-ttu-id="59d63-206">Dodaj poniższy kod, aby utworzyć mapę wyszukiwania:</span><span class="sxs-lookup"><span data-stu-id="59d63-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="59d63-207">Dodaj `Action`, aby zmienić rozmiar tablicy tablica liczb całkowitych wyrazów o zmiennej długości do tablicy o stałym rozmiarze, z następnymi wierszami kodu:</span><span class="sxs-lookup"><span data-stu-id="59d63-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="59d63-208">Załaduj wstępnie szkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="59d63-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="59d63-209">Dodaj kod, aby załadować model TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="59d63-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="59d63-210">Po załadowaniu modelu można wyodrębnić jego schemat wejściowy i wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="59d63-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="59d63-211">Schematy są wyświetlane tylko dla zainteresowania i tylko do celów szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="59d63-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="59d63-212">Ten kod nie jest potrzebny do działania końcowej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="59d63-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="59d63-213">Schemat wejściowy jest tablicą o stałej długości w postaci słów szyfrowanych liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="59d63-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="59d63-214">Schemat danych wyjściowych jest tablicą zmiennoprzecinkową prawdopodobieństwa wskazującą, czy tonacji przeglądu jest ujemna, czy dodatnia.</span><span class="sxs-lookup"><span data-stu-id="59d63-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="59d63-215">Te wartości są sumowane do 1, ponieważ prawdopodobieństwo wystąpienia pozytywnego jest uzupełnieniem prawdopodobieństwa, że tonacji jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="59d63-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="59d63-216">Tworzenie potoku ML.NET</span><span class="sxs-lookup"><span data-stu-id="59d63-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="59d63-217">Utwórz potok i Podziel tekst wejściowy na słowa przy użyciu transformacji [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) , aby podzielić tekst na wyrazy jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="59d63-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="59d63-218">Transformacja [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) używa spacji do analizowania tekstu/ciągu w słowach.</span><span class="sxs-lookup"><span data-stu-id="59d63-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="59d63-219">Tworzy nową kolumnę i dzieli każdy ciąg wejściowy na wektor podciągów w oparciu o separator zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="59d63-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="59d63-220">Mapuj słowa na ich kodowanie całkowite przy użyciu tabeli odnośników zadeklarowanej powyżej:</span><span class="sxs-lookup"><span data-stu-id="59d63-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="59d63-221">Zmień rozmiar kodowania Integer o zmiennej długości na stałą długość określoną przez model:</span><span class="sxs-lookup"><span data-stu-id="59d63-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="59d63-222">Klasyfikuj dane wejściowe za pomocą załadowanego modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="59d63-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="59d63-223">Dane wyjściowe modelu TensorFlow są nazywane `Prediction/Softmax`.</span><span class="sxs-lookup"><span data-stu-id="59d63-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="59d63-224">Należy pamiętać, że nazwa `Prediction/Softmax` jest określana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="59d63-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="59d63-225">Nie można zmienić tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="59d63-225">You cannot change this name.</span></span>

1. <span data-ttu-id="59d63-226">Utwórz nową kolumnę przewidywania danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="59d63-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="59d63-227">Należy skopiować kolumnę `Prediction/Softmax` na jedną z nazwą, która może być używana jako właściwość w C# klasie: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="59d63-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="59d63-228">Znak `/` nie jest dozwolony w nazwie C# właściwości.</span><span class="sxs-lookup"><span data-stu-id="59d63-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="59d63-229">Tworzenie modelu ML.NET z potoku</span><span class="sxs-lookup"><span data-stu-id="59d63-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="59d63-230">Dodaj kod, aby utworzyć model z potoku:</span><span class="sxs-lookup"><span data-stu-id="59d63-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="59d63-231">Model ML.NET jest tworzony na podstawie łańcucha szacowania w potoku przez wywołanie metody `Fit`.</span><span class="sxs-lookup"><span data-stu-id="59d63-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="59d63-232">W takim przypadku nie dopasowujemy żadnych danych w celu utworzenia modelu, ponieważ model TensorFlow został już wcześniej przeszkolony.</span><span class="sxs-lookup"><span data-stu-id="59d63-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="59d63-233">Dostarczamy pusty obiekt widoku danych w celu spełnienia wymagań metody `Fit`.</span><span class="sxs-lookup"><span data-stu-id="59d63-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="59d63-234">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="59d63-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="59d63-235">Dodaj metodę `PredictSentiment` poniżej metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="59d63-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="59d63-236">Dodaj następujący kod, aby utworzyć `PredictionEngine` jako pierwszy wiersz w `PredictSentiment()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="59d63-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="59d63-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="59d63-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="59d63-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="59d63-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="59d63-239">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="59d63-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="59d63-240">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, Użyj usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59d63-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="59d63-241">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania z `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="59d63-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="59d63-242">rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="59d63-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="59d63-243">Dodaj komentarz, aby przetestować prognozę przeszkolonego modelu w metodzie `Predict()`, tworząc wystąpienie `MovieReview`:</span><span class="sxs-lookup"><span data-stu-id="59d63-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="59d63-244">Przekaż dane komentarzy testowych do `Prediction Engine` przez dodanie następnych wierszy kodu w metodzie `PredictSentiment()`:</span><span class="sxs-lookup"><span data-stu-id="59d63-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="59d63-245">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) wykonuje prognozowanie w jednym wierszu danych:</span><span class="sxs-lookup"><span data-stu-id="59d63-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="59d63-246">Właściwość</span><span class="sxs-lookup"><span data-stu-id="59d63-246">Property</span></span>| <span data-ttu-id="59d63-247">Wartość</span><span class="sxs-lookup"><span data-stu-id="59d63-247">Value</span></span>|<span data-ttu-id="59d63-248">Typ</span><span class="sxs-lookup"><span data-stu-id="59d63-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="59d63-249">Przewidując</span><span class="sxs-lookup"><span data-stu-id="59d63-249">Prediction</span></span>|<span data-ttu-id="59d63-250">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="59d63-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="59d63-251">float []</span><span class="sxs-lookup"><span data-stu-id="59d63-251">float[]</span></span>|

1. <span data-ttu-id="59d63-252">Wyświetl prognozowanie tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="59d63-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="59d63-253">Dodaj wywołanie do `PredictSentiment` na końcu metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="59d63-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="59d63-254">Wyniki</span><span class="sxs-lookup"><span data-stu-id="59d63-254">Results</span></span>

<span data-ttu-id="59d63-255">Kompiluj i uruchamiaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="59d63-255">Build and run your application.</span></span>

<span data-ttu-id="59d63-256">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="59d63-256">Your results should be similar to the following.</span></span> <span data-ttu-id="59d63-257">Podczas przetwarzania wyświetlane są komunikaty.</span><span class="sxs-lookup"><span data-stu-id="59d63-257">During processing, messages are displayed.</span></span> <span data-ttu-id="59d63-258">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="59d63-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="59d63-259">Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="59d63-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="59d63-260">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="59d63-260">Congratulations!</span></span> <span data-ttu-id="59d63-261">Pomyślnie skompilowano model uczenia maszynowego do klasyfikowania i przewidywania komunikatów tonacji przez ponowne użycie wstępnie nauczonego modelu `TensorFlow` w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="59d63-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="59d63-262">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="59d63-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="59d63-263">W tym samouczku przedstawiono sposób wykonywania tych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="59d63-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="59d63-264">Załaduj wstępnie szkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="59d63-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="59d63-265">Przekształć tekst komentarza witryny internetowej w funkcje odpowiednie dla modelu</span><span class="sxs-lookup"><span data-stu-id="59d63-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="59d63-266">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="59d63-266">Use the model to make a prediction</span></span>
