---
title: 'Samouczek: Analizowanie komentarzy na stronie internetowej - klasyfikacja binarna'
description: W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonację z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania. Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6e13cfca93c54648b1a0423c5983013d3e2a1a0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243300"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="6e6df-104">Samouczek: Analizowanie nastrojów komentarzy na stronie internetowej z klasyfikacją binarną w ML.NET</span><span class="sxs-lookup"><span data-stu-id="6e6df-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="6e6df-105">W tym samouczku pokazano, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonację z komentarzy w witrynie sieci Web i podejmuje odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="6e6df-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="6e6df-106">Klasyfikator tonacji binarnych używa języka C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="6e6df-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="6e6df-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6e6df-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6e6df-108">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="6e6df-108">Create a console application</span></span>
> - <span data-ttu-id="6e6df-109">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-109">Prepare data</span></span>
> - <span data-ttu-id="6e6df-110">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-110">Load the data</span></span>
> - <span data-ttu-id="6e6df-111">Zbuduj i trenuj model</span><span class="sxs-lookup"><span data-stu-id="6e6df-111">Build and train the model</span></span>
> - <span data-ttu-id="6e6df-112">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="6e6df-112">Evaluate the model</span></span>
> - <span data-ttu-id="6e6df-113">Użyj modelu, aby dokonać prognozowania</span><span class="sxs-lookup"><span data-stu-id="6e6df-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="6e6df-114">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="6e6df-114">See the results</span></span>

<span data-ttu-id="6e6df-115">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)</span><span class="sxs-lookup"><span data-stu-id="6e6df-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e6df-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6e6df-116">Prerequisites</span></span>

