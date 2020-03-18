---
title: 'Samouczek: Analizowanie komentarzy na stronie internetowej - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonacji z komentarzy do witryny sieci Web i wykonuje odpowiednie działania. Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241133"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="e9797-104">Samouczek: Analizuj nastroje komentarzy na stronie internetowej z klasyfikacją binarną w ML.NET</span><span class="sxs-lookup"><span data-stu-id="e9797-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="e9797-105">W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonacji z komentarzy do witryny sieci Web i wykonuje odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="e9797-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="e9797-106">Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e9797-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="e9797-107">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e9797-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e9797-108">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e9797-108">Create a console application</span></span>
> - <span data-ttu-id="e9797-109">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-109">Prepare data</span></span>
> - <span data-ttu-id="e9797-110">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-110">Load the data</span></span>
> - <span data-ttu-id="e9797-111">Zbuduj i wytrenuj model</span><span class="sxs-lookup"><span data-stu-id="e9797-111">Build and train the model</span></span>
> - <span data-ttu-id="e9797-112">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="e9797-112">Evaluate the model</span></span>
> - <span data-ttu-id="e9797-113">Użyj modelu, aby dokonać przewidywania</span><span class="sxs-lookup"><span data-stu-id="e9797-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="e9797-114">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="e9797-114">See the results</span></span>

<span data-ttu-id="e9797-115">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)</span><span class="sxs-lookup"><span data-stu-id="e9797-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9797-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e9797-116">Prerequisites</span></span>

- <span data-ttu-id="e9797-117">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core cross-platform development"</span><span class="sxs-lookup"><span data-stu-id="e9797-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="e9797-118">[Zestaw danych zdań oznaczonych etykietami UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik ZIP)</span><span class="sxs-lookup"><span data-stu-id="e9797-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e9797-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e9797-119">Create a console application</span></span>

1. <span data-ttu-id="e9797-120">Utwórz **aplikację .NET Core Console** o nazwie "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="e9797-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="e9797-121">Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="e9797-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="e9797-122">Zainstaluj **pakiet Microsoft.ML NuGet:**</span><span class="sxs-lookup"><span data-stu-id="e9797-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="e9797-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="e9797-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e9797-124">Wybierz "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj.** Wyszukaj **Microsoft.ML**wybierz odpowiedni pakiet, a następnie wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="e9797-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="e9797-125">Kontynuuj instalację, zgadzając się na warunki licencyjne dla wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="e9797-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="e9797-126">Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9797-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="e9797-127">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="e9797-128">Zestawy danych dla tego samouczka są z "Od grupy do pojedynczych etykiet przy użyciu funkcji głębokich", Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="e9797-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="e9797-129">Al.</span><span class="sxs-lookup"><span data-stu-id="e9797-129">al,.</span></span> <span data-ttu-id="e9797-130">KDD 2015 i gościł w UCI Machine Learning Repozytorium - Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="e9797-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="e9797-131">Repozytorium uczenia maszynowegohttp://archive.ics.uci.edu/mlUCI [ ].</span><span class="sxs-lookup"><span data-stu-id="e9797-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="e9797-132">Irvine, Kalifornia: Uniwersytet Kalifornijski, Szkoła Informacji i Informatyki.</span><span class="sxs-lookup"><span data-stu-id="e9797-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="e9797-133">Pobierz [plik ZIP zestawu danych UCI Sentiment Labeled Sentences](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpakuj.</span><span class="sxs-lookup"><span data-stu-id="e9797-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="e9797-134">Skopiuj `yelp_labelled.txt` plik do utworzonego katalogu *danych.*</span><span class="sxs-lookup"><span data-stu-id="e9797-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="e9797-135">W Eksploratorze `yelp_labeled.txt` rozwiązań kliknij prawym przyciskiem myszy plik i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e9797-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="e9797-136">W obszarze **Zaawansowane**zmień wartość **kopiuj do katalogu wyjściowego,** aby **skopiować, jeśli nowsza**.</span><span class="sxs-lookup"><span data-stu-id="e9797-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="e9797-137">Tworzenie klas i definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="e9797-137">Create classes and define paths</span></span>

