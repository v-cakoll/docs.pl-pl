---
title: 'Samouczek: Analizowanie komentarzy witryny sieci Web — klasyfikacja binarna'
description: W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: f89174204c13b907db5a41ed374e1a31c61dcf11
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929027"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="a77e9-104">Samouczek: Analizuj tonacji komentarzy witryny internetowej za pomocą klasyfikacji binarnej w ML.NET</span><span class="sxs-lookup"><span data-stu-id="a77e9-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="a77e9-105">W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="a77e9-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="a77e9-106">Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a77e9-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="a77e9-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a77e9-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a77e9-108">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a77e9-108">Create a console application</span></span>
> - <span data-ttu-id="a77e9-109">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="a77e9-109">Prepare data</span></span>
> - <span data-ttu-id="a77e9-110">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a77e9-110">Load the data</span></span>
> - <span data-ttu-id="a77e9-111">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-111">Build and train the model</span></span>
> - <span data-ttu-id="a77e9-112">Oceń model</span><span class="sxs-lookup"><span data-stu-id="a77e9-112">Evaluate the model</span></span>
> - <span data-ttu-id="a77e9-113">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="a77e9-114">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="a77e9-114">See the results</span></span>

<span data-ttu-id="a77e9-115">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="a77e9-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a77e9-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a77e9-116">Prerequisites</span></span>

- <span data-ttu-id="a77e9-117">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a77e9-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="a77e9-118">[UCI tonacji — zestaw danych zdań z etykietą](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (Plik ZIP)</span><span class="sxs-lookup"><span data-stu-id="a77e9-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a77e9-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a77e9-119">Create a console application</span></span>

1. <span data-ttu-id="a77e9-120">Utwórz **aplikację konsolową .NET Core** o nazwie "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="a77e9-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="a77e9-121">Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="a77e9-122">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="a77e9-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="a77e9-123">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a77e9-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a77e9-124">Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz kartę **przeglądanie** . Wyszukaj pozycję **Microsoft.ml**, wybierz żądany pakiet, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="a77e9-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="a77e9-125">Kontynuuj instalację, zgadzając się z postanowieniami licencyjnymi dotyczącymi wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="a77e9-126">Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="a77e9-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="a77e9-127">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="a77e9-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="a77e9-128">Zestawy danych dla tego samouczka pochodzą z grupy "from do poszczególnych etykiet przy użyciu funkcji głębokiej", Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="a77e9-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="a77e9-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="a77e9-129">al,.</span></span> <span data-ttu-id="a77e9-130">KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="a77e9-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="a77e9-131">/Na Machine Learning repozytorium http://archive.ics.uci.edu/ml [].</span><span class="sxs-lookup"><span data-stu-id="a77e9-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="a77e9-132">Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputerowe.</span><span class="sxs-lookup"><span data-stu-id="a77e9-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="a77e9-133">Pobierz [UCI tonacji oznaczone zdaniami w pliku zip](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="a77e9-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="a77e9-134">Skopiuj plik do utworzonego katalogu *danych.* `yelp_labelled.txt`</span><span class="sxs-lookup"><span data-stu-id="a77e9-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="a77e9-135">W Eksplorator rozwiązań kliknij prawym przyciskiem `yelp_labeled.txt` myszy plik i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a77e9-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="a77e9-136">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="a77e9-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a77e9-137">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="a77e9-137">Create classes and define paths</span></span>

1. <span data-ttu-id="a77e9-138">Dodaj następujące dodatkowe `using` instrukcje na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="a77e9-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="a77e9-139">Utwórz dwa pola globalne do przechowywania ostatnio pobranej ścieżki pliku zestawu danych i zapisanej ścieżki pliku modelu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    - <span data-ttu-id="a77e9-140">`_dataPath`ma ścieżkę do zestawu danych używanego do uczenia modelu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    - <span data-ttu-id="a77e9-141">`_modelPath`ma ścieżkę, w której jest zapisywany model szkolony.</span><span class="sxs-lookup"><span data-stu-id="a77e9-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="a77e9-142">Dodaj następujący kod do wiersza bezpośrednio powyżej `Main` metody, aby określić ścieżki:</span><span class="sxs-lookup"><span data-stu-id="a77e9-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="a77e9-143">Następnie utwórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="a77e9-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="a77e9-144">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="a77e9-145">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="a77e9-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="a77e9-146">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="a77e9-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="a77e9-147">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="a77e9-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="a77e9-148">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="a77e9-149">Dodaj następującą `using` instrukcję na początku *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="a77e9-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="a77e9-150">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `SentimentData` i `SentimentPrediction`, do pliku *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="a77e9-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="a77e9-151">Jak dane zostały przygotowane</span><span class="sxs-lookup"><span data-stu-id="a77e9-151">How the data was prepared</span></span>
<span data-ttu-id="a77e9-152">Wejściowa Klasa DataSet, `SentimentData`, `string` ma dla `bool` komentarzy użytkownika (`SentimentText`) i (`Sentiment`) wartość 1 (pozytywna) lub 0 (ujemna) dla tonacji.</span><span class="sxs-lookup"><span data-stu-id="a77e9-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="a77e9-153">Oba pola mają dołączone atrybuty [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) , które opisują kolejność plików danych każdego pola.</span><span class="sxs-lookup"><span data-stu-id="a77e9-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="a77e9-154">Ponadto `Sentiment` właściwość ma atrybut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) , aby `Label` wyznaczyć go jako pole.</span><span class="sxs-lookup"><span data-stu-id="a77e9-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="a77e9-155">Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="a77e9-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="a77e9-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="a77e9-156">SentimentText</span></span>                         |<span data-ttu-id="a77e9-157">Tonacji (etykieta)</span><span class="sxs-lookup"><span data-stu-id="a77e9-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="a77e9-158">Waitress był nieco wolny w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a77e9-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="a77e9-159">0</span><span class="sxs-lookup"><span data-stu-id="a77e9-159">0</span></span>     |
|<span data-ttu-id="a77e9-160">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="a77e9-160">Crust is not good.</span></span>                    |    <span data-ttu-id="a77e9-161">0</span><span class="sxs-lookup"><span data-stu-id="a77e9-161">0</span></span>     |
|<span data-ttu-id="a77e9-162">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="a77e9-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="a77e9-163">1</span><span class="sxs-lookup"><span data-stu-id="a77e9-163">1</span></span>     |
|<span data-ttu-id="a77e9-164">Usługa była bardzo monitem.</span><span class="sxs-lookup"><span data-stu-id="a77e9-164">Service was very prompt.</span></span>              |    <span data-ttu-id="a77e9-165">1</span><span class="sxs-lookup"><span data-stu-id="a77e9-165">1</span></span>     |