- <span data-ttu-id="6e6df-117">[Visual Studio 2017 w wersji 15.6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem ".NET Core rozwoju między platformami"</span><span class="sxs-lookup"><span data-stu-id="6e6df-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="6e6df-118">[Zestaw danych Zdania z etykietami uci sentiment](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik ZIP)</span><span class="sxs-lookup"><span data-stu-id="6e6df-118">[UCI Sentiment Labeled Sentences dataset](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="6e6df-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="6e6df-119">Create a console application</span></span>

1. <span data-ttu-id="6e6df-120">Utwórz **aplikację konsoli .NET** Core o nazwie "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="6e6df-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="6e6df-121">Utwórz katalog o nazwie *Dane* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="6e6df-122">Zainstaluj **pakiet nuget Microsoft.ML:**</span><span class="sxs-lookup"><span data-stu-id="6e6df-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="6e6df-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6e6df-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="6e6df-124">Wybierz "nuget.org" jako źródło pakietu, a następnie wybierz kartę **Przeglądaj.** Wyszukaj **Microsoft.ML**, wybierz odpowiedni pakiet, a następnie wybierz przycisk **Zainstaluj.**</span><span class="sxs-lookup"><span data-stu-id="6e6df-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="6e6df-125">Kontynuuj instalację, zgadzając się na warunki licencji dla wybranego pakietu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="6e6df-126">Zrób to samo dla pakietu **Microsoft.ML.FastTree** NuGet.</span><span class="sxs-lookup"><span data-stu-id="6e6df-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="6e6df-127">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="6e6df-128">Zestawy danych dla tego samouczka pochodzą z "Od grupy do poszczególnych etykiet przy użyciu funkcji głębokich", Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="6e6df-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="6e6df-129">Al.</span><span class="sxs-lookup"><span data-stu-id="6e6df-129">al,.</span></span> <span data-ttu-id="6e6df-130">KDD 2015 i gościł w repozytorium uczenia maszynowego UCI - Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="6e6df-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="6e6df-131">Repozytorium uczenia maszynowego UCI [ ].http://archive.ics.uci.edu/ml</span><span class="sxs-lookup"><span data-stu-id="6e6df-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="6e6df-132">Irvine, CA: Uniwersytet Kalifornijski, Szkoła Informatyki i Informatyki.</span><span class="sxs-lookup"><span data-stu-id="6e6df-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="6e6df-133">Pobierz [plik ZIP zestawu danych UCI Sentiment Labeled Sentences](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i rozpaj.</span><span class="sxs-lookup"><span data-stu-id="6e6df-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="6e6df-134">Skopiuj `yelp_labelled.txt` plik do utworzonego katalogu *Danych.*</span><span class="sxs-lookup"><span data-stu-id="6e6df-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="6e6df-135">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6e6df-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="6e6df-136">W obszarze **Zaawansowane**zmień wartość **kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli jest nowszy**.</span><span class="sxs-lookup"><span data-stu-id="6e6df-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="6e6df-137">Tworzenie klas i definiowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="6e6df-137">Create classes and define paths</span></span>

1. <span data-ttu-id="6e6df-138">Dodaj następujące `using` dodatkowe instrukcje w górnej części pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="6e6df-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="6e6df-139">Dodaj następujący kod do wiersza `Main` tuż nad metodą, aby utworzyć pole do przechowywania ostatnio pobranej ścieżki pliku zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="6e6df-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="6e6df-140">Następnie utwórz klasy dla danych wejściowych i prognoz.</span><span class="sxs-lookup"><span data-stu-id="6e6df-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="6e6df-141">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="6e6df-142">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="6e6df-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="6e6df-143">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję **Klasa** i zmień pole **Nazwa** na *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="6e6df-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="6e6df-144">Następnie wybierz przycisk **Dodaj.**</span><span class="sxs-lookup"><span data-stu-id="6e6df-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="6e6df-145">Plik *SentimentData.cs* zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="6e6df-146">Dodaj następującą `using` instrukcję do górnej części *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="6e6df-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="6e6df-147">Usuń istniejącą definicję klasy i dodaj następujący `SentimentData` `SentimentPrediction`kod, który ma dwie klasy i , do pliku *SentimentData.cs:*</span><span class="sxs-lookup"><span data-stu-id="6e6df-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="6e6df-148">Sposób przygotowania danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-148">How the data was prepared</span></span>

<span data-ttu-id="6e6df-149">Klasa wejściowego zestawu `SentimentData`danych, `string` ma dla`SentimentText`komentarzy `bool` użytkownika`Sentiment`( ) i ( ) wartość 1 (dodatnia) lub 0 (ujemna) dla tonacji.</span><span class="sxs-lookup"><span data-stu-id="6e6df-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="6e6df-150">Oba pola mają atrybuty [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) dołączone do nich, który opisuje kolejność plików danych każdego pola.</span><span class="sxs-lookup"><span data-stu-id="6e6df-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="6e6df-151">Ponadto `Sentiment` właściwość ma atrybut [ColumnName,](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) aby wyznaczyć `Label` go jako pole.</span><span class="sxs-lookup"><span data-stu-id="6e6df-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="6e6df-152">Poniższy przykładowy plik nie ma wiersza nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="6e6df-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="6e6df-153">SentimentText (Tekst sentymentu)</span><span class="sxs-lookup"><span data-stu-id="6e6df-153">SentimentText</span></span>                         |<span data-ttu-id="6e6df-154">Tonację (etykieta)</span><span class="sxs-lookup"><span data-stu-id="6e6df-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="6e6df-155">Kelnerka była trochę powolna w służbie.</span><span class="sxs-lookup"><span data-stu-id="6e6df-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="6e6df-156">0</span><span class="sxs-lookup"><span data-stu-id="6e6df-156">0</span></span>     |
|<span data-ttu-id="6e6df-157">Skorupa nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="6e6df-157">Crust is not good.</span></span>                    |    <span data-ttu-id="6e6df-158">0</span><span class="sxs-lookup"><span data-stu-id="6e6df-158">0</span></span>     |
|<span data-ttu-id="6e6df-159">Wow... Bardzo dobre miejsce na życie.</span><span class="sxs-lookup"><span data-stu-id="6e6df-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="6e6df-160">1</span><span class="sxs-lookup"><span data-stu-id="6e6df-160">1</span></span>     |
|<span data-ttu-id="6e6df-161">Obsługa była bardzo szybka.</span><span class="sxs-lookup"><span data-stu-id="6e6df-161">Service was very prompt.</span></span>              |    <span data-ttu-id="6e6df-162">1</span><span class="sxs-lookup"><span data-stu-id="6e6df-162">1</span></span>     |

<span data-ttu-id="6e6df-163">`SentimentPrediction`jest klasą przewidywania używane po szkoleniu modelu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="6e6df-164">Dziedziczy z `SentimentData` tak, `SentimentText` aby dane wejściowe mogą być wyświetlane wraz z przewidywanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="6e6df-165">Wartość `Prediction` logiczna jest wartością, którą model przewiduje `SentimentText`po podaniu nowego wejścia .</span><span class="sxs-lookup"><span data-stu-id="6e6df-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="6e6df-166">Klasa `SentimentPrediction` danych wyjściowych zawiera dwie inne `Score` właściwości obliczone przez model: `Probability` - wynik pierwotny obliczony przez model i - wynik skalibrowany do prawdopodobieństwa, że tekst ma pozytywny sentyment.</span><span class="sxs-lookup"><span data-stu-id="6e6df-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="6e6df-167">W tym samouczku najważniejszą `Prediction`właściwością jest .</span><span class="sxs-lookup"><span data-stu-id="6e6df-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6e6df-168">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-168">Load the data</span></span>

<span data-ttu-id="6e6df-169">Dane w ML.NET są reprezentowane jako [klasa IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="6e6df-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="6e6df-170">`IDataView`jest elastycznym, skutecznym sposobem opisywania danych tabelaryjskich (liczbowych i tekstowych).</span><span class="sxs-lookup"><span data-stu-id="6e6df-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="6e6df-171">Dane można ładować z pliku tekstowego lub w czasie rzeczywistym (na przykład bazy danych SQL lub plików dziennika) do obiektu. `IDataView`</span><span class="sxs-lookup"><span data-stu-id="6e6df-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="6e6df-172">[Klasa MLContext](xref:Microsoft.ML.MLContext) jest punktem wyjścia dla wszystkich operacji ML.NET.</span><span class="sxs-lookup"><span data-stu-id="6e6df-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="6e6df-173">Inicjowanie `mlContext` tworzy nowe środowisko ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="6e6df-174">Jest podobny, koncepcyjnie, do `DBContext` w entity framework.</span><span class="sxs-lookup"><span data-stu-id="6e6df-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="6e6df-175">Przygotuj aplikację, a następnie ładuj dane:</span><span class="sxs-lookup"><span data-stu-id="6e6df-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="6e6df-176">Zastąp `Console.WriteLine("Hello World!")` `Main` wiersz w metodzie następującym kodem, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="6e6df-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="6e6df-177">Dodaj następujące jako następny wiersz kodu `Main()` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="6e6df-178">Utwórz `LoadData()` metodę, zaraz `Main()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="6e6df-179">Metoda `LoadData()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6e6df-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="6e6df-180">Ładuje dane.</span><span class="sxs-lookup"><span data-stu-id="6e6df-180">Loads the data.</span></span>
    - <span data-ttu-id="6e6df-181">Dzieli załadowany zestaw danych do zestawów danych pociągu i testu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="6e6df-182">Zwraca zestaw danych pociągu podzielonego i testu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="6e6df-183">Dodaj następujący kod jako pierwszy `LoadData()` wiersz metody:</span><span class="sxs-lookup"><span data-stu-id="6e6df-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="6e6df-184">Metoda [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="6e6df-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) method defines the data schema and reads in the file.</span></span> <span data-ttu-id="6e6df-185">Przyjmuje zmienne ścieżki danych i `IDataView`zwraca plik .</span><span class="sxs-lookup"><span data-stu-id="6e6df-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="6e6df-186">Dzielenie zestawu danych do szkolenia i testowania modelu</span><span class="sxs-lookup"><span data-stu-id="6e6df-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="6e6df-187">Podczas przygotowywania modelu, należy użyć części zestawu danych, aby go wyszkolić i część zestawu danych, aby przetestować dokładność modelu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="6e6df-188">Aby podzielić załadowane dane na potrzebne zestawy danych, dodaj następujący `LoadData()` kod jako następny wiersz metody:</span><span class="sxs-lookup"><span data-stu-id="6e6df-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="6e6df-189">Poprzedni kod używa [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metoda podzielić załadowany zestaw danych do zestawu danych pociągu <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> i testowania i zwrócić je w klasie.</span><span class="sxs-lookup"><span data-stu-id="6e6df-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> class.</span></span> <span data-ttu-id="6e6df-190">Określ procent testu zestawu `testFraction`danych z parametrem.</span><span class="sxs-lookup"><span data-stu-id="6e6df-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="6e6df-191">Wartość domyślna to 10%, w tym przypadku używasz 20% do oceny większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="6e6df-192">Zwraca `splitDataView` na końcu `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="6e6df-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="6e6df-193">Zbuduj i trenuj model</span><span class="sxs-lookup"><span data-stu-id="6e6df-193">Build and train the model</span></span>

1. <span data-ttu-id="6e6df-194">Dodaj następujące wywołanie `BuildAndTrainModel`metody jako następny wiersz `Main()` kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="6e6df-195">Metoda `BuildAndTrainModel()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6e6df-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="6e6df-196">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="6e6df-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="6e6df-197">Trenuje model.</span><span class="sxs-lookup"><span data-stu-id="6e6df-197">Trains the model.</span></span>
    - <span data-ttu-id="6e6df-198">Prognozuje tonację na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="6e6df-199">Zwraca model.</span><span class="sxs-lookup"><span data-stu-id="6e6df-199">Returns the model.</span></span>

2. <span data-ttu-id="6e6df-200">Utwórz `BuildAndTrainModel()` metodę, zaraz `Main()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="6e6df-201">Wyodrębnianie i przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-201">Extract and transform the data</span></span>

1. <span data-ttu-id="6e6df-202">Zadzwoń `FeaturizeText` jako następny wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="6e6df-203">Metoda `FeaturizeText()` w poprzednim kodzie konwertuje`SentimentText`kolumnę tekstową `Features` ( ) na kolumnę typu klucza numerycznego używaną przez algorytm uczenia maszynowego i dodaje ją jako nową kolumnę zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="6e6df-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="6e6df-204">SentimentText (Tekst sentymentu)</span><span class="sxs-lookup"><span data-stu-id="6e6df-204">SentimentText</span></span>                         |<span data-ttu-id="6e6df-205">Opinia</span><span class="sxs-lookup"><span data-stu-id="6e6df-205">Sentiment</span></span> |<span data-ttu-id="6e6df-206">Funkcje</span><span class="sxs-lookup"><span data-stu-id="6e6df-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="6e6df-207">Kelnerka była trochę powolna w służbie.</span><span class="sxs-lookup"><span data-stu-id="6e6df-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="6e6df-208">0</span><span class="sxs-lookup"><span data-stu-id="6e6df-208">0</span></span>     |<span data-ttu-id="6e6df-209">[0.76, 0.65, 0.44, ...]</span><span class="sxs-lookup"><span data-stu-id="6e6df-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="6e6df-210">Skorupa nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="6e6df-210">Crust is not good.</span></span>                    |    <span data-ttu-id="6e6df-211">0</span><span class="sxs-lookup"><span data-stu-id="6e6df-211">0</span></span>     |<span data-ttu-id="6e6df-212">[0.98, 0.43, 0.54, ...]</span><span class="sxs-lookup"><span data-stu-id="6e6df-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="6e6df-213">Wow... Bardzo dobre miejsce na życie.</span><span class="sxs-lookup"><span data-stu-id="6e6df-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="6e6df-214">1</span><span class="sxs-lookup"><span data-stu-id="6e6df-214">1</span></span>     |<span data-ttu-id="6e6df-215">[0.35, 0.73, 0.46, ...]</span><span class="sxs-lookup"><span data-stu-id="6e6df-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="6e6df-216">Obsługa była bardzo szybka.</span><span class="sxs-lookup"><span data-stu-id="6e6df-216">Service was very prompt.</span></span>              |    <span data-ttu-id="6e6df-217">1</span><span class="sxs-lookup"><span data-stu-id="6e6df-217">1</span></span>     |<span data-ttu-id="6e6df-218">[0.39, 0, 0.75, ...]</span><span class="sxs-lookup"><span data-stu-id="6e6df-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="6e6df-219">Dodawanie algorytmu uczenia się</span><span class="sxs-lookup"><span data-stu-id="6e6df-219">Add a learning algorithm</span></span>

<span data-ttu-id="6e6df-220">Ta aplikacja używa algorytmu klasyfikacji, który kategoryzuje elementy lub wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="6e6df-221">Aplikacja kategoryzuje komentarze witryny sieci Web jako pozytywne lub negatywne, więc użyj zadania klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="6e6df-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="6e6df-222">Dołącz zadanie uczenia maszynowego do definicji transformacji danych, dodając następujące `BuildAndTrainModel()`elementy jako następny wiersz kodu w:</span><span class="sxs-lookup"><span data-stu-id="6e6df-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="6e6df-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) jest algorytm szkolenia klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="6e6df-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="6e6df-224">Jest to dołączone do `estimator` i akceptuje `SentimentText` featurized`Features`( `Label` ) i parametry wejściowe, aby dowiedzieć się z danych historycznych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="6e6df-225">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="6e6df-225">Train the model</span></span>

<span data-ttu-id="6e6df-226">Dopasuj `splitTrainSet` model do danych i zwróć przeszkolony model, dodając następujący `BuildAndTrainModel()` wiersz kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="6e6df-227">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) Metoda trenuje modelu przez przekształcenie zestawu danych i stosowania szkolenia.</span><span class="sxs-lookup"><span data-stu-id="6e6df-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="6e6df-228">Zwraca model przeszkolony do wykorzystania do oceny</span><span class="sxs-lookup"><span data-stu-id="6e6df-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="6e6df-229">Zwraca model na końcu `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="6e6df-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="6e6df-230">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="6e6df-230">Evaluate the model</span></span>

<span data-ttu-id="6e6df-231">Po przeszkoleniu modelu należy użyć danych testowych sprawdź poprawność wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="6e6df-232">Utwórz `Evaluate()` metodę, `BuildAndTrainModel()`zaraz po , z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="6e6df-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="6e6df-233">Metoda `Evaluate()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6e6df-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="6e6df-234">Ładuje testowy zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="6e6df-235">Tworzy binaryclassification oceniającego.</span><span class="sxs-lookup"><span data-stu-id="6e6df-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="6e6df-236">Ocenia model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="6e6df-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="6e6df-237">Wyświetla dane.</span><span class="sxs-lookup"><span data-stu-id="6e6df-237">Displays the metrics.</span></span>