1. <span data-ttu-id="e9797-138">Dodaj następujące `using` dodatkowe instrukcje do górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="e9797-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="e9797-139">Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby utworzyć pole do przechowywania ostatnio pobranej ścieżki pliku zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="e9797-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="e9797-140">Następnie utwórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="e9797-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="e9797-141">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="e9797-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="e9797-142">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="e9797-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="e9797-143">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="e9797-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="e9797-144">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="e9797-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="e9797-145">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="e9797-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="e9797-146">Dodaj następującą `using` instrukcję na górze *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="e9797-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="e9797-147">Usuń istniejącą definicję klasy i dodaj następujący `SentimentData` `SentimentPrediction`kod, który ma dwie klasy i , do *pliku SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="e9797-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="e9797-148">Jak przygotowano dane</span><span class="sxs-lookup"><span data-stu-id="e9797-148">How the data was prepared</span></span>

<span data-ttu-id="e9797-149">Klasa zestawu danych `SentimentData`wejściowych `string` , ma`SentimentText`wartość dla `bool` `Sentiment`komentarzy użytkownika ( ) i ( ) wartość 1 (dodatni) lub 0 (ujemna) dla tonacji.</span><span class="sxs-lookup"><span data-stu-id="e9797-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="e9797-150">Oba pola mają dołączonych atrybutów [LoadColumn,](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) które opisują kolejność plików danych każdego pola.</span><span class="sxs-lookup"><span data-stu-id="e9797-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="e9797-151">Ponadto `Sentiment` właściwość ma [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atrybut, aby wyznaczyć go jako `Label` pole.</span><span class="sxs-lookup"><span data-stu-id="e9797-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="e9797-152">Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="e9797-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="e9797-153">SentymentTekst</span><span class="sxs-lookup"><span data-stu-id="e9797-153">SentimentText</span></span>                         |<span data-ttu-id="e9797-154">Sentyment (etykieta)</span><span class="sxs-lookup"><span data-stu-id="e9797-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="e9797-155">Kelnerka była trochę powolna w służbie.</span><span class="sxs-lookup"><span data-stu-id="e9797-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="e9797-156">0</span><span class="sxs-lookup"><span data-stu-id="e9797-156">0</span></span>     |
|<span data-ttu-id="e9797-157">Skorupa nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="e9797-157">Crust is not good.</span></span>                    |    <span data-ttu-id="e9797-158">0</span><span class="sxs-lookup"><span data-stu-id="e9797-158">0</span></span>     |
|<span data-ttu-id="e9797-159">Wow... Uwielbiałem to miejsce.</span><span class="sxs-lookup"><span data-stu-id="e9797-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="e9797-160">1</span><span class="sxs-lookup"><span data-stu-id="e9797-160">1</span></span>     |
|<span data-ttu-id="e9797-161">Obsługa była bardzo szybka.</span><span class="sxs-lookup"><span data-stu-id="e9797-161">Service was very prompt.</span></span>              |    <span data-ttu-id="e9797-162">1</span><span class="sxs-lookup"><span data-stu-id="e9797-162">1</span></span>     |

<span data-ttu-id="e9797-163">`SentimentPrediction`jest klasy przewidywania używane po treningu modelu.</span><span class="sxs-lookup"><span data-stu-id="e9797-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="e9797-164">Dziedziczy `SentimentData` z tak, `SentimentText` że dane wejściowe mogą być wyświetlane wraz z prognozą danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="e9797-165">Wartość `Prediction` logiczna jest wartością, którą model przewiduje `SentimentText`po dostarczeniu z nowym wejściem.</span><span class="sxs-lookup"><span data-stu-id="e9797-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="e9797-166">Klasa `SentimentPrediction` danych wyjściowych zawiera dwie inne właściwości `Score` obliczone przez model: - `Probability` wynik raw obliczony przez model oraz - wynik skalibrowany do prawdopodobieństwa, że tekst ma pozytywne nastawienie.</span><span class="sxs-lookup"><span data-stu-id="e9797-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="e9797-167">W tym samouczku najważniejszą `Prediction`właściwością jest .</span><span class="sxs-lookup"><span data-stu-id="e9797-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="e9797-168">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-168">Load the data</span></span>

<span data-ttu-id="e9797-169">Dane w ML.NET jest reprezentowana jako [klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="e9797-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="e9797-170">`IDataView`to elastyczny i skuteczny sposób opisywania danych tabelarycznych (numerycznych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="e9797-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="e9797-171">Dane mogą być ładowane z pliku tekstowego lub w czasie rzeczywistym `IDataView` (na przykład bazy danych SQL lub plików dziennika) do obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9797-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="e9797-172">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e9797-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="e9797-173">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="e9797-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="e9797-174">Jest to podobne, koncepcyjnie, `DBContext` do w ramach jednostki.</span><span class="sxs-lookup"><span data-stu-id="e9797-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="e9797-175">Przygotuj aplikację, a następnie załaduj dane:</span><span class="sxs-lookup"><span data-stu-id="e9797-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="e9797-176">Zamień `Console.WriteLine("Hello World!")` wiersz `Main` w metodzie na następujący kod, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="e9797-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="e9797-177">Dodaj następujące jako następny wiersz kodu `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="e9797-178">Utwórz `LoadData()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="e9797-179">Metoda `LoadData()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e9797-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e9797-180">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="e9797-180">Loads the data.</span></span>
    - <span data-ttu-id="e9797-181">Dzieli załadowany zestaw danych na zestawy danych pociągu i testów.</span><span class="sxs-lookup"><span data-stu-id="e9797-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="e9797-182">Zwraca zestawy danych podzielonego pociągu i testu.</span><span class="sxs-lookup"><span data-stu-id="e9797-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="e9797-183">Dodaj następujący kod jako pierwszy `LoadData()` wiersz metody:</span><span class="sxs-lookup"><span data-stu-id="e9797-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="e9797-184">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczyty w pliku.</span><span class="sxs-lookup"><span data-stu-id="e9797-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="e9797-185">Przyjmuje zmienne ścieżki danych i `IDataView`zwraca .</span><span class="sxs-lookup"><span data-stu-id="e9797-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="e9797-186">Dzielenie zestawu danych do szkolenia i testowania modelu</span><span class="sxs-lookup"><span data-stu-id="e9797-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="e9797-187">Podczas przygotowywania modelu, należy użyć części zestawu danych do nauczenia go i część zestawu danych, aby przetestować dokładność modelu.</span><span class="sxs-lookup"><span data-stu-id="e9797-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="e9797-188">Aby podzielić załadowane dane na potrzebne zestawy danych, dodaj `LoadData()` następujący kod jako następny wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="e9797-189">Poprzedni kod używa [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metoda podzielić załadowany zestaw danych do pociągu i testów zestawów danych i zwrócić je w [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) klasy.</span><span class="sxs-lookup"><span data-stu-id="e9797-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="e9797-190">Określ procent zestawu testów `testFraction`danych z parametrem.</span><span class="sxs-lookup"><span data-stu-id="e9797-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="e9797-191">Wartość domyślna to 10%, w tym przypadku do oceny większej liczby danych jest używany chorować na 20%.</span><span class="sxs-lookup"><span data-stu-id="e9797-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="e9797-192">Zwraca `splitDataView` na końcu `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="e9797-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="e9797-193">Zbuduj i wytrenuj model</span><span class="sxs-lookup"><span data-stu-id="e9797-193">Build and train the model</span></span>

1. <span data-ttu-id="e9797-194">Dodaj następujące wywołanie `BuildAndTrainModel`do metody jako następny `Main()` wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="e9797-195">Metoda `BuildAndTrainModel()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e9797-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e9797-196">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="e9797-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="e9797-197">Trenuje model.</span><span class="sxs-lookup"><span data-stu-id="e9797-197">Trains the model.</span></span>
    - <span data-ttu-id="e9797-198">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="e9797-199">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="e9797-199">Returns the model.</span></span>

2. <span data-ttu-id="e9797-200">Utwórz `BuildAndTrainModel()` metodę, tuż `Main()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="e9797-201">Wyodrębnianie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-201">Extract and transform the data</span></span>

1. <span data-ttu-id="e9797-202">Wywołaj `FeaturizeText` jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="e9797-203">Metoda `FeaturizeText()` w poprzednim kodzie konwertuje kolumnę tekstową (`SentimentText`) na kolumnę typu `Features` klucza numerycznego używaną przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="e9797-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="e9797-204">SentymentTekst</span><span class="sxs-lookup"><span data-stu-id="e9797-204">SentimentText</span></span>                         |<span data-ttu-id="e9797-205">Opinia</span><span class="sxs-lookup"><span data-stu-id="e9797-205">Sentiment</span></span> |<span data-ttu-id="e9797-206">Funkcje</span><span class="sxs-lookup"><span data-stu-id="e9797-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="e9797-207">Kelnerka była trochę powolna w służbie.</span><span class="sxs-lookup"><span data-stu-id="e9797-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="e9797-208">0</span><span class="sxs-lookup"><span data-stu-id="e9797-208">0</span></span>     |<span data-ttu-id="e9797-209">[0.76, 0.65, 0.44, ...]</span><span class="sxs-lookup"><span data-stu-id="e9797-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="e9797-210">Skorupa nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="e9797-210">Crust is not good.</span></span>                    |    <span data-ttu-id="e9797-211">0</span><span class="sxs-lookup"><span data-stu-id="e9797-211">0</span></span>     |<span data-ttu-id="e9797-212">[0.98, 0.43, 0.54, ...]</span><span class="sxs-lookup"><span data-stu-id="e9797-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="e9797-213">Wow... Uwielbiałem to miejsce.</span><span class="sxs-lookup"><span data-stu-id="e9797-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="e9797-214">1</span><span class="sxs-lookup"><span data-stu-id="e9797-214">1</span></span>     |<span data-ttu-id="e9797-215">[0.35, 0.73, 0.46, ...]</span><span class="sxs-lookup"><span data-stu-id="e9797-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="e9797-216">Obsługa była bardzo szybka.</span><span class="sxs-lookup"><span data-stu-id="e9797-216">Service was very prompt.</span></span>              |    <span data-ttu-id="e9797-217">1</span><span class="sxs-lookup"><span data-stu-id="e9797-217">1</span></span>     |<span data-ttu-id="e9797-218">[0.39, 0, 0.75, ...]</span><span class="sxs-lookup"><span data-stu-id="e9797-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="e9797-219">Dodawanie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="e9797-219">Add a learning algorithm</span></span>

<span data-ttu-id="e9797-220">Ta aplikacja używa algorytmu klasyfikacji, który kategoryzuje elementy lub wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="e9797-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="e9797-221">Aplikacja kategoryzuje komentarze witryny jako pozytywne lub negatywne, więc użyj zadania klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="e9797-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="e9797-222">Dołącz zadanie uczenia maszynowego do definicji przekształcania danych, dodając następujące `BuildAndTrainModel()`wierszy kodu w:</span><span class="sxs-lookup"><span data-stu-id="e9797-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="e9797-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytm szkolenia klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e9797-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="e9797-224">Jest to dołączone `estimator` do i akceptuje featurized `SentimentText` ( `Label` `Features`) i parametry wejściowe, aby dowiedzieć się z danych historycznych.</span><span class="sxs-lookup"><span data-stu-id="e9797-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="e9797-225">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="e9797-225">Train the model</span></span>

<span data-ttu-id="e9797-226">Dopasuj `splitTrainSet` model do danych i zwróć uczonego modelu, `BuildAndTrainModel()` dodając następujące wierszy kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="e9797-227">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda szkoli modelu przez przekształcenie zestawu danych i stosowania szkolenia.</span><span class="sxs-lookup"><span data-stu-id="e9797-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="e9797-228">Powrót modelu przeszkolonego do wykorzystania do oceny</span><span class="sxs-lookup"><span data-stu-id="e9797-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="e9797-229">Zwraca model na końcu `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="e9797-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="e9797-230">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="e9797-230">Evaluate the model</span></span>

<span data-ttu-id="e9797-231">Po uczonego modelu należy użyć danych testowych sprawdź poprawność wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="e9797-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="e9797-232">Utwórz `Evaluate()` metodę, `BuildAndTrainModel()`zaraz po , z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="e9797-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="e9797-233">Metoda `Evaluate()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e9797-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e9797-234">Ładuje testowy zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="e9797-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="e9797-235">Tworzy oceniającego BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="e9797-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="e9797-236">Ocenia model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="e9797-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="e9797-237">Wyświetla metryki.</span><span class="sxs-lookup"><span data-stu-id="e9797-237">Displays the metrics.</span></span>

2. <span data-ttu-id="e9797-238">Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio w wywołaniu `BuildAndTrainModel()` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="e9797-239">Przekształć dane, `splitTestSet` dodając `Evaluate()`następujący kod do:</span><span class="sxs-lookup"><span data-stu-id="e9797-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="e9797-240">Poprzedni kod używa [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda do prognozowania dla wielu dostarczonych wierszy wejściowych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="e9797-241">Oceń model, dodając następujący wiersz kodu w `Evaluate()` metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="e9797-242">Po ustawie przewidywanie`predictions`( ), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia model, który porównuje przewidywane `Labels` wartości z rzeczywistym w zestawie danych testowych i zwraca [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiektu, w jaki sposób model działa.</span><span class="sxs-lookup"><span data-stu-id="e9797-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="e9797-243">Wyświetlanie metryk do sprawdzania poprawności modelu</span><span class="sxs-lookup"><span data-stu-id="e9797-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="e9797-244">Użyj następującego kodu, aby wyświetlić metryki:</span><span class="sxs-lookup"><span data-stu-id="e9797-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="e9797-245">Metryka `Accuracy` pobiera dokładność modelu, który jest proporcją poprawnych prognoz w zestawie testów.</span><span class="sxs-lookup"><span data-stu-id="e9797-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="e9797-246">Metryka `AreaUnderRocCurve` wskazuje, jak pewny siebie model poprawnie klasyfikuje klasy dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="e9797-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="e9797-247">Chcesz, `AreaUnderRocCurve` aby być jak najbliżej jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e9797-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="e9797-248">Metryka `F1Score` pobiera wynik F1 modelu, który jest miarą równowagi między [precyzją](../resources/glossary.md#precision) a [wycofaniem.](../resources/glossary.md#recall)</span><span class="sxs-lookup"><span data-stu-id="e9797-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="e9797-249">Chcesz, `F1Score` aby być jak najbliżej jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e9797-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="e9797-250">Przewidywanie wyników danych testowych</span><span class="sxs-lookup"><span data-stu-id="e9797-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="e9797-251">Utwórz `UseModelWithSingleItem()` metodę, tuż `Evaluate()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="e9797-252">Metoda `UseModelWithSingleItem()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e9797-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e9797-253">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="e9797-254">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="e9797-255">Łączy dane testowe i prognozy dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="e9797-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="e9797-256">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="e9797-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="e9797-257">Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio w wywołaniu `Evaluate()` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="e9797-258">Dodaj następujący kod do utworzenia jako `UseModelWithSingleItem()` pierwszy wiersz w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="e9797-259">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejs emanujący interfejsu API wygody, który umożliwia wykonywanie przewidywanie na pojedyncze wystąpienie danych.</span><span class="sxs-lookup"><span data-stu-id="e9797-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="e9797-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla nici.</span><span class="sxs-lookup"><span data-stu-id="e9797-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="e9797-261">Dopuszczalne jest stosowanie w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="e9797-262">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiektów [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9797-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="e9797-263">Zobacz ten przewodnik, jak [ `PredictionEnginePool` używać w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="e9797-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e9797-264">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="e9797-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="e9797-265">Dodaj komentarz, aby przetestować przewidywanie `UseModelWithSingleItem()` uczonego modelu `SentimentData`w metodzie, tworząc wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="e9797-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="e9797-266">Przekaż dane komentarza testowego [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do, dodając następujące wiersze `UseModelWithSingleItem()` kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="e9797-267">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie dla pojedynczego wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="e9797-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="e9797-268">Wyświetlanie `SentimentText` i odpowiednie przewidywanie tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="e9797-269">Użyj modelu do przewidywania</span><span class="sxs-lookup"><span data-stu-id="e9797-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="e9797-270">Wdrażanie i przewidywanie elementów wsadowych</span><span class="sxs-lookup"><span data-stu-id="e9797-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="e9797-271">Utwórz `UseModelWithBatchItems()` metodę, tuż `UseModelWithSingleItem()` po tej metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="e9797-272">Metoda `UseModelWithBatchItems()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="e9797-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="e9797-273">Tworzy dane testowe partii.</span><span class="sxs-lookup"><span data-stu-id="e9797-273">Creates batch test data.</span></span>
    - <span data-ttu-id="e9797-274">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="e9797-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="e9797-275">Łączy dane testowe i prognozy dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="e9797-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="e9797-276">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="e9797-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="e9797-277">Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio w wywołaniu `UseModelWithSingleItem()` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="e9797-278">Dodaj kilka komentarzy, aby przetestować prognozy `UseModelWithBatchItems()` uczonego modelu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e9797-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="e9797-279">Przewiduj nastroje komentarzy</span><span class="sxs-lookup"><span data-stu-id="e9797-279">Predict comment sentiment</span></span>

<span data-ttu-id="e9797-280">Użyj modelu do przewidywania tonacji danych komentarza przy użyciu metody [Transform():](xref:Microsoft.ML.ITransformer.Transform%2A)</span><span class="sxs-lookup"><span data-stu-id="e9797-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="e9797-281">Łączenie i wyświetlanie prognoz</span><span class="sxs-lookup"><span data-stu-id="e9797-281">Combine and display the predictions</span></span>

<span data-ttu-id="e9797-282">Utwórz nagłówek dla prognoz przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="e9797-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="e9797-283">Ponieważ `SentimentPrediction` jest dziedziczona z `SentimentData`, `Transform()` metoda wypełniona `SentimentText` przewidywanych pól.</span><span class="sxs-lookup"><span data-stu-id="e9797-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="e9797-284">W miarę ML.NET procesów każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:</span><span class="sxs-lookup"><span data-stu-id="e9797-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="e9797-285">Wyniki</span><span class="sxs-lookup"><span data-stu-id="e9797-285">Results</span></span>

<span data-ttu-id="e9797-286">Wyniki powinny być podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="e9797-286">Your results should be similar to the following.</span></span> <span data-ttu-id="e9797-287">Podczas przetwarzania są wyświetlane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="e9797-287">During processing, messages are displayed.</span></span> <span data-ttu-id="e9797-288">Mogą być wyświetlane ostrzeżenia lub wiadomości przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="e9797-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="e9797-289">Zostały one usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="e9797-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="e9797-290">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="e9797-290">Congratulations!</span></span> <span data-ttu-id="e9797-291">Teraz pomyślnie skonstruowano model uczenia maszynowego do klasyfikowania i przewidywania tonacji wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e9797-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="e9797-292">Budowanie udanych modeli jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="e9797-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="e9797-293">Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="e9797-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="e9797-294">Jeśli nie jesteś zadowolony z jakości modelu, możesz spróbować go poprawić, udostępniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkolenia z [różnymi hiperparametrami](../resources/glossary.md#hyperparameter) dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="e9797-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="e9797-295">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)</span><span class="sxs-lookup"><span data-stu-id="e9797-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e9797-296">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e9797-296">Next steps</span></span>

<span data-ttu-id="e9797-297">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e9797-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e9797-298">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="e9797-298">Create a console application</span></span>
> - <span data-ttu-id="e9797-299">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-299">Prepare data</span></span>
> - <span data-ttu-id="e9797-300">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="e9797-300">Load the data</span></span>
> - <span data-ttu-id="e9797-301">Zbuduj i wytrenuj model</span><span class="sxs-lookup"><span data-stu-id="e9797-301">Build and train the model</span></span>
> - <span data-ttu-id="e9797-302">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="e9797-302">Evaluate the model</span></span>
> - <span data-ttu-id="e9797-303">Użyj modelu, aby dokonać przewidywania</span><span class="sxs-lookup"><span data-stu-id="e9797-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="e9797-304">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="e9797-304">See the results</span></span>

<span data-ttu-id="e9797-305">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="e9797-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e9797-306">Klasyfikacja wydania</span><span class="sxs-lookup"><span data-stu-id="e9797-306">Issue Classification</span></span>](github-issue-classification.md)