<span data-ttu-id="a77e9-166">`SentimentPrediction`jest klasą przewidywania używaną po przekształceniu modelu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-166">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="a77e9-167">Dziedziczy po `SentimentData` , tak aby dane wejściowe `SentimentText` mogły być wyświetlane wraz z przewidywaniam danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-167">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="a77e9-168">Wartość logiczna jest wartością przewidywalną przez model, gdy jest dostarczany z nowymi danymi wejściowymi `SentimentText`. `Prediction`</span><span class="sxs-lookup"><span data-stu-id="a77e9-168">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="a77e9-169">Klasa `SentimentPrediction` Output zawiera dwie inne właściwości obliczone przez model: `Score` — nieprzetworzony wynik obliczony przez model i `Probability` -wynik uzyskany do prawdopodobieństwa, że tekst ma dodatnie tonacji.</span><span class="sxs-lookup"><span data-stu-id="a77e9-169">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="a77e9-170">W tym samouczku najważniejszym właściwość jest `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="a77e9-170">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="a77e9-171">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a77e9-171">Load the data</span></span>
<span data-ttu-id="a77e9-172">Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="a77e9-172">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="a77e9-173">`IDataView`to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="a77e9-173">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="a77e9-174">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-174">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="a77e9-175">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET.</span><span class="sxs-lookup"><span data-stu-id="a77e9-175">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="a77e9-176">Inicjowanie `mlContext` tworzy nowe środowisko ml.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-176">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a77e9-177">Jest to podobne, pojęciowo do `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a77e9-177">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="a77e9-178">Przygotujesz aplikację, a następnie załadujesz dane:</span><span class="sxs-lookup"><span data-stu-id="a77e9-178">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="a77e9-179">Zastąp `Main` wiersz w metodzie poniższym kodem, aby zadeklarować i zainicjować zmienną mlContext: `Console.WriteLine("Hello World!")`</span><span class="sxs-lookup"><span data-stu-id="a77e9-179">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="a77e9-180">Dodaj następujący kod jako następny wiersz kodu w `Main()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-180">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="a77e9-181">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `LoadData()`</span><span class="sxs-lookup"><span data-stu-id="a77e9-181">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="a77e9-182">`LoadData()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a77e9-182">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="a77e9-183">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="a77e9-183">Loads the data.</span></span>
    - <span data-ttu-id="a77e9-184">Dzieli załadowany zestaw danych na pociąg i testowe zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-184">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="a77e9-185">Zwraca zestawienie pociągów i testów zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-185">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="a77e9-186">Dodaj następujący kod jako pierwszy wiersz `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="a77e9-186">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="a77e9-187">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="a77e9-187">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="a77e9-188">Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="a77e9-188">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="a77e9-189">Podziel zestaw danych na potrzeby szkolenia i testowania modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-189">Split the dataset for model training and testing</span></span>