2. <span data-ttu-id="6e6df-238">Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio pod wywołaniem `BuildAndTrainModel()` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="6e6df-239">Przekształć `splitTestSet` dane, `Evaluate()`dodając następujący kod do:</span><span class="sxs-lookup"><span data-stu-id="6e6df-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="6e6df-240">Poprzedni kod używa [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metoda do przewidywania dla wielu wierszy wejściowych dostarczonych zestawu danych testowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="6e6df-241">Oceń model, dodając następujące jako następny wiersz `Evaluate()` kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="6e6df-242">Po ustawieniu prognozowania`predictions`( ), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia model, który porównuje przewidywane wartości z rzeczywistym `Labels` w zestawie danych testu i zwraca [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiektu na jak model wykonuje.</span><span class="sxs-lookup"><span data-stu-id="6e6df-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="6e6df-243">Wyświetlanie metryk sprawdzania poprawności modelu</span><span class="sxs-lookup"><span data-stu-id="6e6df-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="6e6df-244">Użyj następującego kodu, aby wyświetlić dane:</span><span class="sxs-lookup"><span data-stu-id="6e6df-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="6e6df-245">Metryka `Accuracy` pobiera dokładność modelu, który jest proporcją poprawnych prognoz w zestawie testów.</span><span class="sxs-lookup"><span data-stu-id="6e6df-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="6e6df-246">`AreaUnderRocCurve` Metryka wskazuje, jak pewny siebie model jest poprawnie klasyfikowanie dodatnich i ujemnych klas.</span><span class="sxs-lookup"><span data-stu-id="6e6df-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="6e6df-247">Chcesz być `AreaUnderRocCurve` jak najbliżej jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6e6df-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="6e6df-248">Metryka `F1Score` pobiera wynik F1 modelu, który jest miarą równowagi między [precyzją](../resources/glossary.md#precision) a [przywoływaniem.](../resources/glossary.md#recall)</span><span class="sxs-lookup"><span data-stu-id="6e6df-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="6e6df-249">Chcesz być `F1Score` jak najbliżej jednego, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="6e6df-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="6e6df-250">Przewidywanie wyników danych testowych</span><span class="sxs-lookup"><span data-stu-id="6e6df-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="6e6df-251">Utwórz `UseModelWithSingleItem()` metodę, zaraz `Evaluate()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="6e6df-252">Metoda `UseModelWithSingleItem()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6e6df-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="6e6df-253">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="6e6df-254">Prognozuje tonację na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="6e6df-255">Łączy dane testowe i prognozy do raportowania.</span><span class="sxs-lookup"><span data-stu-id="6e6df-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="6e6df-256">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="6e6df-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="6e6df-257">Dodaj wywołanie do nowej `Main()` metody z metody, bezpośrednio pod wywołaniem `Evaluate()` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="6e6df-258">Dodaj następujący kod, aby utworzyć jako `UseModelWithSingleItem()` pierwszy wiersz w Method:</span><span class="sxs-lookup"><span data-stu-id="6e6df-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="6e6df-259">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest interfejsem API wygody, który umożliwia wykonywanie prognozowania na jednym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="6e6df-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="6e6df-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="6e6df-261">Jest dopuszczalne do użycia w środowiskach jednowątkowych lub prototypowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="6e6df-262">Aby zwiększyć wydajność i bezpieczeństwo wątków `PredictionEnginePool` w środowiskach [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) produkcyjnych, należy użyć usługi, która tworzy obiekty [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do użycia w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e6df-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="6e6df-263">Zobacz ten przewodnik dotyczący [używania `PredictionEnginePool` w ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="6e6df-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e6df-264">`PredictionEnginePool`rozszerzenie usługi jest obecnie w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="6e6df-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="6e6df-265">Dodaj komentarz, aby przetestować przewidywanie uczonego modelu w `UseModelWithSingleItem()` `SentimentData`metodzie, tworząc wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="6e6df-266">Przekaż dane komentarza testu [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) do, dodając następujące jako następne `UseModelWithSingleItem()` wiersze kodu w metodzie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="6e6df-267">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) Funkcja sprawia, że przewidywanie w jednym wierszu danych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="6e6df-268">Wyświetlanie `SentimentText` i odpowiednie przewidywanie tonacji przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="6e6df-269">Użyj modelu do przewidywania</span><span class="sxs-lookup"><span data-stu-id="6e6df-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="6e6df-270">Wdrażanie i przewidywanie elementów wsadowych</span><span class="sxs-lookup"><span data-stu-id="6e6df-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="6e6df-271">Utwórz `UseModelWithBatchItems()` metodę, zaraz `UseModelWithSingleItem()` po metodzie, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="6e6df-272">Metoda `UseModelWithBatchItems()` wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6e6df-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="6e6df-273">Tworzy dane testu wsadowego.</span><span class="sxs-lookup"><span data-stu-id="6e6df-273">Creates batch test data.</span></span>
    - <span data-ttu-id="6e6df-274">Prognozuje tonację na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="6e6df-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="6e6df-275">Łączy dane testowe i prognozy do raportowania.</span><span class="sxs-lookup"><span data-stu-id="6e6df-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="6e6df-276">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="6e6df-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="6e6df-277">Dodaj wywołanie do nowej `Main` metody z metody, bezpośrednio pod wywołaniem `UseModelWithSingleItem()` metody, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="6e6df-278">Dodaj kilka komentarzy, aby przetestować przewidywania modelu `UseModelWithBatchItems()` uczonego w metodzie:</span><span class="sxs-lookup"><span data-stu-id="6e6df-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="6e6df-279">Przewidywanie tonacji komentarzy</span><span class="sxs-lookup"><span data-stu-id="6e6df-279">Predict comment sentiment</span></span>

<span data-ttu-id="6e6df-280">Model służy do przewidywania tonacji danych komentarzy przy użyciu metody [Transform():](xref:Microsoft.ML.ITransformer.Transform%2A)</span><span class="sxs-lookup"><span data-stu-id="6e6df-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="6e6df-281">Łączenie i wyświetlanie prognoz</span><span class="sxs-lookup"><span data-stu-id="6e6df-281">Combine and display the predictions</span></span>

<span data-ttu-id="6e6df-282">Utwórz nagłówek dla prognoz przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="6e6df-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="6e6df-283">Ponieważ `SentimentPrediction` jest dziedziczona `SentimentData` `Transform()` z `SentimentText` metody wypełnionej przewidywanymi polami.</span><span class="sxs-lookup"><span data-stu-id="6e6df-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="6e6df-284">W miarę procesów ML.NET procesów każdy składnik dodaje kolumny, co ułatwia wyświetlanie wyników:</span><span class="sxs-lookup"><span data-stu-id="6e6df-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="6e6df-285">Wyniki</span><span class="sxs-lookup"><span data-stu-id="6e6df-285">Results</span></span>

<span data-ttu-id="6e6df-286">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="6e6df-286">Your results should be similar to the following.</span></span> <span data-ttu-id="6e6df-287">Podczas przetwarzania są wyświetlane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="6e6df-287">During processing, messages are displayed.</span></span> <span data-ttu-id="6e6df-288">Mogą być widoczne ostrzeżenia lub przetwarzania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6e6df-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="6e6df-289">Zostały one usunięte z następujących wyników dla jasności.</span><span class="sxs-lookup"><span data-stu-id="6e6df-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="6e6df-290">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="6e6df-290">Congratulations!</span></span> <span data-ttu-id="6e6df-291">Pomyślnie zbudowano model uczenia maszynowego do klasyfikowania i przewidywania tonacji wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6e6df-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="6e6df-292">Tworzenie udanych modeli jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="6e6df-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="6e6df-293">Ten model ma początkową niższą jakość, ponieważ samouczek używa małych zestawów danych, aby zapewnić szybkie szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="6e6df-294">Jeśli nie jesteś zadowolony z jakości modelu, można spróbować go poprawić, zapewniając większe zestawy danych szkoleniowych lub wybierając różne algorytmy szkoleniowe z różnymi [hiper-parametrów](../resources/glossary.md#hyperparameter) dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="6e6df-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="6e6df-295">Kod źródłowy tego samouczka można znaleźć w repozytorium [dotnet/samples.](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis)</span><span class="sxs-lookup"><span data-stu-id="6e6df-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6e6df-296">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6e6df-296">Next steps</span></span>

<span data-ttu-id="6e6df-297">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6e6df-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6e6df-298">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="6e6df-298">Create a console application</span></span>
> - <span data-ttu-id="6e6df-299">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-299">Prepare data</span></span>
> - <span data-ttu-id="6e6df-300">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="6e6df-300">Load the data</span></span>
> - <span data-ttu-id="6e6df-301">Zbuduj i trenuj model</span><span class="sxs-lookup"><span data-stu-id="6e6df-301">Build and train the model</span></span>
> - <span data-ttu-id="6e6df-302">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="6e6df-302">Evaluate the model</span></span>
> - <span data-ttu-id="6e6df-303">Użyj modelu, aby dokonać prognozowania</span><span class="sxs-lookup"><span data-stu-id="6e6df-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="6e6df-304">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="6e6df-304">See the results</span></span>

<span data-ttu-id="6e6df-305">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="6e6df-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="6e6df-306">Klasyfikacja problemów</span><span class="sxs-lookup"><span data-stu-id="6e6df-306">Issue Classification</span></span>](github-issue-classification.md)
