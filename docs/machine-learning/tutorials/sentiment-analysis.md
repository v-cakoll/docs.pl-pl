---
title: 'Samouczek: Analizowanie komentarze witryny sieci Web — Klasyfikacja binarna'
description: Ten samouczek pokazuje, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonacji z witryny sieci Web, komentarze i podejmuje odpowiednie działanie. Klasyfikator binarny wskaźniki nastrojów klientów używa C# w programie Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a766d95c62fd3a89e3291e1ab803f5222fac46ea
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306169"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="bb08e-104">Samouczek: Analizowanie opinii komentarze witryny sieci Web przy użyciu klasyfikacji binarnej w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="bb08e-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="bb08e-105">Ten samouczek pokazuje, jak utworzyć aplikację konsoli .NET Core, która klasyfikuje tonacji z witryny sieci Web, komentarze i podejmuje odpowiednie działanie.</span><span class="sxs-lookup"><span data-stu-id="bb08e-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="bb08e-106">Klasyfikator binarny wskaźniki nastrojów klientów używa C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bb08e-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="bb08e-107">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bb08e-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bb08e-108">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="bb08e-108">Create a console application</span></span>
> * <span data-ttu-id="bb08e-109">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-109">Prepare data</span></span>
> * <span data-ttu-id="bb08e-110">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-110">Load the data</span></span>
> * <span data-ttu-id="bb08e-111">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-111">Build and train the model</span></span>
> * <span data-ttu-id="bb08e-112">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-112">Evaluate the model</span></span>
> * <span data-ttu-id="bb08e-113">Użyj modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="bb08e-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="bb08e-114">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="bb08e-114">See the results</span></span>

<span data-ttu-id="bb08e-115">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="bb08e-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb08e-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bb08e-116">Prerequisites</span></span>