<span data-ttu-id="a77e9-190">Podczas przygotowywania modelu należy użyć części zestawu danych, aby szkolić i części zestawu danych w celu przetestowania dokładności modelu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-190">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="a77e9-191">Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod jako następny wiersz w `LoadData()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-191">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="a77e9-192">Poprzedni kod używa metody [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) , aby podzielić załadowany zestaw danych na pociąg i test zestawy danych i zwrócić je w klasie [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) .</span><span class="sxs-lookup"><span data-stu-id="a77e9-192">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="a77e9-193">Określ wartość procentową zestawu testów dla danych z `testFraction`parametrem.</span><span class="sxs-lookup"><span data-stu-id="a77e9-193">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="a77e9-194">Wartość domyślna to 10%, w tym przypadku do obliczenia większej ilości danych służy 20%.</span><span class="sxs-lookup"><span data-stu-id="a77e9-194">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="a77e9-195">Zwróć na końcu `LoadData()`metody: `splitDataView`</span><span class="sxs-lookup"><span data-stu-id="a77e9-195">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="a77e9-196">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-196">Build and train the model</span></span>

1. <span data-ttu-id="a77e9-197">Dodaj następujące wywołanie do `BuildAndTrainModel`metody jako następny wiersz kodu `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-197">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="a77e9-198">`BuildAndTrainModel()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a77e9-198">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="a77e9-199">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="a77e9-199">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="a77e9-200">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="a77e9-200">Trains the model.</span></span>
    - <span data-ttu-id="a77e9-201">Przewidywania tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-201">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="a77e9-202">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="a77e9-202">Returns the model.</span></span>

2. <span data-ttu-id="a77e9-203">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Main()` `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="a77e9-203">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="a77e9-204">Wyodrębnij i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="a77e9-204">Extract and transform the data</span></span>

