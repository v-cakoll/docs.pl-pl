---
title: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji
description: Dowiedz się, jak używać strukturze ML.NET w scenariuszu klasyfikacji binarnej zrozumienie, jak na potrzeby prognozowania tonacji podjąć odpowiednie działania.
ms.date: 04/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 9b07668f19219040ea5a4dbfd7f175088f38357d
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808240"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="892a1-103">Samouczek: Użyj strukturze ML.NET w scenariuszu klasyfikacji binarnej analizy tonacji</span><span class="sxs-lookup"><span data-stu-id="892a1-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="892a1-104">Ten przykładowy samouczek przedstawia tworzenie klasyfikatora tonacji uzyskiwania opinii przychodzących komentarze witryny sieci Web, aby podjąć odpowiednie działania, za pośrednictwem używany aplikację konsoli .NET Core przy użyciu strukturze ML.NET C# w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="892a1-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to understand sentiment of incoming website comments to take the appropriate action via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="892a1-105">W środowisku usługi machine learning tego rodzaju prognozowania nosi nazwę klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="892a1-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="892a1-106">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="892a1-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="892a1-107">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="892a1-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="892a1-108">Obecnie używasz tego samouczka, a powiązane próbki **(wersja zapoznawcza) w strukturze ML.NET wersji 1.0.0**.</span><span class="sxs-lookup"><span data-stu-id="892a1-108">This tutorial and related sample are currently using **ML.NET version 1.0.0 preview**.</span></span> <span data-ttu-id="892a1-109">Aby uzyskać więcej informacji, zobacz informacje o wersji w [dotnet/machinelearning repozytorium GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="892a1-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="892a1-110">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="892a1-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="892a1-111">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="892a1-111">Understand the problem</span></span>
> * <span data-ttu-id="892a1-112">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="892a1-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="892a1-113">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="892a1-113">Prepare your data</span></span>
> * <span data-ttu-id="892a1-114">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="892a1-114">Transform the data</span></span>
> * <span data-ttu-id="892a1-115">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-115">Train the model</span></span>
> * <span data-ttu-id="892a1-116">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-116">Evaluate the model</span></span>
> * <span data-ttu-id="892a1-117">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-117">Predict with the trained model</span></span>
> * <span data-ttu-id="892a1-118">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-118">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="892a1-119">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="892a1-119">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="892a1-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="892a1-120">Prerequisites</span></span>