* <span data-ttu-id="bb08e-117">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core"</span><span class="sxs-lookup"><span data-stu-id="bb08e-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="bb08e-118">[Zdania etykietą tonacji na zestaw danych](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (plik ZIP)</span><span class="sxs-lookup"><span data-stu-id="bb08e-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="bb08e-119">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="bb08e-119">Create a console application</span></span>

1. <span data-ttu-id="bb08e-120">Tworzenie **aplikacji konsoli .NET Core** o nazwie "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="bb08e-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="bb08e-121">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="bb08e-122">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="bb08e-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="bb08e-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="bb08e-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="bb08e-124">Wybierz pozycję "nuget.org" jako źródło pakietu, a następnie wybierz **Przeglądaj** kartę. Wyszukaj **Microsoft.ML**, wybierz pakiet, a następnie wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bb08e-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="bb08e-125">Kontynuuj instalację poprzez zgodę na postanowienia licencyjne dla pakietów, które wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="bb08e-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="bb08e-126">Tym samym **Microsoft.ML.FastTree** pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="bb08e-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="bb08e-127">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="bb08e-128">Zestawy danych, w tym samouczku są z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="bb08e-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="bb08e-129">Al.</span><span class="sxs-lookup"><span data-stu-id="bb08e-129">al,.</span></span> <span data-ttu-id="bb08e-130">KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="bb08e-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="bb08e-131">UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="bb08e-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="bb08e-132">Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.</span><span class="sxs-lookup"><span data-stu-id="bb08e-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="bb08e-133">Pobierz [pliku ZIP zestawu danych zdania etykietą tonacji UCI](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go.</span><span class="sxs-lookup"><span data-stu-id="bb08e-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="bb08e-134">Kopiuj `yelp_labelled.txt` mezzanine do *danych* katalog został utworzony.</span><span class="sxs-lookup"><span data-stu-id="bb08e-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="bb08e-135">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bb08e-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="bb08e-136">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="bb08e-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="bb08e-137">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="bb08e-137">Create classes and define paths</span></span>

1. <span data-ttu-id="bb08e-138">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="bb08e-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="bb08e-139">Utwórz dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="bb08e-140">`_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="bb08e-141">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="bb08e-142">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić ścieżki:</span><span class="sxs-lookup"><span data-stu-id="bb08e-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="bb08e-143">Następnie utwórz klasy danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="bb08e-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="bb08e-144">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="bb08e-145">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="bb08e-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="bb08e-146">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="bb08e-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="bb08e-147">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bb08e-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="bb08e-148">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="bb08e-149">Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="bb08e-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="bb08e-150">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="bb08e-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="bb08e-151">Jak przygotowano danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-151">How the data was prepared</span></span>
<span data-ttu-id="bb08e-152">Klasa wejściowy zestaw danych `SentimentData`, ma `string` dla komentarzy do użytkownika (`SentimentText`) i `bool` (`Sentiment`) wartość 1 (pozytywna) lub 0 (negatywna) wskaźniki nastrojów klientów.</span><span class="sxs-lookup"><span data-stu-id="bb08e-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="bb08e-153">Oba pola mają [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybuty do nich dołączone, która opisuje kolejność plików danych każdego pola.</span><span class="sxs-lookup"><span data-stu-id="bb08e-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="bb08e-154">Ponadto `Sentiment` właściwość ma [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atrybutu, aby uczynić go `Label` pola.</span><span class="sxs-lookup"><span data-stu-id="bb08e-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="bb08e-155">Następujący przykład pliku nie ma wiersz nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="bb08e-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="bb08e-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="bb08e-156">SentimentText</span></span>                         |<span data-ttu-id="bb08e-157">Wskaźniki nastrojów klientów (etykieta)</span><span class="sxs-lookup"><span data-stu-id="bb08e-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="bb08e-158">Waitress była nieco wolno w usłudze.</span><span class="sxs-lookup"><span data-stu-id="bb08e-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="bb08e-159">0</span><span class="sxs-lookup"><span data-stu-id="bb08e-159">0</span></span>     |
|<span data-ttu-id="bb08e-160">Skórki nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="bb08e-160">Crust is not good.</span></span>                    |    <span data-ttu-id="bb08e-161">0</span><span class="sxs-lookup"><span data-stu-id="bb08e-161">0</span></span>     |
|<span data-ttu-id="bb08e-162">WOW... Pracowałem z tego miejsca.</span><span class="sxs-lookup"><span data-stu-id="bb08e-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="bb08e-163">1</span><span class="sxs-lookup"><span data-stu-id="bb08e-163">1</span></span>     |
|<span data-ttu-id="bb08e-164">Usługa była bardzo szybkie.</span><span class="sxs-lookup"><span data-stu-id="bb08e-164">Service was very prompt.</span></span>              |    <span data-ttu-id="bb08e-165">1</span><span class="sxs-lookup"><span data-stu-id="bb08e-165">1</span></span>     |

<span data-ttu-id="bb08e-166">`SentimentPrediction` Klasa prognozowania służy po szkoleń modelowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-166">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="bb08e-167">Dziedziczy `SentimentData` do wyświetlania `SentimentText` z prognozy.</span><span class="sxs-lookup"><span data-stu-id="bb08e-167">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="bb08e-168">`SentimentPrediction` zawiera pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-168">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="bb08e-169">`Label` Umożliwia tworzenie i uczenie modelu, a także używane z Podziel się z zestawu danych testowych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-169">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="bb08e-170">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="bb08e-170">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="bb08e-171">W wersji ewaluacyjnej są używane dane szkoleniowe, przewidywane wartości i modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-171">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="bb08e-172">[Klasy MLContext](xref:Microsoft.ML.MLContext) stanowi punkt wyjścia dla wszystkich operacji w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="bb08e-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="bb08e-173">Inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="bb08e-174">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bb08e-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="bb08e-175">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-175">Load the data</span></span>
<span data-ttu-id="bb08e-176">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="bb08e-176">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="bb08e-177">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="bb08e-177">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="bb08e-178">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-178">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="bb08e-179">Przygotowywanie aplikacji, a następnie załadować dane:</span><span class="sxs-lookup"><span data-stu-id="bb08e-179">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="bb08e-180">Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="bb08e-180">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="bb08e-181">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-181">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="bb08e-182">Tworzenie `LoadData()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="bb08e-183">`LoadData()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="bb08e-183">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="bb08e-184">Służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-184">Loads the data.</span></span>
    * <span data-ttu-id="bb08e-185">Dzieli załadowanego zestawu danych na szkolenie i testowanie zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-185">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="bb08e-186">Zwraca podziału nauczenia i przetestowania zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-186">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="bb08e-187">Dodaj następujący kod jako pierwsza linia `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-187">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="bb08e-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="bb08e-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="bb08e-189">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="bb08e-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="bb08e-190">Podziel zestaw danych dla modelu, szkolenia i testowania</span><span class="sxs-lookup"><span data-stu-id="bb08e-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="bb08e-191">Podczas przygotowywania modelu, użyjesz część zestawu danych do nauczenia go, a część zestawu danych, aby przetestować dokładność modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-191">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="bb08e-192">Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod w następnym wierszu `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="bb08e-193">W poprzednim kodzie użyto [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metodę, aby podzielić załadowanego zestawu danych na szkolenie i testowanie zestawy danych i zwraca je w [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) klasy.</span><span class="sxs-lookup"><span data-stu-id="bb08e-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="bb08e-194">Ustawienia testu procent danych za pomocą `testFraction`parametru.</span><span class="sxs-lookup"><span data-stu-id="bb08e-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="bb08e-195">Wartość domyślna wynosi 10%, w tym przypadku używasz 20% do oceny większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-195">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="bb08e-196">Zwróć `splitDataView` na końcu `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="bb08e-197">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-197">Build and train the model</span></span>

1. <span data-ttu-id="bb08e-198">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="bb08e-199">`BuildAndTrainModel()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="bb08e-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="bb08e-200">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="bb08e-200">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="bb08e-201">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-201">Trains the model.</span></span>
    * <span data-ttu-id="bb08e-202">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-202">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="bb08e-203">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-203">Returns the model.</span></span>

2. <span data-ttu-id="bb08e-204">Tworzenie `BuildAndTrainModel()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="bb08e-205">Wyodrębnianie i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-205">Extract and transform the data</span></span>

1. <span data-ttu-id="bb08e-206">Wywołaj `FeaturizeText` jako następnego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-206">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="bb08e-207">`FeaturizeText()` Metoda w poprzednim kodzie Konwertuje kolumny tekstowej (`SentimentText`) na typ liczbowy klucza `Features` kolumny używane przez algorytmu uczenia maszynowego i dodaje go jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="bb08e-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="bb08e-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="bb08e-208">SentimentText</span></span>                         |<span data-ttu-id="bb08e-209">wskaźniki nastrojów klientów</span><span class="sxs-lookup"><span data-stu-id="bb08e-209">Sentiment</span></span> |<span data-ttu-id="bb08e-210">Funkcje</span><span class="sxs-lookup"><span data-stu-id="bb08e-210">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="bb08e-211">Waitress była nieco wolno w usłudze.</span><span class="sxs-lookup"><span data-stu-id="bb08e-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="bb08e-212">0</span><span class="sxs-lookup"><span data-stu-id="bb08e-212">0</span></span>     |<span data-ttu-id="bb08e-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="bb08e-213">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="bb08e-214">Skórki nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="bb08e-214">Crust is not good.</span></span>                    |    <span data-ttu-id="bb08e-215">0</span><span class="sxs-lookup"><span data-stu-id="bb08e-215">0</span></span>     |<span data-ttu-id="bb08e-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="bb08e-216">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="bb08e-217">WOW... Pracowałem z tego miejsca.</span><span class="sxs-lookup"><span data-stu-id="bb08e-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="bb08e-218">1</span><span class="sxs-lookup"><span data-stu-id="bb08e-218">1</span></span>     |<span data-ttu-id="bb08e-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="bb08e-219">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="bb08e-220">Usługa była bardzo szybkie.</span><span class="sxs-lookup"><span data-stu-id="bb08e-220">Service was very prompt.</span></span>              |    <span data-ttu-id="bb08e-221">1</span><span class="sxs-lookup"><span data-stu-id="bb08e-221">1</span></span>     |<span data-ttu-id="bb08e-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="bb08e-222">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="bb08e-223">Dodaj algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="bb08e-223">Add a learning algorithm</span></span>

<span data-ttu-id="bb08e-224">Ta aplikacja używa algorytm klasyfikacji, który kategoryzuje elementy lub wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-224">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="bb08e-225">Aplikacja kategoryzuje komentarze witryny sieci Web jako dodatnie lub ujemne, a więc zadanie klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="bb08e-225">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="bb08e-226">Dołącz zadanie uczenia maszynowego z definicjami przekształcania danych, dodając następujące jako następnego wiersza kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="bb08e-226">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="bb08e-227">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) to algorytm klasyfikacji szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bb08e-227">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="bb08e-228">To jest dołączany do `estimator` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-228">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="bb08e-229">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-229">Train the model</span></span>

<span data-ttu-id="bb08e-230">Dopasuj do modelu `splitTrainSet` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-230">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="bb08e-231">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="bb08e-231">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="bb08e-232">Zwraca czy model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="bb08e-232">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="bb08e-233">Zwraca model na końcu `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-233">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="bb08e-234">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-234">Evaluate the model</span></span>

<span data-ttu-id="bb08e-235">Po model jest uczony, za pomocą testu danych sprawdź poprawność wydajności modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-235">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="bb08e-236">Tworzenie `Evaluate()` metody tuż za `BuildAndTrainModel()`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-236">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="bb08e-237">`Evaluate()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="bb08e-237">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="bb08e-238">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-238">Loads the test dataset.</span></span>
    * <span data-ttu-id="bb08e-239">Tworzy ewaluatora BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="bb08e-239">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="bb08e-240">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="bb08e-240">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="bb08e-241">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="bb08e-241">Displays the metrics.</span></span>

2. <span data-ttu-id="bb08e-242">Dodaj wywołanie do nowej metody z `Main()` metody, po prawej stronie w obszarze `BuildAndTrainModel()` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-242">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="bb08e-243">Przekształcanie `splitTestSet` danych przez dodanie poniższego kodu `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="bb08e-243">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="bb08e-244">W poprzednim kodzie użyto [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metodę, aby tworzyć prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="bb08e-244">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="bb08e-245">Ocena modelu przez dodanie poniższego jako następnego wiersza kodu w `Evaluate()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-245">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="bb08e-246">Po utworzeniu prognozowania, ustaw (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` zestawu danych testowych i zwraca [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiekt jak działa model.</span><span class="sxs-lookup"><span data-stu-id="bb08e-246">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="bb08e-247">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-247">Displaying the metrics for model validation</span></span>

<span data-ttu-id="bb08e-248">Użyj poniższego kodu, aby wyświetlić metryki:</span><span class="sxs-lookup"><span data-stu-id="bb08e-248">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="bb08e-249">`Accuracy` Metryki pobiera dokładności modelu, część poprawne prognozy w zestawie testów.</span><span class="sxs-lookup"><span data-stu-id="bb08e-249">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="bb08e-250">`AreaUnderRocCurve` Metryka wskazuje, jak pewność modelu jest poprawnie klasyfikowania klasy dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="bb08e-250">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="bb08e-251">Chcesz `AreaUnderRocCurve` sposób maksymalnie zbliżony jeden, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="bb08e-251">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="bb08e-252">`F1Score` Metryki pobiera wynik F1 modelu, który jest miarą równowagi między [dokładności](../resources/glossary.md#precision) i [odwołania](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="bb08e-252">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="bb08e-253">Chcesz `F1Score` sposób maksymalnie zbliżony jeden, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="bb08e-253">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="bb08e-254">Przewidywanie wyników danych testowych</span><span class="sxs-lookup"><span data-stu-id="bb08e-254">Predict the test data outcome</span></span>

1. <span data-ttu-id="bb08e-255">Tworzenie `UseModelWithSingleItem()` metody tuż za `Evaluate()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-255">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="bb08e-256">`UseModelWithSingleItem()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="bb08e-256">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="bb08e-257">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-257">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="bb08e-258">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-258">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="bb08e-259">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="bb08e-259">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="bb08e-260">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="bb08e-260">Displays the predicted results.</span></span>

2. <span data-ttu-id="bb08e-261">Dodaj wywołanie do nowej metody z `Main()` metody, po prawej stronie w obszarze `Evaluate()` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-261">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="bb08e-262">Dodaj następujący kod do utworzenia jako pierwszy wiersz w `UseModelWithSingleItem()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-262">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="bb08e-263">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać, a następnie wykonaj prognozowania w pojedynczym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-263">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="bb08e-264">Dodaj komentarz do testowania uczonego modelu prognozowania w `UseModelWithSingleItem()` metody przez utworzenie wystąpienia `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="bb08e-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="bb08e-265">Przekaż dane komentarz testu do `Prediction Engine` przez dodanie poniższego jako z następującymi wierszami kodu w `UseModelWithSingleItem()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-265">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="bb08e-266">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognoz na pojedynczy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="bb08e-267">Wyświetlanie `SentimentText` i odpowiednie wskaźniki nastrojów klientów przewidywania, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="bb08e-268">Użyj modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="bb08e-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="bb08e-269">Wdrażanie i przewidywanie elementów usługi batch</span><span class="sxs-lookup"><span data-stu-id="bb08e-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="bb08e-270">Tworzenie `UseModelWithBatchItems()` metody tuż za `UseModelWithSingleItem()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="bb08e-271">`UseModelWithBatchItems()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="bb08e-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="bb08e-272">Tworzy dane testowe usługi batch.</span><span class="sxs-lookup"><span data-stu-id="bb08e-272">Creates batch test data.</span></span>
    * <span data-ttu-id="bb08e-273">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="bb08e-273">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="bb08e-274">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="bb08e-274">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="bb08e-275">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="bb08e-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="bb08e-276">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `UseModelWithSingleItem()` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="bb08e-277">Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `UseModelWithBatchItems()` metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="bb08e-278">Przewidywanie tonacji komentarz</span><span class="sxs-lookup"><span data-stu-id="bb08e-278">Predict comment sentiment</span></span>

<span data-ttu-id="bb08e-279">Zastosowanie modelu do prognozowania, komentarz dane opinii za pomocą [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="bb08e-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="bb08e-280">Łączenie i wyświetlanie prognozy</span><span class="sxs-lookup"><span data-stu-id="bb08e-280">Combine and display the predictions</span></span>

<span data-ttu-id="bb08e-281">Utwórz nagłówek dla prognoz, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bb08e-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="bb08e-282">Ponieważ `SentimentPrediction` jest dziedziczony z `SentimentData`, `Transform()` metoda wypełnione `SentimentText` z polami przewidywane.</span><span class="sxs-lookup"><span data-stu-id="bb08e-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="bb08e-283">Zgodnie z procesu strukturze ML.NET przetwarza, każdy składnik dodaje kolumn i dzięki temu można łatwo wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="bb08e-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="bb08e-284">Wyniki</span><span class="sxs-lookup"><span data-stu-id="bb08e-284">Results</span></span>

<span data-ttu-id="bb08e-285">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="bb08e-285">Your results should be similar to the following.</span></span> <span data-ttu-id="bb08e-286">Podczas przetwarzania, komunikaty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="bb08e-286">During processing, messages are displayed.</span></span> <span data-ttu-id="bb08e-287">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="bb08e-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="bb08e-288">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="bb08e-288">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="bb08e-289">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="bb08e-289">Congratulations!</span></span> <span data-ttu-id="bb08e-290">Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="bb08e-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="bb08e-291">Tworzenie modeli pomyślne jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="bb08e-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="bb08e-292">Ten model jest początkowa niższa jakość samouczek używa małych zestawów danych na przeszkolenie szybkiego modelu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="bb08e-293">Jeśli nie jesteś zadowolony z jakość modelu, możesz spróbować ją ulepszyć, dostarczając większych zestawów danych szkoleniowych lub wybierając inną szkolenia algorytmów z różnymi [hiper parametrami](../resources/glossary.md##hyperparameter) dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="bb08e-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="bb08e-294">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="bb08e-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb08e-295">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="bb08e-295">Next steps</span></span>

<span data-ttu-id="bb08e-296">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bb08e-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bb08e-297">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="bb08e-297">Create a console application</span></span>
> * <span data-ttu-id="bb08e-298">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-298">Prepare data</span></span>
> * <span data-ttu-id="bb08e-299">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="bb08e-299">Load the data</span></span>
> * <span data-ttu-id="bb08e-300">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-300">Build and train the model</span></span>
> * <span data-ttu-id="bb08e-301">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="bb08e-301">Evaluate the model</span></span>
> * <span data-ttu-id="bb08e-302">Użyj modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="bb08e-302">Use the model to make a prediction</span></span>
> * <span data-ttu-id="bb08e-303">Zobacz wyniki</span><span class="sxs-lookup"><span data-stu-id="bb08e-303">See the results</span></span>

<span data-ttu-id="bb08e-304">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="bb08e-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="bb08e-305">Klasyfikacja problemu</span><span class="sxs-lookup"><span data-stu-id="bb08e-305">Issue Classification</span></span>](github-issue-classification.md)