1. <span data-ttu-id="a77e9-205">Wywołaj `FeaturizeText` jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-205">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="a77e9-206">Metoda w poprzednim kodzie konwertuje kolumnę tekstową (`SentimentText`) na kolumnę typu `Features` wartości liczbowej używanej przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych: `FeaturizeText()`</span><span class="sxs-lookup"><span data-stu-id="a77e9-206">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="a77e9-207">SentimentText</span><span class="sxs-lookup"><span data-stu-id="a77e9-207">SentimentText</span></span>                         |<span data-ttu-id="a77e9-208">Tonacji</span><span class="sxs-lookup"><span data-stu-id="a77e9-208">Sentiment</span></span> |<span data-ttu-id="a77e9-209">Funkcje</span><span class="sxs-lookup"><span data-stu-id="a77e9-209">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="a77e9-210">Waitress był nieco wolny w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a77e9-210">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="a77e9-211">0</span><span class="sxs-lookup"><span data-stu-id="a77e9-211">0</span></span>     |<span data-ttu-id="a77e9-212">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="a77e9-212">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="a77e9-213">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="a77e9-213">Crust is not good.</span></span>                    |    <span data-ttu-id="a77e9-214">0</span><span class="sxs-lookup"><span data-stu-id="a77e9-214">0</span></span>     |<span data-ttu-id="a77e9-215">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="a77e9-215">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="a77e9-216">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="a77e9-216">Wow... Loved this place.</span></span>              |    <span data-ttu-id="a77e9-217">1</span><span class="sxs-lookup"><span data-stu-id="a77e9-217">1</span></span>     |<span data-ttu-id="a77e9-218">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="a77e9-218">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="a77e9-219">Usługa była bardzo monitem.</span><span class="sxs-lookup"><span data-stu-id="a77e9-219">Service was very prompt.</span></span>              |    <span data-ttu-id="a77e9-220">1</span><span class="sxs-lookup"><span data-stu-id="a77e9-220">1</span></span>     |<span data-ttu-id="a77e9-221">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="a77e9-221">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="a77e9-222">Dodawanie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="a77e9-222">Add a learning algorithm</span></span>

<span data-ttu-id="a77e9-223">Ta aplikacja używa algorytmu klasyfikacji, który klasyfikuje elementy lub wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-223">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="a77e9-224">Aplikacja klasyfikuje Komentarze witryny sieci Web jako wartość dodatnią lub ujemną, więc Użyj zadania klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="a77e9-224">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="a77e9-225">Dołącz zadanie uczenia maszynowego do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="a77e9-225">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="a77e9-226">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytmem szkoleniowym klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="a77e9-226">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="a77e9-227">Ta wartość jest dołączana `estimator` do i akceptuje featurized `SentimentText` (`Features`) i `Label` parametry wejściowe, aby poznać dane historyczne.</span><span class="sxs-lookup"><span data-stu-id="a77e9-227">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="a77e9-228">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-228">Train the model</span></span>

<span data-ttu-id="a77e9-229">Dopasuj model do `splitTrainSet` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu `BuildAndTrainModel()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-229">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="a77e9-230">Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="a77e9-230">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="a77e9-231">Zwróć model przeszkolony do użycia na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="a77e9-231">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="a77e9-232">Zwróć model na końcu `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="a77e9-232">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="a77e9-233">Oceń model</span><span class="sxs-lookup"><span data-stu-id="a77e9-233">Evaluate the model</span></span>

<span data-ttu-id="a77e9-234">Po przeszkoleniu modelu Użyj danych testowych, aby sprawdzić wydajność modelu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-234">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="a77e9-235">Utwórz metodę, tuż po `BuildAndTrainModel()`, przy użyciu następującego kodu: `Evaluate()`</span><span class="sxs-lookup"><span data-stu-id="a77e9-235">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="a77e9-236">`Evaluate()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a77e9-236">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="a77e9-237">Ładuje zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-237">Loads the test dataset.</span></span>
    - <span data-ttu-id="a77e9-238">Tworzy ewaluatora BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="a77e9-238">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="a77e9-239">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="a77e9-239">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="a77e9-240">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="a77e9-240">Displays the metrics.</span></span>

