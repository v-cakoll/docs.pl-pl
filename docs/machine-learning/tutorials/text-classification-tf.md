---
title: 'Samouczek: Analizuj tonacjie przeglądy filmów przy użyciu wstępnie przeszkolonego modelu TensorFlow'
description: W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach w witrynie sieci Web. Tonacji klasyfikator binarny jest aplikacją C# konsolową opracowaną przy użyciu programu Visual Studio.
ms.date: 09/11/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 38b935814d713284dae1ca931b90c63bbcac332b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216897"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="1ae70-104">Samouczek: Analizuj tonacjie przeglądy filmów przy użyciu wstępnie przeszkolonego modelu TensorFlow w ML.NET</span><span class="sxs-lookup"><span data-stu-id="1ae70-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="1ae70-105">W tym samouczku przedstawiono sposób użycia wstępnie przeszkolonego modelu TensorFlow do klasyfikowania tonacji w komentarzach w witrynie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ae70-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="1ae70-106">Tonacji klasyfikator binarny jest aplikacją C# konsolową opracowaną przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ae70-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="1ae70-107">Model TensorFlow używany w tym samouczku został przeszkolony przy użyciu recenzji filmów z bazy danych IMDB.</span><span class="sxs-lookup"><span data-stu-id="1ae70-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="1ae70-108">Po zakończeniu opracowywania aplikacji będzie można dostarczyć tekst z recenzji filmu, a aplikacja poinformuje użytkownika o tym, czy przegląd ma pozytywne czy negatywne tonacji.</span><span class="sxs-lookup"><span data-stu-id="1ae70-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="1ae70-109">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1ae70-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1ae70-110">Załaduj wstępnie szkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="1ae70-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="1ae70-111">Przekształć tekst komentarza witryny internetowej w funkcje odpowiednie dla modelu</span><span class="sxs-lookup"><span data-stu-id="1ae70-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="1ae70-112">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="1ae70-112">Use the model to make a prediction</span></span>

<span data-ttu-id="1ae70-113">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="1ae70-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ae70-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1ae70-114">Prerequisites</span></span>

* <span data-ttu-id="1ae70-115">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ae70-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="1ae70-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1ae70-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="1ae70-117">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1ae70-117">Create the application</span></span>

