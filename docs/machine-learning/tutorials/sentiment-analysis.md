---
title: 'Samouczek: analizowanie komentarzy witryny sieci Web — klasyfikacja binarna'
description: W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e241ae8c0d39e6573b40c69611985f7095114629
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320144"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="e7b78-104">Samouczek: analizowanie tonacji komentarzy w witrynie sieci Web za pomocą klasyfikacji binarnej w ML.NET</span><span class="sxs-lookup"><span data-stu-id="e7b78-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="e7b78-105">W tym samouczku przedstawiono sposób tworzenia aplikacji konsolowej .NET Core, która klasyfikuje tonacji z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="e7b78-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="e7b78-106">Użycie C# binarnego klasyfikatora tonacji w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e7b78-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="e7b78-107">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e7b78-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e7b78-108">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e7b78-108">Create a console application</span></span>
> - <span data-ttu-id="e7b78-109">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="e7b78-109">Prepare data</span></span>
> - <span data-ttu-id="e7b78-110">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="e7b78-110">Load the data</span></span>
> - <span data-ttu-id="e7b78-111">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-111">Build and train the model</span></span>
> - <span data-ttu-id="e7b78-112">Oceń model</span><span class="sxs-lookup"><span data-stu-id="e7b78-112">Evaluate the model</span></span>
> - <span data-ttu-id="e7b78-113">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="e7b78-114">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="e7b78-114">See the results</span></span>

<span data-ttu-id="e7b78-115">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="e7b78-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7b78-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e7b78-116">Prerequisites</span></span>