2. <span data-ttu-id="a77e9-241">Dodaj wywołanie do nowej metody z `Main()` metody, bezpośrednio `BuildAndTrainModel()` pod wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-241">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="a77e9-242">Przekształć `Evaluate()`dane, dodając następujący kod do: `splitTestSet`</span><span class="sxs-lookup"><span data-stu-id="a77e9-242">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="a77e9-243">Poprzedni kod używa metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) do przeprowadzania prognoz dla wielu podanych danych wejściowych dla testu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-243">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="a77e9-244">Oceń model poprzez dodanie następujących elementów jako następny wiersz kodu w `Evaluate()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-244">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="a77e9-245">Gdy posiadasz zestaw predykcyjny (`predictions`), Metoda [oceny ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z wartością rzeczywistą `Labels` w testowym zestawie danych i zwraca [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) Obiekt, na którym działa model.</span><span class="sxs-lookup"><span data-stu-id="a77e9-245">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="a77e9-246">Wyświetlanie metryk na potrzeby walidacji modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-246">Displaying the metrics for model validation</span></span>

<span data-ttu-id="a77e9-247">Użyj następującego kodu, aby wyświetlić metryki:</span><span class="sxs-lookup"><span data-stu-id="a77e9-247">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="a77e9-248">`Accuracy` Metryka pobiera dokładność modelu, który jest proporcją prawidłowych prognoz w zestawie testów.</span><span class="sxs-lookup"><span data-stu-id="a77e9-248">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="a77e9-249">`AreaUnderRocCurve` Metryka wskazuje, jak pewność, że model prawidłowo klasyfikuje klasy dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="a77e9-249">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="a77e9-250">Ma `AreaUnderRocCurve` być tak blisko jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a77e9-250">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="a77e9-251">Metryka pobiera wynik F1 modelu, który jest miarą równowagi między [dokładnością](../resources/glossary.md#precision) i [odwołaniem.](../resources/glossary.md#recall) `F1Score`</span><span class="sxs-lookup"><span data-stu-id="a77e9-251">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="a77e9-252">Ma `F1Score` być tak blisko jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a77e9-252">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="a77e9-253">Przewidywanie wyniku danych testowych</span><span class="sxs-lookup"><span data-stu-id="a77e9-253">Predict the test data outcome</span></span>

1. <span data-ttu-id="a77e9-254">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `Evaluate()` `UseModelWithSingleItem()`</span><span class="sxs-lookup"><span data-stu-id="a77e9-254">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="a77e9-255">`UseModelWithSingleItem()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a77e9-255">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="a77e9-256">Tworzy pojedynczy komentarz dotyczący danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-256">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="a77e9-257">Przewidywania tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-257">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="a77e9-258">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="a77e9-258">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="a77e9-259">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="a77e9-259">Displays the predicted results.</span></span>

2. <span data-ttu-id="a77e9-260">Dodaj wywołanie do nowej metody z `Main()` metody, bezpośrednio `Evaluate()` pod wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-260">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="a77e9-261">Dodaj następujący kod, aby utworzyć jako pierwszy wiersz w `UseModelWithSingleItem()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-261">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="a77e9-262">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który pozwala na przekazywanie danych, a następnie wykonywanie prognozowania na jednym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-262">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="a77e9-263">Dodaj komentarz, aby przetestować prognozę przeszkolonego modelu w `UseModelWithSingleItem()` metodzie, tworząc `SentimentData`wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-263">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="a77e9-264">Przekaż dane komentarza testowego do `Prediction Engine` elementu przez dodanie następujących elementów jako następnych wierszy kodu `UseModelWithSingleItem()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-264">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="a77e9-265">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-265">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="a77e9-266">Wyświetlaj `SentimentText` i odpowiadaj prognozie tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-266">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="a77e9-267">Używanie modelu do przewidywania</span><span class="sxs-lookup"><span data-stu-id="a77e9-267">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="a77e9-268">Wdrażanie i prognozowanie elementów wsadowych</span><span class="sxs-lookup"><span data-stu-id="a77e9-268">Deploy and predict batch items</span></span>

1. <span data-ttu-id="a77e9-269">Utwórz metodę, tuż po metodzie, przy użyciu następującego kodu: `UseModelWithSingleItem()` `UseModelWithBatchItems()`</span><span class="sxs-lookup"><span data-stu-id="a77e9-269">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="a77e9-270">`UseModelWithBatchItems()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a77e9-270">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="a77e9-271">Tworzy dane testów wsadowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-271">Creates batch test data.</span></span>
    - <span data-ttu-id="a77e9-272">Przewidywania tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="a77e9-272">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="a77e9-273">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="a77e9-273">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="a77e9-274">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="a77e9-274">Displays the predicted results.</span></span>