* <span data-ttu-id="892a1-121">[Visual Studio 2017 15.6 lub nowszym](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="892a1-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="892a1-122">Plik zip zdania etykietą tonacji na zestaw danych</span><span class="sxs-lookup"><span data-stu-id="892a1-122">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="create-a-console-application"></a><span data-ttu-id="892a1-123">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="892a1-123">Create a console application</span></span>

1. <span data-ttu-id="892a1-124">Tworzenie **aplikacji konsoli .NET Core** o nazwie "SentimentAnalysis".</span><span class="sxs-lookup"><span data-stu-id="892a1-124">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="892a1-125">Utwórz katalog o nazwie *danych* w projekcie, aby zapisać pliki zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-125">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="892a1-126">Zainstaluj **pakietu NuGet Microsoft.ML**:</span><span class="sxs-lookup"><span data-stu-id="892a1-126">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="892a1-127">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="892a1-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="892a1-128">Wybierz pozycję "nuget.org" jako źródło pakietu, wybierz kartę przeglądania, wyszukaj **Microsoft.ML**, a następnie wybierz pakiet z listy i wybierz **zainstalować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="892a1-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="892a1-129">Wybierz **OK** znajdujący się na **podgląd zmian** okna dialogowego, a następnie wybierz **akceptuję** znajdujący się na **akceptacja licencji** okno dialogowe Jeśli możesz Akceptuję postanowienia licencyjne dla pakietów wymienionych.</span><span class="sxs-lookup"><span data-stu-id="892a1-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="892a1-130">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="892a1-130">Prepare your data</span></span>

1. <span data-ttu-id="892a1-131">Pobierz [pliku zip zestawu danych na wskaźniki nastrojów klientów etykietą zdań (patrz cytaty poniżej)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)i Rozpakuj go.</span><span class="sxs-lookup"><span data-stu-id="892a1-131">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="892a1-132">Kopiuj `yelp_labelled.txt` mezzanine do *danych* katalog został utworzony.</span><span class="sxs-lookup"><span data-stu-id="892a1-132">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="892a1-133">Zestawy danych, w tym samouczku są z "From grupy do poszczególnych etykiet korzystanie z funkcji głębokiego" Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="892a1-133">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="892a1-134">Al.</span><span class="sxs-lookup"><span data-stu-id="892a1-134">al,.</span></span> <span data-ttu-id="892a1-135">KDD 2015 i hostowanej na Machine Learning repozytorium — Dua, D. i Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="892a1-135">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="892a1-136">UCI usługi Machine Learning repozytorium [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="892a1-136">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="892a1-137">Irvine, CA: Uniwersytet kalifornijski School informacji i informatyki.</span><span class="sxs-lookup"><span data-stu-id="892a1-137">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="892a1-138">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `yelp_labeled.txt` plik i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="892a1-138">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="892a1-139">W obszarze **zaawansowane**, zmień wartość właściwości **Kopiuj do katalogu wyjściowego** do **Kopiuj Jeśli nowszy**.</span><span class="sxs-lookup"><span data-stu-id="892a1-139">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="892a1-140">Tworzenie klas i definiowania ścieżek</span><span class="sxs-lookup"><span data-stu-id="892a1-140">Create classes and define paths</span></span>

<span data-ttu-id="892a1-141">Dodaj następujące dodatkowe `using` instrukcji na górze *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="892a1-141">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="892a1-142">Należy utworzyć dwa pola globalnego na potrzeby przechowywania ostatnio pobrane dataset ścieżkę pliku i ścieżka pliku zapisanego modelu:</span><span class="sxs-lookup"><span data-stu-id="892a1-142">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="892a1-143">`_dataPath` zawiera ścieżkę do zestawu danych, używane do trenowania modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-143">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="892a1-144">`_modelPath` ma ścieżkę, w którym jest zapisany trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-144">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="892a1-145">Dodaj następujący kod po prawej stronie wiersza powyżej `Main` metodę, aby określić tych ścieżek:</span><span class="sxs-lookup"><span data-stu-id="892a1-145">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="892a1-146">Musisz utworzyć niektóre klasy dla danych wejściowych i prognozy.</span><span class="sxs-lookup"><span data-stu-id="892a1-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="892a1-147">Dodaj nową klasę do projektu:</span><span class="sxs-lookup"><span data-stu-id="892a1-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="892a1-148">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="892a1-148">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="892a1-149">W **Dodaj nowy element** okno dialogowe, wybierz opcję **klasy** i zmień **nazwa** pole *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="892a1-149">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="892a1-150">Następnie wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="892a1-150">Then, select the **Add** button.</span></span>

    <span data-ttu-id="892a1-151">*SentimentData.cs* plik zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="892a1-151">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="892a1-152">Dodaj następujący kod `using` instrukcji na górze *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="892a1-152">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="892a1-153">Usuń istniejącą definicję klasy i Dodaj następujący kod, który zawiera dwie klasy `SentimentData` i `SentimentPrediction`, *SentimentData.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="892a1-153">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="892a1-154">Klasa wejściowy zestaw danych `SentimentData`, ma `string` dla komentarza (`SentimentText`) i `bool` (`Sentiment`) z wartością dla tonacji dodatnie (1) lub fałszywie ujemny (0).</span><span class="sxs-lookup"><span data-stu-id="892a1-154">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive (1) or negative (0).</span></span> <span data-ttu-id="892a1-155">Oba pola mają [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) atrybuty do nich dołączone, która opisuje kolejność plików danych każdego pola.</span><span class="sxs-lookup"><span data-stu-id="892a1-155">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="892a1-156">Ponadto `Sentiment` właściwość ma [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) atrybutu, aby uczynić go `Label` pola.</span><span class="sxs-lookup"><span data-stu-id="892a1-156">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="892a1-157">Następujący przykład pliku nie ma wiersz nagłówka i wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="892a1-157">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="892a1-158">SentimentText</span><span class="sxs-lookup"><span data-stu-id="892a1-158">SentimentText</span></span>                         |<span data-ttu-id="892a1-159">Wskaźniki nastrojów klientów (etykieta)</span><span class="sxs-lookup"><span data-stu-id="892a1-159">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="892a1-160">Waitress była nieco wolno w usłudze.</span><span class="sxs-lookup"><span data-stu-id="892a1-160">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="892a1-161">0</span><span class="sxs-lookup"><span data-stu-id="892a1-161">0</span></span>     |
|<span data-ttu-id="892a1-162">Skórki nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="892a1-162">Crust is not good.</span></span>                    |    <span data-ttu-id="892a1-163">0</span><span class="sxs-lookup"><span data-stu-id="892a1-163">0</span></span>     |
|<span data-ttu-id="892a1-164">WOW... Pracowałem z tego miejsca.</span><span class="sxs-lookup"><span data-stu-id="892a1-164">Wow... Loved this place.</span></span>              |    <span data-ttu-id="892a1-165">1</span><span class="sxs-lookup"><span data-stu-id="892a1-165">1</span></span>     |
|<span data-ttu-id="892a1-166">Usługa była bardzo szybkie.</span><span class="sxs-lookup"><span data-stu-id="892a1-166">Service was very prompt.</span></span>              |    <span data-ttu-id="892a1-167">1</span><span class="sxs-lookup"><span data-stu-id="892a1-167">1</span></span>     |

<span data-ttu-id="892a1-168">`SentimentPrediction` Klasa prognozowania służy po szkoleń modelowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-168">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="892a1-169">Dziedziczy `SentimentData` do wyświetlania `SentimentText` z prognozy.</span><span class="sxs-lookup"><span data-stu-id="892a1-169">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="892a1-170">`SentimentPrediction` zawiera pojedynczy atrybut typu wartość logiczna (`Sentiment`) i `PredictedLabel` `ColumnName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="892a1-170">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="892a1-171">`Label` Umożliwia tworzenie i uczenie modelu, a także używane z Podziel się z zestawu danych testowych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-171">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="892a1-172">`PredictedLabel` Używany podczas prognoz i oceny.</span><span class="sxs-lookup"><span data-stu-id="892a1-172">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="892a1-173">W wersji ewaluacyjnej są używane dane szkoleniowe, przewidywane wartości i modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-173">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="892a1-174">[Klasy MLContext](xref:Microsoft.ML.MLContext) to punkt początkowy dla wszystkich operacji w strukturze ML.NET oraz inicjowanie `mlContext` tworzy nowe środowisko strukturze ML.NET, które mogą być współużytkowane przez obiekty przepływu pracy tworzenia modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-174">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="892a1-175">Przypomina, model `DBContext` platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="892a1-175">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="892a1-176">Inicjowanie zmiennych w głównym oknie</span><span class="sxs-lookup"><span data-stu-id="892a1-176">Initialize variables in Main</span></span>

<span data-ttu-id="892a1-177">Zastąp `Console.WriteLine("Hello World!")` linię `Main` metody za pomocą następującego kodu, aby zadeklarować i zainicjować zmienną mlContext:</span><span class="sxs-lookup"><span data-stu-id="892a1-177">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="892a1-178">Dodaj następujący kod jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-178">Add the following as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="892a1-179">`LoadData()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="892a1-179">The `LoadData()` method executes the following tasks:</span></span>

* <span data-ttu-id="892a1-180">Służy do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-180">Loads the data.</span></span>
* <span data-ttu-id="892a1-181">Dzieli załadowanego zestawu danych na szkolenie i testowanie zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-181">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="892a1-182">Zwraca podziału nauczenia i przetestowania zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-182">Returns the split train and test datasets.</span></span>

<span data-ttu-id="892a1-183">Tworzenie `LoadData()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-183">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
public static TrainTestData LoadData(MLContext mlContext)
{

}
```

## <a name="load-the-data"></a><span data-ttu-id="892a1-184">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="892a1-184">Load the data</span></span>

<span data-ttu-id="892a1-185">Dane w strukturze ML.NET jest reprezentowany jako [klasy IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="892a1-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="892a1-186">`IDataView` jest elastyczny i wydajny sposób opisu danych tabelarycznych (liczbowe i tekstowe).</span><span class="sxs-lookup"><span data-stu-id="892a1-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="892a1-187">Dane można załadować z pliku tekstowego lub w czasie rzeczywistym (na przykład SQL bazy danych lub dziennika plików) do `IDataView` obiektu.</span><span class="sxs-lookup"><span data-stu-id="892a1-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>
<span data-ttu-id="892a1-188">Dodaj następujący kod jako pierwsza linia `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-188">Add the following code as the first line of the `LoadData()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="892a1-189">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) definiuje schemat danych i odczytuje w pliku.</span><span class="sxs-lookup"><span data-stu-id="892a1-189">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="892a1-190">Pobiera zmienne ścieżek danych i zwraca `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="892a1-190">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="892a1-191">Podziel zestaw danych dla modelu, szkolenia i testowania</span><span class="sxs-lookup"><span data-stu-id="892a1-191">Split the dataset for model training and testing</span></span>

<span data-ttu-id="892a1-192">Następnie należy zarówno zestaw danych szkoleniowych do nauczenia modelu, jak i zestawy danych testowych do ewaluacji modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-192">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span>

<span data-ttu-id="892a1-193">Aby podzielić dane załadowane do wymaganych zestawów danych, Dodaj następujący kod w następnym wierszu `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-193">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

[!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="892a1-194">W poprzednim kodzie użyto [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metodę, aby podzielić załadowanego zestawu danych na szkolenie i testowanie zestawy danych i zwraca je w [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) klasy.</span><span class="sxs-lookup"><span data-stu-id="892a1-194">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="892a1-195">Ustawienia testu procent danych za pomocą `testFraction`parametru.</span><span class="sxs-lookup"><span data-stu-id="892a1-195">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="892a1-196">Wartość domyślna wynosi 10%, ale w tym przypadku użyj 20% do oceny większej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-196">The default is 10% but you use 20% in this case to evaluate more data.</span></span>  

<span data-ttu-id="892a1-197">Zwróć `splitDataView` na końcu `LoadData()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-197">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

[!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="892a1-198">Tworzenie i trenowanie modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-198">Build and train the model</span></span>

<span data-ttu-id="892a1-199">Dodaj następujące wywołanie do `BuildAndTrainModel`metodę jako następnego wiersza kodu w `Main()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-199">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="892a1-200">`BuildAndTrainModel()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="892a1-200">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="892a1-201">Wyodrębnia i przekształca dane.</span><span class="sxs-lookup"><span data-stu-id="892a1-201">Extracts and transforms the data.</span></span>
* <span data-ttu-id="892a1-202">Szkolenie modeli modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-202">Trains the model.</span></span>
* <span data-ttu-id="892a1-203">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-203">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="892a1-204">Zwraca wartość modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-204">Returns the model.</span></span>

<span data-ttu-id="892a1-205">Tworzenie `BuildAndTrainModel()` metody tuż za `Main()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-205">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="892a1-206">Wyodrębnianie i przekształcania danych</span><span class="sxs-lookup"><span data-stu-id="892a1-206">Extract and transform the data</span></span>

<span data-ttu-id="892a1-207">Wywołaj `FeaturizeText` jako następnego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-207">Call `FeaturizeText` as the next line of code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

<span data-ttu-id="892a1-208">`FeaturizeText()` Metoda w poprzednim kodzie Konwertuje kolumny tekstowej (`SentimentText`) na typ liczbowy klucza `Features` kolumny używane przez algorytmu uczenia maszynowego i dodaje go jako nowe kolumny zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="892a1-208">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

|<span data-ttu-id="892a1-209">SentimentText</span><span class="sxs-lookup"><span data-stu-id="892a1-209">SentimentText</span></span>                         |<span data-ttu-id="892a1-210">wskaźniki nastrojów klientów</span><span class="sxs-lookup"><span data-stu-id="892a1-210">Sentiment</span></span> |<span data-ttu-id="892a1-211">Funkcje</span><span class="sxs-lookup"><span data-stu-id="892a1-211">Features</span></span>              |
|--------------------------------------|----------|----------------------|
|<span data-ttu-id="892a1-212">Waitress była nieco wolno w usłudze.</span><span class="sxs-lookup"><span data-stu-id="892a1-212">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="892a1-213">0</span><span class="sxs-lookup"><span data-stu-id="892a1-213">0</span></span>     |<span data-ttu-id="892a1-214">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="892a1-214">[0.76, 0.65, 0.44, …]</span></span> |
|<span data-ttu-id="892a1-215">Skórki nie jest dobra.</span><span class="sxs-lookup"><span data-stu-id="892a1-215">Crust is not good.</span></span>                    |    <span data-ttu-id="892a1-216">0</span><span class="sxs-lookup"><span data-stu-id="892a1-216">0</span></span>     |<span data-ttu-id="892a1-217">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="892a1-217">[0.98, 0.43, 0.54, …]</span></span> |
|<span data-ttu-id="892a1-218">WOW... Pracowałem z tego miejsca.</span><span class="sxs-lookup"><span data-stu-id="892a1-218">Wow... Loved this place.</span></span>              |    <span data-ttu-id="892a1-219">1</span><span class="sxs-lookup"><span data-stu-id="892a1-219">1</span></span>     |<span data-ttu-id="892a1-220">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="892a1-220">[0.35, 0.73, 0.46, …]</span></span> |
|<span data-ttu-id="892a1-221">Usługa była bardzo szybkie.</span><span class="sxs-lookup"><span data-stu-id="892a1-221">Service was very prompt.</span></span>              |    <span data-ttu-id="892a1-222">1</span><span class="sxs-lookup"><span data-stu-id="892a1-222">1</span></span>     |<span data-ttu-id="892a1-223">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="892a1-223">[0.39, 0, 0.75, …]</span></span>    |

## <a name="add-a-learning-algorithm"></a><span data-ttu-id="892a1-224">Dodaj algorytmu uczenia</span><span class="sxs-lookup"><span data-stu-id="892a1-224">Add a learning algorithm</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="892a1-225">O zadaniu klasyfikacji</span><span class="sxs-lookup"><span data-stu-id="892a1-225">About the classification task</span></span>

<span data-ttu-id="892a1-226">"Chodzi A lub B?"</span><span class="sxs-lookup"><span data-stu-id="892a1-226">"Is it A or B?"</span></span>

![algorytmu uczenia maszynowego klasyfikacji](./media/sentiment-analysis/classification.png)

<span data-ttu-id="892a1-228">Klasyfikacja jest algorytm uczenia maszynowego, która korzysta z danych do **określić** kategorii, typ lub klasa elementu lub wiersz danych i jest często jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="892a1-228">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="892a1-229">Plik binarny: A i B.</span><span class="sxs-lookup"><span data-stu-id="892a1-229">Binary: either A or B.</span></span>
* <span data-ttu-id="892a1-230">Kontra: wielu kategorii, które można przewidzieć przy użyciu pojedynczego modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-230">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="892a1-231">Ponieważ komentarze witryny sieci Web muszą być klasyfikowane jako dodatnie lub ujemne, możesz użyć zadania klasyfikacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="892a1-231">Because the website comments need to be classified as either positive or negative, you use the Binary Classification task.</span></span>

<span data-ttu-id="892a1-232">Dołącz zadanie uczenia maszynowego z definicjami przekształcania danych, dodając następujące jako następnego wiersza kodu w `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="892a1-232">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="892a1-233">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) to algorytm klasyfikacji szkolenia.</span><span class="sxs-lookup"><span data-stu-id="892a1-233">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="892a1-234">To jest dołączany do `estimator` i akceptuje neural `SentimentText` (`Features`) i `Label` parametrów, aby dowiedzieć się więcej na podstawie historycznych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-234">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="892a1-235">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-235">Train the model</span></span>

<span data-ttu-id="892a1-236">Dopasuj do modelu `splitTrainSet` danych i zwracają uczonego modelu przez dodanie poniższego jako następnego wiersza kodu w `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-236">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="892a1-237">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) metoda szkolenie modeli modelu przekształcania zestawu danych i stosując szkolenia.</span><span class="sxs-lookup"><span data-stu-id="892a1-237">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="892a1-238">Zwraca czy model jest uczony na potrzeby oceny</span><span class="sxs-lookup"><span data-stu-id="892a1-238">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="892a1-239">Zwraca model na końcu `BuildAndTrainModel()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-239">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="892a1-240">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-240">Evaluate the model</span></span>

<span data-ttu-id="892a1-241">Po model jest uczony, należy użyć danych testowych do oceny, jak działa model kontroli jakości i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="892a1-241">After your model is trained, use your test data to evaluate how your model is performing for quality assurance and validation.</span></span> <span data-ttu-id="892a1-242">Tworzenie `Evaluate()` metody tuż za `BuildAndTrainModel()`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-242">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="892a1-243">`Evaluate()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="892a1-243">The `Evaluate()` method executes the following tasks:</span></span>

* <span data-ttu-id="892a1-244">Ładuje zestawy danych testowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-244">Loads the test dataset.</span></span>
* <span data-ttu-id="892a1-245">Tworzy ewaluatora BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="892a1-245">Creates the BinaryClassification evaluator.</span></span>
* <span data-ttu-id="892a1-246">Oblicza model i tworzy metryki.</span><span class="sxs-lookup"><span data-stu-id="892a1-246">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="892a1-247">Przedstawia metryki.</span><span class="sxs-lookup"><span data-stu-id="892a1-247">Displays the metrics.</span></span>

<span data-ttu-id="892a1-248">Dodaj wywołanie do nowej metody z `Main()` metody, po prawej stronie w obszarze `BuildAndTrainModel()` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-248">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="892a1-249">Przekształcanie `splitTestSet` danych przez dodanie poniższego kodu `Evaluate()`:</span><span class="sxs-lookup"><span data-stu-id="892a1-249">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="892a1-250">W poprzednim kodzie użyto [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metodę, aby tworzyć prognozy dla wielu podać wiersze danych wejściowych zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="892a1-250">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="892a1-251">Ocena modelu przez dodanie poniższego jako następnego wiersza kodu w `Evaluate()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-251">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="892a1-252">Po utworzeniu prognozowania, ustaw (`predictions`), [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) metoda ocenia modelu, który porównuje przewidywane wartości z rzeczywistych `Labels` zestawu danych testowych i zwraca [ CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) obiekt jak działa model.</span><span class="sxs-lookup"><span data-stu-id="892a1-252">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="892a1-253">Wyświetlanie metryki dotyczące weryfikacji modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-253">Displaying the metrics for model validation</span></span>

<span data-ttu-id="892a1-254">Użyj poniższego kodu, aby wyświetlić metryki:</span><span class="sxs-lookup"><span data-stu-id="892a1-254">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="892a1-255">`Accuracy` Metryki pobiera dokładności modelu, część poprawne prognozy w zestawie testów.</span><span class="sxs-lookup"><span data-stu-id="892a1-255">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="892a1-256">`AreaUnderRocCurve` Metryka wskazuje, jak pewność modelu jest poprawnie klasyfikowania klasy dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="892a1-256">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="892a1-257">Chcesz `AreaUnderRocCurve` sposób maksymalnie zbliżony jeden, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="892a1-257">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="892a1-258">`F1Score` Metryki pobiera wynik F1 modelu, który jest miarą równowagi między [dokładności](../resources/glossary.md#precision) i [odwołania](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="892a1-258">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="892a1-259">Chcesz `F1Score` sposób maksymalnie zbliżony jeden, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="892a1-259">You want the `F1Score` to be as close to one as possible.</span></span>

## <a name="predict-the-test-data-outcome"></a><span data-ttu-id="892a1-260">Przewidywanie wyników danych testowych</span><span class="sxs-lookup"><span data-stu-id="892a1-260">Predict the test data outcome</span></span>

<span data-ttu-id="892a1-261">Tworzenie `UseModelWithSingleItem()` metody tuż za `Evaluate()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-261">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="892a1-262">`UseModelWithSingleItem()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="892a1-262">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

* <span data-ttu-id="892a1-263">Tworzy pojedynczy komentarz danych testowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-263">Creates a single comment of test data.</span></span>
* <span data-ttu-id="892a1-264">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-264">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="892a1-265">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="892a1-265">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="892a1-266">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="892a1-266">Displays the predicted results.</span></span>

<span data-ttu-id="892a1-267">Dodaj wywołanie do nowej metody z `Main()` metody, po prawej stronie w obszarze `Evaluate()` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-267">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="892a1-268">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) jest wygoda interfejsu API, dzięki czemu można przekazać, a następnie wykonaj prognozowania w pojedynczym wystąpieniu danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-268">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="892a1-269">Dodaj następujący kod do utworzenia jako pierwszy wiersz w `Predict()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-269">add the following code to create as the first line in the `Predict()` Method:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="892a1-270">Dodaj komentarz do testowania uczonego modelu prognozowania w `Predict()` metody przez utworzenie wystąpienia `SentimentData`:</span><span class="sxs-lookup"><span data-stu-id="892a1-270">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

<span data-ttu-id="892a1-271">Przekaż dane komentarz testu do `Prediction Engine` przez dodanie poniższego jako z następującymi wierszami kodu w `UseModelWithSingleItem()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-271">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

<span data-ttu-id="892a1-272">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) funkcja sprawia, że prognoz na pojedynczy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="892a1-272">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

### <a name="use-the-model-prediction"></a><span data-ttu-id="892a1-273">Użyj modelu: prognoz</span><span class="sxs-lookup"><span data-stu-id="892a1-273">Use the model: prediction</span></span>

<span data-ttu-id="892a1-274">Wyświetlanie `SentimentText` i odpowiednie wskaźniki nastrojów klientów przewidywania, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-274">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="892a1-275">Wdrażanie i przewidywanie elementów usługi batch</span><span class="sxs-lookup"><span data-stu-id="892a1-275">Deploy and predict batch items</span></span>

<span data-ttu-id="892a1-276">Tworzenie `UseModelWithBatchItems()` metody tuż za `UseModelWithSingleItem()` metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-276">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

```csharp
public static void UseModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="892a1-277">`UseModelWithBatchItems()` Metoda wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="892a1-277">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

* <span data-ttu-id="892a1-278">Tworzy dane testowe usługi batch.</span><span class="sxs-lookup"><span data-stu-id="892a1-278">Creates batch test data.</span></span>
* <span data-ttu-id="892a1-279">Prognozuje tonacji na podstawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="892a1-279">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="892a1-280">Łączy w sobie testowanie, danych i prognoz dla raportowania.</span><span class="sxs-lookup"><span data-stu-id="892a1-280">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="892a1-281">Wyświetla przewidywane wyniki.</span><span class="sxs-lookup"><span data-stu-id="892a1-281">Displays the predicted results.</span></span>

<span data-ttu-id="892a1-282">Dodaj wywołanie do nowej metody z `Main` metody, po prawej stronie w obszarze `UseModelWithSingleItem()` wywołania metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-282">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

<span data-ttu-id="892a1-283">Dodaj niektóre komentarze, aby przetestować prognozy uczonego modelu w `UseModelWithBatchItems()` metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-283">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="use-the-model-for-prediction"></a><span data-ttu-id="892a1-284">Użyj modelu do prognozowania</span><span class="sxs-lookup"><span data-stu-id="892a1-284">Use the model for prediction</span></span>

<span data-ttu-id="892a1-285">Zastosowanie modelu do prognozowania, komentarz dane opinii za pomocą [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) metody:</span><span class="sxs-lookup"><span data-stu-id="892a1-285">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="892a1-286">Łączenie i wyświetlanie prognozy</span><span class="sxs-lookup"><span data-stu-id="892a1-286">Combine and display the predictions</span></span>

<span data-ttu-id="892a1-287">Utwórz nagłówek dla prognoz, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="892a1-287">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="892a1-288">Ponieważ `SentimentPrediction` odziedziczone `SentimentData`, `Transform()` metoda wypełnione `SentimentText` z polami przewidywane.</span><span class="sxs-lookup"><span data-stu-id="892a1-288">Because `SentimentPrediction` inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="892a1-289">Zgodnie z procesu strukturze ML.NET przetwarza, każdy składnik dodaje kolumn i dzięki temu można łatwo wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="892a1-289">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="892a1-290">Wyniki</span><span class="sxs-lookup"><span data-stu-id="892a1-290">Results</span></span>

<span data-ttu-id="892a1-291">Wyniki powinny być podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="892a1-291">Your results should be similar to the following.</span></span> <span data-ttu-id="892a1-292">Podczas przetwarzania, komunikaty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="892a1-292">During processing, messages are displayed.</span></span> <span data-ttu-id="892a1-293">Może zostać wyświetlony ostrzeżenia lub komunikaty przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="892a1-293">You may see warnings, or processing messages.</span></span> <span data-ttu-id="892a1-294">Te zostały usunięte z następujących wyników dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="892a1-294">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="892a1-295">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="892a1-295">Congratulations!</span></span> <span data-ttu-id="892a1-296">Model uczenia maszynowego dla klasyfikacji i prognozowanie tonacji wiadomości teraz zostały pomyślnie skompilowane.</span><span class="sxs-lookup"><span data-stu-id="892a1-296">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="892a1-297">Tworzenie modeli pomyślne jest procesem iteracyjnym.</span><span class="sxs-lookup"><span data-stu-id="892a1-297">Building successful models is an iterative process.</span></span> <span data-ttu-id="892a1-298">Ten model jest początkowa niższa jakość samouczek używa małych zestawów danych na przeszkolenie szybkiego modelu.</span><span class="sxs-lookup"><span data-stu-id="892a1-298">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="892a1-299">Jeśli nie jesteś zadowolony z jakość modelu, możesz spróbować ją ulepszyć, dostarczając większych zestawów danych szkoleniowych lub wybierając inną szkolenia algorytmów z różnymi [hiper parametrami](../resources/glossary.md##hyperparameter) dla każdego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="892a1-299">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="892a1-300">Kod źródłowy można znaleźć w tym samouczku na [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="892a1-300">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="892a1-301">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="892a1-301">Next steps</span></span>

<span data-ttu-id="892a1-302">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="892a1-302">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="892a1-303">Omówienie problemu</span><span class="sxs-lookup"><span data-stu-id="892a1-303">Understand the problem</span></span>
> * <span data-ttu-id="892a1-304">Wybieranie algorytmu uczenia maszynowego odpowiednie</span><span class="sxs-lookup"><span data-stu-id="892a1-304">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="892a1-305">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="892a1-305">Prepare your data</span></span>
> * <span data-ttu-id="892a1-306">Przekształcanie danych</span><span class="sxs-lookup"><span data-stu-id="892a1-306">Transform the data</span></span>
> * <span data-ttu-id="892a1-307">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-307">Train the model</span></span>
> * <span data-ttu-id="892a1-308">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-308">Evaluate the model</span></span>
> * <span data-ttu-id="892a1-309">Prognozowanie za pomocą uczonego modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-309">Predict with the trained model</span></span>
> * <span data-ttu-id="892a1-310">Wdrażanie i przewidywanie załadować modelu</span><span class="sxs-lookup"><span data-stu-id="892a1-310">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="892a1-311">Przejdź do następnego samouczka, aby dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="892a1-311">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="892a1-312">Klasyfikacja problemu</span><span class="sxs-lookup"><span data-stu-id="892a1-312">Issue Classification</span></span>](github-issue-classification.md)