1. <span data-ttu-id="1ae70-118">Utwórz **aplikację konsolową .NET Core** o nazwie "TextClassificationTF".</span><span class="sxs-lookup"><span data-stu-id="1ae70-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="1ae70-119">Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="1ae70-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="1ae70-120">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="1ae70-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="1ae70-121">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1ae70-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="1ae70-122">Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz kartę **przeglądanie** . Wyszukaj pozycję **Microsoft.ml**, wybierz żądany pakiet, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="1ae70-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="1ae70-123">Kontynuuj instalację, zgadzając się z postanowieniami licencyjnymi dotyczącymi wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="1ae70-124">Powtórz te kroki dla **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="1ae70-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="1ae70-125">Dodawanie modelu TensorFlow do projektu</span><span class="sxs-lookup"><span data-stu-id="1ae70-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="1ae70-126">Model tego samouczka pochodzi z repozytorium w witrynie GitHub [/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="1ae70-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="1ae70-127">Model jest w formacie TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="1ae70-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="1ae70-128">Pobierz [plik zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="1ae70-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="1ae70-129">Plik zip zawiera:</span><span class="sxs-lookup"><span data-stu-id="1ae70-129">The zip file contains:</span></span>

    * <span data-ttu-id="1ae70-130">`saved_model.pb`: sam model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1ae70-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="1ae70-131">Model przyjmuje stałą długość (w rozmiarze 600) tablicę funkcji reprezentujących tekst w ciągu przeglądu IMDB i wyprowadza dwa prawdopodobieństwa, które są sumowane do 1: prawdopodobieństwo, że przegląd danych wejściowych ma pozytywne tonacji, i prawdopodobieństwo, że przegląd danych wejściowych ma ujemna tonacji.</span><span class="sxs-lookup"><span data-stu-id="1ae70-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="1ae70-132">`imdb_word_index.csv`: mapowanie poszczególnych wyrazów na wartość całkowitą.</span><span class="sxs-lookup"><span data-stu-id="1ae70-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="1ae70-133">Mapowanie jest używane do generowania funkcji wejściowych dla modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1ae70-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="1ae70-134">Skopiuj zawartość wewnętrznego `sentiment_model` katalogu do katalogu projektu `sentiment_model` *TextClassificationTF* .</span><span class="sxs-lookup"><span data-stu-id="1ae70-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="1ae70-135">Ten katalog zawiera model i dodatkowe pliki pomocnicze, które są odpowiednie dla tego samouczka, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="1ae70-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![zawartość katalogu sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="1ae70-137">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy każdy plik w `sentiment_model` katalogu i podkatalogu, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1ae70-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="1ae70-138">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="1ae70-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="1ae70-139">Dodaj instrukcje using i zmienne globalne</span><span class="sxs-lookup"><span data-stu-id="1ae70-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="1ae70-140">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="1ae70-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="1ae70-141">Utwórz dwie zmienne globalne bezpośrednio powyżej `Main` metody przechowywania zapisanej ścieżki pliku modelu i długość wektora funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ae70-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="1ae70-142">`_modelPath`jest ścieżką do pliku nauczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="1ae70-143">`FeatureLength`jest długością tablicy funkcji całkowitej, której oczekuje model.</span><span class="sxs-lookup"><span data-stu-id="1ae70-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="1ae70-144">Modelowanie danych</span><span class="sxs-lookup"><span data-stu-id="1ae70-144">Model the data</span></span>

<span data-ttu-id="1ae70-145">Przeglądy filmów są bezpłatne tekstu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-145">Movie reviews are free form text.</span></span> <span data-ttu-id="1ae70-146">Aplikacja konwertuje tekst na format wejściowy oczekiwany przez model w wielu odrębnych etapach.</span><span class="sxs-lookup"><span data-stu-id="1ae70-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="1ae70-147">Pierwszym jest podział tekstu na oddzielne słowa i użycie podanego pliku mapowania do mapowania każdego wyrazu na kodowanie całkowite.</span><span class="sxs-lookup"><span data-stu-id="1ae70-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="1ae70-148">Wynikiem tej transformacji jest tablica o zmiennej długości całkowitej o długości odpowiadającej liczbie wyrazów w zdaniu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="1ae70-149">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1ae70-149">Property</span></span>| <span data-ttu-id="1ae70-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="1ae70-150">Value</span></span>|<span data-ttu-id="1ae70-151">Typ</span><span class="sxs-lookup"><span data-stu-id="1ae70-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="1ae70-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="1ae70-152">ReviewText</span></span>|<span data-ttu-id="1ae70-153">Ta folia jest naprawdę dobra</span><span class="sxs-lookup"><span data-stu-id="1ae70-153">this film is really good</span></span>|<span data-ttu-id="1ae70-154">string</span><span class="sxs-lookup"><span data-stu-id="1ae70-154">string</span></span>|
|<span data-ttu-id="1ae70-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="1ae70-155">VariableLengthFeatures</span></span>|<span data-ttu-id="1ae70-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="1ae70-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="1ae70-157">int []</span><span class="sxs-lookup"><span data-stu-id="1ae70-157">int[]</span></span>|

<span data-ttu-id="1ae70-158">Rozmiar tablicy funkcji o zmiennej długości jest zmieniany na stałą długość wynoszącą 600.</span><span class="sxs-lookup"><span data-stu-id="1ae70-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="1ae70-159">Jest to długość oczekiwana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1ae70-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="1ae70-160">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1ae70-160">Property</span></span>| <span data-ttu-id="1ae70-161">Wartość</span><span class="sxs-lookup"><span data-stu-id="1ae70-161">Value</span></span>|<span data-ttu-id="1ae70-162">Typ</span><span class="sxs-lookup"><span data-stu-id="1ae70-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="1ae70-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="1ae70-163">ReviewText</span></span>|<span data-ttu-id="1ae70-164">Ta folia jest naprawdę dobra</span><span class="sxs-lookup"><span data-stu-id="1ae70-164">this film is really good</span></span>|<span data-ttu-id="1ae70-165">string</span><span class="sxs-lookup"><span data-stu-id="1ae70-165">string</span></span>|
|<span data-ttu-id="1ae70-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="1ae70-166">VariableLengthFeatures</span></span>|<span data-ttu-id="1ae70-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="1ae70-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="1ae70-168">int []</span><span class="sxs-lookup"><span data-stu-id="1ae70-168">int[]</span></span>|
|<span data-ttu-id="1ae70-169">Funkcje</span><span class="sxs-lookup"><span data-stu-id="1ae70-169">Features</span></span>|<span data-ttu-id="1ae70-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="1ae70-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="1ae70-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="1ae70-171">int[600]</span></span>|

1. <span data-ttu-id="1ae70-172">Utwórz klasę danych wejściowych po `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="1ae70-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="1ae70-173">Klasa danych wejściowych, `MovieReview`, `string` ma dla komentarzy użytkownika (`ReviewText`).</span><span class="sxs-lookup"><span data-stu-id="1ae70-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="1ae70-174">Utwórz klasę dla funkcji o zmiennej długości, po `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="1ae70-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="1ae70-175">Właściwość ma atrybut vectortype służący do wyznaczania go jako wektor. [](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) `VariableLengthFeatures`</span><span class="sxs-lookup"><span data-stu-id="1ae70-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="1ae70-176">Wszystkie elementy wektorowe muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="1ae70-177">W przypadku zestawów danych z dużą liczbą kolumn ładowanie wielu kolumn jako jednego wektora zmniejsza liczbę danych przekazywanych w przypadku zastosowania transformacji danych.</span><span class="sxs-lookup"><span data-stu-id="1ae70-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="1ae70-178">Ta klasa jest używana w `ResizeFeatures` akcji.</span><span class="sxs-lookup"><span data-stu-id="1ae70-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="1ae70-179">Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania kolumn w widoku danych, które mogą być używane jako _dane wejściowe_ niestandardowej akcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="1ae70-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="1ae70-180">Utwórz klasę dla funkcji o stałej długości, po zastosowaniu `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="1ae70-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="1ae70-181">Ta klasa jest używana w `ResizeFeatures` akcji.</span><span class="sxs-lookup"><span data-stu-id="1ae70-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="1ae70-182">Nazwy jego właściwości (w tym przypadku tylko jeden) są używane do wskazania kolumn w widoku danych, które mogą być używane jako _dane wyjściowe_ niestandardowej akcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="1ae70-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="1ae70-183">Należy zauważyć, że nazwa właściwości `Features` jest określana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1ae70-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="1ae70-184">Nie można zmienić tej nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="1ae70-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="1ae70-185">Utwórz klasę dla przewidywania po `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="1ae70-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="1ae70-186">`MovieReviewSentimentPrediction`jest klasą predykcyjną używaną po przekształceniu modelu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="1ae70-187">`MovieReviewSentimentPrediction`ma jedną `float` tablicę (`Prediction`) i `VectorType` atrybut.</span><span class="sxs-lookup"><span data-stu-id="1ae70-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="1ae70-188">Tworzenie MLContext, słownika wyszukiwania i akcji w celu zmiany rozmiaru funkcji</span><span class="sxs-lookup"><span data-stu-id="1ae70-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="1ae70-189">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET.</span><span class="sxs-lookup"><span data-stu-id="1ae70-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="1ae70-190">Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="1ae70-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="1ae70-191">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1ae70-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="1ae70-192">Zastąp `Main` wiersz w metodzie poniższym kodem, aby zadeklarować i zainicjować zmienną mlContext: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="1ae70-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="1ae70-193">Utwórz słownik do kodowania wyrazów jako liczby całkowite przy użyciu [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metody ładowania danych mapowania z pliku, jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="1ae70-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="1ae70-194">Word</span><span class="sxs-lookup"><span data-stu-id="1ae70-194">Word</span></span>     |<span data-ttu-id="1ae70-195">Indeks</span><span class="sxs-lookup"><span data-stu-id="1ae70-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="1ae70-196">bezpiecznego</span><span class="sxs-lookup"><span data-stu-id="1ae70-196">kids</span></span>     |  <span data-ttu-id="1ae70-197">362</span><span class="sxs-lookup"><span data-stu-id="1ae70-197">362</span></span>    |
    |<span data-ttu-id="1ae70-198">Możesz</span><span class="sxs-lookup"><span data-stu-id="1ae70-198">want</span></span>     |  <span data-ttu-id="1ae70-199">181</span><span class="sxs-lookup"><span data-stu-id="1ae70-199">181</span></span>    |
    |<span data-ttu-id="1ae70-200">odpowiednich</span><span class="sxs-lookup"><span data-stu-id="1ae70-200">wrong</span></span>    |  <span data-ttu-id="1ae70-201">355</span><span class="sxs-lookup"><span data-stu-id="1ae70-201">355</span></span>    |
    |<span data-ttu-id="1ae70-202">efekty</span><span class="sxs-lookup"><span data-stu-id="1ae70-202">effects</span></span>  |  <span data-ttu-id="1ae70-203">302</span><span class="sxs-lookup"><span data-stu-id="1ae70-203">302</span></span>    |
    |<span data-ttu-id="1ae70-204">całkiem</span><span class="sxs-lookup"><span data-stu-id="1ae70-204">feeling</span></span>  |  <span data-ttu-id="1ae70-205">547</span><span class="sxs-lookup"><span data-stu-id="1ae70-205">547</span></span>    |

    <span data-ttu-id="1ae70-206">Dodaj poniższy kod, aby utworzyć mapę wyszukiwania:</span><span class="sxs-lookup"><span data-stu-id="1ae70-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="1ae70-207">Dodaj, `Action` aby zmienić rozmiar tablicy tablica liczb całkowitych wyrazów o zmiennej długości do tablicy o stałym rozmiarze, z następnymi wierszami kodu:</span><span class="sxs-lookup"><span data-stu-id="1ae70-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="1ae70-208">Załaduj wstępnie szkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="1ae70-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="1ae70-209">Dodaj kod, aby załadować model TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="1ae70-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="1ae70-210">Po załadowaniu modelu można wyodrębnić jego schemat wejściowy i wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="1ae70-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="1ae70-211">Schematy są wyświetlane tylko dla zainteresowania i tylko do celów szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="1ae70-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="1ae70-212">Ten kod nie jest potrzebny do działania końcowej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="1ae70-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="1ae70-213">Schemat wejściowy jest tablicą o stałej długości w postaci słów szyfrowanych liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="1ae70-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="1ae70-214">Schemat danych wyjściowych jest tablicą zmiennoprzecinkową prawdopodobieństwa wskazującą, czy tonacji przeglądu jest ujemna, czy dodatnia.</span><span class="sxs-lookup"><span data-stu-id="1ae70-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="1ae70-215">Te wartości są sumowane do 1, ponieważ prawdopodobieństwo wystąpienia pozytywnego jest uzupełnieniem prawdopodobieństwa, że tonacji jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="1ae70-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="1ae70-216">Tworzenie potoku ML.NET</span><span class="sxs-lookup"><span data-stu-id="1ae70-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="1ae70-217">Utwórz potok i Podziel tekst wejściowy na słowa przy użyciu transformacji [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) , aby podzielić tekst na wyrazy jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="1ae70-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="1ae70-218">Transformacja [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) używa spacji do analizowania tekstu/ciągu w słowach.</span><span class="sxs-lookup"><span data-stu-id="1ae70-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="1ae70-219">Tworzy nową kolumnę i dzieli każdy ciąg wejściowy na wektor podciągów w oparciu o separator zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1ae70-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="1ae70-220">Mapuj słowa na ich kodowanie całkowite przy użyciu tabeli odnośników zadeklarowanej powyżej:</span><span class="sxs-lookup"><span data-stu-id="1ae70-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="1ae70-221">Zmień rozmiar kodowania Integer o zmiennej długości na stałą długość określoną przez model:</span><span class="sxs-lookup"><span data-stu-id="1ae70-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="1ae70-222">Klasyfikuj dane wejściowe za pomocą załadowanego modelu TensorFlow:</span><span class="sxs-lookup"><span data-stu-id="1ae70-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="1ae70-223">Zostanie wywołana `Prediction/Softmax`wartość wyjściowa modelu TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1ae70-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="1ae70-224">Należy zauważyć, że `Prediction/Softmax` nazwa jest określana przez model TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="1ae70-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="1ae70-225">Nie można zmienić tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ae70-225">You cannot change this name.</span></span>

1. <span data-ttu-id="1ae70-226">Utwórz nową kolumnę przewidywania danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="1ae70-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="1ae70-227">Należy skopiować `Prediction/Softmax` kolumnę na jedną z nazwą, która może być używana jako właściwość w C# klasie: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="1ae70-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="1ae70-228">Znak jest niedozwolony w nazwie C# właściwości. `/`</span><span class="sxs-lookup"><span data-stu-id="1ae70-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="1ae70-229">Tworzenie modelu ML.NET z potoku</span><span class="sxs-lookup"><span data-stu-id="1ae70-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="1ae70-230">Dodaj kod, aby utworzyć model z potoku:</span><span class="sxs-lookup"><span data-stu-id="1ae70-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="1ae70-231">Model ml.NET jest tworzony na podstawie łańcucha szacowania w potoku przez wywołanie `Fit` metody.</span><span class="sxs-lookup"><span data-stu-id="1ae70-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="1ae70-232">W takim przypadku nie dopasowujemy żadnych danych w celu utworzenia modelu, ponieważ model TensorFlow został już wcześniej przeszkolony.</span><span class="sxs-lookup"><span data-stu-id="1ae70-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="1ae70-233">Dostarczamy pusty obiekt widoku danych w celu spełnienia wymagań `Fit` metody.</span><span class="sxs-lookup"><span data-stu-id="1ae70-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="1ae70-234">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="1ae70-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="1ae70-235">`PredictSentiment` Dodaj metodę`Main` poniżej metody:</span><span class="sxs-lookup"><span data-stu-id="1ae70-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="1ae70-236">Dodaj następujący kod, aby utworzyć `PredictionEngine` jako pierwszy wiersz `PredictSentiment()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="1ae70-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="1ae70-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="1ae70-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to make a prediction on a single instance of data.</span></span>

1. <span data-ttu-id="1ae70-238">Dodaj komentarz, aby przetestować prognozę przeszkolonego modelu w `Predict()` metodzie, tworząc `MovieReview`wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="1ae70-238">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="1ae70-239">Przekaż dane komentarza testowego do `Prediction Engine` obiektu przez dodanie następnych wierszy kodu `PredictSentiment()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="1ae70-239">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="1ae70-240">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) wykonuje prognozowanie w jednym wierszu danych:</span><span class="sxs-lookup"><span data-stu-id="1ae70-240">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="1ae70-241">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1ae70-241">Property</span></span>| <span data-ttu-id="1ae70-242">Wartość</span><span class="sxs-lookup"><span data-stu-id="1ae70-242">Value</span></span>|<span data-ttu-id="1ae70-243">Typ</span><span class="sxs-lookup"><span data-stu-id="1ae70-243">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="1ae70-244">Prognozy</span><span class="sxs-lookup"><span data-stu-id="1ae70-244">Prediction</span></span>|<span data-ttu-id="1ae70-245">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="1ae70-245">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="1ae70-246">float []</span><span class="sxs-lookup"><span data-stu-id="1ae70-246">float[]</span></span>|

1. <span data-ttu-id="1ae70-247">Wyświetl prognozowanie tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1ae70-247">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="1ae70-248">Dodaj wywołanie do `PredictSentiment` końca `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="1ae70-248">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="1ae70-249">Wyniki</span><span class="sxs-lookup"><span data-stu-id="1ae70-249">Results</span></span>

<span data-ttu-id="1ae70-250">Kompiluj i uruchamiaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="1ae70-250">Build and run your application.</span></span>

<span data-ttu-id="1ae70-251">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="1ae70-251">Your results should be similar to the following.</span></span> <span data-ttu-id="1ae70-252">Podczas przetwarzania wyświetlane są komunikaty.</span><span class="sxs-lookup"><span data-stu-id="1ae70-252">During processing, messages are displayed.</span></span> <span data-ttu-id="1ae70-253">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1ae70-253">You may see warnings, or processing messages.</span></span> <span data-ttu-id="1ae70-254">Te komunikaty zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="1ae70-254">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="1ae70-255">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="1ae70-255">Congratulations!</span></span> <span data-ttu-id="1ae70-256">Pomyślnie skompilowano model uczenia maszynowego do klasyfikowania i przewidywania komunikatów tonacji przez ponowne użycie wstępnie nauczonego `TensorFlow` modelu w ml.NET.</span><span class="sxs-lookup"><span data-stu-id="1ae70-256">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="1ae70-257">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) .</span><span class="sxs-lookup"><span data-stu-id="1ae70-257">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="1ae70-258">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1ae70-258">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="1ae70-259">Załaduj wstępnie szkolony model TensorFlow</span><span class="sxs-lookup"><span data-stu-id="1ae70-259">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="1ae70-260">Przekształć tekst komentarza witryny internetowej w funkcje odpowiednie dla modelu</span><span class="sxs-lookup"><span data-stu-id="1ae70-260">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="1ae70-261">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="1ae70-261">Use the model to make a prediction</span></span>