- <span data-ttu-id="e7b78-117">[Program Visual Studio 2017 15,6 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e7b78-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="e7b78-118">[UCI tonacji z etykietą zestawu danych](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik zip)</span><span class="sxs-lookup"><span data-stu-id="e7b78-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e7b78-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e7b78-119">Create a console application</span></span>

1. <span data-ttu-id="e7b78-120">Utwórz **aplikację konsolową .NET Core** o nazwie "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="e7b78-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="e7b78-121">Utwórz katalog o nazwie *dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="e7b78-122">Zainstaluj **pakiet NuGet Microsoft.ml**:</span><span class="sxs-lookup"><span data-stu-id="e7b78-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="e7b78-123">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="e7b78-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e7b78-124">Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj** . wyszukaj pozycję **Microsoft.ml**, wybierz pakiet, a następnie wybierz przycisk **Instaluj** .</span><span class="sxs-lookup"><span data-stu-id="e7b78-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="e7b78-125">Kontynuuj instalację, zgadzając się z postanowieniami licencyjnymi dotyczącymi wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="e7b78-126">Wykonaj te same czynności dla pakietu NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="e7b78-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="e7b78-127">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="e7b78-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="e7b78-128">Zestawy danych dla tego samouczka pochodzą z grupy "from do poszczególnych etykiet przy użyciu funkcji głębokiej", Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="e7b78-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="e7b78-129">Al,.</span><span class="sxs-lookup"><span data-stu-id="e7b78-129">al,.</span></span> <span data-ttu-id="e7b78-130">KDD 2015 i hostowana w repozytorium Machine Learning/Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="e7b78-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="e7b78-131">/Na Machine Learning repozytorium [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="e7b78-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="e7b78-132">Irvine, CA: University of Kalifornii, szkolna informacja i nauka komputera.</span><span class="sxs-lookup"><span data-stu-id="e7b78-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="e7b78-133">Pobierz [UCI tonacji oznaczone zdaniami w pliku zip](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="e7b78-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="e7b78-134">Skopiuj plik `yelp_labelled.txt` do utworzonego katalogu *danych* .</span><span class="sxs-lookup"><span data-stu-id="e7b78-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="e7b78-135">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik `yelp_labeled.txt` i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e7b78-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="e7b78-136">W obszarze **Zaawansowane**Zmień wartość opcji **Kopiuj do katalogu wyjściowego** na Kopiuj, **jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="e7b78-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="e7b78-137">Tworzenie klas i Definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="e7b78-137">Create classes and define paths</span></span>

1. <span data-ttu-id="e7b78-138">Dodaj następujące dodatkowe instrukcje `using` na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="e7b78-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="e7b78-139">Dodaj następujący kod do wiersza bezpośrednio powyżej metody `Main`, aby utworzyć pole do przechowywania niedawno pobranej ścieżki pliku zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="e7b78-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="e7b78-140">Następnie utwórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="e7b78-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="e7b78-141">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="e7b78-142">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="e7b78-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="e7b78-143">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **Klasa** i zmień wartość pola **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="e7b78-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="e7b78-144">Następnie wybierz przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="e7b78-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="e7b78-145">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="e7b78-146">Dodaj następującą instrukcję `using` na początku *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="e7b78-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="e7b78-147">Usuń istniejącą definicję klasy i Dodaj następujący kod, który ma dwie klasy `SentimentData` i `SentimentPrediction` do pliku *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="e7b78-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="e7b78-148">Jak dane zostały przygotowane</span><span class="sxs-lookup"><span data-stu-id="e7b78-148">How the data was prepared</span></span>
<span data-ttu-id="e7b78-149">Wejściowa Klasa zestawu danych, `SentimentData`, ma `string` dla komentarzy użytkownika (`SentimentText`) i `bool` (`Sentiment`) wartości 1 (dodatni) lub 0 (wartość ujemna) dla tonacji.</span><span class="sxs-lookup"><span data-stu-id="e7b78-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="e7b78-150">Oba pola mają dołączone atrybuty [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) , które opisują kolejność plików danych każdego pola.</span><span class="sxs-lookup"><span data-stu-id="e7b78-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="e7b78-151">Ponadto Właściwość `Sentiment` ma atrybut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) , aby wyznaczyć go jako pole `Label`.</span><span class="sxs-lookup"><span data-stu-id="e7b78-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="e7b78-152">Następujący przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="e7b78-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="e7b78-153">SentimentText</span><span class="sxs-lookup"><span data-stu-id="e7b78-153">SentimentText</span></span>                         |<span data-ttu-id="e7b78-154">Tonacji (etykieta)</span><span class="sxs-lookup"><span data-stu-id="e7b78-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="e7b78-155">Waitress był nieco wolny w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e7b78-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="e7b78-156">0</span><span class="sxs-lookup"><span data-stu-id="e7b78-156">0</span></span>     |
|<span data-ttu-id="e7b78-157">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="e7b78-157">Crust is not good.</span></span>                    |    <span data-ttu-id="e7b78-158">0</span><span class="sxs-lookup"><span data-stu-id="e7b78-158">0</span></span>     |
|<span data-ttu-id="e7b78-159">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="e7b78-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="e7b78-160">1</span><span class="sxs-lookup"><span data-stu-id="e7b78-160">1</span></span>     |
|<span data-ttu-id="e7b78-161">Usługa była bardzo monitem.</span><span class="sxs-lookup"><span data-stu-id="e7b78-161">Service was very prompt.</span></span>              |    <span data-ttu-id="e7b78-162">1</span><span class="sxs-lookup"><span data-stu-id="e7b78-162">1</span></span>     |

<span data-ttu-id="e7b78-163">`SentimentPrediction` jest klasą przewidywania używaną po przekształceniu modelu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="e7b78-164">Dziedziczy po `SentimentData`, aby można było wyświetlić dane wejściowe `SentimentText` wraz z prognozą wyjściową.</span><span class="sxs-lookup"><span data-stu-id="e7b78-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="e7b78-165">Wartość logiczna `Prediction` jest wartością przewidywalną przez model, gdy jest dostarczany z nowymi danymi wejściowymi `SentimentText`.</span><span class="sxs-lookup"><span data-stu-id="e7b78-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="e7b78-166">Klasa wyjściowa `SentimentPrediction` zawiera dwie inne właściwości obliczone przez model: `Score` — nieprzetworzony wynik obliczony przez model i `Probability` — wynik kalibrowany do prawdopodobieństwa, że tekst ma pozytywne tonacji.</span><span class="sxs-lookup"><span data-stu-id="e7b78-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="e7b78-167">W tym samouczku najważniejszym właściwością jest `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="e7b78-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="e7b78-168">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="e7b78-168">Load the data</span></span>
<span data-ttu-id="e7b78-169">Dane w ML.NET są reprezentowane jako [Klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="e7b78-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="e7b78-170">`IDataView` to elastyczny i wydajny sposób opisywania danych tabelarycznych (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="e7b78-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="e7b78-171">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="e7b78-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="e7b78-172">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem początkowym dla wszystkich operacji ml.NET.</span><span class="sxs-lookup"><span data-stu-id="e7b78-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="e7b78-173">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które może być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="e7b78-174">Jest to podobne, pojęciowo, aby `DBContext` w Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e7b78-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="e7b78-175">Przygotujesz aplikację, a następnie załadujesz dane:</span><span class="sxs-lookup"><span data-stu-id="e7b78-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="e7b78-176">Zastąp wiersz `Console.WriteLine("Hello World!")` w metodzie `Main` następującym kodem, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="e7b78-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="e7b78-177">Dodaj następujący kod jako następny wiersz kodu w metodzie `Main()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="e7b78-178">Utwórz metodę `LoadData()` zaraz po metodzie `Main()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="e7b78-179">Metoda `LoadData()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e7b78-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e7b78-180">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="e7b78-180">Loads the data.</span></span>
    - <span data-ttu-id="e7b78-181">Dzieli załadowany zestaw danych na pociąg i testowe zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="e7b78-182">Zwraca zestawienie pociągów i testów zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="e7b78-183">Dodaj następujący kod jako pierwszy wiersz metody `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="e7b78-184">[LoadFromTextFile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="e7b78-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="e7b78-185">Przyjmuje zmienne ścieżki danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="e7b78-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="e7b78-186">Podziel zestaw danych na potrzeby szkolenia i testowania modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="e7b78-187">Podczas przygotowywania modelu należy użyć części zestawu danych, aby szkolić i części zestawu danych w celu przetestowania dokładności modelu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="e7b78-188">Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod jako następny wiersz w metodzie `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="e7b78-189">Poprzedni kod używa metody [TrainTestSplit ()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) , aby podzielić załadowany zestaw danych na pociąg i test zestawy danych i zwrócić je w klasie [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) .</span><span class="sxs-lookup"><span data-stu-id="e7b78-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="e7b78-190">Określ wartość procentową zestawu testów dla `testFraction`parameter.</span><span class="sxs-lookup"><span data-stu-id="e7b78-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="e7b78-191">Wartość domyślna to 10%, w tym przypadku do obliczenia większej ilości danych służy 20%.</span><span class="sxs-lookup"><span data-stu-id="e7b78-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="e7b78-192">Zwróć `splitDataView` na końcu metody `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="e7b78-193">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-193">Build and train the model</span></span>

1. <span data-ttu-id="e7b78-194">Dodaj następujące wywołanie do `BuildAndTrainModel`method jako następny wiersz kodu w metodzie `Main()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="e7b78-195">Metoda `BuildAndTrainModel()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e7b78-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e7b78-196">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="e7b78-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="e7b78-197">Pociąga za siebie model.</span><span class="sxs-lookup"><span data-stu-id="e7b78-197">Trains the model.</span></span>
    - <span data-ttu-id="e7b78-198">Przewidywania tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="e7b78-199">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="e7b78-199">Returns the model.</span></span>

2. <span data-ttu-id="e7b78-200">Utwórz metodę `BuildAndTrainModel()` zaraz po metodzie `Main()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="e7b78-201">Wyodrębnij i Przekształć dane</span><span class="sxs-lookup"><span data-stu-id="e7b78-201">Extract and transform the data</span></span>

1. <span data-ttu-id="e7b78-202">Wywołaj `FeaturizeText` jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="e7b78-203">Metoda `FeaturizeText()` w poprzednim kodzie konwertuje kolumnę tekstową (`SentimentText`) na typ klucza numerycznego `Features` kolumny używanej przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="e7b78-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="e7b78-204">SentimentText</span><span class="sxs-lookup"><span data-stu-id="e7b78-204">SentimentText</span></span>                         |<span data-ttu-id="e7b78-205">Tonacji</span><span class="sxs-lookup"><span data-stu-id="e7b78-205">Sentiment</span></span> |<span data-ttu-id="e7b78-206">Funkcje</span><span class="sxs-lookup"><span data-stu-id="e7b78-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="e7b78-207">Waitress był nieco wolny w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e7b78-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="e7b78-208">0</span><span class="sxs-lookup"><span data-stu-id="e7b78-208">0</span></span>     |<span data-ttu-id="e7b78-209">[0,76, 0,65, 0,44,...]</span><span class="sxs-lookup"><span data-stu-id="e7b78-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="e7b78-210">Crust nie jest dobry.</span><span class="sxs-lookup"><span data-stu-id="e7b78-210">Crust is not good.</span></span>                    |    <span data-ttu-id="e7b78-211">0</span><span class="sxs-lookup"><span data-stu-id="e7b78-211">0</span></span>     |<span data-ttu-id="e7b78-212">[0,98, 0,43, 0,54,...]</span><span class="sxs-lookup"><span data-stu-id="e7b78-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="e7b78-213">Wow... Uwielbiane to miejsce.</span><span class="sxs-lookup"><span data-stu-id="e7b78-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="e7b78-214">1</span><span class="sxs-lookup"><span data-stu-id="e7b78-214">1</span></span>     |<span data-ttu-id="e7b78-215">[0,35, 0,73, 0,46,...]</span><span class="sxs-lookup"><span data-stu-id="e7b78-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="e7b78-216">Usługa była bardzo monitem.</span><span class="sxs-lookup"><span data-stu-id="e7b78-216">Service was very prompt.</span></span>              |    <span data-ttu-id="e7b78-217">1</span><span class="sxs-lookup"><span data-stu-id="e7b78-217">1</span></span>     |<span data-ttu-id="e7b78-218">[0,39, 0, 0,75,...]</span><span class="sxs-lookup"><span data-stu-id="e7b78-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="e7b78-219">Dodawanie algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="e7b78-219">Add a learning algorithm</span></span>

<span data-ttu-id="e7b78-220">Ta aplikacja używa algorytmu klasyfikacji, który klasyfikuje elementy lub wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="e7b78-221">Aplikacja klasyfikuje Komentarze witryny sieci Web jako wartość dodatnią lub ujemną, więc Użyj zadania klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="e7b78-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="e7b78-222">Dołącz zadanie uczenia maszynowego do definicji transformacji danych, dodając następujący kod jako następny wiersz kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="e7b78-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytmem szkoleniowym klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e7b78-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="e7b78-224">Jest to dołączane do `estimator` i akceptuje featurized `SentimentText` (`Features`) i `Label` parametry wejściowe, aby poznać dane historyczne.</span><span class="sxs-lookup"><span data-stu-id="e7b78-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="e7b78-225">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-225">Train the model</span></span>

<span data-ttu-id="e7b78-226">Dopasuj model do `splitTrainSet` danych i zwróć przeszkolony model, dodając następujący kod jako następny wiersz kodu w metodzie `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="e7b78-227">Metoda [dopasowywania ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) pociąga za siebie model poprzez transformowanie zestawu danych i zastosowanie szkolenia.</span><span class="sxs-lookup"><span data-stu-id="e7b78-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="e7b78-228">Zwróć model przeszkolony do użycia na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="e7b78-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="e7b78-229">Zwróć model na końcu metody `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="e7b78-230">Oceń model</span><span class="sxs-lookup"><span data-stu-id="e7b78-230">Evaluate the model</span></span>

<span data-ttu-id="e7b78-231">Po przeszkoleniu modelu Użyj danych testowych, aby sprawdzić wydajność modelu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="e7b78-232">Utwórz metodę `Evaluate()` zaraz po `BuildAndTrainModel()`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="e7b78-233">Metoda `Evaluate()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e7b78-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e7b78-234">Ładuje zestaw danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="e7b78-235">Tworzy ewaluatora BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="e7b78-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="e7b78-236">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="e7b78-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="e7b78-237">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="e7b78-237">Displays the metrics.</span></span>

2. <span data-ttu-id="e7b78-238">Dodaj wywołanie do nowej metody z metody `Main()` bezpośrednio w wywołaniu metody `BuildAndTrainModel()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="e7b78-239">Przekształć dane `splitTestSet`, dodając następujący kod do `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="e7b78-240">Poprzedni kod używa metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) do przeprowadzania prognoz dla wielu podanych danych wejściowych dla testu zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="e7b78-241">Oceń model, dodając następujący wiersz kodu w metodzie `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="e7b78-242">Po utworzeniu zestawu predykcyjnego (`predictions`) Metoda [oceny ()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) ocenia model, który porównuje wartości przewidywane z rzeczywistym `Labels` w zestawie danych testów i zwraca obiekt [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) na sposób Trwa wykonywanie modelu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="e7b78-243">Wyświetlanie metryk na potrzeby walidacji modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="e7b78-244">Użyj następującego kodu, aby wyświetlić metryki:</span><span class="sxs-lookup"><span data-stu-id="e7b78-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="e7b78-245">Metryka `Accuracy` pobiera dokładność modelu, który jest proporcją prawidłowych prognoz w zestawie testów.</span><span class="sxs-lookup"><span data-stu-id="e7b78-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="e7b78-246">Metryka `AreaUnderRocCurve` wskazuje, jak pewność, że model prawidłowo klasyfikuje klasy dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="e7b78-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="e7b78-247">Chcesz, aby `AreaUnderRocCurve` był możliwie blisko jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e7b78-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="e7b78-248">Metryka `F1Score` pobiera wynik F1 modelu, który jest miarą równowagi między [dokładnością](../resources/glossary.md#precision) i [odwołaniem](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="e7b78-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="e7b78-249">Chcesz, aby `F1Score` był możliwie blisko jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e7b78-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="e7b78-250">Przewidywanie wyniku danych testowych</span><span class="sxs-lookup"><span data-stu-id="e7b78-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="e7b78-251">Utwórz metodę `UseModelWithSingleItem()` zaraz po metodzie `Evaluate()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="e7b78-252">Metoda `UseModelWithSingleItem()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e7b78-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e7b78-253">Tworzy pojedynczy komentarz dotyczący danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="e7b78-254">Przewidywania tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="e7b78-255">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="e7b78-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="e7b78-256">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="e7b78-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="e7b78-257">Dodaj wywołanie do nowej metody z metody `Main()` bezpośrednio w wywołaniu metody `Evaluate()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="e7b78-258">Dodaj następujący kod, aby utworzyć jako pierwszy wiersz w metodzie `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="e7b78-259">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest WYGODNYm interfejsem API, który umożliwia prognozowanie jednego wystąpienia danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="e7b78-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nie jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="e7b78-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="e7b78-261">Jest to możliwe do użycia w środowiskach wielowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="e7b78-262">Aby zwiększyć wydajność i bezpieczeństwo wątków w środowiskach produkcyjnych, Użyj usługi `PredictionEnginePool`, która tworzy [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) obiektów do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7b78-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="e7b78-263">Zapoznaj się z tym przewodnikiem dotyczącym [korzystania z `PredictionEnginePool` w ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="e7b78-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

    > [!NOTE]
    > <span data-ttu-id="e7b78-264">rozszerzenie usługi `PredictionEnginePool` jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="e7b78-264">`PredictionEnginePool` service extension is currently in preview.</span></span>
    
4. <span data-ttu-id="e7b78-265">Dodaj komentarz, aby przetestować prognozę przeszkolonego modelu w metodzie `UseModelWithSingleItem()` przez utworzenie wystąpienia `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="e7b78-266">Przekaż dane komentarzy testowych do [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) przez dodanie następujących elementów jako następnych wierszy kodu w metodzie `UseModelWithSingleItem()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="e7b78-267">Funkcja [przewidywania ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) dokonuje prognozowania dla pojedynczego wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="e7b78-268">Wyświetl `SentimentText` i odpowiednie przewidywania tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="e7b78-269">Używanie modelu do przewidywania</span><span class="sxs-lookup"><span data-stu-id="e7b78-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="e7b78-270">Wdrażanie i prognozowanie elementów wsadowych</span><span class="sxs-lookup"><span data-stu-id="e7b78-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="e7b78-271">Utwórz metodę `UseModelWithBatchItems()` zaraz po metodzie `UseModelWithSingleItem()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="e7b78-272">Metoda `UseModelWithBatchItems()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e7b78-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e7b78-273">Tworzy dane testów wsadowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-273">Creates batch test data.</span></span>
    - <span data-ttu-id="e7b78-274">Przewidywania tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e7b78-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="e7b78-275">Łączy dane testowe i prognozy na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="e7b78-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="e7b78-276">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="e7b78-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="e7b78-277">Dodaj wywołanie do nowej metody z metody `Main` bezpośrednio w wywołaniu metody `UseModelWithSingleItem()` przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="e7b78-278">Dodaj komentarze, aby przetestować przewidywania modeli przeszkolonych w metodzie `UseModelWithBatchItems()`:</span><span class="sxs-lookup"><span data-stu-id="e7b78-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="e7b78-279">Tonacji komentarz przewidywania</span><span class="sxs-lookup"><span data-stu-id="e7b78-279">Predict comment sentiment</span></span>

<span data-ttu-id="e7b78-280">Użyj modelu, aby przewidzieć tonacji danych komentarzy przy użyciu metody [Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="e7b78-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="e7b78-281">Łączenie i wyświetlanie prognoz</span><span class="sxs-lookup"><span data-stu-id="e7b78-281">Combine and display the predictions</span></span>

<span data-ttu-id="e7b78-282">Utwórz nagłówek dla prognoz przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e7b78-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="e7b78-283">Ponieważ `SentimentPrediction` jest dziedziczone z `SentimentData`, Metoda `Transform()` zapełniona `SentimentText` z prognozowanymi polami.</span><span class="sxs-lookup"><span data-stu-id="e7b78-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="e7b78-284">Gdy proces ML.NET przetwarza, każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:</span><span class="sxs-lookup"><span data-stu-id="e7b78-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="e7b78-285">Wyniki</span><span class="sxs-lookup"><span data-stu-id="e7b78-285">Results</span></span>

<span data-ttu-id="e7b78-286">Wyniki powinny wyglądać podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="e7b78-286">Your results should be similar to the following.</span></span> <span data-ttu-id="e7b78-287">Podczas przetwarzania wyświetlane są komunikaty.</span><span class="sxs-lookup"><span data-stu-id="e7b78-287">During processing, messages are displayed.</span></span> <span data-ttu-id="e7b78-288">Mogą pojawić się ostrzeżenia lub przetwarzanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e7b78-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="e7b78-289">Zostały one usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="e7b78-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="e7b78-290">Nabycia!</span><span class="sxs-lookup"><span data-stu-id="e7b78-290">Congratulations!</span></span> <span data-ttu-id="e7b78-291">Pomyślnie skompilowano model uczenia maszynowego do klasyfikowania i przewidywania komunikatów tonacji.</span><span class="sxs-lookup"><span data-stu-id="e7b78-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="e7b78-292">Kompilowanie udanych modeli jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="e7b78-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="e7b78-293">Ten model ma wstępną niższą jakość, ponieważ samouczek używa małych zestawów danych w celu zapewnienia szybkiego szkolenia modeli.</span><span class="sxs-lookup"><span data-stu-id="e7b78-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="e7b78-294">Jeśli jakość modelu jest niezadowalająca, możesz spróbować go ulepszyć, dostarczając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi [parametrami funkcji Hyper-Parameters](../resources/glossary.md##hyperparameter) dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="e7b78-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="e7b78-295">Kod źródłowy dla tego samouczka można znaleźć w repozytorium [dotnet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) .</span><span class="sxs-lookup"><span data-stu-id="e7b78-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e7b78-296">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e7b78-296">Next steps</span></span>

<span data-ttu-id="e7b78-297">W tym samouczku przedstawiono sposób wykonywania tych instrukcji:</span><span class="sxs-lookup"><span data-stu-id="e7b78-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e7b78-298">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e7b78-298">Create a console application</span></span>
> - <span data-ttu-id="e7b78-299">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="e7b78-299">Prepare data</span></span>
> - <span data-ttu-id="e7b78-300">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="e7b78-300">Load the data</span></span>
> - <span data-ttu-id="e7b78-301">Kompilowanie i uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-301">Build and train the model</span></span>
> - <span data-ttu-id="e7b78-302">Oceń model</span><span class="sxs-lookup"><span data-stu-id="e7b78-302">Evaluate the model</span></span>
> - <span data-ttu-id="e7b78-303">Tworzenie prognoz przy użyciu modelu</span><span class="sxs-lookup"><span data-stu-id="e7b78-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="e7b78-304">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="e7b78-304">See the results</span></span>

<span data-ttu-id="e7b78-305">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="e7b78-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e7b78-306">Klasyfikacja problemu</span><span class="sxs-lookup"><span data-stu-id="e7b78-306">Issue Classification</span></span>](github-issue-classification.md)