2. <span data-ttu-id="a77e9-275">Dodaj wywołanie do nowej metody z `Main` metody, bezpośrednio `UseModelWithSingleItem()` pod wywołaniem metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-275">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="a77e9-276">Dodaj komentarze, aby przetestować przewidywania modeli przeszkolonych w `UseModelWithBatchItems()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="a77e9-276">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="a77e9-277">Tonacji komentarz przewidywania</span><span class="sxs-lookup"><span data-stu-id="a77e9-277">Predict comment sentiment</span></span>

<span data-ttu-id="a77e9-278">Użyj modelu, aby przewidzieć tonacji danych komentarzy przy użyciu metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="a77e9-278">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="a77e9-279">Łączenie i wyświetlanie prognoz</span><span class="sxs-lookup"><span data-stu-id="a77e9-279">Combine and display the predictions</span></span>

<span data-ttu-id="a77e9-280">Utwórz nagłówek dla prognoz przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a77e9-280">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="a77e9-281">Ponieważ `SentimentPrediction` jest dziedziczona z `SentimentData`, `Transform()` Metoda jest wypełniana `SentimentText` polami przewidywanymi.</span><span class="sxs-lookup"><span data-stu-id="a77e9-281">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="a77e9-282">Gdy proces ML.NET przetwarza, każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:</span><span class="sxs-lookup"><span data-stu-id="a77e9-282">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="a77e9-283">Wyniki</span><span class="sxs-lookup"><span data-stu-id="a77e9-283">Results</span></span>

<span data-ttu-id="a77e9-284">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="a77e9-284">Your results should be similar to the following.</span></span> <span data-ttu-id="a77e9-285">Podczas przetwarzania wyświetlane są komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a77e9-285">During processing, messages are displayed.</span></span> <span data-ttu-id="a77e9-286">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a77e9-286">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a77e9-287">Zostały one usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="a77e9-287">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="a77e9-288">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="a77e9-288">Congratulations!</span></span> <span data-ttu-id="a77e9-289">Pomyślnie skompilowano model uczenia maszynowego do klasyfikowania i przewidywania komunikatów tonacji.</span><span class="sxs-lookup"><span data-stu-id="a77e9-289">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="a77e9-290">Kompilowanie udanych modeli jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="a77e9-290">Building successful models is an iterative process.</span></span> <span data-ttu-id="a77e9-291">Ten model ma wstępną niższą jakość, ponieważ samouczek używa małych zestawów danych w celu zapewnienia szybkiego szkolenia modeli.</span><span class="sxs-lookup"><span data-stu-id="a77e9-291">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="a77e9-292">Jeśli jakość modelu jest niezadowalająca, możesz spróbować go ulepszyć, dostarczając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi [parametrami funkcji Hyper-Parameters](../resources/glossary.md##hyperparameter) dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="a77e9-292">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="a77e9-293">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="a77e9-293">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a77e9-294">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a77e9-294">Next steps</span></span>

<span data-ttu-id="a77e9-295">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a77e9-295">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a77e9-296">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="a77e9-296">Create a console application</span></span>
> - <span data-ttu-id="a77e9-297">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="a77e9-297">Prepare data</span></span>
> - <span data-ttu-id="a77e9-298">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="a77e9-298">Load the data</span></span>
> - <span data-ttu-id="a77e9-299">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-299">Build and train the model</span></span>
> - <span data-ttu-id="a77e9-300">Oceń model</span><span class="sxs-lookup"><span data-stu-id="a77e9-300">Evaluate the model</span></span>
> - <span data-ttu-id="a77e9-301">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="a77e9-301">Use the model to make a prediction</span></span>
> - <span data-ttu-id="a77e9-302">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="a77e9-302">See the results</span></span>

<span data-ttu-id="a77e9-303">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="a77e9-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a77e9-304">Klasyfikacja problemu</span><span class="sxs-lookup"><span data-stu-id="a77e9-304">Issue Classification</span></span>](github-issue-classification.md)
